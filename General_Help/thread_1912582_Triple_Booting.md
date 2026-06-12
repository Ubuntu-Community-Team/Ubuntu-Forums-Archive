---
title: "Triple Booting?"
date: 2012-01-20
forum: General Help
---

### Post by stevennlv on 2012-01-20
OK, I like to tinker with stuff. That's how I learn. But, sometimes I  blow stuff up in the process. I'd like to not melt my current  configuration if I decide to try this.

I'm trying to get away from doze completely. I've been on it since 3.1,  but in the last year or two I have become very unhappy with it.

Long story short: I got hacked hard on XP and old hardware / security  software. I had to upgrade my skill set, my OS, my software and my  hardware. There's still tons for me to learn. But, I think I'm picking  up pretty quickly.

When I got my shiny new box it got infected. It took quite a while to get it straightened out.

I upped my skill level and it works great; for now. Until some butthead  figures out a way to write a new type of virus that gets around all the  extraordinary measures that I had to use to make a win7 box somewhat  secure. And most of that was not letting it connect directly to the net  anymore (Ubuntu VMs) plus a ton of other junk: sandboxes, virtualization,  AV, yada, yada, yada.  I bet my box could run 3x plus faster without  all that crap.

While learning and fixing I tried to go with 11.04 straight on the shiny  new box. But, trying to figure out how to install the driver for my  NVidia card was very confusing. 

(Has that gotten any easier with 11.10 / will it get easier with 12.04?)

And, as far as I could tell there were no *nix drivers for my sound chip  set at all in 11.04. And writing one is so far beyond my skill level  that I just gave up and used 7 as the host. 

(Is there a way to find out if that chip set is currently supported in 11.10 or will be in 12.04?)

Right now I'm dual booting 7 and 7. I set it up this way because of  security concerns. On the main install I have the LGPE locked down so  hard it's not even funny. But, some stuff wouldn't run that way (games).  

So I set up a second boot for the games and locked it with Bit Locker. I  did that so that I when I booted the second (less secure) install it  would mount all the virtual drives in my main install as read only. That  way if the second install gets infected then it should not be able to  pass the infection to the first install.

So when I boot now I have two choices: win7 system and win7 games. If I  want system I just hit enter. If I want games I have to have the Bit  Locker USB key plugged in.

I want a third option without $%^&* the first two.

I have tons of room on the HD I'm not using and it is all chopped up in to lots of virtual drives.

I'd like to take one of those unused partitions and give it to Ubuntu so I can experiment with new releases.

As soon as one comes out that will run all of my hardware I'm switching.  (At my skill level, as long as the hardware will work I can usually  figure everything else out eventually.)

But, in the mean time, while I'm experimenting I need to know for a fact  BEFOREHAND that if I give my boot over to GRUB that I can still get into  the "Bit Lockered" drive. 

Worst case scenario I'll have to restore an image of my drive, but that takes all day!!! And it's headaches I'd like to avoid.

So, does anybody know if I can triple boot 7/7/UB with one 7 drive Bit Locked? 

And, lets say 11.10 won't run my hardware: Then how will upgrading to  12.04 (or whatever) when it's released effect the triple boot? (Kaboom /  have to do some tech stuff / no effect.)

I appreciate any and all help.

Thanks.

---

### Post by oldfred on 2012-01-21
Normally the issue is that users have bitlocker in the MBR of sda or first/main drive and when they install Ubuntu it overwrites the boot loader in sda and destroys the bitlocker boot. It sounds like you have a standard MBR and have the bitlocker in a flash drive?

The workaround for booting Linux with bitlocker is often just to install the grub2 boot loader to another MBR like (if I understand correctly) you have done with bit locker. If you use manual install you can choose where to install the grub2 boot loader. Some then have installed to a external device like a flash drive. Others that are mainly Windows use EasyBCD and force grub2's boot loader into the PBR or partition boot sector. That is not recommended for grub2 as it is larger than old grub and has to use blocklists or hardcoded addresses. An update to grub may change where the rest of grub is on the drive and break system until you reinstall the grub2 boot loader to the PBR.

But Windows normally installs all boot files to the active partition or boot flag. So do both Windows have boot files in one partition or are they on the flash drive?

This shows entire configuration. You can download and run from a Ubuntu liveCD.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

