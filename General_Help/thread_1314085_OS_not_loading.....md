---
title: "OS not loading...."
date: 2009-11-04
forum: General Help
---

### Post by Chelseagirl on 2009-11-04
I have managed to have a complete disaster with my son's netbook.  He has an Aspire One.  It came with a very basic Linux system which, with hindsight, I should have kept on there...what I decided to do was replace it with a Windows based OS.  After much hassle, I loaded Vista but it didn't work well.  I therefore decided to try out the ubuntu.  I made the CD and loaded it onto the netbook.   Success!!  The wifi hooked up, it looked good....son happy.   
 
So....  He used it for one day (Monday) and when he turned it on Tuesday evening, the OS wouldn't load.  It just goes to a GRUB page, giving the option of starting the OS normally, in recovery mode or two types of checking the memory (both of which turn out fine).  
 
I've tried everything and have now registered on here to beg for some help from you clever people.  It won't boot from the disc - it just stays on the GRUB page.  I thought I'd try a different OS, so prepared a Kabuntu disc and it won't take from that either.
I can hear the disc whirring round, but it just doesn't load.  
 
Not understanding computer programming, I have no idea what to do next.  I am at work so can't give you details of what it brings up, but it gives a list of block numbers.  
 
I am totally at a loss what to do.

---

### Post by m4tic on 2009-11-04
Calm down, you are saying you want to run it from the disc or you already installed it on the laptop?

---

### Post by Chelseagirl on 2009-11-04
I have already installed it on the laptop and it worked fine.  Then when he turned it on again, it won't load and it's stuck on the GRUB screen.   I thought I could try and reload it and that would fix the problem, but it won't boot.

---

### Post by P4man on 2009-11-04
Do I understand you correclty that its not booting the CD anymore either? Do you get the ubuntu CD menu?

Is it possible you never really (successfully) installed ubuntu, but you were just using it off the CD (so called live session)? Another way of asking, did you ever boot ubuntu without the cd in the cdrom drive?

Not to insult your intelligence or anything, just making sure...

---

### Post by HiImTye on 2009-11-04
did you install regular ubuntu or the netbook remix?

---

### Post by Chelseagirl on 2009-11-04
> **P4man said:**
> Do I understand you correclty that its not booting the CD anymore either? Do you get the ubuntu CD menu?
 
Is it possible you never really (successfully) installed ubuntu, but you were just using it off the CD (so called live session)? Another way of asking, did you ever boot ubuntu without the cd in the cdrom drive?
 
Not to insult your intelligence or anything, just making sure...
 
Ha ha...no please feel free to insult my intelligence...I think I'm clever but am actually useless!! 
 
I put the disc in and booted the netbook from it. It asked me which partition I wanted to use and I indicated the one with the Vista already in it, so I waited for ages whilst it reformatted it and then it loaded the Ubuntu. My son set up the wifi and that was it - all fine. That must have been Sunday night.
 
When he got home from school on Monday, he was using it, so it must have turned on and booted up OK. 
 
By Tuesday evening, the thing is in complete limbo.
 
So then I tried the GRUB menu items, i.e. restarting in rescue mode etc., none of which worked.  It then went into maintenance shell mode for hours and hours.  So then I had my bright idea of trying to get it to reinstall from the disc, with no luck.

---

### Post by Chelseagirl on 2009-11-04
> **HiImTye said:**
> did you install regular ubuntu or the netbook remix?
 
 
I'm pretty sure it was regular.

---

### Post by P4man on 2009-11-04
Ok, so it sounds like either your son messed up the installed ubuntu, or something went haywire with the machine, or perhaps updates killed it.

Your best best is booting off the cd again. In the first menu you have the option "try ubuntu without changing your computer" or something along those lines. thats a so called live session. See if that works. See if you can access the internal harddrive from the Places menu. If all that works, we can try and fix it. But what you said about bad blocks worries me it may be a  harddrive problem...

---

### Post by m4tic on 2009-11-04
> **Chelseagirl said:**
> Ha ha...no please feel free to insult my intelligence...I think I'm clever but am actually useless!!  
 
