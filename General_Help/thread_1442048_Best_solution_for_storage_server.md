---
title: "Best solution for storage server"
date: 2010-03-29
forum: General Help
---

### Post by satjat on 2010-03-29
I am in the proccess of building a storage server, that could be expanded to a cluster structure.
Cluster structure will be used to achieve high availability and data replication with little need for load balancing or huge transfer speeds.
I have been checking out gluster (the storage platform and the glusterfs on ubuntu machines) and I was also wondering if a similar solution could be achieved with ubuntu enterprise cloud.
The total storage is not expected to rise much above 15-20 TB and the total number of servers won't be more than 10. The storage network will be accessed mostly through windows machines, which poses a problem in the high availability field as the cifs or even nfs shares won't reproduce if the main server fails. iSCSI served from 2 machines, while the other 8 deal with the storage looks like a decent redundant solution. I would like to stay away from any striping solution and keep whole files in generic filesystems so that the disks can be mounted on other machines to rescue files if needed.

Still, gluster platform looks promising but maybe glusterfs or a cloud solution could be better... or something else I haven't thought of.

---

