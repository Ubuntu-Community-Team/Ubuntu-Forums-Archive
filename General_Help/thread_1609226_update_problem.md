---
title: "update problem"
date: 2010-10-30
forum: General Help
---

### Post by slonnnik on 2010-10-30
Hi

When I update my Ubuntu I receive message (screenshot). 
When I check details I can see following message (screenshot-1) 

Could you please help me to solve this?
Thank you

---

### Post by Rubi1200 on 2010-10-30
What does the output from ```
sudo dpkg --configure -a
``` show?

---

### Post by slonnnik on 2010-10-30
Setting up linux-image-2.6.32-25-generic (2.6.32-25.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-25.44 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-25.44 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 8: quite splash: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 linux-image-2.6.32-25-generic

---

### Post by Rubi1200 on 2010-10-30
It looks like there might be a problem with the GRUB configuration:
> /etc/default/grub: 8: quite splash: not found

Could you please also post the output of the /etc/default/grub file.

---

### Post by Quackers on 2010-10-30
Shouldn't that be "quiet splash"?

---

### Post by Soul-Sing on 2010-10-30
> **Quackers said:**
> Shouldn't that be "quiet splash"?

yeah indeed, the OP should as rubi said, change that in /etc/default/grub
and run a ```
sudo update-grub
``` after that

---

### Post by slonnnik on 2010-11-04
> **Rubi1200 said:**
> It looks like there might be a problem with the GRUB configuration:


Could you please also post the output of the /etc/default/grub file.

Here is Grub file:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true GRUB_TIMEOUT=10 
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` 
GRUB_CMDLINE_LINUX_DEFAULT= "quite splash" 
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



I tried to change GRUB_CMDLINE_LINUX_DEFAULT= "quite splash"  to  "quiet splash", but it didn't work. When I tried to update it I received:

 /etc/default/grub: 8: quiet splash: not found

Is there anything else that should be changed?

---

### Post by slonnnik on 2010-11-08
Any help Please?

---

### Post by Hippytaff on 2010-11-08
No luck with the instructions above?

---

### Post by Rubi1200 on 2010-11-08
Not sure if you copied/pasted incorrectly?

This is how my file looks:

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=15
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

# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"I suggest you put the > GRUB_TIMEOUT=10 on its own line and change this > GRUB_CMDLINE_LINUX_DEFAULT= "quite splash" to this > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"Then save and run ```
sudo update-grub
```

---

### Post by slonnnik on 2010-11-08
no luck

I put 
GRUB_TIMEOUT=10 			 		
on its own line

corrected
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 			 		
to this  	
	 	 		 			 				GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

then saved and run
sudo update-grub

and I receive following:
/etc/default/grub: 9: quiet splash: not found

---

### Post by Rubi1200 on 2010-11-08
Run this command and report back if there are errors:

```
sudo apt-get install -f
```

followed by ```
sudo dpkg --configure -a
```

And post the /etc/default/grub file again please.

Thanks.

---

### Post by slonnnik on 2010-11-08
sudo apt-get install -f

result:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.32-25-generic (2.6.32-25.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-25.44 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-25.44 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 9: quiet splash: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 linux-image-2.6.32-25-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)sudo dpkg --configure -a

result:
> Setting up linux-image-2.6.32-25-generic (2.6.32-25.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-25.44 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-25.44 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 9: quiet splash: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 linux-image-2.6.32-25-generic
/etc/default/grub file:
> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10 
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` 
GRUB_CMDLINE_LINUX_DEFAULT= "quiet splash" 
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by sikander3786 on 2010-11-08
The space after = and before " is causing problems.

```
GRUB_CMDLINE_LINUX_DEFAULT= "quiet splash" 
```

Please remove it and run

```
sudo update-grub
```

again to see if worked.

---

### Post by slonnnik on 2010-11-08
it worked.

Thank you

---

### Post by Rubi1200 on 2010-11-08
Ha, nice one sikander, well spotted!

@slonnnik; glad you got it finally worked out :)

Please mark this thread Solved using the Thread Tools near the top of the page.

Enjoy!

---