I put the disc in and booted the netbook from it.  It asked me which partition I wanted to use and I indicated the one with the Vista already in it, so I waited for ages whilst it reformatted it and then it loaded the Ubuntu.  My son set up the wifi and that was it - all fine.   That must have been Sunday night.
 
When he got home from school on Monday, he was using it, so it must have turned on and booted up OK.  
 
By Tuesday evening, the thing is in complete limbo.

How old is your son by the way, i rememver my first days of using ubuntu were fun and adventurous that i ended up messing things up. Try booting from the ubuntu cd and open terminal, Applications->terminal. and type: sudo e2fsck -f -y -v /dev/sda1
assuming the file system has errors

---

### Post by Chelseagirl on 2009-11-04
It won't boot off the CD - I have it all set up for booting from it, but it just ignores that and goes straight to the GRUB menu.   
 
Is there any way I can force it to boot from it?
 
I can come back on here after work when I get home and paste in the codes it brings up if that would give any clues?  
 
I wish software came with an idiot's guide :(

---

### Post by fela on 2009-11-04
Have you looked in the BIOS settings? Make sure it's set to boot from the CD first.

OK, this is what I would do. Goto ubuntu.com and download the UNR (netbook remix). There will be instructions on how to prepare an installer for this on a USB flash drive. Then goto the netbook BIOS settings and make sure it's set to boot up from USB first. now plug the prepared UNR installer USB into the netbook and see if it boots off that. If it does, install UNR and hope it works. Also, I would use jaunty (9.04) instead of the new karmic (9.10), as there are still alot of bugs with karmic. You can get old releases off either releases.ubuntu.com or cdimage.ubuntu.com (one or the other, I forget). I use jaunty and it works much better than karmic, in fact karmic didn't run at all.

HTH

---

### Post by HiImTye on 2009-11-04
I would try the netbook remix. it is optimized for the atom processors and any applicable hardware. if there is a version of ubuntu that will have limited problems it is the netbook remix.

make sure you do a proper install of the netbook remix. if your lve CD boots up then reboot and select 'install' rather than booting the live CD

---

### Post by Chelseagirl on 2009-11-04
> **m4tic said:**
> How old is your son by the way, i rememver my first days of using ubuntu were fun and adventurous that i ended up messing things up. Try booting from the ubuntu cd and open terminal, Applications->terminal. and type: sudo e2fsck -f -y -v /dev/sda1
assuming the file system has errors
 
He's 15 and spends most time on Facebook and messenger talking to his girlfriend.  I think he downloaded BBC iPlayer as a first thing too.  I wondered if he'd picked up a virus.

---

### Post by fela on 2009-11-04
> **Chelseagirl said:**
> It won't boot off the CD - I have it all set up for booting from it, but it just ignores that and goes straight to the GRUB menu.   
 
Is there any way I can force it to boot from it?
 
I can come back on here after work when I get home and paste in the codes it brings up if that would give any clues?  
 
I wish software came with an idiot's guide :(

Are you sure the CD is clean? Try booting it with another computer. Sounds to me just like a bad burn or a dirty/scratched CD.

---

### Post by fela on 2009-11-04
> **Chelseagirl said:**
> He's 15 and spends most time on Facebook and messenger talking to his girlfriend.  I think he downloaded BBC iPlayer as a first thing too.  I wondered if he'd picked up a virus.

No such thing as viruses in the land of Linux, sorry that's a Windows-only problem. For now.

---

### Post by Chelseagirl on 2009-11-04
> **fela said:**
> Have you looked in the BIOS settings? Make sure it's set to boot from the CD first.
 
OK, this is what I would do. Goto ubuntu.com and download the UNR (netbook remix). There will be instructions on how to prepare an installer for this on a USB flash drive. Then goto the netbook BIOS settings and make sure it's set to boot up from USB first. now plug the prepared UNR installer USB into the netbook and see if it boots off that. If it does, install UNR and hope it works. Also, I would use jaunty (9.04) instead of the new karmic (9.10), as there are still alot of bugs with karmic. You can get old releases off either releases.ubuntu.com or cdimage.ubuntu.com (one or the other, I forget). I use jaunty and it works much better than karmic, in fact karmic didn't run at all.
 
