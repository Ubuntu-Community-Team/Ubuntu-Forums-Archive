---
title: "Folder for a remote terminal directory"
date: 2011-06-07
forum: General Help
---

### Post by salmontres on 2011-06-07
Hi guys,

Is there a way to make a folder on my computer to point to a directory in a remote terminal? I want to be able to open it and explore the files like any other folder in a browser without using the terminal.

---

### Post by blueridgedog on 2011-06-07
You will need to share the remote directory via CIFS samba or similar and then mount it locally.

What is the OS of the remote system?

---

### Post by salmontres on 2011-06-07
Thanks for the quick response Blue,

The OS is CentOS, a Red Hat clone. Do I need to install Samba on the remote cluster or do I run it from my local computer?

---

### Post by nothingspecial on 2011-06-07
> **salmontres said:**
> Thanks for the quick response Blue,

The OS is CentOS, a Red Hat clone. Do I need to install Samba on the remote cluster or do I run it from my local computer?

If the both computers are linux, you do not need samba.

Install openssh-server on the remote (or whatever the package is called in centos)

On your ubuntu machine open the file browser and click file > connect to server

Use ssh in the top box.

Fill in the ipadress, username and directory you want to browse (this can be / if you like) then click connect.

If you want to make a bookmark then go ahead.

---

### Post by blueridgedog on 2011-06-07
You will have to install or just setup an already installed SAMBA server on the remote (see [http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/) for example) then use the SAMBA client on your system to mount the share locally.

---

