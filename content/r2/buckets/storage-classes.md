---
title: Storage classes
pcx_content_type: how-to
---

# Storage classes

Storage classes allow you to trade off between the cost of storage and the cost of accessing data. Every object stored in R2 has an associated storage class.

All storage classes share the following characteristics:
- Compatible with Workers API, S3 API, and public buckets.
- 99.999999999% (eleven 9s) of annual durability.
- No minimum object size.

## Available storage classes

<table>
  <tbody>
    <th style="width:25%">
      Storage class
    </th>
    <th style="width:25%">
      Minimum storage duration
    </th>
    <th style="width:25%">
      Data retrieval fees (processing)
    </th>
    <th style="width:25%">
      Egress fees (data transfer to Internet)
    </th>
    <tr>
      <td>
        Standard
      </td>
      <td>
        None
      </td>
      <td>
        None
      </td>
      <td>
        None
      </td>
    </tr>
    <tr>
      <td>
        Infrequent Access <inline-pill style="beta" />
      </td>
      <td>
        30 days
      </td>
      <td>
        Yes
      </td>
      <td>
        None
      </td>
    </tr>
  </tbody>
</table>

For more information on how storage classes impact pricing, refer to [Pricing](/r2/pricing/).

### Standard storage

Standard storage is designed for data that is accessed frequently. This is the default storage class for new R2 buckets unless otherwise specified.

#### Example use cases

- Website and application data
- Media content (e.g., images, video)
- Storing large datasets for analysis and processing
- AI training data
- Other workloads involving frequently accessed data

{{<heading-pill style="beta" heading="h3">}}Infrequent Access storage{{</heading-pill>}}

{{<Aside type="note" header="Open Beta">}}

This feature is currently in beta. To report bugs or request features, go to the #r2-storage channel in the [Cloudflare Developer Discord](https://discord.cloudflare.com) or fill out the [feedback form](https://forms.gle/5FqffSHcsL8ifEG8A).

{{</Aside>}}

Infrequent Access storage is ideal for data that is accessed less frequently. This storage class offers lower storage cost compared to Standard storage, but includes [retrieval fees](/r2/pricing/#data-retrieval) and a 30 day [minimum storage duration](/r2/pricing/#minimum-storage-duration) requirement.

{{<Aside type="note">}}

For objects stored in Infrequent Access storage, you will be charged for the object for the minimum storage duration even if the object was deleted, moved, or replaced before the specified duration.

{{</Aside>}}

#### Example use cases

- Long-term data archiving (for example, logs and historical records needed for compliance)
- Data backup and disaster recovery
- Long tail user-generated content

## Set default storage class for buckets

By setting the default storage class for a bucket, all objects uploaded into the bucket will automatically be assigned the selected storage class unless otherwise specified. Default storage class can be changed after bucket creation in the Dashboard.

To learn more about creating R2 buckets, refer to [Create new buckets](/r2/buckets/create-buckets/).

## Set storage class for objects

### Specify storage class during object upload

To learn more about how to specify the storage class for new objects, refer to the [Workers API](/r2/api/workers/) and [S3 API](/r2/api/s3/) documentation.

### Use object lifecycle rules to transition objects to Infrequent Access storage

To learn more about how to transition objects from Standard storage to Infrequent Access storage, refer to [Object lifecycles](/r2/buckets/object-lifecycles/).

