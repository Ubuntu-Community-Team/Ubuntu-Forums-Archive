---
title: "Ubuntu 10.04 blank screen at boot"
date: 2010-06-06
forum: General Help
---

### Post by Manuwash on 2010-06-06
So I solved this by getting the 9.10 ubuntu and forget about the hassle, It&#347; working flawlessly now so there you go.


Hey fellows Im a linux noob and I am already going through hell to get ubuntu to work, but I am having some fun at it and learning some stuff already ( I have always been a windows user, and quite basic level for that matter).

So to help out a bit, I think I already know what the problem is, my ATI radeon 1250 graphics card. It seems many people have been getting this bug of the blank screen of death because of some sort of graphic card conflict. 

To install ubuntu I already had to do some research and fix some code on the installation menu. But I don´t remember exactly what right now. Point is I get to the grub menu and whatever I choose regarding ubuntu I end up on a blank screen, nothing happens, nothing to do.

Doing some forum research I ended up finding ways to get to the GUI, by changing a piece of the kernel code in the grub menu ( pressing e). If add either "nomodeset" or "radeon.modeset=0" after "quiet splash" on the code I can get to a user prompt and then I end up on a regular command prompt, to which I learned that writing "startx" command gets me to the desktop. All this already took me like a couple of days I´d say.

So problem is, I haven´t really solved anything, ubuntu still doesn´t boot as it should and when I´m on the desktop I can´t get the wifi icon, mount drives or get into several preference options. As far as it seems, I have booted into some limited desktop option.

Any help here would be great, or should I just dump the 10.04 and get a prior version? I heard the blank screen of death due to graphic card conflict is mostly specific to this last version. 

Thanks in advance.

---

### Post by utnubuuser on 2010-06-06
You can add the nomodeset to your grub file so it's a permanent fix for that particular issue, then deal with the other issues seperately. Open a terminanl and paste in:> sudo gedit /etc/default/grub, find this line:> GRUB_CMDLINE_LINUX=""and change it to > GRUB_CMDLINE_LINUX="i915.modeset=0"or maybe> GRUB_CMDLINE_LINUX="i915.modeset=1"or > GRUB_CMDLINE_LINUX="nomodeset=1"or > GRUB_CMDLINE_LINUX="nomodeset=0"save, then, in a terminal again, run > sudo update-grub2or > sudo update-grub
then reboot.
Here is a link to the Lucid release notes, there are several links there for various issues too> [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes")
and the forum "Lucid known issues/workarounds" sticky> [http://ubuntuforums.org/showthread.php?t=1469475]("http://ubuntuforums.org/showthread.php?t=1469475")

PS. the nomodeset fix should only be a temporary fix for you - in some machines there is quite a performance loss. - As the Lucid Lynx matures, people will probably find precise card settings to fix the issue more permanently, so check back.

---

### Post by Manuwash on 2010-06-06
Yeah problem is nomodeset only allows me to progress further to a command prompt, I have been using startx to be able to get the GUI, but it´s not fully functional. 

A friend told me to load the GUI correctly I need to use the GDM command( I don´t know much about it) but then when I tried starting it with that command I get a message saying I ought to use the service command or something like that and that doesn´t work.

So basically I know right now I can´t expect the OS to load smoothly as it should but how can I at least get into the GUI in a moderately functional mode? Or should I just install a previous version? ( and which would you recommend in that case?)

Thanks

---

### Post by Manuwash on 2010-06-07
Well guys anything else? should I get a previous version? which do you recommend?

Also I wanted to add that when I boot the live cd, with nomodeset of course otherwise i get the blank screen, I am able to get to a fully functional desktop, get on the internet etc, so even with the ati bug, there must be a way around it i´d say.

---

### Post by UsedBits on 2010-06-11
The GRUB instructions appear to be for version 2.  I have version 1 and am limited to the menu.lst file.

Also, adding 'nomodeset' to the boot configuration simply allowed the error messages to display.  Removing 'quiet splash' did nothing.

What command can build/rebuild the xorg.conf file?  I'd like it to build one in its simplest form, and one matching my hardware configuration.

Does having an HDTV on a VGA cable matter?  It REALLY screwed things up to have the HDTV connected on the HDMI port.

But for starters, I'd like to get startx to actually start. I don't care how, whether by init 5, or gdm, or what-ever.  How 'bout a rundown of the various components one might look at?

---

