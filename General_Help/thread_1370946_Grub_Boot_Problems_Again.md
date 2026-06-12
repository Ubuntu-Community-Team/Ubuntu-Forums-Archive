---
title: "Grub Boot Problems Again"
date: 2010-01-02
forum: General Help
---

### Post by boosterjet on 2010-01-02
Hi all, this is my first post so I hope I have come to the right place.
Have just installed karmic two days ago. Installed cleanly  but I am having a lot of problems with the "GRUB". I have two separate hard drives on my computer a 160GB which has Windows XP and a 80 GB drive that was just sitting there so I installed Ubuntu there - no problems so far. However trying to get Grub2 to boot into Windows is driving me nuts. I have read all the different methods and all the posts here and google and none seem to work! Startup Manager loaded and did nothing so I unloaded it, now its not available any more. I edited the grub menu with the sudo set-grub-default command and I have the print out of File:/etc/default/grub in front of me and the first entry shows GRUB_DEFAULT=6 (which is the entry number for Windows on the Grub menu. Updated Grub - still no change- boots straight to Ubuntu. My BIOS has Windows as the first boot disc shown as IDE Channel 0 Master and IED Channel 0 Slave for Ubuntu. What can I try now. Many thanks John :confused:

---

### Post by john newbuntu on 2010-01-02
Are you able to at least choose the windows menu in Grub and boot to Windows normally?

If I am right, in order to set the first grub entry as default, the GRUB_DEFAULT has to be set to 0.  So if you find windows as the 6th entry in the menu, then set GRUB_DEFAULT=5 and run "sudo update-grub2".
Your other option is to set GRUB_DEFAULT=saved so that when you choose to boot into windows once, Ubuntu remembers this and will boot again on to Windows the next time around.

---

### Post by boosterjet on 2010-01-02
Thanks, yes I can boot to windows normally from the grub menu where it sits at number 7 on the list hence default number 6

---

### Post by boosterjet on 2010-01-02
I will now try the saved option

---

### Post by boosterjet on 2010-01-02
I have edited the grub file to saved - loaded and unloaded windows still booting back to line 0 -Linux,2-6-31-16-generic

---

### Post by boosterjet on 2010-01-03
Bump..... I  really do need to solve this.

---

### Post by john newbuntu on 2010-01-03
Did you run "sudo update-grub2" after you set the saved option?

---

### Post by Leppie on 2010-01-03
Hi and welcome to the community,
Check the exact menu entry with the following command:
```
cat /boot/grub/grub.cfg | grep Windows
```
if you're menu entry looks something like "Microsoft Windows XP (on /dev/sda2)" you need the complete entry including the part in between the brackets.
then open your grub defaults file:
```
gksudo gedit /etc/default/grub
```
change the option GRUB_DEFAULT=0, if you set it to a custom choice I'd suggest changing from numbers to the text found with the previous command:
```
GRUB_DEFAULT="Microsoft Windows XP (on /dev/sda2)"
```
regenerate your grub.cfg:
```
$sudo update-grub
```

---

### Post by Leppie on 2010-01-03
i think the sudo grub-set-default command is for grub legacy and not for grub2 (the one in karmic).

---

### Post by boosterjet on 2010-01-03
Tried that for info this is what happened 
  	 	 	 	 	 	  ohn@john-desktop:~$ gksudo gedit /etc/default/grub 
 john@john-desktop:~$ $sudo update-grub 
 debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied 
 Searching for GRUB installation directory ... found: /boot/grub 
 /etc/default/grub: line 4: syntax error near unexpected token `(' 
 john@john-desktop:~$ ^C 
 john@john-desktop:~$ 



I tried it before without the brackets - no good

---

### Post by boosterjet on 2010-01-03
This is what the etc/ file looks like now, as Windows is the 7th entry on the grub menu I think I'll go back to Default=6. 
  	 	 	 	 	 	  # If you change this file, run 'update-grub' afterwards to update 
 # /boot/grub/grub.cfg. 
  
 GRUB_DEFAULT=Microsoft Windows XP Home Edition (on/dev/SDA1) 
 #GRUB_HIDDEN_TIMEOUT=0 
 GRUB_HIDDEN_TIMEOUT_QUIET=true 
 GRUB_TIMEOUT=10 
 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` 
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
 GRUB_CMDLINE_LINUX="" 
  
 # Uncomment to disable graphical terminal (grub-pc only) 
 #GRUB_TERMINAL=console 
  
 # The resolution used on graphical terminal 
 # note that you can use only modes which your graphic card supports via VBE 
 # you can see them in real GRUB with the command `vbeinfo' 
 #GRUB_GFXMODE=640x480 
  
 # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux 
 #GRUB_DISABLE_LINUX_UUID=true 
  
 # Uncomment to disable generation of recovery mode menu entrys 
 #GRUB_DISABLE_LINUX_RECOVERY="true"

---

### Post by boosterjet on 2010-01-03
I'm bumping this again - surely some one out there knows how to make these changes work. It looks like the file is writing OK buy just not executing (if that makes sense). This is the tutorial I have been using:-
                                  [COLOR=#000080][SIZE=3]**Lifted from Drs305 Tutorial and Tips  Oct 28**[/SIZE][/COLOR][COLOR=#000080][SIZE=3]**th**[/SIZE][/COLOR][COLOR=#000080][SIZE=3]** 2009**[/SIZE][/COLOR]
 [COLOR=#000080][SIZE=3]**Menu Default Entry**[/SIZE][/COLOR]
File: */etc/default/grub*
Line to edit (4): *DEFAULT=0*
Example: *DEFAULT=1* # (The second "menuentry" item).

There are several ways to update the default selection in GRUB 2. Below are choices for using a simple GUI app to make the change for you, a manual way via editing the GRUB 2 files. A third method, using the command "grub-set-default" does not appear to work in GRUB 2 with Ubuntu at this time.
 
[LIST=1]
[*]StartUp-Manager: For those who prefer a GUI app to change the     default selection.
If you want a simple, GUI-based app that can     change the default entry, you can install and run StartUp-Manager.     This app was written for Grub legacy but still works for this option     in Grub 2. Click on the "SUM" link in my signature line     for instructions on how to install and an explanation of the various     settings you can change with StartUp-Manager.
[*]"sudo grub-set-default"
If the /etc/default/grub     "DEFAULT=" setting is set to "saved", you can     change the default setting at any time by running "sudo     grub-set-default [COLOR=#ff0000]X[/COLOR]", with [COLOR=#ff0000]X[/COLOR]     being either the menuentry position (the first menuentry is 0), or     with the exact menu string from the menuentry. For more details,     refer to [Grub     2 Basics]("http://ubuntuforums.org/showthread.php?t=1302743").
Examples: *sudo grub-set-default 3* or *sudo     grub-set-default "Ubuntu, Linux 2.6.31-14-generic"*
[*]Edit the Files: Get to Know GRUB     2

If you prefer to change the GRUB 2 files manually:

You     can see the current "menuentry" items listed in the     */boot/grub/grub.cfg* by running this command:
     Code:
     grep "menuentry" /boot/grub/grub.cfg     Counting starts with zero (0). The first "menuentry" item     is "0", the second is "1", etc. The third     visible "menuentry" would be 2. 

Determine the     number you wish to make the default, and enter it in     */etc/default/grub*. Make the change and save the file.
     Code:
     gksu gedit /etc/default/grub     The user can also select "saved" as an option, which will     use the last successfully booted kernel/OS as the default     selection.
Example: DEFAULT="saved"

Save the     file, then update the menu:
     Code:
     sudo update-grub
[/LIST]

---

### Post by Leppie on 2010-01-03
You need to use double quotes (as per the instructions i provided in post #8 ). If you don't use the double quotes, the brackets will have special meanings for the processing script.
so it should look like this:
```
GRUB_DEFAULT=**"**Microsoft Windows XP Home Edition (on /dev/SDA1)**"**
```

---

### Post by boosterjet on 2010-01-03
OK,done all that - still boots to linux. Here a copy of the grub menu file

  	 	 	 	 	 	  john@john-desktop:~$ grep "menuentry" /boot/grub/grub.cfg  
 menuentry "Ubuntu, Linux 2.6.31-16-generic" {  
 menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {  
 menuentry "Ubuntu, Linux 2.6.31-14-generic" {  
 menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {  
 menuentry "Memory test (memtest86+)" {  
 menuentry "Memory test (memtest86+, serial console 115200)" {  
 menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {  
 john@john-desktop:~$ 



Here a copy of the default file


   	 	 	 	 	 	  # If you change this file, run 'update-grub' afterwards to update  
 # /boot/grub/grub.cfg.  
 

 GRUB_DEFAULT="Microsoft Windows Home Edition (on /dev/sda1)"  
 #GRUB_HIDDEN_TIMEOUT=0  
 GRUB_HIDDEN_TIMEOUT_QUIET=true  
 GRUB_TIMEOUT=10  
 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`  
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"  
 GRUB_CMDLINE_LINUX=""  
 

 # Uncomment to disable graphical terminal (grub-pc only)  
 #GRUB_TERMINAL=console  
 

 # The resolution used on graphical terminal  
 # note that you can use only modes which your graphic card supports via VBE  
 # you can see them in real GRUB with the command `vbeinfo'  
 #GRUB_GFXMODE=640x480  
 

 # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux  
 #GRUB_DISABLE_LINUX_UUID=true  
 

 # Uncomment to disable generation of recovery mode menu entrys  
 #GRUB_DISABLE_LINUX_RECOVERY="true"


The command line has been copied exactly, and here a copy of the update log


   	 	 	 	 	 	  john@john-desktop:~$ gksu gedit /etc/default/grub  
 john@john-desktop:~$ sudo update-grub  
 Searching for GRUB installation directory ... found: /boot/grub  
 Searching for default file ... found: /boot/grub/default  
 Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst  
 Searching for splash image ... none found, skipping ...  
 Found kernel: /boot/vmlinuz-2.6.31-16-generic  
 Found kernel: /boot/vmlinuz-2.6.31-14-generic  
 Found GRUB 2: /boot/grub/core.img  
 Found kernel: /boot/memtest86+.bin  
 Updating /boot/grub/menu.lst ... done  
 

 WHAT NOW ??

---

### Post by boosterjet on 2010-01-04
Bump....

---

### Post by boosterjet on 2010-01-04
Ok been siting on this overnight -still no nearer to a solve, however looking at copies made of the update files, one shown above - Grub recognises two linux kernels, itself, and a MEM kernel, it does not even find Windows so I cannot see how it can default too it. What gives?

---

### Post by boosterjet on 2010-01-04
Doesn't seem to matter, have tried changing default to another menu item other than Windows - still defaults to "Ubuntu, Linux 2.6.31-16-generic" . Will not go any where else. Naughty maggot!!

---

### Post by boosterjet on 2010-01-05
OK looks like I have to give up on this. Nobody seems to be able to give me a solution. Many thanks anyway.Now looks like I will have to un-install, shame the system looks good and works well, but I do need the first boot preference to be Windows. Thanks again.

---

### Post by boosterjet on 2010-01-06
If any one is interested I put another request for help on the Upgrade & Installation forum where I received excellent help from Kansasnoob. Many thanks again and the problem is now solved. If interested you can see what we did on that forum.

---

