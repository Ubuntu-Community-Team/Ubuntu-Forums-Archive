---
title: "(bad!) upgrade and boot problems"
date: 2010-10-20
forum: General Help
---

### Post by 1984dc on 2010-10-20
[SIZE=2][COLOR=Black]Hello  everyone here on the forums i am in a bit of a pickle (to say the least) and i was  wondering if anyone of you would be kind enough to help me out on this  one as at the moment my terminal seems to be completely unresponsive and unfix-able [/COLOR][/SIZE]:cry:  [SIZE=2][COLOR=Black]
[/COLOR][/SIZE]
 [SIZE=2][COLOR=Black]I am a  fairly new  to Ubuntu i´ve been using it for  about a year now and when  the upgrade to lucid lynx 10.4 came along i jumped on it and upgraded  without any problems. Fantastic! The current upgrade to Maverick Meerkat  10.10 has on the other hand been a complete nightmare.[/COLOR][/SIZE][SIZE=2][COLOR=Black]
[/COLOR][/SIZE]
 [SIZE=2][COLOR=Black]Whilst  upgrading i got rid of any 3rd party software as stated in the upgrade  instructions, updated the system, then went on to upgrade. During the  upgrade i was asked about various options (all of which i chose to  install the new packages that came with Meerkat), but i didn't get any  messages about updating my grub. I thought this was weird as on the  online description of the upgrade procedure i found on a 3rd party  website there seemed to be an option to keep the grub configuration or  to install the new one that was available from Meerkat. Unable to do  anything as i was mid upgrade i continued with the installation. Big  mistake! [/COLOR][/SIZE]](*,)
  
 [SIZE=2][COLOR=Black]When my computer rebooted  after the upgrade instead of being greeted with my new operating system  i got this message: error: the symbol 'grub-xputs' not found. and a  command line screen titled ¨grub rescue¨ .

I found various fixes for this but most of them involve booting a live  cd (i would like to point out that  i have a netbook and therefore no  optical drive) so i created a bootable usb to boot from, but when i  tried to boot from the live usb i get this message: SYSLINUX 4.02 debian-20100714 EDD Copyright (C) 1994-2010 H. Peter Anvin et al. I know the live usb drive works as i´ve tried it on other computers with a successful boot with no problems.
[/COLOR][/SIZE]
 [SIZE=2][COLOR=Black]If i hit LS on my emergency grub screen it seems as though all of  my partitions are intact as i get the hd list  (hd0)(hd0,6)(hd0,5)(hd0,1). I have tried to boot into using this code i  found on-line without any luck:
grub rescue>root=/dev/sdX # with /boot partition
grub rescue>linux(or kernel depends of your grub version) kernel_image_name.img
[/COLOR][/SIZE]
 [SIZE=2][COLOR=Black]If anyone could help me with this problem or shed some light on why  i cannot boot from my usb it would be a great help as at the moment i  basically have an unusable computer that googling doesn't seem to be  able to fix.[/COLOR] Please save my p.c! [/SIZE]
 
 [SIZE=2][COLOR=Black]Many, many, many thanks in advance. [/COLOR][/SIZE]
 
 [SIZE=2][COLOR=Black]dc[/COLOR][/SIZE]

---

### Post by drs305 on 2010-10-20
Don't know which sites you've seen, but this thread should be able to walk you through booting from the Grub rescue prompt:
[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

If it becomes necessary, I also wrote a guide this week on booting from the LiveCD ISO so netbook users could install without a CD.
[HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt]("http://ubuntuforums.org/showthread.php?t=1599293")

---

### Post by oldfred on 2010-10-20
I found these issues with syslinux.

[http://ubuntuforums.org/showthread.php?t=1589852](http://ubuntuforums.org/showthread.php?t=1589852)
[http://my.opera.com/toman/blog/setting-up-squeezebox-server-on-new-hardware](http://my.opera.com/toman/blog/setting-up-squeezebox-server-on-new-hardware)
After some fiddling around with the syslinux config files and still not getting it to boot properly, I found a deceptively simple workaround for this: Just type "help" on the BOOT prompt, and when you get the help menu, just hit enter. The system will now boot!

Maverick images burned to usb key on lucid fail to boot - different syslinux version 
ui in /isolinux/isolinux.cfg

---

### Post by 1984dc on 2010-10-21
Thanking you!
 
@ drs305; i had seen similar threads but not the full version. 
@ oldfred i like the idea of a simple solution if at all possible.
 
I will certainly try both of these when i get back to my own computer (@ work now).
 
once again many thanks :)

---

### Post by 1984dc on 2010-10-21
Okay i was halfway through the boot from the grub rescue prompt instructions on the ¨Grub rescue prompt mega thread¨ and i came across a few hurdles which i´m sure is just down to me being a goof but;

1- **insmod linux normal help ****insmod /boot/grub/linux.mod  /boot/grub/normal.mod /boot/grub/help.mod **= the symbol´grub_xputs´not found. for all commands

2- **linux /vmlinuz /dev/sda5 ro **= unknown command 'linux'

3- I haven't come across this problem yet but i´m sure i will when it comes to it. As i upgraded and didn´t install the .iso myself i don´t know accurately what the name of the img will be. Any suggestions?

Once again many thanks.

dc


[]("http://ubuntuforums.org/showthread.php?t=1594052")

---

### Post by drs305 on 2010-10-21
> **1984dc said:**
> Okay i was halfway through the boot from the grub rescue prompt instructions on the ¨Grub rescue prompt mega thread¨ and i came across a few hurdles which i´m sure is just down to me being a goof but;

1- **insmod linux normal help ****insmod /boot/grub/linux.mod  /boot/grub/normal.mod /boot/grub/help.mod **= the symbol´grub_xputs´not found. for all commands

2- **linux /vmlinuz /dev/sda5 ro **= unknown command 'linux'

3- I haven't come across this problem yet but i´m sure i will when it comes to it. As i upgraded and didn´t install the .iso myself i don´t know accurately what the name of the img will be. Any suggestions?

Once again many thanks.

dc


[]("http://ubuntuforums.org/showthread.php?t=1594052")


I'm about off to work so I can only respond briefly. The xputs error message means that Grub was not completely installed. Did you try to reinstall Grub?  From the thread:
> 
If you can get to the LiveCD, many Grub 2 problems can be solved by 1) reinstalling the bootloader or 2) purging/reinstalling Grub2. Purging and reinstalling has the advantage of repairing corrupted files and installing files manually deleted by the user. Nevertheless, the reinstall option should be attempted first.

    * These methods are both detailed in the following thread: [HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099").


Since you aren't able to load the modules, you won't be able to load linux. That's what the messages you are getting mean.

I'll check back after work to see how you are getting on. Good luck.

---

### Post by 1984dc on 2010-10-21
Thanks drs305 i will try once again with the live cd/usb option.

---

### Post by 1984dc on 2010-10-21
Okay so after using Unetbootin aka the link that oldfred provided and the steps to purge and re-install grub chrooting from the live cd i've now got my grub up and running again and i'm happily running 10.10.

I will let pen-drive linux know about the glitch with the universal usb installer and linux live usb creator (as i tried them too and they had the same problem, which i think is specific to my type of box.

Many thanks to you both for all your help. especially drs305 for your detailed and accurate mega-thread. 

All the best.

Dc

---

