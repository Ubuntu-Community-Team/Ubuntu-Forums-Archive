---
title: "I beeeeeppped UP!!!!"
date: 2011-06-07
forum: General Help
---

### Post by Tappet Head on 2011-06-07
Ok, I got that friggen Go-google redirect root virus on my Win 7 Hdd in my computer. I normally rin Ubuntu 10.10, and love it to deaf, only use windows to run Cad when I need to, otherwise, it never gets used. I run them both on separate Hard drives, never had a problem until now, cause I have made a mistake, and unsure on how to cure it.

I Removed my linux HDD, formatted my windows disk and reloaded win 7.Not worry, plugged my Linux drive back in, reset my cmos to choose the linux drive as first boot, now it goes all teh way to verifying disk drive and hangs, and hangs for ever, I had lilo configured and the dual boot worked a treat, until now, since linux wont boot, even with the win7 disc removed, I cant even reconfig my lilo and sort my problem, to top it off, I havent backed up any of my emails or info from my linux drive, so a re-install isnt on the simple fix list atm.

So, who has an idea that will help me out?, oh, and I cant view my linux drive from windows, it simply cant see it. 

cheers
TH

---

### Post by Bucky Ball on 2011-06-07
Windows won't see EXT partitions, or labels them 'Unknown'. Doesn't natively recognise EXT so I would forget grabbing valuable data via that avenue. Sorry can't help with the rest.

---

### Post by gandaran on 2011-06-07
> **Tappet Head said:**
> Ok, I got that friggen Go-google redirect root virus on my Win 7 Hdd in my computer. I normally rin Ubuntu 10.10, and love it to deaf, only use windows to run Cad when I need to, otherwise, it never gets used. I run them both on separate Hard drives, never had a problem until now, cause I have made a mistake, and unsure on how to cure it.

I Removed my linux HDD, formatted my windows disk and reloaded win 7.Not worry, plugged my Linux drive back in, reset my cmos to choose the linux drive as first boot, now it goes all teh way to verifying disk drive and hangs, and hangs for ever, I had lilo configured and the dual boot worked a treat, until now, since linux wont boot, even with the win7 disc removed, I cant even reconfig my lilo and sort my problem, to top it off, I havent backed up any of my emails or info from my linux drive, so a re-install isnt on the simple fix list atm.

So, who has an idea that will help me out?, oh, and I cant view my linux drive from windows, it simply cant see it. 

cheers
TH
you can backup your data using the Ubuntu live cd or live usb

---

### Post by mastablasta on 2011-06-07
you probably need to update LILO. why are you not using GRUB to boot?
 
GRUB would then be easilly reconfigured and "fixed" using the LiveCD.

---

### Post by Tappet Head on 2011-06-07
> **gandaran said:**
> you can backup your data using the Ubuntu live cd or live usb


I tried that but it wouldnt grant me access to the files I wanted, but instead I have installed 3rd linux os on the windows HD in a small partition, of which gave me the ability to reboot into my old linux via choosing it threw the boot menu, so Now i'm backing EVERYTHING up, but would like to make a ISO image of my current setup, and reload onto a NEW HD as I have found errors on its current one. I tried to repair my lilo once in 10.10, but no luck with that, I have an error in the Fstab, at least for now its operable and I have been able to get to my valuable emails and documents. 

I would like to try and fix it properly before I reload it all, so will keep trying for another week.

---

### Post by gandaran on 2011-06-07
> I tried that but it wouldnt grant me access to the files I wanted,
you would need to use a root file browser window
typing in terminal
```
sudo -i nautilus
```
opens the root file browser window in the live cd, no password required.

---

### Post by Tappet Head on 2011-06-08
> **gandaran said:**
> you would need to use a root file browser window
typing in terminal
```
sudo -i nautilus
```opens the root file browser window in the live cd, no password required.

 Thanks mate, I'll keep that in mind next time I need it, How would I go about repairing my Grub now that I can access 10.10 again?

 I have made the image of my current setup, but want to back up my emails and all my bookmarks aswell, I have backed up my email settings, but couldn't get the emails across. I'm not to worried about losing my book marks, but it would be nice to be able to bring em back.

---

### Post by jwcalla on 2011-06-08
You're able to boot into your original linux install now, right?

---

### Post by Tappet Head on 2011-06-08
Yes I am.

---

### Post by wildmanne39 on 2011-06-09
> **Tappet Head said:**
> Yes I am.
Hi, boot into ubuntu and run
```
sudo update-grub
 
```

---

### Post by Tappet Head on 2011-06-10
That seemed to easy and it was, it did update, but still not able to boot of the master HD, it will just hang, so I still require to boot of my slave HD with the dummy linux and windows installed on it, and select 10.10, thanks for the help and I'll keep it in handy, but unfortunately it didn't play the game.

---

### Post by Tappet Head on 2011-06-19
Ya wont believe it, it fixed itself!!!!

---

### Post by wildmanne39 on 2011-06-19
> **Tappet Head said:**
> Ya wont believe it, it fixed itself!!!!HI, thats great maybe it just needed a little kick to get it going after you reinstalled grub. Would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by Tappet Head on 2011-07-09
I ws about todo that after I read it, but its done it again and I'm unable to boot into any thing at all, bar my USB Boot, I last used it on windows and it did an update, now its playing up, just keeps restarting over and over, somethimes it may hang.

---

### Post by wildmanne39 on 2011-07-09
> **Tappet Head said:**
> I ws about todo that after I read it, but its done it again and I'm unable to boot into any thing at all, bar my USB Boot, I last used it on windows and it did an update, now its playing up, just keeps restarting over and over, somethimes it may hang.Hi, if you have usb devices plugged in unplug them and then try to boot.

---

### Post by Tappet Head on 2011-07-09
> **wildmanne39 said:**
> Hi, if you have usb devices plugged in unplug them and then try to boot.

I sorted it Wild man, thanks for the help, I used the Grub Repair thread I found on here, was simple and it worked great.

Thanks all.

---

### Post by Bucky Ball on 2011-07-09
Please mark thread as 'solved'. ;)

---

