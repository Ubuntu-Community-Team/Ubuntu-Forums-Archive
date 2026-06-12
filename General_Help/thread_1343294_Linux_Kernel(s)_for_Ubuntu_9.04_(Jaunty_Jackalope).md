---
title: "Linux Kernel(s) for Ubuntu 9.04 (Jaunty Jackalope)"
date: 2009-12-01
forum: General Help
---

### Post by Johnny M! on 2009-12-01
Tuesday 1st of Dec (Ho Ho Coming)
--------------------------------------------------

Looking for Help understanding Linux Kernel Versions for Ubuntu 9.04:

- Appears that Linux Kernel 2.6.28-11 was installed as the default kernel with 9.04

- (as of Nov-09) In my Places/Computer/Filesystem/boot:  there are multiple versions of the Linux Kernel up to and including 2.6.28-16

- Did Update Manager place the newer versions there when updating my system?   And if so - why didn't Update Manager install the newest kernel version as a bootable option ??

- I manually edited GRUB/menu.lst to force my Ubuntu 9.04 build to use Kernel 2.6.28-16; but why doesn't Update Manager do this for me ?

- I see the latest stable Linux Kernel (at [http://www.kernel.org/](http://www.kernel.org/)) is 2.6.31-6.   Can Unbuntu 9.04 use this Kernel ????

or

- Are there specific Kernels versions that only work with specific Ubuntu Distribution versions ?   If so - where is the documentation that I might reference?

- What is the highest Kernel Jaunty 9.04 can use ???

KERNEL Confusion - any Help appreciated !!

BVR
Johnny M!

---

### Post by coffeecat on 2009-12-01
> **Johnny M! said:**
> - Did Update Manager place the newer versions there when updating my system?

Yes.

> **Johnny M! said:**
>  And if so - why didn't Update Manager install the newest kernel version as a bootable option ??

- I manually edited GRUB/menu.lst to force my Ubuntu 9.04 build to use Kernel 2.6.28-16; but why doesn't Update Manager do this for me ?

It should have done. Did you get a question during the upgrade - a choice between keeping the current version of menu.lst or replacing with the maintainer's version? Or words to that effect. If you choose the current version, menu.lst won't be updated with the latest kernel.

> **Johnny M! said:**
>  - I see the latest stable Linux Kernel (at [http://www.kernel.org/](http://www.kernel.org/)) is 2.6.31-6.   Can Unbuntu 9.04 use this Kernel ????

or

- Are there specific Kernels versions that only work with specific Ubuntu Distribution versions ?

Yes, you keep to a specific kernel release with a specific Ubuntu release. The kernel will be upgraded with security backports but that's about it. Using a newer kernel may introduce incompatibilities with other bits of the system. But the only need for a newer kernel is for security patches (dealt with) or for newer drivers. If you don't need a newer driver you don't need a newer kernel.

However, try enabling the backports repository and see if that offers you a newer kernel.

---

### Post by sgosnell on 2009-12-01
The 2.6.31 series don't boot on my EEE PC, but the latest 2.6.30 kernel runs very well.  The 2.6.32 kernel, when released, may work, but I don't know yet.

---

### Post by Johnny M! on 2009-12-02
Wednesday 2-Dec, 5:15PM US Eastern Standard Time
-------------------------------------------------------------------------------

To Coffeecat and Sgosnell,

Thanks you for your relies !    Very helpful in understanding how Ubuntu migrates to newer Linux Kernels !

BVR
Johnny M!

---

### Post by sgosnell on 2009-12-02
You can download and install newer kernels from [the Ubuntu kernel site](http://kernel.ubuntu.com/~kernel-ppa/mainline/).  Just download the appropriate image and install it with gdebi.  If it doesn't work, you can always boot from a previous kernel and uninstall it with Synaptic, aptitude, or apt-get.  I prefer Synaptic, so that I can see what is installed and what is going to be removed before committing to anything, but it's up to you.

---

### Post by Billee on 2009-12-02
It should have done. Did you get a question during the upgrade - a choice between keeping the current version of menu.lst or replacing with the maintainer's version? Or words to that effect. If you choose the current version, menu.lst won't be updated with the latest kernel.> 

I think this is what happened to me.  Is there some way I can update menu.lst from 2.6.24-16 to 2.6.28-16 ?  I am on Ubuntu 9.04.

---

### Post by Billee on 2009-12-02
I am sorry about my last post.  I was trying to quote coffeecat and didn't get it right.  My quest at the end of the post still stands.  Thanks.

---

### Post by coffeecat on 2009-12-03
> **Billee said:**
> I think this is what happened to me.  Is there some way I can update menu.lst from 2.6.24-16 to 2.6.28-16 ?  I am on Ubuntu 9.04.

2.6.24? Is your Jaunty dist-upgraded from Intrepid?

Anyway, post the contents of your /boot/grub/menu.lst file and the terminal output of these two commands:

```
uname -r
ls -1 /boot/vmlinuz*
```

---

### Post by Billee on 2009-12-03
I upgraded from Hardy (pre-installed by Dell) to Jaunty in September (with disk provided in Ubuntu User magazine).  I have done manual updates weekly since then.

[COLOR="Yellow"]Here is the output of gedit boot/grub/menu.lst[/COLOR]

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro all_generic_ide
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1b666341-204d-4c03-b1e8-5d0382a9b3b6 ro all_generic_ide

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

splashimage=(hd0,2)/boot/grub/splash.xpm.gz

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=1b666341-204d-4c03-b1e8-5d0382a9b3b6 ro all_generic_ide quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=1b666341-204d-4c03-b1e8-5d0382a9b3b6 ro all_generic_ide quiet
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Reinstall Operating System (WARNING: all Hard Drive data will be LOST!)
        root (hd0,1)
        chainloader +1

[COLOR="Yellow"]Here is the output of sudo gedit uname -r[/COLOR]
2.6.24-16-generic

[COLOR="Yellow"]Here is output of ls -l /boot/vmlinuz*[/COLOR]
/boot/vmlinuz-2.6.24-16-generic
/boot/vmlinuz-2.6.28-14-generic
/boot/vmlinuz-2.6.28-15-generic
/boot/vmlinuz-2.6.28-16-generic

---

### Post by ST3ALTHPSYCH0 on 2009-12-03
For future reference, please put large outputs (i.e error logs or config files) between code tags so your post isn't 80 miles long (in case there's confusion it should look like: {code} config file or error log{/code} where {} is replaced with []). 
Also, that yellow font doesn't show for crap on the white background!

---

### Post by coffeecat on 2009-12-03
**Billee**, as I thought, you're running Jaunty with the Hardy kernel. Interesting that it works. Did you do an upgrade from Hardy directly to Jaunty without upgrading to Intrepid, because you don't seem to have an Intrepid kernel?

Anyway, edit menu.lst with administrator privileges with this from a terminal:

```
gksudo gedit /boot/grub/menu.lst
```Now copy and paste the code I've posted below to between these two lines:

splashimage=(hd0,2)/boot/grub/splash.xpm.gz

***Copy and paste here***

title        Ubuntu 8.04, kernel 2.6.24-16-generic

```
title Ubuntu 9.04, kernel 2.6.28-16-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.28-16-generic root=UUID=1b666341-204d-4c03-b1e8-5d0382a9b3b6 ro all_generic_ide quiet splash
initrd /boot/initrd.img-2.6.28-16-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.28-16-generic root=UUID=1b666341-204d-4c03-b1e8-5d0382a9b3b6 ro all_generic_ide quiet
initrd /boot/initrd.img-2.6.28-16-generic

title Ubuntu 9.04, kernel 2.6.28-15-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=1b666341-204d-4c03-b1e8-5d0382a9b3b6 ro all_generic_ide quiet splash
initrd /boot/initrd.img-2.6.28-15-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=1b666341-204d-4c03-b1e8-5d0382a9b3b6 ro all_generic_ide quiet
initrd /boot/initrd.img-2.6.28-15-generic
```That will give you menu entries for the -15 and -16 Jaunty kernels. Try the -15 one if the -16 one gives problems. I haven't given you stanzas for the -14 kernel (which you also have installed) which is probably now surplus to requirement. Let us know how you get on.

---

### Post by Billee on 2009-12-03
> **ST3ALTHPSYCH0 said:**
> For future reference, please put large outputs (i.e error logs or config files) between code tags so your post isn't 80 miles long (in case there's confusion it should look like: {code} config file or error log{/code} where {} is replaced with []). 
Also, that yellow font doesn't show for crap on the white background!

Thanks...I am still getting used to this forum stuff.  I realized the error in the color after I posted it.  I wanted a highlighted text, not font color.

> Did you do an upgrade from Hardy directly to Jaunty without upgrading to Intrepid  Yes.  I will try to get to your suggestions after we finish with Christmas decorations.  I'll let you know how it goes.

---

### Post by coffeecat on 2009-12-03
> **Billee said:**
> Yes.

It's not recommended to skip a version when dist-upgrading. Usually you should Hardy > Intrepid > Jaunty in two steps. Let's hope it doesn't give you problems - apart from not upwriting menu.lst for you.

---

### Post by ST3ALTHPSYCH0 on 2009-12-03
I hope I didn't come across as rude, just trying to help you get help.

---

### Post by coffeecat on 2009-12-03
> **ST3ALTHPSYCH0 said:**
> I hope I didn't come across as rude, just trying to help you get help.

I try to remember to put in a smiley or two if I'm picking someone up on a point of netiquette or forum use. It helps to reassure them I'm being good-humoured. :)

:wink:

---

### Post by ST3ALTHPSYCH0 on 2009-12-03
Good advice.

---

### Post by Billee on 2009-12-04
Thank you, gentlemen.  Coffeecat's suggestion worked! (Did I ever doubt you ;) ).

---

### Post by coffeecat on 2009-12-04
> **Billee said:**
>  (Did I ever doubt you ;) ).

Sounds as though you might have had a couple of wavering moments. :p But I'm glad it's fixed. 

However, talking of doubts, I've just noticed I posted this last night...

> **coffeecat said:**
>  apart from not upwriting menu.lst for you.

Upwriting?! :-k

---

