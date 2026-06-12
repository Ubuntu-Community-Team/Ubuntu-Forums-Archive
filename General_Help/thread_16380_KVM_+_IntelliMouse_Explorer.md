---
title: "KVM + IntelliMouse Explorer"
date: 2005-02-21
forum: General Help
---

### Post by frontline3k on 2005-02-21
Hi.
I tried with Array 5 i386 Live CD, and I have the same issue explained in this thread:
[http://www.ubuntuforums.org/showthread.php?t=15935](http://www.ubuntuforums.org/showthread.php?t=15935) 

Anyone can help me, pls ?

---

### Post by dickinsd on 2005-02-26
[QUOTE=frontline3k]Hi.
I tried with Array 5 i386 Live CD, and I have the same issue explained in this thread:
[http://www.ubuntuforums.org/showthread.php?t=15935](http://www.ubuntuforums.org/showthread.php?t=15935) 

Anyone can help me, pls ?[/QUOTE]

I get this problem also, I think to be honest it is more to do with the KVM in my case, although the link to the other post, mentioned about kernel versions, this is pretty interesting.

I was pretty conviced it was because my KVM cost something like £10 after VAT.

The reason I thought it was my KVM, was because connecting the mouse straight to the PC works fine, OR, disconecting the mouse from the KVM after it has booted, and then reconnecting it seems to also fix the problem.

Currently I have the space for 2 mice so I just have one for each machine!

If you figure it out, I would be interested in your answer, although I do still think it is more to do with the way the KVM passes the signal onto the PC.

Dave

---

### Post by frontline3k on 2005-02-28
Hi.
I tried today to use an external power adapter to the KVM switch. Same problem.
Also, I tried Archlinux and SimplyMEPIS 3.3. Both have the same problem with 2.6 kernel, using the 2.4 kernel doesn't.
I also looked in Ubuntu repository, but there is no 2.4 kernel to test it  :-k 

Looking through /var/log doesn't show up error messages about mouse.

Anyone can help ? :sad:

---

### Post by frontline3k on 2005-03-01
Hi. One step ahead.
Found this: [http://linuxnotes.blogspot.com/2004/09/kvm-switch-26-kernel.html](http://linuxnotes.blogspot.com/2004/09/kvm-switch-26-kernel.html).
Using psmouse.proto=bare in grub with SimplyMephis 3.3 solves the problem, BUT I loose the scrolling and extra buttons.
I'll try today with Ubuntu Live Array 5.

Also, I filed a bug in Bugzilla: [https://bugzilla.ubuntu.com/show_bug.cgi?id=7038](https://bugzilla.ubuntu.com/show_bug.cgi?id=7038)

Seems to be a general problem with Kernel 2.6 and KVMs ([http://www.google.com/linux?q=kvm+switch+kernel+2.6](http://www.google.com/linux?q=kvm+switch+kernel+2.6) )

Regards

---

### Post by Mike Eberhart on 2005-03-01
I have this same problem using a Belkin OmniCube 4-port.
It only happens after I switch between machines.  I am switching between Windows based machine (Windows Server 2003) and the Ubuntu machines.  

I have found that if I UNPLUG the mouse from KVM, and then re-plug it into KVM, it temporarily fixes the problem.  And, as strange as it would be to do this, perhaps just unplugging mouse before switching machines would work.

I sure hope they fix this in the Kernel soon though :)

---

### Post by frontline3k on 2005-03-04
Again, Array 6 Live CD, same error  :cry: 
Also, I forget to mention that I have this problem all the time. I'm launching Ubuntu without switching to another box (there was some posts about this issue when changing to another box).

Help, anyone ?

---

### Post by frontline3k on 2005-03-14
Hi. Me again  :? 
Tried today with Hoary Live Preview Release, and I have the same issue.

Help  :-s

---

### Post by frontline3k on 2005-03-16
I tested today SAM MiniLive Linux SAM 2005-2 beta ([http://sam.hipsurfer.com/)](http://sam.hipsurfer.com/)),
which is based on Mandrake.
'uname -r' says 2.6.11.1-oci0.2.
Amanzingly, the mouse is working, even the scroll wheel.
Kernel command line contains psmouse.proto=imps.

---

### Post by frontline3k on 2005-03-18
I was looking for this problem on kernel.org.
And in [http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.11](http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.11) I found this:
"<dtor_core@ameritech.net>
	Input: psmouse - reset mouse before doing intellimouse/explorer
	       probes in case it got confused by earlier probes; switch
	       to streaming mode before setting scale and resolution,
	       otherwise some KVMs get confused.
	
	Patch-by: Marko Macek <Marko.Macek@gmx.net>
	Signed-off-by: Dmitry Torokhov <dtor@mail.ru>"

This could be the solution for my problem.
Anybody knows if kernel 2.6.11 will be included in the final version of Hoary ?

---

