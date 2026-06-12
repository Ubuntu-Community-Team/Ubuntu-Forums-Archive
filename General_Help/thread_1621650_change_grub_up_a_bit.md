---
title: "change grub up a bit?"
date: 2010-11-14
forum: General Help
---

### Post by owners4life5 on 2010-11-14
how can i change grub from this:

```
Ubuntu, with Linux 2.6.32-25-generic
Ubuntu, with Linux 2.6.32-25-generic (recovery mode)
Ubuntu, with Linux 2.6.32-21-generic
Ubuntu, with Linux 2.6.32-21-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Ubuntu, with Linux 2.6.35-22-generic (on/dev/sda1)
Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on/dev/sda1)
Ubuntu, with Linux 2.6.32-25-generic (on/dev/sda1)

```

and it goes on, listing a few more...

anyway, i want to change it from that to where it is like this:
(note that the first four i listed are lucid, and the rest of them down are maverick, except for the memory tests, of course.


```
Ubuntu 10.04 Lucid Lynx
Ubuntu 10.04 Lucid Lynx (recovery mode)
Ubuntu 10.10 Maverick Meerkat
Ubuntu 10.10 Maverick Meerkat (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
```

i don.t want grub to show the previous versions, also, if that is possible. also note that lucid and maverick are on separate partitions.
____________________________________________________________

if all of this was just on my computer only, i wouldn.t really mind, but my roomate and i share a computer, and he might get confused and logon to lucid instead of maverick, and ask

"where is my account??"

lol...so if anyone can help me with this, it is greatly appreciated. :D

thanks,

---

### Post by sikander3786 on 2010-11-14
First of all, you can use startupmanager to make your Meerkat the default OS your computer boots to so your room-mate doesn't even need to press a key before he gets to the login screen.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

You have got an updated kernel for Lucid. And it is recommended that you keep at least one older kernel so that if the newer one stops working for any reasons, you can boot into the older one and diagnose the problem.

You can always use Synaptic to remove the un-needer kernels and then run update-grub to update your Grub menu.

```
sudo update-grub
```

You can also edit /etc/default/grub to just hide the Recovery mode options so your menu looks less busy. To edit,

```
gksudo gedit /etc/default/grub
```

And just uncomment this line.

```
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

And then update Grub menu by,

```
sudo update-grub
```

Edit: And the question regarding renaming the OS in Grub menu, this thread covers everything related. Courtesy of **drs305**.

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Scroll down to the section "1. CHANGING/LIMITING UBUNTU & LINUX TITLES (on default partition) - /etc/grub.d/10_linux *".

---

### Post by owners4life5 on 2010-11-14
okay i.ll makes sure to do all of that when i get to that computer...

but if i did remove the recovery mode(s) from the grub menu, and my system was not working properly, how would i access them??

removing them does sound like a good idea, and i.ll probably do that...but before i do, how can i make it to where i can access them....even when they aren.t listed on the menu?

---

### Post by drs305 on 2010-11-14
As sikander3786 linked, there is a Title Tweaks thread that allows you to make lots of changes. But it is really geeky stuff.

In fact, I was playing with some of the tweaks this morning. Most of them involve only changing one script. Today I experimented with putting a variable with /etc/default/grub; mainly so the user can make subsequent changes in /etc/default/grub, where the other changes are made.

So I don't feel like my effort was a complete waste (since I decided not to put it in Title Tweaks), here is an alternate way of how many kernels to display.

Open /etc/default/grub and /etc/grub.d/10_linux for editing:
```
gksu gedit /etc/default/grub /etc/grub.d/10_linux
```

In /etc/default/grub, add **[COLOR="DarkRed"]these lines[/COLOR]**:
> GRUB_DEFAULT=1
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
[B][COLOR="DarkRed"]# User Variables
GRUB_KERNELS_DISPLAYED=1
export GRUB_KERNELS_DISPLAYED[/COLOR][/B]


In /etc/grub.d/10_linux (at the end):
> 
.....
.....

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`

[B][COLOR="DarkRed"]counter=$(expr $counter + 1)
if [ ${counter} = ${GRUB_KERNELS_DISPLAYED} ] ; then
list=""
fi
[/COLOR][/B]
done

Notes:
The variable *counter* apparently doesn't have to be defined initially to work.

This will only work for 10_linux entries. I don't currently have extra kernels on my other partitions so I haven't come up with the same means for OS's on other partitions.

---

### Post by owners4life5 on 2010-11-14
> **drs305 said:**
> As sikander3786 linked, there is a Title Tweaks thread that allows you to make lots of changes. But it is really geeky stuff.

ha don.t worry...i.m a total geek, hoping to be a guru. not like the antisocial-nerd-geek, but yeah. so it.s cool...

> In fact, I was playing with some of the tweaks this morning. Most of them involve only changing one script. Today I experimented with putting a variable with /etc/default/grub; mainly so the user can make subsequent changes in /etc/default/grub, where the other changes are made.

So I don't feel like my effort was a complete waste (since I decided not to put it in Title Tweaks), here is an alternate way of how many kernels to display.

oh most definitely not...time used on linux is not time wasted.. (:

---

### Post by owners4life5 on 2010-11-14
well i was just thrown a curveball....i followed your instructions and the pieces of drs305's guide that was needed, updated grub, and none of it changed???

---

### Post by drs305 on 2010-11-14
> **owners4life5 said:**
> well i was just thrown a curveball....i followed your instructions and the pieces of drs305's guide that was needed, updated grub, and none of it changed???

Which pieces? i.e. what were you trying to change? The above, or one of the other tweaks? If you let me know and attach the grub.cfg and whatever scripts you changed I can take a look.

One explanation: each of your Ubuntu installs has a grub.cfg. Editing the one in your currently booted OS won't effect the menu *unless* it is in the Ubuntu which grub actually uses. It's possible to be running one install but using the grub.cfg of another one.

One way I check this is to manually edit the grub.cfg file I am trying to change and misspell one of the menuentry titles. Do not update grub, just save the file and reboot. Then when I reboot, I look to ensure the title is still misspelled.

---

### Post by uRock on 2010-11-14
As soon as I get an updated kernel and see that it works properly I go into Synaptic Package Manager and uninstall the old ones.

---

### Post by owners4life5 on 2010-11-14
> **drs305 said:**
> Which pieces? i.e. what were you trying to change? The above, or one of the other tweaks? If you let me know and attach the grub.cfg and whatever scripts you changed I can take a look.

One explanation: each of your Ubuntu installs has a grub.cfg. Editing the one in your currently booted OS won't effect the menu *unless* it is in the Ubuntu which grub actually uses. It's possible to be running one install but using the grub.cfg of another one.

One way I check this is to manually edit the grub.cfg file I am trying to change and misspell one of the menuentry titles. Do not update grub, just save the file and reboot. Then when I reboot, I look to ensure the title is still misspelled.

thank you for all of the help and info, the world (at least my corner of it) needs to be more like this....not to sound old ;)

anyway, i.ll do this tomorrow after class and let you know the result, and we can fix this

---

### Post by owners4life5 on 2010-11-17
here is a copy of my grub.cfg...sorry it took me so long to get it up...been a bit busy lately :/

---

### Post by drs305 on 2010-11-17
The file attached to the previous post is /etc/default/grub. You can edit that post and add the /boot/grub/grub.cfg file.

Actually though, what I'd need to know while looking at the .cfg file is what you want to have the menu do that it currently isn't.  My last proposal for limiting the kernels by including lines in /etc/default/grub are not in the attachment, so either you decided to do it the other way or elected not to do that at all.

---

