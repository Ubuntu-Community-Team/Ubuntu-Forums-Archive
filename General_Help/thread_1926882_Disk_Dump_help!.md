---
title: "Disk Dump help!"
date: 2012-02-17
forum: General Help
---

### Post by y2j514 on 2012-02-17
I am trying to recover lost pictures from my iPhone.  I have recently installed Ubuntu 11.10 in order to create a disk dump to try and retrieve the files.

I have followed several tutorials, mainly the following:

[http://www.funkyspacemonkey.com/howto-recover-lost-data-iphone](http://www.funkyspacemonkey.com/howto-recover-lost-data-iphone)
[http://www.ghabuntu.com/2009/09/ifuse-mount-your-iphoneipod-touch-in.html](http://www.ghabuntu.com/2009/09/ifuse-mount-your-iphoneipod-touch-in.html)
[http://ubuntuforums.org/showthread.php?t=1861617](http://ubuntuforums.org/showthread.php?t=1861617)
[http://ubuntuforums.org/showthread.php?t=1627054](http://ubuntuforums.org/showthread.php?t=1627054) 

I want to do what the fellow did in the last link above. 

I am having some major trouble.  I don't want to jailbreak the iPhone due to the fact that installing stuff will decrease my likely hood of being able to successfully recover my photos. So I am trying different things out with my iTouch as the guinea pig first.

Using ifuse I am able to sucessfully mount and navigate through my iTouch, but i can not for the life of me create a dd command.  

I tried **dd if=/dev/disk0 of=iphone-dump.img **but I get an error saying the following:
dd: opening `/dev/disk0': No such file or directory

I have no clue as to what to put for the directory of the iTouch.  It does not appear in disc utility, and i even tried ifuse /mnt/ipod  then dd if= /mnt/ipod but i continue to get the same error.

I jailbroke the iTouch to see if I could have better luck and I ran into many similar problems until I found 
[http://log.ijulien.com/post/182804914/iphone-3gs-data-recovery](http://log.ijulien.com/post/182804914/iphone-3gs-data-recovery)

and this command:
ssh user@iphone-ip dd if=/dev/rdisk0 bs=1M | dd of=iphone-dump.img

It appeared to be working.  But it required the iTouch to be jailbroken.  I tried 
dd if=/dev/rdisk0 bs=1M of=iphone-dump.img and once again no such file or directory.

Any suggestions?  

Any and all help is appreciated!

Thank you.

---

### Post by y2j514 on 2012-02-17
So the iPhone is firmware 3.1 and can not be jailbroken without upgrading the firmware (~700mb).  High likely hood of overwriting my pictures.  So jailbreak is not an option meaning no SSH.

---

