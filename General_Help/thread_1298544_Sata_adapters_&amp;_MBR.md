---
title: "Sata adapters &amp; MBR"
date: 2009-10-22
forum: General Help
---

### Post by breakerr on 2009-10-22
Hello there community....

....It has been a long time since I wrote here but I find myself in a situation where I need your wisdom again.....

.....I have 2 IDE drives/hard disk (1 of them have xp already) and 2sata drives so I just got [**[COLOR="Blue"]2adapters[/COLOR]**]("http://cgi.ebay.com/IDE-TO-SATA-Converter-Adapter-100-133-For-HDD-CD-DVD_W0QQitemZ360198807632QQcmdZViewItemQQptZAU_Components?hash=item53dd85a050") to Convert my two IDE to SATA so I can connect my cd-rom and dvd-burner in the only available ide port on motherboard, so my question is can I install ubuntu in any of my SATA or IDE drives without touching the MBR master boot record of my existing Xp installation or Ill need to unplug all drives except the one I wanna use for ubuntu and after finish install plug back all other drives like I used to do be4 having the SATA adapters.

I just wanna install the upcoming final version of ubuntu without messing my xp boot file and don't want grub to be first.

Thanks in advance guys and with your help Ill have the upcoming ubuntu properlly installed, THANKS :D

---

### Post by oldfred on 2009-10-22
Grub has to be first or you will never get to ubuntu. You can unplug your windows hard drive but will have to manually add a boot stanza to grub to get a choice to boot windows. You can leave the windows drive alone and make the other drive boot & be ubuntu. With the adapters I am not sure how you select drive order. Are the adapters just converting the pata drives to sata and in the BIOS you can control which drive boots first?

I would set the windows drive to second and have the ubuntu drive first. When you install ubuntu from the liveCD grub will go into the first drive and automatically add a windows boot stanza with drive mapping so windows will boot to menu.lst. 
IF later you want you can go into BIOS you can make the windows drive first and it will boot just into windows and not even see the ubuntu drive.

Some examples, most assume one drive :
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[http://apcmag.com/how_to_dual_boot_vista_and_xp_with_vista_installed_first__the_stepbystep_guide.htm](http://apcmag.com/how_to_dual_boot_vista_and_xp_with_vista_installed_first__the_stepbystep_guide.htm)
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by breakerr on 2009-10-23
Thanks a lot for the info/help, and YES I can select which drive boot first in bios and all of them appears as SATA in the BIOS, no IDE appears listed.

---

### Post by breakerr on 2009-10-30
Ok...I just got the new 9.10 and installed on a clean drive with a [[COLOR="Blue"]sata adapter[/COLOR]]("http://cgi.ebay.com/IDE-TO-SATA-Converter-Adapter-100-133-For-HDD-CD-DVD_W0QQitemZ360198807632QQcmdZViewItemQQptZAU_Components?hash=item53dd85a050") but I cant boot up from that drive even if I disabled the drive with Windows Xp in BIOS (all it says is Grub Loading and keyboard doesn't respond), the one with the sata adapter is on cable select and xp recognize it but I dont think the jumper have to do with this hence the SATA adapter) **any suggestions????????????**

---

### Post by breakerr on 2009-11-02
Help pleaseeeeeeee!!!!!!!

---

### Post by oldfred on 2009-11-02
Did you try switching the order in BIOS for the Sata drives. It seems that Karmic is even worse than previous Ubuntu/grub in that BIOS, Grub and Ubuntu do not agree on drive order. 

One previous thread had a user with a working drive in windows but it was not enabled in the BIOS so ubuntu installed but grub could not see it.

---

### Post by breakerr on 2009-11-02
Yeah I changed the order and even disabled the Xp drive and when I got to the ubuntu drive was stuck at ¨LOADING GRUB¨ and blinking under line dash...Ill try changing jumper but I dont think so......??????

---

### Post by oldfred on 2009-11-02
Beside switching you could try reinstalling grub as it may have installed to the wrong location.

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)

---

### Post by breakerr on 2009-11-05
I found what I think is a much simpler solution......I unplugged all my drives/hard disk except the one I wanted for Ubuntu and specified in the installation to mount grub in the same drive, finished install, plugged all other drives back and voila!!!!! all working fine and now my pc with both operating system :)and just spcifie which first in my bios; now I just want to know if there is a tool besides palimpdest to fix sectors in my drive since palimdest claims it has to many bad sectors/reallocated.

---

