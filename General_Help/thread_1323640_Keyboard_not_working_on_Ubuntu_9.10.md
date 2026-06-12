---
title: "Keyboard not working on Ubuntu 9.10"
date: 2009-11-11
forum: General Help
---

### Post by thandacoke on 2009-11-11
Hi,

I have installed Ubuntu desktop edition 9.10 recently.
All these days I have been using Ubuntu 9.10 without facing any problem.
But suddenly since yesterday, my keyboard is not getting detected when I try to login to Ubuntu. I was not able to enter my password at the login screen. I used the on-screen keyboard to login but unable to use the keyboard even after logged-in.
I checked if there is any problem with my keyboard by logging into Windows 7. Every thing is working fine and I was able to use my keyboard well.
I re-installed Ubuntu again for a couple of time after formatting my D: partition but of no use, still the same problem.
Don;t know what to do.
Please help me out.
FYI,
my notebook is a HP model dv2911us

Thank you.

---

### Post by Novice_Ark on 2009-11-17
I had the same problem with my Lenovo Y500 laptop keyboard. After installation of Ubuntu (8.10, 9.04 and now 9.10) my keyboard and touchpad froze. :frown: 

U can try this one, though I'm not sure whether it will work for u. At least it worked for me. 
1. Login into Ubuntu by using an USB keyboard. 
2. Open terminal & type "sudo gedit /etc/default grub"  (Avoid the quotes)
You should get something like this:

# If you change this file, run 'update-grub' afterwards to update
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
#GRUB_DISABLE_LINUX_RECOVERY="true"


3. Now edit the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" line to the following 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash locale=fr_FR i8042.reset".

4. Save and close the file.
5. Now type "sudo update-grub" (Avoid the quotes). U should see something like the following:

Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows NT/2000/XP (loader) on /dev/sda1
done

6. Restart your machine and hopefully your keyboard will work again..


Please let me know if the trick works....

---

### Post by thandacoke on 2009-11-20
Hi,

Thank you for your suggestion.
I will try that and will let you know if it works or not.

I have a doubt. The keyboard is not responding even if I re-installed Ubuntu on my system. Isn't it after you install Ubuntu (new install on a different drive) then the grub  should be set to default? And it supposed to work as it was before ??

---

### Post by severvip on 2010-03-11
I recently installed Ubuntu 9.10 64bit on my HP laptop dv2842, the keyboard seemed to be working fine the first time I loaded up ubuntu, but the next day the keyboard stopped working, and it hasn't worked since. I tried removing and reloading the Ubuntu OS, but still the keyboard doesn't work. I tried Novice_Ark's solution but that didn't fix the problem. Any other suggestions.

I've been wanting to switch to linux for a long time, but some problem always leaves me frustrated and I end up going back to Windows. In 8.04 I had power issues and mouse issues. In 8.10 I had boot issues. In 9.04 I again had boot issues. With 9.10 everything seemed fine, it booted up and was working, then the next day keyboard stops working. Please help I don't want to go back to Windows again.

---

### Post by sdrey on 2010-08-25
I have the same issue with a dell studio....I have been running 9.1 with no issues....and then I noticed that the mouse/keyboard wouldn't work on some boots...then few boots....now never..

Seems weird how it just decayed and quit working...

Please help, my system is useless now without a USB keyboard mouse

---

