---
title: "Computer freezes almost daily - 11.04 Installed"
date: 2011-06-10
forum: General Help
---

### Post by mihalybaci on 2011-06-10
Recently, my wife's desktop has been freezing almost daily, leading to a reboot. It's an HP Pavilion (specs [here]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00783599&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&site=null&key=null&product=3254035")) and it has Ubuntu 11.04 installed since soon after 11.04 came out. There doesn't seem to be really any rhyme or reason to the crashes, except that it might happen more often when she's web browsing with Firefox. I tried looking at /var/log/syslog, but to be honest I wasn't really sure what I was looking for. I did notice that syslog would stop recording at the same time the mouse and keyword freeze. Has any one seen this problem or be able to give me some advice on how to find out what's going on?

Thanks

---

### Post by jramshu on 2011-06-10
A lot of times it's flash eating up the cpu. Run top in terminal and see if that's the cause. If it is flash you will see high cpu usage with "plugin-container."

---

### Post by jim_deadlock on 2011-06-10
My old Dell laptop used to do this, in my case it's a known kernel bug, using an older kernel fixed it.

---

### Post by linuxinstalledfromhdd on 2011-06-10
Try 10.10:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by mihalybaci on 2011-06-11
Hm, okay. I do think that the Firefox issue was a bit of a red herring because this morning she turned on the computer and it froze almost immediately. Then we tried to reboot and it loaded a command line interface with "grub recovery > ", but I don't believe grub is even installed on the computer since Ubuntu is the only OS on the drive. I have been thinking about downgrading that computer to 10.10, but until now it seemed like more hassle than it was worth.

---

### Post by DirtyPC on 2011-06-11
I'd go for 10.04 LTS Personally, 3 year support and stable. Although your hard drive could be dying

---

### Post by ferd on 2011-06-11
Try vacuuming the interior of the box especially the cpu fan area.

---

### Post by piratemari on 2011-06-11
So, I've been experiencing this for the past week. Today it all came to a head, my Natty has frozen six timed today, twice in the process of starting up, twice less than ten minutes after loading the. It's the only OS on my laptop, which is a fairly new laptop.

My biggest issue is, this is ******* recent. I've had Natty since I came out, and never had a single problem until now. Plus, I have my hard drive formatted a certain way, and desperately do not want to have to re-install Ubuntu. I've done a lot of customisation, for one. For two, I do not trust myself to totally **** up my hard drive. Thirdly, there are things I need to be able to finish before I can do that anyways, because they aren't stored with my files on the other partition.

Please help, someone :( I'm at a loss.

---

### Post by mihalybaci on 2011-06-11
I've had to get in and vacuum out the box before, I even got used some q-tips to clean off the fan blades and get junk off the CPU heat sink. But that was because the fan was running non-stop and loud, which isn't happening now. I did just install a new supplemental 250  GB hard drive as a backup about 2 months ago, but maybe I'll make that the boot drive. I think I'm going to go back to 10.04 since I didn't have any issues with it on my laptop. Thanks for the advice, I'll post a reply if a downgrading/switching boot drives solves the problem.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **mihalybaci said:**
> Recently, my wife's desktop has been freezing almost daily, leading to a reboot. It's an HP Pavilion (specs [here]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00783599&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&site=null&key=null&product=3254035")) and it has Ubuntu 11.04 installed since soon after 11.04 came out. There doesn't seem to be really any rhyme or reason to the crashes, except that it might happen more often when she's web browsing with Firefox. I tried looking at /var/log/syslog, but to be honest I wasn't really sure what I was looking for. I did notice that syslog would stop recording at the same time the mouse and keyword freeze. Has any one seen this problem or be able to give me some advice on how to find out what's going on?

Thanks

I always go with the most recent previous release from the most recent release, so that way I get something that everyone has had a chance to try out, and iron out the bugs (if any?)...   Personally, I have installed and sticking with 10.10 for now, and I am quite happy with it:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by mihalybaci on 2011-06-13
Things have gotten somewhat more complicated, ever since I tried to copy the results of /var/log/syslog, the computer boots to to either grub recovery > or grub rescue > . I can boot from the 10.04 Live CD (and I'm assuming 10.10, or 11.04 if needed), but I can't get permission to access either the 80 GB boot drive or the 250 GB non-boot drive. What I'd like to do is move everything from the 250 to the 80, load the OS onto the 250, move everything from 80 back onto the 250 and reformat the 80 as a backup drive. And it doesn't matter to me if I have to fix the current install to boot, or just work around it from a CD boot.  One thing that may be important is that I tried a Checkdisk from the Live CD and the 250 came back clean, and the 80 did not.

---

### Post by mihalybaci on 2011-06-14
So, things are "fixed" now, and its a long explanation with this one.

The boot disk ended up getting corrupted somehow, so I ran fsck from the Live CD, but still couldn't boot from the drive. Instead of trying to recover the entire system and use a different kernal, I figured it would be easier to just recover home and forget everything else.So,  I installed Ubuntu 10.04.2 (I like the LTS with it) on the second hard disk, and it went fine. Turns out fsck threw the entire drive into /(drive)/lost+found/ with the inode number, so I followed [this handy page]("http://karuppuswamy.com/wordpress/2010/06/09/how-to-recover-files-from-lostfound-after-fsck-in-linux-how-i-did-it-in-ubuntu/") to recover the files with one slight modification. Since it was the entire drive, not just home, "ls -l" did not produce the nice home list like on page. I used "ls -lhR", which gave the desktop as /meida/(drive)/home/karen/, which means "ls -l" just printed the root "/" directory so a search for "Desktop" did nothing. But now everything is copied over to the new boot drive and seems to work. Jury is still out on the freezing since all of this fix happened today, but if it freezes again it's probably a hardware issue not an OS issue. Thanks for the replies.

---

