---
title: "How do you stop bootup Filesystem checking?"
date: 2006-06-13
forum: General Help
---

### Post by gatekeeper on 2006-06-13
I have got a bit of a dodgy disk which will be replaced in a couple of days time, in the mean time I would like to stop it doing a Filesystem check which is now happening everytime I reboot.

Found this:

[http://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/](http://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/)

About the only think that works, but only works once is:
>>
To disable filesystem integrity check for the next bootup, create a file called /fastboot. So a
$sudo touch /fastboot
will disable filesystem check for the next time you bootup.
<<

Control + C then Control + D just causes the machine to reboot then filesystem check.

Tried: tune2fs -c 0 -i 0 /dev/hda2

and still it's doing it. ](*,) 

Please someone tell me how I stop it?

---

### Post by tristan on 2006-06-13
Try this on for size (it works for me):

sudo chmod -x /etc/init.d/checkfs.sh

That should stop the filesystem from being checked every boot.

If you want to turn it back on try :
sudo chmod +x /etc/init.d/checkfs.sh

Hope this helps

---

### Post by gatekeeper on 2006-06-13
[QUOTE=tristan]Try this on for size (it works for me):

sudo chmod -x /etc/init.d/checkfs.sh

That should stop the filesystem from being checked every boot.

If you want to turn it back on try :
sudo chmod +x /etc/init.d/checkfs.sh

Hope this helps[/QUOTE]

Thanks for the suggestion but not even this works, it still comes up "Checking root file system". :-(

---

### Post by Rui Pais on 2006-06-13
[QUOTE=gatekeeper]Tried: tune2fs -c 0 -i 0 /dev/hda2[/QUOTE]

hi, you may try to pass 0 at last field in /etc/fstab, to see if it skips the file check?
like:
/dev/hda2      /     ext3    defaults,noatime 0 **0**

---

### Post by tristan on 2006-06-14
sudo chmod -x /etc/init.d/checkroot.sh will disable checking of the root filesystem.

---

### Post by Rui Pais on 2006-06-14
tristan, gatekeeper already said that change mod of checkroot.sh didn't work...

Anyway if you want knockout checkroot.sh seems better to rm symlink /etc/rcS.d/S20checkroot.sh then make an init.d file non-executable... less radical i mean :)

---

### Post by tristan on 2006-06-14
[QUOTE=Rui Pais]tristan, gatekeeper already said that change mod of checkroot.sh didn't work...
[/QUOTE]

Actually Rui Pais, he said that checkfs.sh didn't work. Checkroot.sh is a different script which checks /, checkfs.sh checks any other partitions. 

Anyway, we'll see how he goes disabling by your method or my method :)

---

### Post by Rui Pais on 2006-06-14
hi tristan, 
yes you are right, gatekeeper said that refering to checkfs.sh, but thats not my point. 

The design of the init process is have a bunch of init scripts and turn it on/off start/kill by make links at etc/rcx.d/. Not a very elegant method, but at least usually works well. Disable mod of init script goes against that design. The correct action is just remove the link from the rc<levelnumber>.d you don't want. 
If one starts to change mod of /etc/init.d scripts (you suggest two, now) he/she may find, after a few month where those little changes are complete forgotten, that something is not behaves like it should and its hard to detect... or some update will reput the executable mod and the problem appears again...

My suggestion (its not a method :lol:) was only based on the fact that strangelly the filesysstem is been checked no matter the definitions of tune2fs. What i found a little weird... here i have the option to make filesystem checks and root checks turned on but it follows very orderly my own definitions of tune2fs.

hope i have explained myself better now :) 
have fun

---

### Post by gatekeeper on 2006-06-14
Thanks folks for all your good ideas, much appreciated, unfortunately I was unable to get any of them to work.

In my original post I said that if you put an empty file /fastboot then it didn't do the filesystem check. So I had an idea of my own.

[Drum role please...]

Here is what you do:

Open a terminal:
cd /home
sudo nano
Ctrl+o /home/fastboot (i.e. save an empty file in you home directory, I suppose you could put it anywhere).

sudo crontab -e

nano fires up so enter the following command and save:

@reboot cp /home/fastboot /

Job done. 

Every time I boot or reboot fastboot is copied to / preventing the root file system check.

This is only a temporary measure until I get a replacement hard disk. Although Linux runs on this HDD, it seems to be too knackered to let me do a backup and use that. grrr!

Anyway that is my solution and it seems to work a treat. :-)

---

### Post by Rui Pais on 2006-06-14
hi gatekeeper,
your problem is a very wierd one... 

Anyway that sounds a good solution.

May i suggest a simpler thing. Replace
@reboot cp /home/fastboot /
by
@reboot touch /fastboot

So you wont need /home/fastboot there or in anyplace else (and no risks of delete it by mistake)

Have fun.

---

### Post by gatekeeper on 2006-06-14
Thanks Rui Pais. 

Hopefully I will get a new replacement HDD next week (it's on order), which I hope Kubuntu Dapper will install onto without any further problems, and then this will all be just a bad dream. :-)

---

### Post by tristan on 2006-06-14
[QUOTE=Rui Pais]hi tristan, 
yes you are right, gatekeeper said that refering to checkfs.sh, but thats not my point. 

The design of the init process is have a bunch of init scripts and turn it on/off start/kill by make links at etc/rcx.d/. Not a very elegant method, but at least usually works well. Disable mod of init script goes against that design. The correct action is just remove the link from the rc<levelnumber>.d you don't want. 
If one starts to change mod of /etc/init.d scripts (you suggest two, now) he/she may find, after a few month where those little changes are complete forgotten, that something is not behaves like it should and its hard to detect... or some update will reput the executable mod and the problem appears again...

My suggestion (its not a method :lol:) was only based on the fact that strangelly the filesysstem is been checked no matter the definitions of tune2fs. What i found a little weird... here i have the option to make filesystem checks and root checks turned on but it follows very orderly my own definitions of tune2fs.

hope i have explained myself better now :) 
have fun[/QUOTE]

Thanks for the explanation Rui Pais. I just suggested the chmod -x method because by default there are already non-executable scripts sitting in init.d (one which cleans the /tmp directory at boot for instance).

Anyway, that's what I like about this forum - there's more than one way to skin a cat and people are happy to share.

---

### Post by Rui Pais on 2006-06-14
[QUOTE=tristan]Anyway, that's what I like about this forum - there's more than one way to skin a cat and people are happy to share.[/QUOTE]
You can say it again! Thats one of the most nice things about using linux :) 

see you around ;) have fun.

---

