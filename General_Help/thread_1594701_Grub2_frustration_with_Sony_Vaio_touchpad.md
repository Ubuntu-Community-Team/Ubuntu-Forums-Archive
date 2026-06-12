---
title: "Grub2 frustration with Sony Vaio touchpad"
date: 2010-10-12
forum: General Help
---

### Post by skew on 2010-10-12
I am currently running a Vaio that multi-boots from either a win7 or one of two Lucids. The last system which I installed on the drive retains changes I made in the /etc/default/grub file. Specifically those written to enable the Sony Vaio Alps touchpad to function. Without the following i8042 entries in the following grub line, the touchpad does not function. 

GRUB_CMDLINE_LINUX="i*8042.noloop i8042.nomux i8042.reset i8042.nopnp *splash"

  So basically when I boot into the last(2nd) system I installed on the Vaio (a Lucid partition which I use for testing) the touchpad works. On the other hand, If I boot into the 1st lucid partition I installed. The touchpad does not function even though the /etc/default/grub file in that partition has the same information in the GRUB_CMDLINE_LINUX line. 

  When I reboot and press E during the grub menu and edit the entry manually, it will work, but grub refuses to permanently save the changes made from that edit.

Is their anyway to save those changes made in grub so I can use the touchpad with both bootable partitions? 

Thanks

P.S. My Sony Vaio VPCF121FD has many issues functioning w/ Lucid. This is just one of many others headaches I'm contenting with from the Nvidia drivers, to non functional speakers and mic, to bios booting order issues, etc. I'm not a happy camper so far (my two cents) :(

---

### Post by chuseq on 2010-10-13
Thanks, this solved my problem with the touchpad not working on a sony vaio vpcea30el under ubuntu 10.04

After editing the /etc/default/grub file remember to run sudo update-grub

---

### Post by skew on 2010-10-13
> **chuseq said:**
> Thanks, this solved my problem with the touchpad not working on a sony vaio vpcea30el under ubuntu 10.04

After editing the /etc/default/grub file remember to run sudo update-grub

Glad it worked for you! Thanks but I did know about updating the grub. That's how I got it to work with my second Lucid install. I tried it with my first as well but only the last grub installed is the functional one has always been the case.  Like I mentioned above, it only appears to work with dual-boot systems not multi-boot systems, such as mine is.

I am still hoping some grub expert out there can help my multi-boot situation.

---

### Post by drs305 on 2010-10-13
Unless you change the BIOS, you are always going to be presented with the same Grub2 menu. If you boot to another install and edit that install's grub files it won't change things (as you have found out). The only Grub 2 files that matter (mostly) are the ones on the install that boots from the MBR.

You can do what you want in several ways. By far the easiest would be to create a 40_custom file in the /etc/grub.d folder of your booting OS. In there, you can manually add your other installs by copying their menuentries from the current /boot/grub/grub.cfg file. Then you can manually add the options to the 'linux' line for these extra menuentries. You can even change the linux and initrd lines from the specific kernel to  /vmlinuz and /initrd.img so they always boot the latest kernel. They will appear at the bottom of the menu. If you want them at the top, name the custom file 06_custom.

The other way is to alter the 30_os-prober script. If you are good at scripting or just like messing with files, you can instruct the script that if it finds partition 'sdXY' or a unique identifier of a particular installation to add the kernel options to the 'linux' line. 

I'm a poor scripter but even I was able to figure it out - given enough time. There is a link in my signature line that gives some examples, "G2 - Tweaks". If you can't figure it out I or someone else could figure it out if you give us the partitions and what you want.

The disadvantage of the scripts is that if the Grub files are updated (not to be confused with update-grub) you would lose your changes so you would want to keep a copy somewhere else in case the scripts do change.

Hopefully this has given you some ideas. Feel free to ask for further elaboration.

---

### Post by skew on 2010-10-14
> **drs305 said:**
> Unless you change the BIOS, you are always going to be presented with the same Grub2 menu. If you boot to another install and edit that install's grub files it won't change things (as you have found out). The only Grub 2 files that matter (mostly) are the ones on the install that boots from the MBR.

You can do what you want in several ways. By far the easiest would be to create a 40_custom file in the /etc/grub.d folder of your booting OS. In there, you can manually add your other installs by copying their menuentries from the current /boot/grub/grub.cfg file. Then you can manually add the options to the 'linux' line for these extra menuentries. You can even change the linux and initrd lines from the specific kernel to  /vmlinuz and /initrd.img so they always boot the latest kernel. They will appear at the bottom of the menu. If you want them at the top, name the custom file 06_custom.

Hopefully this has given you some ideas. Feel free to ask for further elaboration.


Ah, a Grub Expert fantastic!  I appreciate the assistance.  I figured I'd have to make some changes to the booting grub but wasn't sure how to proceed.   I'll look over your suggestions and read the links you've included. 

 Wow...I can see that I have lots to read. I am pretty sure I want the simplest solution, that being the The 40_custom file suggestion.   Even that one is currently beyond my knowledge base. Which means I've got a S#1t load of reading to do, since I don't even understand much of what you have written. Such is the life of the noob.

I'm sure I'll be getting back to you drs305. Until then, thanks again.

---

### Post by skew on 2010-10-14
It works, but I am slightly unsatisfied with the results basically because I can't figure out why it works. I know I shouldn't complain right. However,I like to see all my ducks in a row so bear with me.  The only thing I did was add a menu entry to the 40_custom file then sudo update-grub followed by a boot. Now this is where things don't fit the model. I should see my menu entry at the bottom of the menu list. however that new entry doesn't show up in the boot menu even though, after verification it does show up in the /boot/grub/grub.cfg file. Another strange result is that making this entry into the 40_custom file has somehow changed all the *linux/boot/vmlinz*..etc lines in all the Lucid entries above it to include the "i8042" entry. Which is the entry I had to make which enables the touchpad to function. While this is basically what I wanted in the first place it's not what I expected. 

Questions; Is this normal for grub2, Where is the 40_custom entry I made?

---

### Post by drs305 on 2010-10-14
> **skew said:**
> Another strange result is that making this entry into the 40_custom file has somehow changed all the *linux/boot/vmlinz*..etc lines in all the Lucid entries above it to include the "i8042" entry. Which is the entry I had to make which enables the touchpad to function. While this is basically what I wanted in the first place it's not what I expected. 

Questions; Is this normal for grub2, Where is the 40_custom entry I made?

No it's not normal. Probably the first thing to do is to run the boot info script which will show us what is in the grub.cfg file. You might also post your 40_custom contents.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Without seeing the results, one thing I can think of is that Grub2 is using the grub.cfg file from your other Ubuntu installation. If you update grub in the 'non-booting' Ubuntu, you will see grub update in the terminal but since it's not the grub.cfg pointed to by the MBR contents it won't display the changes. 

Here is a link for making a custom menu - you can check it just to be sure it was constructed properly:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu")

---

### Post by skew on 2010-10-14
Thanks again. I'll have to get back to you on that the next time I get some freetime. I do appreciate the help you've given.

Unfortunately I'm also contending with a slew of other problems with this Sony Vaio F series. From audio problems(alsa) to video(Nvidia) and non functional firewire port, etc. So many issues besides the touchpad. The list of incompatibilities seems endless. I'd return it to the store if I could. The damn thing is nothing but a major migraine.

 If anyone is counting I'd strongly suggest that if you are in the market for a laptop that you consider getting yours from another manufacturer.:mad:

---

