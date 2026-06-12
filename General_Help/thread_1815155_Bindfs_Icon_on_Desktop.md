---
title: "Bindfs Icon on Desktop"
date: 2011-07-30
forum: General Help
---

### Post by Derek Karpinski on 2011-07-30
I have two users on this computer, and I am attempting to create a shared folder for us.  I'm trying to use bindfs.  Everything I try leaves an icon on the Desktop with the mounted folder.  I'd rather not have this folder on the Desktop if possible.

I'm using an external drive for the shared folder.  It is /dev/sdb1.  So, in fstab, I mounted the external drive to '/mnt/Public' because /mnt doesn't show an icon.  Then, I used bindfs to mount /mnt/Public to /home/{user}/Public.

Everything works great that way, and the correct permissions are set, but I have this annoying icon on my desktop, and it's just going to confuse my wife, and I don't really like it anyways.

Suggestions?

:confused:

---

### Post by Derek Karpinski on 2011-07-30
Solved:

-Mount external drive to /mnt/Public in fstab normally.
-bindfs from /mnt/Public to /home/public
-symbolic links from /home/public to /home/derek/Public folder

Seems like a lot of screwing around..........but it works. :D

---

