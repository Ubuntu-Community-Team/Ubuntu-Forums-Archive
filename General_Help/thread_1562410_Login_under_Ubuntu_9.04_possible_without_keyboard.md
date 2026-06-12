---
title: "Login under Ubuntu 9.04: possible without keyboard?"
date: 2010-08-27
forum: General Help
---

### Post by js31 on 2010-08-27
Hey guys,

have got a real funny problem: My keyboard's broken, some keys I need to login don't work. I can't afford new hardware before Tuesday + no neighbour has a PC keyboard (notebooks...). I would be glad to be able to start normally so at least I can be reached on Ekiga + access the Flash plugin till then.

Is there a way to type a login onscreen with the mouse, or somehow copy the characters I need/disable the user login using the live-CD?

Thanks =)
Joerg

---

### Post by noex869 on 2010-08-27
In one of the newish ubuntu releases they added an on screen keyboard to the login(look at the bottom of the screen, might be under accessibility options).  You can also edit the /etc/shadow (I don't think removing the x in etc/passwd works in ubuntu) with a blank hash I think its $1$VNMbpxGH$sew7cnwH9ixU.x27UbFNn but you should google it.  Make sure you set your password back. Passwords are important!

---

### Post by sisco311 on 2010-08-27
Hi,

I'm not sure how can you add an on-screen keyboard to the legacy GDM screen.

But, if the Ctrl, Shift, Enter, u and 0,1,2... and 9 keys are working, then you can use unicode composition to type in your username & password.

Press Shift+Ctrl+u, release u, enter the hexadecimal (0123456789abcdef) Unicode character code point, then release Shift+Ctrl.

for an uppercase A:
```
Shift+Ctrl+u 41
```
for a lowercase a:
```
Shift+Ctrl+u 61
```

For the hex codes, check out:
[http://www.klcconsulting.net/images/ascii-full.gif](http://www.klcconsulting.net/images/ascii-full.gif)

Once you are logged in you can start onboard, the default on-screen keyboard.

HTH.

---

### Post by js31 on 2010-08-27
Thank you for replying to this exotic thread! <3

I've tried all ways, but I guess it's a problem with the GDM config of Jaunty. - Last method seemed to work, but if I type in the character via unicode, just afterwards releasing Shift+Ctrl GDM deletes everything I had typed in, before. %)

For today, I give up, before I go mental... 8-[ ](*,)

---

### Post by sisco311 on 2010-08-27
> **js31 said:**
> Thank you for replying to this exotic thread! <3

I've tried all ways, but I guess it's a problem with the GDM config of Jaunty. - Last method seemed to work, but if I type in the character via unicode, just afterwards releasing Shift+Ctrl GDM deletes everything I had typed in, before. %)

For today, I give up, before I go mental... 8-[ ](*,)

Strange, it works well with the new GDM. 

Anyway, boot a Live CD, mount the root partition and edit the <mount/point>/etc/gdm.custom file to look like:
```
# GDM configuration storage

[daemon]

AutomaticLoginEnable=true
AutomaticLogin=**username**

[security]

[xdmcp]

[greeter]

[chooser]

[debug]

```

reboot

Check out the GDM doc for more details:
[http://library.gnome.org/admin/gdm/2.20/gdm.html](http://library.gnome.org/admin/gdm/2.20/gdm.html)

---

### Post by js31 on 2010-08-27
Jaunty Jackalope proves to have resilient security -> led me back to the GDM-screen =;

---

### Post by Monotoko on 2010-08-27
boot recover console and use useradd to add a user with the keys you can use, then give him access to the admin group.

Hopefully none of the keys you need to use there are taken...alternatly you can use usermod and change the login name of your current user.

Edit: If the keys dont work, you could chroot from the LiveCD: [http://en.gentoo-wiki.com/wiki/Chroot_from_a_livecd](http://en.gentoo-wiki.com/wiki/Chroot_from_a_livecd)

Daniel

---

### Post by sisco311 on 2010-08-27
> **Monotoko said:**
> 
Edit: If the keys dont work, you could chroot from the LiveCD: [http://en.gentoo-wiki.com/wiki/Chroot_from_a_livecd](http://en.gentoo-wiki.com/wiki/Chroot_from_a_livecd)


+1 

cool

@OP

Here is a script you could use: 
```

#!/bin/bash

############################################################################
# variables                                                                #
############################################################################

# device name of the root partition
ROOT="**/dev/sda1**"

# mount point of the new root partition
MOUNT="/mnt/maverick"

# list of virtual filesystems and additional config files
ARGS="dev dev/pts proc sys etc/resolv.conf"

# list of additional devices and their mount pont. 
# device names must be separated by the mount point with a colon (:)
# e.g. /dev/sda2:/home 
AMOUNT=""

# user name
UNAME="**root**"

############################################################################
# start the chroot environment                                             #
############################################################################

# add user to the list of allowed users to make connections to the X server.
sudo -u $USER xhost SI:localuser:$UNAME

# create the mount point & mount the root partition
mkdir -p $MOUNT
mount $ROOT $MOUNT

# mount the virtual filesystems & resolv.conf to enable the network
for i in $ARGS; do
  mount --bind /$i $MOUNT/$i
done

# mount additional partitions:
for i in $AMOUNT; do
  mkdir -p ${MOUNT}${i//*:/}
  mount ${i//:*/} ${MOUNT}${i//*:/}
done

# chroot into the linux installation
chroot $MOUNT sudo -i -u $UNAME

```

Edit the value of the ROOT variable to fit your needs. Once chrooted into your installation run:
```
/usr/sbin/gdmsetup
```
and enable auto-login, then reboot. :)

---

### Post by js31 on 2010-08-30
Great replies, thank you very much! =) <3

(Sorry for the late answer; two of my teeth showed strange similarity to the keyboard *lol* and the painkiller made me [[img]http://planetsmilies.net/vomit-smiley-549.gif[/img]](http://planetsmilies.net).
At least this thread will help others in this unpleasant feast day/weekend keyboard-failure [[img]http://planetsmilies.net/confused-smiley-17548.gif[/img]](http://planetsmilies.net) kind of situation.)

useradd/-mod contains 1 defunct key, so I'd try the chroot-method. The tutorial is high for me to reach (2 years/Linux slow learner), I don't know if I'll manage to get there today.
@sisco311 does the the script require the chroot-command before/where do I have to copy or at which point should I enter it?

---

### Post by sisco311 on 2010-08-30
> **js31 said:**
> @sisco311 does the the script require the chroot-command before/where do I have to copy or at which point should I enter it?

The script automates the process described in the gentoo wiki.

Simply boot a Live CD, save the script in a file, make it executable and run it in a terminal. It will create the chroot environment for you.

---

### Post by js31 on 2010-08-31
That solves a lot work. You're an [[img]http://planetsmilies.net/angel-smiley-5128.gif[/img]](http://planetsmilies.net)!

@>-->--

---

