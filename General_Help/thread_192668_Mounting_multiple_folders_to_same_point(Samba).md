---
title: "Mounting multiple folders to same point(Samba)"
date: 2006-06-09
forum: General Help
---

### Post by woedend on 2006-06-09
Hi, my brother is staying here for a few weeks and I'd like to network us together.  Now, I got samba working great thankfully, and I can see his and he mine.  The problem is, to listen to his music using xmms, I cannot play directly from his computer(xmms doesnt support smb://).  So, I need to mount it using smbfs.  The problem is this - he has 5 separate folders set to share to me.  So I want all 5 folder to show up under my mount point if possible.  As an example, i would use
sudo mount -t smbfs //ROUTERIPADDRESS/Folder1 /media/john
to mount folder1 to media/john which works fine.  What I tried/want to do is just to mount the ip address like this
sudo mount -t smbfs //routeripaddress/ /media/john  
so that all folders show up but this does not work.  So rather than specify 5 different mount points, is what I am doing possible here?
I understand that I could make 5 different subfolders and link each one, but I'd like for it to be more dynamic than that if even possible.  TIA

---

### Post by garyng on 2006-06-09
there is no ready to use way as a share point is a mount point, windows or linux.

But being linux, you can use the power of script. use the "net" command to query the host then mount each share under one roof. call this script "my_mount"

There is actually an alternative(on the windows side), share them through the web server.

---

