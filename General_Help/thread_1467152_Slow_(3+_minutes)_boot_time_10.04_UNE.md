---
title: "Slow (3+ minutes) boot time 10.04 UNE"
date: 2010-04-30
forum: General Help
---

### Post by poolek on 2010-04-30
Thanks for any help on this:

After selecting ubuntu from grub, the screen sits with a blinking "_" at the top of the screen for 3+ minutes before finally making it to login. All non-boot stuff is working properly.

I am running this on my toshiba nb205 netbook.

I tried using search to find other threads on this with no luck - if you know of any, please direct me.

Thank you!

---

### Post by poolek on 2010-04-30
more like 10 minutes, actually

---

### Post by poolek on 2010-04-30
wow, same with my desktop, too. No one else is having this issue? I do have win7 set up for dual boot on both computers - could this be a problem?

---

### Post by nanog on 2010-04-30
```
sudo apt-get install bootchart
```

```
sudo reboot
```

```
cd /var/log/bootchart; ls
```this should tell you what package/program is causing the hold up.

 please file a bug:
```
ubuntu-bug pkg
```you will likely be directed to an already filed bug which frequently has a solution.

---

### Post by poolek on 2010-04-30
Haha, I just pm'd you!

I'll give it a shot - thanks for your time on this.

---

### Post by nanog on 2010-04-30
hit the shift key immediately after grub first appears. when the menu comes up hit "e" to edit boot options and remove "quiet". this should let you see what is happening during the boot process. but i really recommend you try using bootchart.

---

### Post by -iceblade on 2010-05-01
> **poolek said:**
> Haha, I just pm'd you!

I'll give it a shot - thanks for your time on this.

i have the same issue with my NB205. takes a very very long time where it sits with a flashing command prompt after the grub screen without doing anything for at least and probably close to 10 mins... 

on my desktop it was able to boot in less than 40 seconds (probably closer to 20...)  (10.04, 2gb ram, phenom II X3 720 at 2.8ghz, 500gb sata II seagate drive)

---

### Post by A.Scotchmer on 2010-05-01
My Aspire One boots fine but power management is dreadful.  Only 1hr 40mins after a full charge.

---

### Post by cynical2 on 2010-05-06
I had the same issue with my Toshiba Nb305. I found a solution on a different forum that I figure i would pass on. Simply go to your bios menu and find SATA controller mode under advanced. Change this to compatibility. It fixed the boot issue for me and everything is finally working fine.

Forum thread I used: [http://bbs.archlinux.org/viewtopic.php?id=85640](http://bbs.archlinux.org/viewtopic.php?id=85640)

Hope this works for you guys!

---

### Post by neoanderthal on 2010-05-23
> **cynical2 said:**
> I had the same issue with my Toshiba Nb305. I found a solution on a different forum that I figure i would pass on. Simply go to your bios menu and find SATA controller mode under advanced. Change this to compatibility. It fixed the boot issue for me and everything is finally working fine.

Forum thread I used: [http://bbs.archlinux.org/viewtopic.php?id=85640](http://bbs.archlinux.org/viewtopic.php?id=85640)

Hope this works for you guys!

I've verified this works with the Toshiba NB 205.
To recap the link (for people searching these forums to address this issue):
Enter the BIOS on computer bootup (f2 function key)
Switch to the Advanced tab
Change the SATA Controller Mode from 'AHCI' to 'Compatibility'.
My boot time went from about 10 minutes to 30 seconds.

Thanks for the solution!

---

### Post by infinitee on 2010-05-26
Thanks, the solution of changing SATA to compatibility mode in BIOS helped! I initially thought 30 seconds was far fetched, but UNR really is impressive.

EDIT: Just for reference, this is Toshiba NB205 series netbook.

---

### Post by mogeku on 2010-05-27
here the same problem incl. batterie run on a hp compaq 6820s laptop. but can't found any compatible mode in bios :-( any other tip ?

thans from a ubuntu / pc dummie

---

### Post by OldSmoky2 on 2010-08-18
Thanks... Changing SATA to compatibility worked great for a Toshiba 205 I got from someone who'd left it for dead after a Windows virus killed it. He was told it would take $200 to repair, so he bought a new netbook instead. I asked him for it, put 10.04 netbook remix on it last night, and it's one smooth-running little Ubuntu machine now. Now I can give it to a friend who recently ended up in a nursing home/rehab center (with free wi-fi available, though). :D

---

### Post by Madmoose on 2010-10-13
Hello, 

I would like to thank you for this suggestion. It does work to really speed up the boot time on my Toshiba Netbook, but changing this setting adversely effects my windows partition. It will not boot. When I try I get the windows worm for about 2 sec, blue screen of death, and reboot. If I change the bios setting back windows will boot, but Ubuntu takes forever and a day to boot again. 

Is there any other options people have found to speed up Ubunutu's boot time other then messing with that bios setting?

---