HTH
 
 
OK.  Sounds like something I can cope with.   
Will let you chaps know how I get on.  And yes, I did download Karmic.
Thanks so much.

---

### Post by HiImTye on 2009-11-04
> **Chelseagirl said:**
>  I wondered if he'd picked up a virus.
thats the windows way of thinking. theres a *very* limited set of viruses that can actually run in a linux environment (as they use ELF formatted executables and they need the proper libraries to run). odds are your installation didnt complete correctly

---

### Post by Vernünftiger Verbrecher on 2009-11-04
> **Chelseagirl said:**
> He's 15 and spends most time on Facebook and messenger talking to his girlfriend.  I think he downloaded BBC iPlayer as a first thing too.  I wondered if he'd picked up a virus.
 It's very unlikely he picked up a virus on Ubuntu. Does he have administrator privileges?

---

### Post by m4tic on 2009-11-04
Yeah the disc maybe corrupt, not to insult your intelligence, please and please try the CD on another PC to see if its working, otherwise with the problem you stated looks like its the laptop that has a problem.

---

### Post by P4man on 2009-11-04
Woho fellas, calm down. The issue here is not which version or remix is best, sonething is seriously wrong and lets fix that first. He and she can experiment with other releases or desktop managers later.

> **Chelseagirl said:**
> He's 15 and spends most time on Facebook and messenger talking to his girlfriend.  I think he downloaded BBC iPlayer as a first thing too.  I wondered if he'd picked up a virus.

No virus thats for sure. There is no such thing as a (working) virus for ubuntu. One of the advantages of using linux. 

Anyway Ill wait until you can report back the exact error message and if the cd still boots (and what the result is of the check disk command some else gave). That should give is the info to decide how to proceed.

---

### Post by Chelseagirl on 2009-11-04
OK, I will print this thread off and give everything a go.  I'll let you know how I get on.
Thanks so much for all your advice.  I may well be back pasting up the codes it gives me in maintenance mode!
 
Thanks again.

---

### Post by Chelseagirl on 2009-11-04
> **P4man said:**
> Woho fellas, calm down. The issue here is not which version or remix is best, sonething is seriously wrong and lets fix that first. He and she can experiment with other releases or desktop managers later.
 
 
 
No virus thats for sure. There is no such thing as a (working) virus for ubuntu. One of the advantages of using linux. 
 
Anyway Ill wait until you can report back the exact error message and if the cd still boots (and what the result is of the check disk command some else gave). That should give is the info to decide how to proceed.
 
Thanks so much.  I'll report back tonight.

---

### Post by P4man on 2009-11-04
> **Chelseagirl said:**
> It won't boot off the CD - I have it all set up for booting from it, but it just ignores that and goes straight to the GRUB menu.   
 
Is there any way I can force it to boot from it?
 
I can come back on here after work when I get home and paste in the codes it brings up if that would give any clues?  
 
I wish software came with an idiot's guide :(

I missed this in the torrent of posts.
Yeah check the disk for finger prints or scratches. Double check the bios is set properly. WHile you are in the bios, see if there is an option somewhere called AHCI (in sata or IDE settings) Disable it if you can. Sometimes this option is called "IDE compatibiity"

If all else fails, do you have a USB memory stick and another computer? If so you can make an USB stick too boot and install from.

---

### Post by HiImTye on 2009-11-04
> **P4man said:**
> Woho fellas, calm down. The issue here is not which version or remix is best, sonething is seriously wrong and lets fix that first. He and she can experiment with other releases or desktop managers later.



No virus thats for sure. There is no such thing as a (working) virus for ubuntu. One of the advantages of using linux. 

Anyway Ill wait until you can report back the exact error message and if the cd still boots (and what the result is of the check disk command some else gave). That should give is the info to decide how to proceed.
I mainly suggested the netbook remix because it is optimized for atom processors/associated hardware. if theres a good chance of loading an ubuntu release for a netbook it would be a netbook remix.
also, ensuring the live CD works is a very good step towards making sure it would install correctly (explaing how to check an MD5 is somewhat more convoluted)

