---
title: "How to set up security for NFS server?"
date: 2010-10-07
forum: General Help
---

### Post by chevelleman71 on 2010-10-07
Hi everyone. I have NFS set up on my file server on my local network. Right now I'm allowing all local IP's. Now I want to be able to access the shares from home, across town. 

Can you secure NFS in any way other than IP restriction, ie. password login? I know I could just use sftp but I want the control and seamlessness of NFS.

Anyone know how to do this or have thoughts suggestions? I'd love to hear them.

Thanks

Luke

---

### Post by dougfractal on 2010-10-07
Could you not just use an ssh tunnel.

Places > Connect to server
service type > ssh

This would open up a nautilus window of your folder which you could bookmark

You would of course need to install openssh (sudo apt-get install openssh-server )and enable port forwarding (22) on the router.


There are other tricks of using fuse to create an entree in /etc/fstab or using -X forwarding too.

---

### Post by chevelleman71 on 2010-10-07
Thanks for the quick reply. 

Isn't that the same as using sftp (via Nautilus)? I really want to use NFS so that I can do things like:

[LIST]
[*]Play music across it
[*]Work any different types of files (photoshop, etc) without having to copy them locally first
[*]See the Nautilus(Gnome?) image thumbnail previews
[/LIST]

Am I making sense about what I want to accomplish? Do you think NFS is the way to go or is there a better way?

Thanks

Luke

---

