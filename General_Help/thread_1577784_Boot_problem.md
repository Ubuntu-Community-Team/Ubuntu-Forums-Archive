---
title: "Boot problem"
date: 2010-09-19
forum: General Help
---

### Post by geum on 2010-09-19
x86 64
After a recent kernel update Lucid boots up ok until it gets to the jingle sound,then it goes into a kaliedascope of flashing colours which I can do nothing with until I press Crtl+Alt+F7 then I get my Desktop and everything is ok.
Thank you for any help.

---

### Post by sanderj on 2010-09-19
Can you see (and thus boot) older kernels at startup?

---

### Post by geum on 2010-09-20
sanderj

There is another kernel in the boot menu,but if I select it,it says "no file found press any key to continue".

---

### Post by Rubi1200 on 2010-09-20
What graphics card do you have installed?

---

### Post by geum on 2010-09-20
Rubi1200

Graphics card.ATI Radeon X300 (PCIE)

---

### Post by Rubi1200 on 2010-09-20
Hi,
as the computer boots hold down "Shift" so that the GRUB menu comes up.

Highlight the kernel entry and press "e" to edit.

Find the line that ends with ```
ro quiet splash
``` and remove quiet splash and replace it with xforcevesa

Then "Ctrl" + "x" to boot.

See what happens and report any problems please.

---

### Post by geum on 2010-09-20
Pressing e to edit the kernel I get:

```
uuid ddd3c509-c3ce-4c53-97e2-c401c-7529192
kernel /boot/vmlinuz-2.6.31.19-generic root=(the above number)
initrd /boot/initrd.img-2.6.31-19-generic
quiet
```


Here is my /boot/grub/menu.lst

```
title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		ddd3c590-c3ce-4c53-97e2-c401c7529192
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=ddd3c590-c3ce-4c53-97e2-c401c7529192 ro splash quiet 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		ddd3c590-c3ce-4c53-97e2-c401c7529192
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=ddd3c590-c3ce-4c53-97e2-c401c7529192 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		ddd3c590-c3ce-4c53-97e2-c401c7529192
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=ddd3c590-c3ce-4c53-97e2-c401c7529192 ro splash quiet 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		ddd3c590-c3ce-4c53-97e2-c401c7529192
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=ddd3c590-c3ce-4c53-97e2-c401c7529192 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, memtest86+
uuid		ddd3c590-c3ce-4c53-97e2-c401c7529192
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



```

---

### Post by geum on 2010-09-20
Forget my last post I changed the kernel line to forcevesa as you suggested and it is working fine now.
Will I have to do the same in /boot/grub/menu.lst

---

### Post by Rubi1200 on 2010-09-20
I don't understand something; the file shows you have 9.10 but in your original post you said Lucid. Moreover, Ubuntu versions from 9.10 on use GRUB2, you seem to have legacy-GRUB. Did you upgrade from 9.04 and retain the option to keep legacy-GRUB?

---

### Post by geum on 2010-09-20
Rubi1200

Yes you are quite right something does not add up,sysinfo says I am running 10.04 Lucid,and when I am updating all my updates come from the Lucid repositories,but my menu.lst shows 9.10.
As for Grub I dont recall keeping legacy Grub,but to be honest I cant be sure.

---

### Post by geum on 2010-09-20
Rubi1200

Sorted it all out from the link below,upgraded from legacy GRUB to GRUB2,everything working fine,except it did'nt find my second hard drive with FreeBSD on.
In /boot/grub/menu.lst I should have moved the FreeBSD entry up in the same designated area as the Ubuntu entries,I did'nt find this out until after I upgraded to GRUB2,so now there is no menu.lst to edit.
How can I add my FreeBSD to the boot menu. 

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Rubi1200 on 2010-09-20
I was actually going to suggest you upgrade to GRUB2.

Did you run```
 sudo update-grub
```

I would have thought it would pick up FreeBSD; the OS prober in GRUB2 is pretty good.

Try the command above and if it still does not show we will try and find a solution.

---

### Post by geum on 2010-09-20
Yes I tried update-grub after I upgraded,but I have just done it again but it still only shows the Ubuntu entries and mem test.

---

### Post by Rubi1200 on 2010-09-21
Ok, I am going to assume that the FreeBSD partition is still there.

Take a look at this link for ways to add custom menu entries to GRUB:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I think in your situation the relevant sections are 5 and 6.

If you need more help, feel free to ask.

---

### Post by geum on 2010-09-21
Rubi1200

Thank you for all your help,I did read sections 5and6 as it was on the same page as GRUB2 upgrade,just two more questions.

```
menuentry "FreeBSD-8.0" { 
set root=(hd1,0)
}
```
Is this the right entry I should enter in /etc/grub.d/40_custom
The root entry is the same as it was in /boot/grub/menu.lst.

And when I chmod +x /etc/grub.d/? what should the filename be.

---

### Post by Rubi1200 on 2010-09-21
> **geum said:**
> Rubi1200

Thank you for all your help,I did read sections 5and6 as it was on the same page as GRUB2 upgrade,just two more questions.