---

### Post by HiImTye on 2009-11-04
generally when you are booting there is an initial screen that gives you a bunch of instructions for getting to the settings (generally called BIOS - basic input/output system, though it may be different for netbooks) there will be a key before or after (for instance 'F2 for BIOS'). you will want to use that to get to the motherboards basic configuration system. once there there will be a series of menus. inside one of them (generally, an 'advanced' named menu option) will contain a 'boot order' or 'boot 1st'/'boot first' option. you want to have the CD ROM/DVD ROM to be the first device to boot from. you want to escape to your main menu again and choose the 'save' option (generally on the right side).

this should let you boot from the Ubuntu CD

---

### Post by Chelseagirl on 2009-11-04
> **HiImTye said:**
> generally when you are booting there is an initial screen that gives you a bunch of instructions for getting to the settings (generally called BIOS - basic input/output system, though it may be different for netbooks) there will be a key before or after (for instance 'F2 for BIOS'). you will want to use that to get to the motherboards basic configuration system. once there there will be a series of menus. inside one of them (generally, an 'advanced' named menu option) will contain a 'boot order' or 'boot 1st'/'boot first' option. you want to have the CD ROM/DVD ROM to be the first device to boot from. you want to escape to your main menu again and choose the 'save' option (generally on the right side).
 
this should let you boot from the Ubuntu CD
 
Yes, I know this (*phew*) and the boot from USBCD option is top of the list.  I've also checked in the F12 menu and it's top there too.
 
I am going to try saving to a USB stick tonight and see if I can load a new netbook remix OS from that.   I'll be back!

---

### Post by P4man on 2009-11-04
> **Chelseagirl said:**
> 
 
I am going to try saving to a USB stick tonight and see if I can load a new netbook remix OS from that.   I'll be back!

You may have seen it from the ubuntu download page, but in case you missed it, to make a bootable USB stick use this tool:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by fela on 2009-11-04
Summary of what happened:

Install from CD, worked
Some kind of something happened and it broke. Haven't told us exactly what it was but I guess you don't know.
Now it won't boot of install CD
Obvious choice is to check the CD on another computer, as well as the BIOS settings on the netbook (make sure CD booting is enabled and at top of the list)
If it doesn't work on another computer, burn another CD, at slowest speed; if it does work on another computer, then the netbook might be screwed or its CD drive might be screwed.
???
PROFIT

lol, just had to throw that in

---

### Post by HiImTye on 2009-11-04
> **p4man said:**
> you may have seen it from the ubuntu download page, but in case you missed it, to make a bootable usb stick use this tool:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
+1

---

### Post by fela on 2009-11-04
> **P4man said:**
> You may have seen it from the ubuntu download page, but in case you missed it, to make a bootable USB stick use this tool:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Couldn't you just

```
sudo dd if=/path/to/ubuntu-netbook-remix-9.04.img of=/dev/sdb # or whatever linux likes to call your usb stick
```

???

---

### Post by Chelseagirl on 2009-11-04
See comments in quote.
 
> **fela said:**
> Summary of what happened:
 
Install from CD, worked - **Yes**
Some kind of something happened and it broke. Haven't told us exactly what it was but I guess you don't know. - **no, because son swears he did nothing....**
Now it won't boot off install CD - **nope.  Goes straight to GRUB menu.**
Obvious choice is to check the CD on another computer, as well as the BIOS settings on the netbook (make sure CD booting is enabled and at top of the list) - **BIOS settings fine - CD top.**
If it doesn't work on another computer, burn another CD, at slowest speed; if it does work on another computer, then the netbook might be screwed or its CD drive might be screwed.  **Netbook used about 3 times, so am going to be v. cross if it is screwed.  CD drive likewise....**
???
PROFIT  **(don't understand??)**
 
lol, just had to throw that in

---

### Post by ST3ALTHPSYCH0 on 2009-11-04
Have you tried completely disabling all other boot options?

---

### Post by m4tic on 2009-11-04
As we said, save us time and try the methods we suggested, try disc on a different system

---

