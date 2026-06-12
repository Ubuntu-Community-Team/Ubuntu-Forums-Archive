---
title: "Grub 2 and Burg"
date: 2010-10-08
forum: General Help
---

### Post by Webpope on 2010-10-08
So I'm using Burg over Grub2.  Problem is I have 9 icons when I boot.  I really want to remove them.  I tried removing old packages in synaptics but that didn't work.

At this point I don't care to remove anything so much as just hide the icons I don't want.

Here's a full list.  [X] indicates I would like it hidden.

Ubuntu 2.6.32-25
Ubuntu 2.6.32-25 (recovery)
**[X]** Ubuntu 2.6.32-21
**[X]** Ubuntu 2.6.32-21 (recovery)
Windows 7 Loader
**[X]** Ubuntu 2.6.32-21 (dev/sda 5)
**[X]** Ubuntu 2.6.32-21 (recovery) (dev/sda5)
**[X]** Ubuntu 2.6.31-17
**[X]** Ubuntu 2.6.31-17 (recovery)


Oh and if I just installed updates so that I'm now using -25 can I delete -21?

---

### Post by gordintoronto on 2010-10-08
You tried to remove old kernels in Synaptic, and what happened?  Should be a piece of cake.

Most people keep at least two kernels, just in case something odd happens.

It looks like you have a dual-boot of 10.10 and 10.10.  Is that right?

---

