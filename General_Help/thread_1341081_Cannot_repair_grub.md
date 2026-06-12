---
title: "Cannot repair grub"
date: 2009-11-29
forum: General Help
---

### Post by smerral on 2009-11-29
Hi,

Well, here's the situation:

My original setup was Vista on C: drive and XP Pro on second harddisk. I installed ubuntu 9.10. Later I decided to get rid of Vista and install XP pro over it on C: drive, deleting XP from the second disk. Of course when I had completed this I no longer had the grub boot loader. I had expected this and prepared an Ubuntu boot disk beforehand, so I can still boot Ubuntu from the disk. 

This is fortunate as I have tried everything and cannot reinstall grub. I have tried the supergrub disc to know avail. I have tried booting into Ubuntu live disk and using the terminal commands as instructed also to no avail. I always end up with 'file not found' messages. My guess is that by installing XP over Vista I have corrupted some files.

Any ideas? (I suppose I could delete the Ubuntu partitions and do a fresh install but I would rather avoid this if possible.)

Thanks,

Brian

---

### Post by oldos2er on 2009-11-29
I don't know if Supergrubdisk is aware of grub2 yet. Have you tried [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by smerral on 2009-11-29
Hi Ann,

Well that certainly re-installed grub. However, now, when I reboot I just get the grub command screen. Where do I go from here? Is there something I can type to get to a menu where I can choose between OS's? Now I am using the disk to boot into either system, which rather defeats the object!

Regards,

Brian

---

### Post by ranch hand on 2009-11-29
Have you tried this;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Ignore the edit file instruction, should not be needed.

---

### Post by smerral on 2009-11-29
thanks a lot - making progress I think! Now Ubuntu loads automatically - if I hit escape I get a menu BUT there is no windows entry there! Still need to boot from a CD into windows..................

---

### Post by ranch hand on 2009-11-29
When you are booted in to your Ubuntu, in terminal, run;
```

sudo update-grub

```
I don't know why but there seems to be a problem with grrub2 picking up stuff when run remotely (recovery or installation).  This will fix it about 95% of the time.

If that does not do it I would add an entry to /etc/grub.d/40_custom for your MS.

I really do not know what they are supposed to look like, don't have MS on my box.  The link in my sig is a grub2 intro.  It has some great links in it.  I recommend the 1st three.  In your case the 2nd or 3rd probably have the MS info you need.

---

### Post by smerral on 2009-11-29
Thanks a lot for your help - I already did the update-grub command. I will try the other stuff tomorrow!

---

### Post by smerral on 2009-11-30
Well, bingo! I solved it! About 30 minutes ago.

My mistake was not to run the update-grub2 command from root. When I did this it kindly told me to use apt-get to download one of a list of packages for install. When I did this it ran the update command and updated the menu, so when I boot I now have the original menu with both Ubuntu and vista....great!

Thanks for your help - those links were really useful.

Regards,

Brian

---

