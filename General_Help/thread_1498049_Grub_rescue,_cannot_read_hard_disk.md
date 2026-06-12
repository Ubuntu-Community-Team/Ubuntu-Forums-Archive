---
title: "Grub rescue, cannot read hard disk"
date: 2010-05-31
forum: General Help
---

### Post by ashcarr92 on 2010-05-31
Hello.

Today, I returned to my computer and it had hung. It wasn't doing anything at the time.
After a hard reset, the system failed to boot and dropped me to a grub rescue> prompt.

After a bit of googling, I followed [https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode) and at the
```
insmod /boot/grub/linux.mod
``` it gave me an error, which I cannot remember now. The system then restarted and now I just get 'read error' on boot.

I booted from a liveCD intending to follow
> If still fails...boot up live cd...

at terminal...
sudo grub-setup -d /media/{kubuntu9.10partition}/boot/grub /dev/sda

substitute /media/{kubuntu9.10partition} with actual partition 

If you get error message,(mapping fails), do this..

sudo grub-setup -d /media/{kubuntu9.10partition}/boot/grub -m 
/media/{kubuntu9.10partition}/boot/grub/device.map /dev/sda

All the best!
but my hard drive is unreadable. I try to access it via a fileviewer and get 
'An error occurred while accessing 143.3 GiB Hard Drive', the system responded:' and there is nothing in the /media folder.
Handy.
Plus I can't try the command line because I have no idea what partition the system installation is on. That is probably very dumb of me and easy to find out; my apologies.

I'm not too great with grub and think I've done enough damage as it is.
So, I would really appreciate a way out of this without starting again, as I haven't got a back up of this system and really don't want to loose my data.

I understand more information may be required, I apologize if I haven't provided what is needed. I am actually running Kubuntu, not Ubuntu, but I'm guessing that is irrelevant to this issue, plus I have had good experiences with these forums in the past and would prefer to ask here.
I appreciate your time :)

---

### Post by drs305 on 2010-05-31
ashcarr92, Welcome to the Ubuntu forums!

From the LiveCD, please run the following script and post the results here. Put the contents between "code" tags by clicking the **#** link in the post's menu area.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

This will give us information about your system partitions and boot setup. While your problem may or may not be strictly a Grub problem, this information will help us sort it out.

---

### Post by ashcarr92 on 2010-05-31
Thank you for your reply.

I hate when this happens as  it seems like I'm wasting people's time.

After leaving the system to 'cooldown' for a while, I started it back up. It booted, did a filesystem check, rebooted, and now its fine. Wonderful news, but I apologize for making this thread.

*Does a complete system backup*

---

