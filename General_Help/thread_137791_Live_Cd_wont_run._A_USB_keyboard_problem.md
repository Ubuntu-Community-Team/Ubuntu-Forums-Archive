---
title: "Live Cd wont run. A USB keyboard problem?"
date: 2006-02-28
forum: General Help
---

### Post by thatsall on 2006-02-28
:confused: I try to run live cd and it starts up in beginning then stops before the desktop loads. It says:

 loading.....
Running/etc/hotplug/USB.rc

I think it might be my usb keyboard...because it is not on at that point of the message but then again it lets me press ENTER to start the Live cd...

SOmebody help because im sick of windows and ready to try ubuntu asap.

---

### Post by andrewsawyer on 2006-02-28
Yes, I have experienced the same problem on computers that have USB keyboards.  I just can't get them to boot.  By the look of it, the USB drivers haven't loaded by the time it asks for the first keystroke.

I've yet to find a way around this unfortunately other than borrowing a ps/2 keyboard for 5 minutes off a friend.

---

### Post by thatsall on 2006-02-28
yeah. ok once you loaded it with the other ketboard it worked. so i wonder if you install it like normal on the hard drive rather then a live cd it would work, like if you get the driver for it or something, just using another keyboard of coarse.........? I hope someone can figure this out.


Also im having trouble getting my wireless card to work......do i need driver for that?

---

### Post by andrewsawyer on 2006-02-28
I have used a PS/2 keyboard to get both the LiveCD and standard CD working with USB keyboard support.

As for your wireless card, what make it is, and do you know the chipset?  Can you type 'ifconfig' at the terminal prompt and paste the details into this thread?

---

### Post by LittleBlue on 2006-02-28
In the BIOS, make sure that "USB Legacy Keyboard Support" and "USB Legacy Mouse Support" are enabled.  This might fix your problem.

---

### Post by taurus on 2006-02-28
Just got my new Dell Optiplex GX620 at work (about a month now) that has USB keyboard and mouse and a LCD monitor.  Didn't have any problem booting Ubuntu LiveCD at all.

---

### Post by thatsall on 2006-03-01
I didnt have that under my BIOS. And also is there a way this problem could be fixed because my mouse is USB also. I kina wanted to use ubuntu because of its desktop and ease of use...im first time linux

---

### Post by kranberry on 2006-03-09
Hi,

I am having the exact same problem.  However, the only USB device I have attached is my Canon printer.

I have a 64 bit AMD chip.  I have tried both the regular and 64 bit Live CD - but it hangs in the same place.

I have also tried Mandriva Live CD, and it also hangs.

This leads me to think there is something unusual about my pc, but I don't know what it might be.  It is an eMachine that is currently running the Media Center version of Windows XP.

Are there any options or things to look for?

Thanks.

---

