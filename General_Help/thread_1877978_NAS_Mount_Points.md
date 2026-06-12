---
title: "NAS Mount Points"
date: 2011-11-09
forum: General Help
---

### Post by jamieb22 on 2011-11-09
Hi

I have an application that archives documents to an external mount point. The mount point references a location on a external NAS. The problem I have is that occasionally the connection to the NAS is lost. When this happens, the applications archives documents to local directory where the NAS is mounted. Due to this behaviour, there are now documents archive both locally and remotely. This is not my intention. When the mount point is disconnected, the desired behavior is for Linux to report to the application it does not have sufficient privileges to write to the local directory and its sub-directories. Only when the mount point is connected, should the application have write permissions. Currently the application is running under the ROOT account. I thought about marking the local directory as read only to prevent data from being written locally, but this doesn't seem to help. Are the permissions of the directory changed when the NAS is mounted?  Are there any recommendations on how to prevent an application from writing to the local mount directory when a mount point is disconnected?

Many thanks

Jamie

---

