---
title: "Acsess hda1"
date: 2005-02-20
forum: General Help
---

### Post by bossa on 2005-02-20
Hi 
Trying to play Mp3 on my HD using the Live CD and I get this message in Totem: 
Totem could not play 'file:///mnt/hda1/Documents and Settings/Stephen/My Documents/My Music/Thin Lizzy/Wild One (The Very Best Of Thin Lizzy) [UK]/02 Jailbreak.wma'.
Failed to open; reason unknown
New to Linux but I haven't had this on other distros what do I need to do ?
Thanks Steve

---

### Post by Buffalo Soldier on 2005-02-20
**.wma** codecs are non-free. It is Ubuntu's philosophy of being a 100% free (free as in freedom). There for it only supports free software, applications and codecs.

But there is still a way to run non-free multimedia files. Go to [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by I am Jack's username on 2005-02-21
Ubuntu 5.04 array 3.5 live CD i386.

Created a folder called "suse" in /home/ubuntu with the GUI and then ran [COLOR=DarkGreen]mount -r -t ext3 /dev/hda1 /home/ubuntu/suse/[/COLOR] as root from /home/ which reports [COLOR=DarkRed]mount: /dev/hda1 already mounted or /home/ubuntu/suse/ busy[/COLOR].

I get [COLOR=DarkRed]umount: /dev/hda1: not mounted[/COLOR] and lsof doesn't give anything for /dev/hda1 or /home/ubuntu/suse/. 

Any suggestions on how to mount the harddisk?

---

