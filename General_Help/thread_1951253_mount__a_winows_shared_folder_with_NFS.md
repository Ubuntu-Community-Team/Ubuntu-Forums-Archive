---
title: "mount  a winows shared folder with NFS"
date: 2012-04-02
forum: General Help
---

### Post by tdcarvalho on 2012-04-02
So the situation is this:
I need to backup a VMWare ESXi using a script made by the community. This script can only backup to a remote hosts if it's done by NFS.
The computer I am right now has the IP xxx.xxx.171.55 and the ESXI is ahs the xxx.xxx.171.33
SO i'm performing the tests on my machine since we are on the same IP range.

Here comes the messed up part:

I should backup the ESXi to a USB Disc connected to a windows VM. This Disc has a shared folder which i'm able to mount on my NFS server(ubuntu), but every time i try to mount the folder where the shared folder is i get "access denied". But, if try to mount the same folder without the shared folder mounted in it i do it just fine.

One more thing i belive it is important: if I on my windows server try to access the shared folder by opening the explorer and type "\\IP"  on the address bar i need to authenticate in order to see the folder.

My question is: Am I having problems because of the double authentication?

---

### Post by papibe on 2012-04-02
Hi tdcarvalho. Welcome to the forums!

That sounds like a complicated situation.

Is the Windows VM on your Ubuntu machine?

If you can mount the folder share, why aren't you able to run the script?

Is the target is an external USB hard drive, are you able to mount it directly to the Ubuntu machine?

Regards.

---

