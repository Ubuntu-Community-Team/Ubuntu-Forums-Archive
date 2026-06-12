---
title: "Grub 2 Boot order for dual boot Ubuntu/Windows"
date: 2012-02-10
forum: General Help
---

### Post by edw666 on 2012-02-10
Hello everybody,

I know this is probably an old question but how do you set Windows in a  dual boot environment to boot first?  My understanding is that you have  to set  a value in the file  
   /etc/default/grub

GRUB_DEFAULT=4  

If Windows is the 4th entry in the grub menu!  But what will  happen if the kernal is updated - then there are at least 2 new lines  inserted for the new kernal and Windows will be in the 6th line!  Do I  have to update the default value everytime this happens (alternatively  delete the old kernal and subsequently the repective lines in Grup) or  is there a smarter way around this issue! :confused: 

Thanks for your help and suggestions!

==================================
Attachment:
This is a copy of the file /etc/default/grub:


[I]# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
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
#GRUB_DISABLE_LINUX_RECOVERY="true"[/I]

---

### Post by ajgreeny on 2012-02-10
Have a look at [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") which will give you all the answers about this.
> GRUB_DEFAULT - Sets the default menu entry. Entries may be numeric or "saved"

    GRUB_DEFAULT=0 - Sets the default menu entry by menu position. As Grub Legacy, the first "menuentry" in grub.cfg is 0, the second is 1, etc.
    GRUB_DEFAULT=saved - (Grub 1.98) Enables the "grub-reboot" and "grub-set-default" commands.
        This setting allows the use of the following commands to set a default OS. The default OS will not be set merely by an interactive selection of an OS from the menu.
        grub-set-default. Sets the default boot entry until changed.
            The format is "sudo grub-set-default X, with X being the menuentry position (starting with 0 as the first entry) or the exact menu string. Examples: sudo grub-set-default 3 or sudo grub-set-default "Ubuntu, Linux 2.6.32-15-generic"
            To obtain the existing menuentry choice number (starting from 0) or the menuentry "string", run "grep menuentry /boot/grub/grub.cfg"
        grub-reboot. This command sets the default boot entry for the next boot only. The format of the command is the same as for "grub-set-default" (see above).
        For an example of how to enable the "saved" option with a custom menu, see the "Custom User Entries" section.
    GRUB_DEFAULT="xxxx" - An exact menu entry, including the quotation symbols, may also be used. In this case, location in the menu will not matter. Example: GRUB_DEFAULT="Ubuntu, Linux 2.6.31-9-generic"

---

### Post by drs305 on 2012-02-10
One way to keep a menuentry the default even if the order changes is to use the exact title in the menuentry rather than its position number. 

For example, in /etc/default/grub, use GRUB_DEFAULT="Microsoft Windows XP Home Edition (on /dev/sda1)" rather than GRUB_DEFAULT=4.

---

### Post by Bucky Ball on 2012-02-10
Or you could use Grub Customizer. Easy GUI to change the order and what shows in the grub selection options at boot (and you can do heaps of other stuff too). 

[http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html](http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html)

and

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

Google 'grub customizer' and you will find plenty of info.

---

### Post by bogan on 2012-02-10
Transfered from  **edw666,**s duplicate Post.

 				 				**Re: Grub 2 boot order** 			
 			 			 		   		 		 		Hi! **edw666**,
Rather than having to edit system files, as suggested in this old thread, or Startup Manager, which is a bit iffy with 11.10.

To edit and re-arrange the Grub menu, plus add a background image, alter   fonts and colours, and much else, you want Grub Customizer. It is an   easy to use Graphics tool.

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134) Go to Post #1 for a full explanation.

You are correct that you may have to alter the default setting after a  major update, but with Grub Customizer you can make Windows the top  entry in the Grub Menu. 
You can also choose the default by name instead mof position.; then you will not have to alter it again; at  least, not as long as you still want Win as default. 

Chao!, **boga**n.

---

### Post by Bucky Ball on 2012-02-10
> **bogan said:**
> 
To edit and re-arrange the Grub menu, plus add a background image, alter   fonts and colours, and much else, you want Grub Customizer. It is an   easy to use Graphics tool.

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134) Go to Post #1 for a full explanation.



I suggest Grub Customizer and give links in the post directly before yours. ;)

---