```
menuentry "FreeBSD-8.0" { 
set root=(hd1,0)
}
```Is this the right entry I should enter in /etc/grub.d/40_custom
The root entry is the same as it was in /boot/grub/menu.lst.

And when I chmod +x /etc/grub.d/? what should the filename be.
Is hd1 an external device? 
If you have just one device it would be hd0 and then I believe you add the entry such that it adds the partition where you have the OS e.g. hd0,3 etc.

The filename depends on how you want GRUB to "read" the file e.g. if the OS is last in the GRUB menu list you would create a file called 41_custom but if you wanted it higher in the menu you could do something like 07_custom.

Also, you must run ```
sudo update-grub
``` afterwards so it is added.

See here for a more detailed explanation:
> **[COLOR=Navy][SIZE=3]Adding Entries to Grub 2[/SIZE][/COLOR] **
Menu entries can be added to [COLOR=DarkRed]grub.cfg[/COLOR] automatically or manually.
[LIST]
[*][SIZE=3]**[COLOR=DarkRed]Automatically.[/COLOR]**[/SIZE]
[LIST]
[*]When "[COLOR=Navy]*update-grub*[/COLOR]" or "[COLOR=Navy]*update-grub*[/COLOR]"  is executed, Grub 2 will search for linux kernels and other Operating  Systems. What and where is looks is based on the files contained in  /etc/grub.d folder.
[LIST]
[*][COLOR=DarkRed]10_linux[/COLOR] searches for installed linux kernels on the same partition.
[*][COLOR=DarkRed]30_os-prober[/COLOR] searches for other operating systems.
[/LIST]
 
[/LIST]
[*][SIZE=3]**[COLOR=DarkRed]Custom User Entries  (/etc/grub.d/40_custom).[/COLOR]**[/SIZE]
[LIST]
[*]Entries to [COLOR=DarkRed]*grub.cfg*[/COLOR] can be manually inserted by creating a file in the /etc/grub.d folder.
[LIST]
[*]The  name of the file determines the order in the menu. 30_os-prober entries  will be placed before 40_custom entries, which will be placed before  50_my-sample entries.
[*]Any created file must be made executable. This can be done as root by running "sudo chmod +x /etc/grub.d/*filename*".
[*]The files in the /etc/grub.d folder will be read and the contents included in [COLOR=DarkRed]*grub.cfg*[/COLOR] when the "[COLOR=Navy]*update-grub*[/COLOR]" command is executed as root.
[/LIST]
[*]A sample entry. This file creates a menu item for running the  SystemRescueCD (previously installed) from a partition created on sda10.  Folders and files must have been copied to the correct location in  accordance with the SystemRescueCD if you wish to actually use this  entry. *Note this entry will not work for a SystemRescue ISO. See Section 14 for instructions on how to add an entry to boot ISO images*.
[LIST]
[*] 	Quote:
 	 	 		 			 				#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "System Rescue CD" {
        set root=(hd0,10)
        linux   /sysrcd/rescuecd subdir=sysrcd setkmap=us
        initrd  /sysrcd/initram.igz
}  			 		 	 	 
[*]**[COLOR=Red]Note the new partition naming convention.[/COLOR]** Devices start counting from "0" as done previously. sda is designated as "hd0", sdb is "hd1", etc. However the first *partition* is now designated as **sda1**. Counting *partitions* does **not** start with "0". sda5 is "5".
[*]If the user wishes to get visual confirmation in the terminal that  the 40_custom file contents are being added when "update-grub" is  executed, the following line can be added to the /etc/grub.d/40_custom  file:
[LIST]
[*] 	Quote:
 	 	 		 			 				*[COLOR=Purple]echo "Adding 40_custom menu entries." >&2[/COLOR]* 			 		 	 	 
[*]Place this line immediately after the first line - "#!/bin/bash" - and before the "exec tail -n +3 $0" line.
[/LIST]
 
[/LIST]
[*]**[COLOR=DarkRed]Tip[/COLOR]:** If you want to have your  custom entries at the top of the menu (say you want custom titles),  create a new file and name it "07_xxxx". Since the files in /etc/grub.d/  are read sequentially, those in "07_custom" will be placed before those  of "10_linux". I recommend not naming a custom menu file lower than 06  so that any theme run from 05_debian_theme is allowed to run before any  custom menu is created. After creating the file, run *sudo update-grub* and then check the value of "DEFAULT" in */etc/default/grub*. If it doesn't point to the correct *menuentry*, change the value of *DEFAULT* to the correct *menuentry* value.
[*]**[COLOR=DarkRed]Omitting memtest86+[/COLOR]:** To prevent  "memtest86+" entries in your Grub 2 menu, remove the "executable" bit  from /etc/grub.d/20_memtest86+. You can do this via a file browser by  selecting "Properties (right click), Permissions", or via the command  line:
 	Code:
 	sudo chmod -x /etc/grub.d/20_memtest86+ 
