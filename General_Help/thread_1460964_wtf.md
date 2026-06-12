---
title: "wtf?"
date: 2010-04-23
forum: General Help
---

### Post by mark1c on 2010-04-23
Trying to break up with windows and want to try out ubuntu. Set my computer to boot from cd/dvd drive. All goes fine until after language select, then nothing. Computer no longer recognizes input from keyboard. Just sits at main screen. Any ideas?

---

### Post by Chronon on 2010-04-23
Are you able to check the disk for errors?  It's possible you got a bad download.  

It could be something else too.  I was unable to get the installation to work with either of Ubuntu 9.10 or Kubuntu 9.10 on x86_64.  I ended up installing a remix called Zenix that uses the same repositories to get 9.10 on my box.  Apparently, there was some problem that the mainline installers had with my hardware.  Once I found that Zenix installed smoothly on my hardware I didn't pursue the matter further.

---

### Post by Ebere on 2010-04-23
> **mark1c said:**
> Trying to break up with windows and want to try out ubuntu. Set my computer to boot from cd/dvd drive. All goes fine until after language select, then nothing. Computer no longer recognizes input from keyboard. Just sits at main screen. Any ideas?

Is your cd/dvd drive a scsi or sata, or ide  ?

I have seen references on this forum where people were having problems running/installing/testing, with cd/dvd drives that were sata.

---

### Post by QIII on 2010-04-23
See below.

Brain fart.

---

### Post by QIII on 2010-04-23
Could you post back with the specifications of your machine?

Can you run a Live session from the CD?  ("try Ubuntu without making changes to your disk")


Perform an md5sum check on your iso image.

Make sure the hash matches the one on the page where you downloaded the   iso image.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Insert the LiveCD and select "Check disk for defects"

If the first fails, download again.  If the second fails, re-burn the  iso you downloaded onto a new disk.  Burn  at the slowest rate possible.

If both pass, run memtest for several hours (or overnight...)  *nix systems can sometimes be less tolerant of memory issues than Windows.

Sorry.   Meant to be an edit of the post above...

---

### Post by isecore on 2010-04-23
> **Ebere said:**
> Is your cd/dvd drive a scsi or sata, or ide  ?

I have seen references on this forum where people were having problems running/installing/testing, with cd/dvd drives that were sata.

Just for the record, I've installed Ubuntu off of several different makes/models of SATA-connected optical drives and they all worked fine.

Totally off topic, just wanted to add my US$0.02

---

### Post by no2498 on 2010-04-23
cd/dvd player may be going bad
yep been on that side of the fence too

---

### Post by jburr51 on 2010-04-23
I agree with QIII. Run through those checks, but I would almost bet on a corrupted download or that the ISO didn't burn correctly.
 
Just installed 9.10 on an HP xw6400 Workstation with no problems other than needing to upgrade the NVIDIA driver, which I somehow managed to accomplish without blowing up the machine.
 
Just getting into Ubuntu myself and I feel your pain, but take heart and follow QIII's suggestions.

---

### Post by kanikilu on 2010-04-23
Not sure if this is applicable, but I had a problem on one machine I was installing Ubuntu (don't remember which version) on and the workaround was to press F4 at the main menu and choose "safe graphics mode". 

Although now that I think about it, I believe that is available *after* the language selection screen, so, that's probably not going to work...

The other things I would try would be:

- Check that your ISO and CD are good, as others suggested. Do you have another computer available to try the CD in?

- Use UNetBootin in Windows to create a Live USB flash memory drive, if you have one available:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You can point it to an existing ISO you've downloaded, or have it download it again for you, either way...

- Try the Alternate Install CD ([https://help.ubuntu.com/community/GettingUbuntu#Download%20the%20Alternative%20Installation%20CD](https://help.ubuntu.com/community/GettingUbuntu#Download%20the%20Alternative%20Installation%20CD)) - although this is not a Live CD, so only use it if you are sure you want to install it.

- Try plugging your keyboard into a different port (if it's USB) or even a different keyboard altogether if you have one around.

- Try another distro's Live CD (Fedora?), if it works, you know your hardware is good.

---

### Post by mark1c on 2010-04-26
Thanks all for your suggestions. 

Should have the day off from work today and will have time to play around and see if I can get this to work.

mark1c

---

### Post by Rubi1200 on 2010-04-26
It seems some of the iso images may be corrupt or incomplete. Try some different mirrors, then burn and see what happens.
Good luck!

---

