---
title: "Problem at PC-Startup (GRUB related?)"
date: 2012-01-18
forum: General Help
---

### Post by kleinjakob on 2012-01-18
Hello,

I'm new to ubuntuforums.org and I am posting here, as I have found a lot of help resolving previous problems by reading others' posts in the past here.

My problem: I'm running Ubuntu 10.04 x64 on a 3 year old Core 2 Quad "dimotion" machine for over 18 months now - everything worked fine so far (though there where some problems in the past, but everything was solveable). Today when I tried to turn my machine on, I noticed that it seems to loop around the BIOS POST: first the "Intel"-Splashscreen shows, a beep (which is normal, it does this allways before the GRUB selection shows up) and a black screen with a blinking white underscore shows (where usually GRUB would load) for some seconds before it restarts.

I have switched it off and tried again - same.

Then I unplugged all USB devices (only screen, keyboard, mouse, ethernet and speakers are connected now).

As I was afraid that there might be a hardware problem, I stared from a live CD (both Trinity Rescue Kit 3.4b on a CD; later Ubuntu 10.04 x64) which both worked like I'd expect them to (Ubuntu live worked like ever with sound and full video card recognition). In Ubuntu 10.04 x64 live I ran a check on the main hdd (/dev/sda) with Gparted - which repored no errors on all partitions (ext3 - /, /home; a ntfs - win7 partition), then i mounted them and could access my files normally.

After this out of the way I searched the internet for help: found an about.com article: [http://pcsupport.about.com/od/findbysymptom/tp/computer-wont-turn-on.htm](http://pcsupport.about.com/od/findbysymptom/tp/computer-wont-turn-on.htm) - not much help... and a very short thread here, which seemed promising but was never followed up on: [http://ubuntuforums.org/showthread.php?t=1689237](http://ubuntuforums.org/showthread.php?t=1689237).

I also thought of reinstalling GRUB, but wanted to ask before swiming in for me uncharted waters...

Thank you very much,
Jakob

edit: I forgot to mention that until yesterday everything worked fine and I haven't changed a thing in the last couple of days (maybe there was one small update by the update manager, I'm not sure when it was exactly in the last 7 days...) and i think some 2 or 3 restart cycles back I aborted a routine ext3 partition check...

---

### Post by dino99 on 2012-01-18
hi & welcome to fora :)

your issue looks like ones that so many users have posted in the past. Is it a i965 intel system ?
When you get the grub menu choice:
- select the first line, hold "E" to edit it, and add "nomodeset" (without the quotes) before "quiet splash" around the end of the line; then ctrl+x to boot.

If it still fails, then remove "quiet splash" to let you see & know what going on.

---

### Post by kleinjakob on 2012-01-18
Thank you for the quick reply, maybe I wasn't specific enough, but I don't even get to the GRUB screen. The "blinking underscore" I mentioned is NOT the normal GRUB screen - I don't get to see it at all.

Thanks, Jakob

p.s. I don't know if the Intel Core 2 Quad belongs to the i986 family...

---

### Post by kleinjakob on 2012-01-18
I wanted everyone maybe expiriencing similar problems know how I solved my problems now.  I thought as my last full scale backup is just 3 days old there isn't much I can loose and reinstalled GRUB from the live system. I strongly recomend everyone not having up-to-date backups, to first create them (also posible from a live system)!

Then I checked which partition contains my /boot folder (in my case /dev/sda1) with the graphical representation in Gparted (I know how I have my partitions arranged, if you don't mount them in the live system and check the contents).  I started a Gnome-Terminal Emulator and issued the following commands (where a stands for the drive and X stands for the partition number):

```
sudo mount /dev/sdaX /mnt
```

to mount the partition easily accessible (you could also use the mount point when checking the contents, but this was too long to handle easily in my case (/media/-----long-id----).

Then I started the grub-installer with the additional option to change the base directory to my mounted system:

```
sudo grub-install --root-directory=/mnt /dev/sda
```

That returned: Grub successfully installed. No Errors repored.

Then I restarted the PC and everything is back to normal.

I hope this helps others expiriencing the same problem, if something is not correct, please will someone correct me!

Jakob

---

### Post by kleinjakob on 2012-01-18
Well, seems the problem isn't solved finally yet. After some restarts the same happened again...

I'm still thankful to hear suggestions.

Jakob

---

