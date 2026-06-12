---
title: "ubuntu 12.04 LTS doesn't work with kvm"
date: 2012-04-29
forum: General Help
---

### Post by imachavel on 2012-04-29
when connected to kvm switch it always says "keyboard error" at bios

I tried to reset the bios to factory default but keyboard and mouse only work when not connected to kvm switch. Any ideas?(problem wasn't happening when ubuntu 11.4 was installed and the OS had an animal name)

I know the OS should not effect the bios but am wondering why this install of ubuntu 12.4 effected this, as though it installed some drivers for settings for remote main board management? Could this have effected bios settings if the kernel was upgraded a bit? But then why did restoring to factory defaults not help? When bios loads no OS is yet present until hard drive is booted to, can't understand this error, maybe it's un related?

---

### Post by sudodus on 2012-04-29
I am running an Aten KVM switch, and it works with Lubuntu 12.04 and a multiple-de system, Ubuntu 12.04 (with unity, kubuntu-desktop, lubuntu-desktop and xubuntu-desktop). The muliple-de system was installed during beta testing, but it has been updated and upgraded completely to current state without any KVM problems.

What happens when you run Ubuntu live from a boot CD or USB? Could it be necessary for you to use some boot option?

[[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

---

### Post by imachavel on 2012-04-29
well I don't see how it will make a difference, before I can select boot device, if my keyboard and mouse are connected to my 4 port kvm switch, I get keyboard error after bios load, in fact at that point can't really switch boot device. Tell you what, I'll go into the bios now and switch boot device to cd rom drive, that way it will boot to live cd either way, not sure how a keyboard and mouse error can be caused by grub when the bios starts loading EXTREMELY slow and then a keyboard mouse error occurs.

But then that is at my fault, since I mentioned the change occurred right after I upgraded to version 12.4 LTS, which it did of course. But maybe something in the bios has inadvertently changed for some reason. It's unknown to me, I reset the bios to factory default, and the problem persists. However, maybe what I need is an upgrade, not default reset.

My pc is a dell dimension 4700. standard

---

### Post by imachavel on 2012-04-29
no go. No change. Anyone sure that the new ubuntu 12.4 didn't install something to detect and reset some bios settings making kvm incompatible with i/o keyboard and mouse?

btw the switch isn't broken. I used it with another computer earlier. One last option, turn off the switch and turn it back on - actually that idea is useless, KVM switch has no power plug, it's getting power apparently from my computer monitor vga port, so when I rebooted the computer the green light should have gone off, if I shut the computer down all the way, which I did. Just wasn't watching the green light(sorry to make everything a running commentary synopsis)

do you think articles like these?:

[http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html)

will lead me to an answer of why my kernel upgraded incorrectly? I know it's somewhat un related, but this article explains the concept of how initramfs is a small amount of drivers that is loaded into ram before the OS file system loads completely and your main boot device is read, and the main file system is mounted. Is it possible a kernel upgrade will change how these drivers are loaded after basic input output? Or am I far off? I notice at bios loading, the bios loads quick until about the last 19/20 spot on the loading bar, then it just about freezes for almost a whole minute. Keyboard and mouse work just fine, I just can't get kvm to work at all with this computer.

---

### Post by sudodus on 2012-04-30
I don't think that Ubuntu has changed the bios setting, but it does create that early environment, that is discussed in the link in post #4.

The only thing I can help with is to suggest some more questions and testing:

- Have you tried to use another port at the KVM switch and/or the same port with another computer?
- Have you tried if the KVM switch works with that computer when you boot from some live CD or USB drives (12.04 and some other version)?
- Have you tried another keyboard?

- Does the keyboard work in the grub menu, and stops working when [L]ubuntu is started, or is it dead from the very beginning, when you boot?

Is there a difference if another computer is running and you [try to] switch from the other computer to the one with problems, compared to if no other computer is running?

---

### Post by Sir Alan on 2012-05-01
I too am having trouble with an Aten USB 4-way KVM switch and 12.04.  I am using an Acer netbook with a Samsung screen on the switch, and the problem occurred after upgrading to 12.04 from 11.10.

On bootup, both screens show the Ubuntu logo in - as far as I can judge - 1024x768 aspect ratio.  Once the desktop has loaded, the netbook screen fades slowly to white, and the desktop displays on the Samsung screen in 800x600.  Everything works fine, apart from the aspect ratio, until I switch to another pc; on returning to the netbook the Samsung screen stays dark with no signal being received, and the netbook screen goes white again.  If I try changing the aspect ratio to 1024x768 the Samsung screen shows the background as four tiles, but nothing else appears.

In 11.10, although the aspect ratio issue was there, the screens switched correctly.

The same behaviour occurs in Unity ('scuse my language), Gnome Classic, MATE, and Cinnamon; this suggests that the underlying problem is in 12.04 itself.

The other 3 pcs run 10.04 or 11.04 and everything is fine, although they do not have other screens attached.

---

### Post by sudodus on 2012-05-02
> **Sir Alan said:**
> I too am having trouble with an Aten USB 4-way KVM switch and 12.04.  I am using an Acer netbook with a Samsung screen on the switch, and the problem occurred after upgrading to 12.04 from 11.10.

On bootup, both screens show the Ubuntu logo in - as far as I can judge - 1024x768 aspect ratio.  Once the desktop has loaded, the netbook screen fades slowly to white, and the desktop displays on the Samsung screen in 800x600.  Everything works fine, apart from the aspect ratio, until I switch to another pc; on returning to the netbook the Samsung screen stays dark with no signal being received, and the netbook screen goes white again.  If I try changing the aspect ratio to 1024x768 the Samsung screen shows the background as four tiles, but nothing else appears.

In 11.10, although the aspect ratio issue was there, the screens switched correctly.

The same behaviour occurs in Unity ('scuse my language), Gnome Classic, MATE, and Cinnamon; this suggests that the underlying problem is in 12.04 itself.

The other 3 pcs run 10.04 or 11.04 and everything is fine, although they do not have other screens attached.

I realize there is a real problem, and now you are two people, telling that there is a problem with 12.04. I use the KVM switch to manage desktop computers, so I tested with a Toshiba laptop and a Lubuntu 12.04 install USB drive. The only 'issue' is that the first menu only shows up externally (on the screen via the KVM), but later there is dual command with the laptop screen, keyboard and local mouse as well as the screen, keyboard and mouse via the KVM. My KVM is a 4-port vga Aten system. Sorry but I cannot reproduce your problem.

---

### Post by Sir Alan on 2012-05-02
I have found an (the?) answer.  Go into the Monitors function, untick the Mirror Images box, select the laptop, click on Monitor Off, select the remote screen.  Now I can change the screen resolution for the remote monitor and save it as default, and everything works properly again.  (But why did it change?)  Now I'm a happy bunny.

---

### Post by jpap4711 on 2012-05-04
I have the same problem using a equip 4-port switch.
[http://www.equip-info.net/equipenglish/index.php?page=equiplife&series=4&kat=14&id=1964](http://www.equip-info.net/equipenglish/index.php?page=equiplife&series=4&kat=14&id=1964) 

Is working without problems for more than 2 years with windows, freebsd, and Ubuntu desktop ( up to 11.10).

When i upgrade to 12.04 LTS I got black screen (no signal) and swicthing to another host and switch back to ubuntu sometimes i got 1024x768 resolution.

xrandr confirms only one resolution (1024x768).
using xrandr --output --auto i get black screen (no signal).

any ideas are welcome..


Jpap.

---

### Post by sudodus on 2012-05-04
It would be interesting to see if the problem is associated with some particular motherboard or graphics card or bios (brand and version).

---

### Post by realitarian on 2012-05-11
Another data point here.

I started having issues with my switch since I updated to 12.04. My system:

[LIST]
[*]IOGear 2-port switch (VGA)
[*]Dual-boot Ubuntu 12.04 and Windows 7
[*]Dell monitor
[*]A generic Dell keyboard
[*]Microsoft trackball mouse
[*]Computer is AMD CPU. ASUS MB
[/LIST]

The switch actually works a few times whenever I boot up and start using my computer (I switch between my personal computer above, and my work laptop on a docking station). After about 5 or 6 switches, the switch doesn't work on 12.04. The trackball remains unlit and keyboard+mouse don't respond. I end up plugging a portable keyboard just so I can do a normal shutdown.

I did not have this problem with Ubuntu 11.10. It started only after I upgraded a couple of weeks ago.

Addendum: I don't have this problem when I boot into Windows 7 (whether with 11.10 or 12.04).

---

### Post by dylanthomasfan on 2012-11-22
I have the same problem with an IOGear 4-port KVM switch/12.04. Any solutions yet for this problem?

---

### Post by dylanthomasfan on 2012-11-22
For what its worth, I tried setting nomodeset like so in /etc/default/grub:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

And it appears like the problem went away.

---

### Post by wb0gaz on 2013-02-09
I'm having a version of this problem and it is *VERY* irritating:

I'm running Ubuntu 12.04 LTS on an Atom machine with Intel 945 graphics. It is one of several machines connected via KVM to VGA monitor and USB keyboard/mouse.

If I switch away from the Ubuntu machine for more than about two seconds (this duration seems critical), then switch back, I get a black screen with only cursor visible (and the cursor is able to move.) I need to hit Alt-F1/Alt-F7 to restore the screen.

If I cycle quickly through the PCs with the KVM (so that the cycle is completed in less than about two seconds), I do not see this problem. I can power down my monitor (while the KVM is pointing to the PC in question) for any duration without problem.

I have "brightness and lock" set so that "turn screen off" is "never", and "lock" is "off". On "power", I have "suspend when inactive" set to "don't suspend."

The machine is current (with respect to updates.) The problem happens regardless of the load on the machine (idle or busy.)

I've searched for solutions to this but this one has me stumped.

Thank you for any suggestions.

---

