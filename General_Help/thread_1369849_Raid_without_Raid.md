---
title: "Raid without Raid?"
date: 2010-01-01
forum: General Help
---

### Post by Kumaru on 2010-01-01
Hello,
I've been looking at RAID options for a while but decided it's too much of a hassle/cost to work with. 

At the college I go to, I have a media server connecting my friend over the hamachi VPN. Right now it runs Windows XP, but since I no longer have time for PC gaming I'm planning on switching all of my computers back over to linux. 

I have a terabyte harddive which is nearly full (one of those external USB ones from walmart which has been gutted to an internal drive), and I'm planning on getting another. So my question is, would there be any way for Samba, or any other file manager/sharing system, to combine the contents of two drives into one? 

I have directories for Movies, Music, Games, Anime, TV Shows, and File Storage already being split among the 1T and a 160G, but considering Media takes up the most space, it would overflow from one to the other, making things inconvenient to go through files, even with two 1T drives.

To set up RAID I'd need to find a lot of harddrive space for temp storage, and get some new equipment, and then if I lost one of those drive it would all be ruined, so I'd like to avoid that if possible.

I don't see this as likely, but maybe someone found a way to do this and I'd be missing out on it.

Thanks for your time guys,
K

---

### Post by falconindy on 2010-01-01
What you want isn't RAID. You're just looking for a way to span a bunch of disks together (usually called JBOD). You can "merge" to mounts together using aufs2, but its fairly technical. I'm also not sure if Ubuntu provides the aufs2 module/progs by default. There may be some compiling in your future if you go this route... the eventual entry in your /etc/fstab would be something along the lines of:
```
media    /media   aufs   udba=reval,br:/path/to/media1:/path/to/media2   0 0
```
The two paths specified can be anything: local disks, nfs mounts, samba mounts, sshfs... just as long as its already mounted and accessible via the local filesystem. The path /media will then contain the contents of the 2 paths specified. I would heavily encourage you not to write to this union but rather to make it read only (add 'ro' to the mount options). Otherwise, you can't control where data is written to. Rather, write to the paths used in the Aufs merge.

---

### Post by HiImTye on 2010-01-01
or alternatively you can just use symbolic links for different folders, for instance I have all of my data folders in my home folder symbolically linked to my storage drive and Wine symbolically links to my gaming drive

from nautilus just 'make link' from the right click menu of any folder and move it where you want

---

### Post by Kumaru on 2010-01-01
> **falconindy said:**
> What you want isn't RAID. You're just looking for a way to span a bunch of disks together (usually called JBOD). You can "merge" to mounts together using aufs2, but its fairly technical. I'm also not sure if Ubuntu provides the aufs2 module/progs by default. There may be some compiling in your future if you go this route... the eventual entry in your /etc/fstab would be something along the lines of:
```
media    /media   aufs   udba=reval,br:/path/to/media1:/path/to/media2   0 0
```The two paths specified can be anything: local disks, nfs mounts, samba mounts, sshfs... just as long as its already mounted and accessible via the local filesystem. The path /media will then contain the contents of the 2 paths specified. I would heavily encourage you not to write to this union but rather to make it read only (add 'ro' to the mount options). Otherwise, you can't control where data is written to. Rather, write to the paths used in the Aufs merge.


Thanks man, that sounds like exactly what I'm aiming for! Yes, the media is generally Read Only, besides the Storage directory which I was planning on having as a separate  network drive. I'll start playing around with it in a virtual machine once I get back on campus.

> **HiImTye said:**
> or alternatively you can just use symbolic links for different folders, for instance I have all of my data folders in my home folder symbolically linked to my storage drive and Wine symbolically links to my gaming drive

from nautilus just 'make link' from the right click menu of any folder and move it where you want

That would work, and probably be faster and easier, but then I'd have to continually maintain all of the shortcuts, and I'm not sure if that would effect download-ability at all.

Thanks guys!
K

---

### Post by JohnnyC35 on 2010-03-05
> **HiImTye said:**
> or alternatively you can just use symbolic links for different folders, for instance I have all of my data folders in my home folder symbolically linked to my storage drive and Wine symbolically links to my gaming drive

from nautilus just 'make link' from the right click menu of any folder and move it where you want

Is it at all possible to symlink multiple drives together? I've been Googling and search the forums but I haven't heard of this being possible. It would be great if it could tho :)

I thought I found the answer here (specifically post 13, posted below): [http://ubuntuforums.org/showthread.php?t=1072396&page=2](http://ubuntuforums.org/showthread.php?t=1072396&page=2) but when I try to move files around I just move their symlinks :P   Would be handy after I figured out where everything has to go. My Movies, and Anime directories are a mess :P

> You could of course make a script to run...
btw a little tip with the linking command
(assuming your hard drives are sda, sdb, sdc, sdd all using partition  one)     
Code:     ln -s --target-directory=~/Media /media/sd{a,b,c,d}1/* 
try changing how do you need it...
There is one caveat though... new files you save in ~/Media will end up  on drive where ~/Media is on, of course... always save into those  symlinked folders

I also read about LVM but with lots of files on my drives I would want to wipe them off just to JBOD them together with it.

---

