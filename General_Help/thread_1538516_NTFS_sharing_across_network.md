---
title: "NTFS sharing across network"
date: 2010-07-25
forum: General Help
---

### Post by Gordon D on 2010-07-25
Hi, I am very new to Ubuntu, so please bear with me!

I have a dual boot PC with an NTFS partition on it that I want to share across the network. It has my music on it which I am going to keep for a while until I find a suitable iTunes replacement.

I also have a server and have mounted those shared ext3 drives ok using NFS and configuring fstab and exports. Works a treat.

With this one, I am getting a error: "ntfs-3g: Failed to access volume '192.168.xx.xx:/nfs/xpdata': No such file or directory" when I try to mount it on the remote client machine. I can access the local mount fine.

Any assistance would be very much appreciated as I am on a very steep learning curve :)

---

### Post by GlazedDonut on 2010-07-25
You should be able to mount the shares just like you would any other NFS share, without using ntfs-3g on the client.

---

### Post by Gordon D on 2010-08-20
Err, yep ... all works fine ... no idea what I was doing!

Thanks for your help.

Gordon

---

### Post by samg34 on 2010-08-20
I think I have a simmaler problem/bug. whenever I access a remote windows filesystem or get files to/from my windows desktop, i get an error, but the files display in the file browser perfectly fine

---

