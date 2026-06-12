---
title: "Anyone who is GOOD with ubuntu please help me this is frustrating me so much."
date: 2010-10-28
forum: General Help
---

### Post by jameshampshire on 2010-10-28
Ok so I've checked out threads.
None of them answer my problem.

For about 2 months now i can't install or upgrade certain packages because of THIS DAMN ERROR linux-image-2.6.32-24-generic-pae

I thought with updates it would fix my problem and it hasn't.
I've checked on other threads they don't fix my problem.
For the love of god can someone please help me.

My main dist is kubuntu but the same thing happens on ubuntu and lubuntu and so on and so fourth.

---

### Post by rajeevisonline on 2010-10-28
Please cite more info so that if not me, someone else will be able to help you...

what are the packages you are trying to update?

what is the exact error message you are getting with the -pae image file?

are you using synaptic to install or update..i would suggest using apt-get...synaptic includes so many packages..its graphical and easy..but you could end up installing conflicting packages..because it gives you several alternatives for dependencies to satisfy..sometimes the option you pick may conflict with another package..this may not be the answer to your question i am only trying to help

---

### Post by jameshampshire on 2010-10-28
ANY packages i try to install or update that's why i'm so frustrated.
Everything i try to install or update ends up with that error message.
And i tried apt get which was reccomended on another post but it does the same thing.


This is the error:

E: linux-image-2.6.32-24-generic-pae: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.32-25-generic-pae: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic-pae: dependency problems - leaving unconfigured
E: linux-generic-pae: dependency problems - leaving unconfigured

---

### Post by jameshampshire on 2010-10-28
And i also tried the fix dependency's it says fixed but it isn't fixed.
Does the same thing.

---

### Post by DaninFuchs on 2010-10-28
We're gonna need a bigger block than just those few lines. Post the entirity of the output after an apt-command, like 'apt-get upgrade' - then post *everything* that comes out after that, until your prompt.

---

### Post by drpjkurian on 2010-10-28
Hi
Will you try this command
```
dpkg --purge nvidia-common; dpkg --configure -a
```

---

### Post by rajeevisonline on 2010-10-28
try to force apt-get to ignore dependencies with --ignore-missing
or use dpkg with the option --ignore-depends

i really hope someone can suggest a better solution..its a problem involving the kernel image..i wouldnt suggest removing anything 

but the advantage you have since you are using -pae, u have a very good system with lots of RAM you can always use remastersys to create a complete backup of your system will take u less than half an hour, open up a virtual machine, and install this as the OS. this way u have a mirror image of what you have in a virtual machine...you can do all the testing there and if anything works replicate it in your actual OS

i am sure the experts will come up with a better answer...one thing i like about these forums is that almost every question is answered

---

### Post by jameshampshire on 2010-10-28
[FONT=monospace]I get this.

dpkg: warning: ignoring request to remove nvidia-common which isn't installed.
dpkg: requested operation requires superuser privilege


i think because i removed it previously because i read on another post to do so but it didn't fix my problem.
[/FONT]

---

### Post by jameshampshire on 2010-10-28
Here's the entire output.


