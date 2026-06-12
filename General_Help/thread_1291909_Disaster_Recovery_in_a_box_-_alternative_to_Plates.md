---
title: "Disaster Recovery in a box - alternative to Platespin Forge?"
date: 2009-10-15
forum: General Help
---

### Post by bluntknife on 2009-10-15
Hi,

I'm trying to discover whether it is possible to replicate the functionality of Novell's Platespin Forge disaster recovery product.
Forge will allow you to make a copy of live servers (not sure whether this is Wintel and Linux based) and store them locally as virtual machines.  You can also configure the Forge to make periodic backups of the entire server stack so that the Operating System, Application binaries AND data is backed up frequently to the Forge storage.
In the event of a disaster you can perform a V2P, V2V restore of the failed server or just boot the Forge's local copy of the live server and run it from the Forge.  Forge uses an embedded VMware hypervisor for this.

So, using an Ubuntu server is it possible to perform the following?;
1.  Create a virtual machine on the Ubuntu server using a live physical or virtual server as the source.

2.  Schedule the replication of the source server's disks (the data delta, not the entire set of disks each time) to the Ubuntu server.  (wonder if RSYNC can help here or do you need an RSYNC agent or client installed on the source server?!)

3.  Restore the copied VM from the Ubuntu server to a new physical or virtual server.

4.  Bring the copied server online locally within the Ubuntu server if there are no spare servers to restore the copied server image to.

I'd like to try to create the solution above utilising open source (and supported by Canonical) software, where possible.

Ah, and one more requirement / nice to have / would be to manage all of the above from a headless Ubuntu server via some kind of web interface(s).

I really hope the above is possible somehow and many thanks in advance for any input to my project.

Best regards.  :)

---

