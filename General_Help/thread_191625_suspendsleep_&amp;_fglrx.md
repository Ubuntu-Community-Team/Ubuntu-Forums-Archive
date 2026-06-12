---
title: "suspend/sleep &amp; fglrx"
date: 2006-06-07
forum: General Help
---

### Post by ehula on 2006-06-07
I had the suspend and resume that is built-in to the kernel working fine on my Thinkpad T43p under Breezy, but now that I've upgraded to Dapper, it is broken. It works occasionally, but not consistently.

I am using the Ubuntu supplied fglrx drivers, and have removed "splash" from the kernel command in grub.

Does anyone have suspend/sleep and resume working under Dapper with fglrx?

---

### Post by jbrader on 2006-06-07
I'm trying to get my hibernate working as well, how do you remove the splash like you mentioned?

---

### Post by scxtt on 2006-06-07
[QUOTE=jbrader]I'm trying to get my hibernate working as well, how do you remove the splash like you mentioned?[/QUOTE]edit your /boot/grub/menu.lst
[INDENT][FONT="Courier New"]title           Dapper Drake, kernel 2.6.15-23-386 (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sdb1 ro quiet [COLOR="Red"]splash[/COLOR]
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot
[/FONT][/INDENT]
and remove splash

---

### Post by jbrader on 2006-06-07
Well I did that and now when I try to restart from hibernate I boot into a black screen, which is actually progress I guess before it booted into a bunch of broken video.
P.S. I'm also using fglrx with a ati mobility 9600.

---

### Post by scxtt on 2006-06-07
i had initial problems w/ fglrx in dapper (none in breezy) ...

i wasn't able to have fglrx working in breezy, then upgrade to dapper (which makes sense since it's a new kernel) -- even when i followed the directions i used for breezy again on dapper, it was a no go ...

i had to do a fresh install of dapper and then follow my breezy instructions (with trivial mods) to get fglrx working in dapper as it did in breezy ...

i have an ATI X850Pro and as far as i can tell, it's working just fine (~1300 FPS in fgl_glxgears) ...

some people have said that using the radeon module works for them - have you tried that?

---

### Post by TrinitronX on 2006-06-08
Ever since an update to fglrx a while ago I'm getting no usplash at shutdown.  I have to use the power button to turn my computer off, otherwise it just hangs with a blank screen.

---

### Post by hvbakel on 2006-06-08
[QUOTE=TrinitronX]Ever since an update to fglrx a while ago I'm getting no usplash at shutdown.  I have to use the power button to turn my computer off, otherwise it just hangs with a blank screen.[/QUOTE]

You might want to checkout [bug number 30447]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/30447") in launchpad which has a couple of solutions listed that solved this problem for me. Depending on which login manager you are using (gdm for ubuntu, kdm for kubuntu) you can do the following (for details, please see the link above):

Kubuntu: in /etc/kde3/kdm/kdmrc change
#TerminateServer=true
to
TerminateServer=true


Ubuntu: in gdm.conf change
#AlwaysRestartServer=true
to
AlwaysRestartServer=true

Note that you will need superuser privileges to make changes to these files. After making the changes, restart X or reboot the computer and the problem should be resolved. The changes above result in the X-server being restarted rather than just reset when you logout from a session, which fixes the freezes (at least for me).

---

### Post by ehula on 2006-06-08
Bump.

Does anyone have suspend/sleep and resume working under Dapper with fglrx?

---

### Post by ehula on 2006-06-16
Bump...

---

### Post by nanotube on 2006-06-23
[QUOTE=ehula]Bump...[/QUOTE]
i've had similar problems.
check my thread here for possible solution (worked for me, i think)

[http://ubuntuforums.org/showthread.php?t=201960&highlight=fglrx+suspend](http://ubuntuforums.org/showthread.php?t=201960&highlight=fglrx+suspend)

---