james@james-desktop:~/Documents$ apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
james@james-desktop:~/Documents$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.32-24-generic-pae (2.6.32-24.43) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic-pae
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-24.41 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-24.41 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 28: Syntax error: EOF in backquote substitution
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.32-24-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.32-25-generic-pae (2.6.32-25.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic-pae
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 28: Syntax error: EOF in backquote substitution
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.32-25-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-2.6.32-25-generic-pae; however:
  Package linux-image-2.6.32-25-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 2.6.32.25.27); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        Errors were encountered while processing:
 linux-image-2.6.32-24-generic-pae
 linux-image-2.6.32-25-generic-pae
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by allu john sudhakar on 2010-10-28
:KS   	 	 	 	p { margin-bottom: 0.21cm; }  I have P4 system in my home and system configaration is  
 

 BIOS: Mother Board version ZX-865v v1.0 (2009-04-22-4m)
 Processor: Intel(R) Pentium(R) CPU 2.40 Ghz
 Memory: 1024 MB RAM
 

 Display:   
 

 Name: NVIDIA GeForce FX 5500
 Manufacture: NVIDIA
 Chip Type: GeForce FX 5500
 DACType: Integrated RAMDAC
 Approx Total Memory:256.0MB
 Current Display mode: 1024X768(32bit)(60HZ)
 Monitor: Plug and Play monitor
 and in that system i have SAMSUNG HD321Hj hard disk of 320GB and made three partitions (C D E) in that i have installed xp with sp3 in C & D partitions and in E pratition i installed ubuntu 9.10.
 

 in this month ubuntu 10.10 was released and i  tried to install ubuntu 10.10 on my system. Instalation was not done because of NVIDIA Graphic Card, as this card supports only windows vista and xp. Ubuntu is a free and open source software and so it will not support NVIDIA Graphic card. This is where the problem lies  
 

 So I want to Install ubuntu 10.10 along with xp. First i have removed NVIDIA Graphic Card on my system and installed ubuntu 10.10. And after installation is over i opned my internet conncetion and i gon to system/Administration you will see 15(fifteen subheadings like disk utitity, Login screen, priting etc..,). In that i have gon to update manager and install updates.
 

 After updating i shutdown my computer and  put graphic card (NVIDIA)  and  started my system
 

 when system start box will open with five options that is  
 ubuntu with Linux 2.6.35.22 generic
 ubuntu with Linux 2.6.35.22 generic(Recovery mode)
 Memory test (memtest86+)
 memory (memtest 86+, serial console 115200)
 microsoft windows xp professional (on/ext/sda1)
 

 go to 2nd option (ubuntu with Linux 2.6.35.22 generic(Recovery mode) and press enter after entering a few seconds later it will ask to enter once again press enter now  
 

 after enter you will see Recovery menu box will open with six options
 

 resume   resume normal boot
 

 clean  Try to make free space
 

 dpkg   repair broken packages
 

 failsafex   Run infailsafe graphic mode 
 

 grub  update grub boot
 

 netroot   loader drop to root shell prompt with networking
 

 now go to 5th option(grub  update grub boot) press enter and later go to 3rd option
 

 now go to 4th option (failsafex   Run infailsafe graphic mode ) press enter
 

 now it will open your new ubuntu 10.10 after open your system you have right click on desktop
 

 it will open one window in that goto change desktop back ground option
 

 and now you have to go visual effects
 

 you will find 3 options goto 2nd option that is ( Normal:  provides improved usability and good balance between attractiveness and moderate performance requirements). It will take update of your graphic card through internet (inter net connection shoud open on your system) after downloding update system will ask for restart you shoud restrat your system  
 

 after restarting system  once again your have to go system/administrator now you will see 16 (sixteen) option in that one is new that is NVIDIA Xserver setting  
 

 open NVIDIA Xserver setting now after open you have to go  
 xserver display congiguration you will see model and resolution size (1024X768)
 

 in this way i have installed ubunt 10.10 with NVIDIA GE force FX 5500 graphic card.
 

 Do samething and enjoy now
 

 Allu John Sudhakar
       System/Network Administrator
       UCE,OU  Osmania University  
       Hyderbad
     
  any help mail to me [email]aj_sudhakar@yahoo.co.in[/email]

---

### Post by DaninFuchs on 2010-10-28
Blindly purging entire packages and ignoring dependency problems is only going to cause more problems. What we need is more information. Post the entirity of the output of something such as 'apt-get upgrade' and we might be able to help, but we do need that information to proceed. Or at least, I do - otherwise I feel like I'd be guessing randomly.


EDIT: Didn't notice you had posted it, let me review..one moment..

---

### Post by DaninFuchs on 2010-10-28
Your problem is an issue with your /etc/default/grub file - check that with an editor of some form - I use nano, personally - and if you can't find an issue yourself, post its contents here.

---

### Post by jameshampshire on 2010-10-28
Hey mate i'll let you edit it you're probably smarter at using linux then i am.

```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 479fd27e-84aa-43f7-bb95-de89a107461e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 479fd27e-84aa-43f7-bb95-de89a107461e
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 479fd27e-84aa-43f7-bb95-de89a107461e
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=479fd27e-84aa-43f7-bb95-de89a107461e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 479fd27e-84aa-43f7-bb95-de89a107461e
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=479fd27e-84aa-43f7-bb95-de89a107461e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 479fd27e-84aa-43f7-bb95-de89a107461e
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=479fd27e-84aa-43f7-bb95-de89a107461e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 479fd27e-84aa-43f7-bb95-de89a107461e
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=479fd27e-84aa-43f7-bb95-de89a107461e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 479fd27e-84aa-43f7-bb95-de89a107461e
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=479fd27e-84aa-43f7-bb95-de89a107461e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 479fd27e-84aa-43f7-bb95-de89a107461e
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=479fd27e-84aa-43f7-bb95-de89a107461e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 479fd27e-84aa-43f7-bb95-de89a107461e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 479fd27e-84aa-43f7-bb95-de89a107461e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

---

### Post by DaninFuchs on 2010-10-28
Wrong file. But I figured it out for you. Known bug. Edit /etc/default/grub - willing to bet yours looks similar to this, on the first few lines.

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="

```See where GRUB_CMDLINE_LINUX ends in =" there? You want a second quote. Change the line to read;
```

GRUB_CMDLINE_LINUX=""

```Then run update-grub as it suggests. Should take care of your problem.


EDIT: Also, found this too. Lead me to the fix.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/575823](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/575823)

