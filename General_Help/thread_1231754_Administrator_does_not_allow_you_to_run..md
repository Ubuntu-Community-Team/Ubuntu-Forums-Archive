---
title: "Administrator does not allow you to run."
date: 2009-08-04
forum: General Help
---

### Post by myhelipad on 2009-08-04
Hi,

I just update my ubuntu 9.04 with all current update and Sun VirtualBox to Ver. 3.0.2.

Today when try to browse local 2nd harddisk I got this error:

> Unable to mount Local Disk

DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
trying to configure startup manager also give me an error, with not authorise as me as administrator. 

> Failed to run /usr/sbin/startupmanager as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.try run **groups** command on terminal give me this answer:

> administrator vboxusers
I'm very new to this ubuntu and hope you all can guide hoe to solve this error

Regards

---

### Post by darolu on 2009-08-04
All of this is happening on a virtual machine?

For your second hard drive you may need to edit your fstab file (**if** this is not happening on a virtual machine).

---