### Post by wilee-nilee on 2010-10-08
One of the easiest ways to remove kernels is with Ubuntu Tweak.
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Here is the ppa if you want to use it and get updates.
[https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

---

### Post by Alessandro.g89 on 2010-10-08
simply remove any kernel you don't want, the run 
```
sudo update-burg
```
in a terminal

---

### Post by RJ12 on 2010-10-08
I was just about to say, you forgot to run

```
sudo update-burg
```

After you are trying to change BURG

---

### Post by Webpope on 2010-10-09
Thats just it, I deleted the packages and ran the updates and they didn't disappear :\


> **gordintoronto said:**
> You tried to remove old kernels in Synaptic, and what happened?  Should be a piece of cake.

Most people keep at least two kernels, just in case something odd happens.

It looks like you have a dual-boot of 10.10 and 10.10.  Is that right?

I have a Win7 and an Ubuntu 10.10 dual boot.  The .31-17 is there because i had to reinstall Ubuntu and the .32-21 for some reason, I have no idea why.


Edit:

Okay I just got rid of .32-21 using Synaptics.  That worked but the .32-21 on dev/sda5 was not removed and I cant find it anywhere.  Same goes for -17.  Ubuntu tweak can't find them either so I don't know what to do.

---

### Post by drs305 on 2010-10-09
> **Webpope said:**
> Thats just it, I deleted the packages and ran the updates and they didn't disappear :\

Oh and after I updated it changed my default boot to -25, does this mean I can delete -21?

I have a Win7 and an Ubuntu 10.10 dual boot.  The .31-17 is there because i had to reinstall Ubuntu and the .32-21 for some reason, I have no idea why.

Did you use Ubuntu Tweak to remove the packages? UT makes sure everything is removed. It also has a benefit that it won't display a running kernel so anything you see can be safely deleted. You may want to keep one older kernel as 'insurance'.

For details on how to use Ubuntu Tweak see the first section of  [this link]("http://ubuntuforums.org/showthread.php?t=1587462").

---

### Post by Webpope on 2010-10-09
> **drs305 said:**
> Did you use Ubuntu Tweak to remove the packages? UT makes sure everything is removed. It also has a benefit that it won't display a running kernel so anything you see can be safely deleted. You may want to keep one older kernel as 'insurance'.

For details on how to use Ubuntu Tweak see the first section of  [this link]("http://ubuntuforums.org/showthread.php?t=1587462").

I did but kernel options still remain in burg and grub that UT can not find.  I did remove -21 with UT though so I did get it to work for that kernel but not any of the other kernals.

---

### Post by drs305 on 2010-10-09
> **Webpope said:**
> I did but kernel options still remain in burg and grub that UT can not find.  I did remove -21 with UT though so I did get it to work for that kernel but not any of the other kernals.

The entries come from a variety of sources, including other partition menu.lst and grub.cfg files and existing kernels. You can get an idea where grub is picking up the menu entries by looking at /boot/grub/grub.cfg  (or the BURG equivalent). The file is broken down into sections. Assuming it takes the same format as GRUB, the 10 section is on the current OS's partition, and the 30_ section is from other partitions.

If you want to do a bit of sleuthing, you could run these commands to seek out any which exist on your system. If you find grub menus on other partitions you can manually edit them and remove kernels which no longer exist (or boot into that OS and update it's grub files).

You can also search for linux kernels and image files which might trigger an entry. Make sure all your OS partitions are mounted.
```

sudo find / -type f -name '*2.6.32-<...>'  # < > complete the kernel name you are looking for
sudo find / -type f -name menu.lst
sudo find / -type f -name grub.cfg
```

After you have altered or deleted things, don't forget to update grub.

---

### Post by Webpope on 2010-10-09
> **drs305 said:**
> The entries come from a variety of sources, including other partition menu.lst and grub.cfg files and existing kernels. You can get an idea where grub is picking up the menu entries by looking at /boot/grub/grub.cfg  (or the BURG equivalent). The file is broken down into sections. Assuming it takes the same format as GRUB, the 10 section is on the current OS's partition, and the 30_ section is from other partitions.

If you want to do a bit of sleuthing, you could run these commands to seek out any which exist on your system. If you find grub menus on other partitions you can manually edit them and remove kernels which no longer exist (or boot into that OS and update it's grub files).

You can also search for linux kernels and image files which might trigger an entry. Make sure all your OS partitions are mounted.
```

sudo find / -type f -name '*2.6.32-<...>'  # < > complete the kernel name you are looking for
sudo find / -type f -name menu.lst
sudo find / -type f -name grub.cfg
```

After you have altered or deleted things, don't forget to update grub.

The first two commands didn't come back with anything and I let them sit for a bit.  But the third gave me a bunch of directories.

/boot/grub/grub.cfg
/usr/share/doc/burg-common/examples/grub.cfg
/usr/share/doc/grub-common/examples/grub.cfg
/media/252f5f1e-a0c7-4328-b7f7-b904b2fd990a/boot/grub/grub.cfg
/media/252f5f1e-a0c7-4328-b7f7-b904b2fd990a/usr/share/doc/grub-common/examples/grub.cfg

Should I edit all of them, just one?

---

### Post by drs305 on 2010-10-09
> **Webpope said:**
> The first two commands didn't come back with anything and I let them sit for a bit.  But the third gave me a bunch of directories.

/boot/grub/grub.cfg
/usr/share/doc/burg-common/examples/grub.cfg
/usr/share/doc/grub-common/examples/grub.cfg
**[COLOR="DarkRed"]/media/252f5f1e-a0c7-4328-b7f7-b904b2fd990a/boot/grub/grub.cfg[/COLOR]**
/media/252f5f1e-a0c7-4328-b7f7-b904b2fd990a/usr/share/doc/grub-common/examples/grub.cfg

Should I edit all of them, just one?

This would be the one that Grub/BURG may be grabbing the 'non-existent' kernels from. You can inspect it from your current install with the following command. If you find one of the entries is listing the non-existent kernel you could open the file for manual editing or boot to that system and update BURG.

```
cat /media/252f5f1e-a0c7-4328-b7f7-b904b2fd990a/boot/grub/grub.cfg | grep menuentry
```

The command should return the lines which include the titles you see on your Grub/BURG boot screen, assuming BURGs files are in the same format as Grub's.

---

### Post by Webpope on 2010-10-09
> **drs305 said:**
> This would be the one that Grub/BURG may be grabbing the 'non-existent' kernels from. You can inspect it from your current install with the following command. If you find one of the entries is listing the non-existent kernel you could open the file for manual editing or boot to that system and update BURG.

```
cat /media/252f5f1e-a0c7-4328-b7f7-b904b2fd990a/boot/grub/grub.cfg | grep menuentry
```

The command should return the lines which include the titles you see on your Grub/BURG boot screen, assuming BURGs files are in the same format as Grub's.

Ok its showing those kernels.  I'll edit it and update you.

---

### Post by Webpope on 2010-10-09
Do I just comment them out?

---

### Post by drs305 on 2010-10-09
> **Webpope said:**
> Do I just comment them out?

First, are you sure you don't need those menuentries on *that* system?

Yes, you can just edit them out. I'd just copy the full file somewhere outside the system folders and then delete the specific menuentries. Assuming it works like Grub, you would delete the entry starting with the line "menuentry...." and ending with it's ending **}** 

The entry is probably about 8-10 lines long.

Although grub.cfg (or equivalent) isn't meant to be edited, if you access it from your current partition I believe you can edit it without having to make it writeable.

---

### Post by Webpope on 2010-10-09
This is interesting.  The only menuentries that are in there are the ones I want to remove.  My Win7 loader and .32-25 loader are absent.

One last question.  If I comment them out is there potential for something catastrophic to happen?

---

### Post by drs305 on 2010-10-09
> **Webpope said:**
> This is interesting.  The only menuentries that are in there are the ones I want to remove.  My Win7 loader and .32-25 loader are absent.

One last question.  If I comment them out is there potential for something catastrophic to happen?

That doesn't sound right unless BURG uses different configuration files. I wouldn't comment out the only entries in a grub.cfg file quite yet. 

What I'm guessing is that perhaps BURG uses a burg.cfg file but it is still mining information from residual GRUB files which your bootloader isn't even using. Is there such a thing as a burg.cfg?

At this point, I'd wait for someone who has experience with BURG to speak up. I'd also run the boot info script and let us take a look, assuming it picks up the BURG files. 

If you really want to play with it right now, I'd move the entire file *out* of the grub folder (say to your /home), run update-grub (or burg) on your current system to see if the entries disappear, then put the file back where it belongs.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Webpope on 2010-10-09
> **drs305 said:**
> That doesn't sound right unless BURG uses different configuration files. I wouldn't comment out the only entries in a grub.cfg file quite yet. 

What I'm guessing is that perhaps BURG uses a burg.cfg file but it is still mining information from residual GRUB files which your bootloader isn't even using. Is there such a thing as a burg.cfg?

At this point, I'd wait for someone who has experience with BURG to speak up. I'd also run the boot info script and let us take a look, assuming it picks up the BURG files. 

If you really want to play with it right now, I'd move the entire file *out* of the grub folder (say to your /home), run update-grub on your current system to see if the entries disappear, then put the file back where it belongs.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

I think its pertinent to note that the entries I would comment out don't boot anyway.  They're nonfunctioning.

---

### Post by drs305 on 2010-10-09
> **Webpope said:**
> I think its pertinent to note that the entries I would comment out don't boot anyway.  They're nonfunctioning.

Then have at it !  :guitar:

---

### Post by Webpope on 2010-10-09
I ran sudo update-grub and sudo update-burg after saving the file and rebooted.  Nothing has changed :\

---

### Post by drs305 on 2010-10-09
> **Webpope said:**
> I ran sudo update-grub and sudo update-burg after saving the file and rebooted.  Nothing has changed :\

:-(

Guess I'll have to leave this one for your BURG mates then...

Best wishes.

---

### Post by watupgroupie on 2010-10-09
Just use folding mode. I believe you just click the f key at the main burg menu. It will compile all of the kernels for all of your OS's into one icon.

---

### Post by Webpope on 2010-10-09
Thanks that worked.  All though I still have one extra icon than I'd like (the dev/sda5 ubuntu) its something I can live with.

Thanks drs305 for your help :)  I learned a ton.

---

### Post by dcstar on 2010-10-09
> **Webpope said:**
> The first two commands didn't come back with anything and I let them sit for a bit.  But the third gave me a bunch of directories.

/boot/grub/grub.cfg
/usr/share/doc/burg-common/examples/grub.cfg
/usr/share/doc/grub-common/examples/grub.cfg
/media/252f5f1e-a0c7-4328-b7f7-b904b2fd990a/boot/grub/grub.cfg
/media/252f5f1e-a0c7-4328-b7f7-b904b2fd990a/usr/share/doc/grub-common/examples/grub.cfg

Should I edit all of them, just one?

Burg uses /boot/burg/**burg**.cfg

There is not point playing with Grub files if you are using Burg, you should totally get rid of Grub if you are using Burg, it just confuses things.

Burg will search out all OSs on all mounted drives (exactly the same as Grub will do), if you do not want Burg/Grub to detect these on removable drives then UNPLUG the removable drives when you do an update-burg/grub.

---

### Post by Webpope on 2010-10-10
Thanks a ton!  Marking as solved.

---