---

### Post by jameshampshire on 2010-10-28
Hey man i can't find that part in the cfg.
Could you edit it into the grub file i posted and post it here so i can delete all the info out of the grub file i did and paste the fix you have. Sorry for the hassle. I'm just new to all this editing in ubuntu. I'm trying to get the run of things after being on windows for so long.

---

### Post by Elfy on 2010-10-28
Open a terminal - apps > accessories menu to open the file for editing as root

```
gksudo gedit /etc/default/grub
```

The line should be easy enough to find.

Update grub from the terminal

```
sudo update-grub
```


You don't want to edit the cfg file - it get's rewritten by the system and any changes you make will be gone.

---

### Post by jameshampshire on 2010-10-28
Thanks dude helped out.
I'll edit it now and see how it goes.

---

### Post by jameshampshire on 2010-10-28
I have a second quote on there.
This is what mine looks like.


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=1
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap""
GRUB_CMDLINE_LINUX=" vga=792 splash"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=1280x1024

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by DaninFuchs on 2010-10-28
EDIT: Nevermind, missed a few posts..

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap""
```

Related issue, wrong line - remove the second quote at the end. I was close though, haha.

---

### Post by jameshampshire on 2010-10-28
Mate you're a legend!.

I posted asking for help on this like 5 different occasions and you're the only decent bloke to help me on it. Thank you big time.

---

### Post by DaninFuchs on 2010-10-28
Hey man, you're totally welcome. Really though, be fair - this isn't your average problem, there were definitely others trying to help along the way. I can't take all the credit. Thilled to hear it's going though - ironically, I was only here tonight to try to find a resolution for my own problem, which presently remains unfixed. Haha. Enjoy!

---

### Post by jameshampshire on 2010-10-28
Hey mate sorry for a late reply on this.
I booted my pc today and it came up with this scrolling info then took me to the grub menu.
Saying their is a problem with my display, all i can do atm is run it in low graphics mode it gives me the option installing broken packages but it didn't fix my problem. I know it's a problem that can be fixed easy could you or someone sort me out? im in low graphics mode right now.

---

### Post by jameshampshire on 2010-10-28
Bumping. (Because I'm stuck in shitty low graphics mode).

---

### Post by HarvesterOfSorrow on 2010-10-28
hey can anyone help me. i just installed ubuntu and i have ran all the up date

but i cant find a way to get the visual effects to stay on extra.

when i click on extra it finds my drivers(nvidia 9500 GT) and apparently it loads just fine 

it says its on extra so i exit and then its like nothing took effect and yes i clicked the dialoug box that says keep settings 

can somebody help me?

---

### Post by jameshampshire on 2010-10-28
This is more help for you guys to help me on.

james@james-desktop:~$ nvidia-xconfig

WARNING: Unable to locate/open X configuration file.


ERROR: Unable to write to directory '/etc/X11'.

james@james-desktop:~$ sudo nvidia-xconfig
[sudo] password for james: 

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'

james@james-desktop:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

---

### Post by jameshampshire on 2010-11-10
Hey guys i'm still stuck with the grub boot menu and only being able to boot in low graphics mode

---