[*]**[COLOR=DarkRed]Omitting Recovery Mode entries[/COLOR]:** **The file /etc/grub.d/10_linux was recently updated to include a check for recovery mode options.** Edit /etc/default/grub and add or change this line:
 	Quote:
 	 	 		 			 				GRUB_DISABLE_LINUX_RECOVERY=true 			 		 	 	 
If you have an older version of /etc/grub.d/10_linux and the above  does not work after updating grub, you can prevent "Recovery mode"  entries in your Grub 2 menu, by editing /etc/grub.d/10_linux. If there  are no conditional "if" statements concerning the recovery mode, place a  comment symbol (#) in front of the following lines (at approximately  line 146) of the old file:
 	Quote:
 	 	 		 			 				**[COLOR=DarkRed]#[/COLOR]** linux_entry "${OS}, Linux ${version} (recovery mode)" \
**[COLOR=DarkRed]#[/COLOR]** "single ${GRUB_CMDLINE_LINUX}" 			 		 	 	 
If you wish to retain one "Recovery mode" entry for insurance, you  can add an entry to /etc/grub.d/40_custom which will appear at the  bottom of your grub menu.
[*]**[COLOR=DarkRed]Building a Totally Customized Menu[/COLOR]:** Ok, admit you are a control freak and you want to see only what you build yourself - customized titles, no "*memtest86+*" and no extra kernels. Here is how you do it:
[LIST]
[*]Run *sudo update-grub* to get the current available kernels.
[*]Copy the desired "menuentry" listings from /boot/grub/grub.cfg to  /etc/grub.d/40_custom The entry begins with the line starting with  "menuentry" and ends with a line containing "}".
[*]Add any other "menuentry" items you wish to see on the boot menu.
[*]Edit the titles of the "menuentry" line if desired (between the  quotation symbols). Do not change the lines following the "menuentry"  line. Each entry should start with a "menuentry" line and end with a "}"  on the last line.
[*]Remove the executable bit from */etc/grub.d/10_linux, /etc/grub.d/20_memtest86+* and */etc/grub.d/30_os-prober*
Removing the executable bit from any file in /etc/grub.d will exclude the file from being included in grub updates.
 	Code:
 	sudo chmod -x /etc/grub.d/10_linux /etc/grub.d/20_memtest86+ /etc/grub.d/30_os-prober 
[*]Run "sudo update-grub"
[*]The updated /boot/grub/grub.cfg file should now contain only sections for "00_header", "05_debian_theme" and "40_custom".
[*]The grub.cfg file will not be updated with the addition of a new  kernel. To add a new kernel, make "10_linux" executable, run "sudo  update-grub" to refresh the available kernels, and repeat these  instructions.
[/LIST]
[*][COLOR=DarkRed]**Don't forget to run "sudo update-grub" after making any changes to your /etc/grub.d files.**[/COLOR]
[/LIST]
[/LIST]

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by geum on 2010-09-21
```
#!/bin/sh
echo "Adding 40_custom menu entries." >&2
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry FreeBSD-8.0 {
set root=(hd1,0)
}
```

I also did chmod +x /etc/grub.d/40_custom then update-grub
but it still does not find my FreeBSD o/s.
hd1(sdb) is my second internal drive where FreeBSd is installed.
hd0(sda) is my first internal drive where Ubuntu is installed.
The set root entry above(hd1,0)was how it was set in /boot/grub/menu.lst

---

### Post by Rubi1200 on 2010-09-21
Does FreeBSD take up the whole drive or are there other partitions/operating systems?

EDIT: try this; instead of using hd1,0 set it to hd1,1 and see what happens after updating grub.

---

### Post by geum on 2010-09-21
FreeBSD takes up the whole drive the same goes for Ubuntu on the other drive.

---

### Post by Rubi1200 on 2010-09-21
Did you see my edit above?

---

### Post by geum on 2010-09-21
Set it to hd1,1 updated grub still no joy.

---

### Post by Rubi1200 on 2010-09-21
I am a little bit stumped here with this one. 

I was looking at another post where someone pointed out that GRUB2 changed the convention regarding where the counting of partitions starts.

Then I noticed something else, namely that the poster pointed out if this is for other operating systems that use GRUB as the bootloader.

Correct me if I am wrong, but I don't think FreeBSD uses GRUB.

May I suggest you either ask on the FreeBSD forum or wait to see if someone else here has an idea how to solve this.

If I find anything else in the meantime I will post back and let you know.

Sorry I am not able to help more with this.

EDIT: I am determined to try and help you even if it kills me (just kidding)

I found this:
[http://forums.freebsd.org/showthread.php?t=14199](http://forums.freebsd.org/showthread.php?t=14199)

---

### Post by geum on 2010-09-21
```
menuentry "FreeBSD" {
insmod ufs2
set root=(hd1,1)
chainloader +1
}
```
Thank you for the link,it done the business,FreeBSD is back on the menu,and to prove it I am typing this in the very same.
Rubi1200 I want to thank you for your patience in putting up with me for so long.

---

### Post by Rubi1200 on 2010-09-21
Believe me you are more than welcome :D
Enjoy!

---

