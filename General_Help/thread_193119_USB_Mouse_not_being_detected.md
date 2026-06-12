---
title: "USB Mouse not being detected"
date: 2006-06-09
forum: General Help
---

### Post by IndigoMontoya on 2006-06-09
Hi. I am using a Toshiba a45-s130 laptop. My problem is that I use a USB optical mouse. It works fine if it is plugged in the the computer boots, but if it is plugged in after boot the red light on the bottom, which is usually constantly on, flashes on and off.

when I plug it in dmesg says this:
hub 1-0:1.0: Cannot enable port 1. Maybe the USB cable is bad?

clearly the cable is fine, because it works when in at boot. Any thoughts?
I have a similar problem with a USB webcam, but am not as concerned with that. Oh, a thumbdrive I use is recognized fine. The mouse is Logitech USB optical mouse P/N 830524-0000. I originally installed the server install (minimal) then did apt-get xubuntu-desktop and a day later apt-get ubuntu-desktop.

I had the same problem in breezy.

Thanks,
Scott

---

### Post by IndigoMontoya on 2006-06-11
anyone have an idea?  It would be a great help

---

### Post by IndigoMontoya on 2006-06-13
I hate to reply to myself to get back to the top, but fixing this would be awesome.

Does anyone have any ideas, or even an idea of what forum to post in?

---

### Post by cheuschober on 2006-07-03
@Indigo-

I've been posting on this exact same problem for the last 9 months... so far no one has taken interest in solving it. I think we're basically SOL. I've not received any replies nor do I expect to. Sorry man. It sucks but any time we want to plug in a usb peripheral be it a mouse a gamepad a camera or printer we'll have to restart the entire system.

Don't think I haven't thought of returning to M$. I've got a laptop here. Restarting just so I can print an email isn't an annoyance it practically makes it useless.

---

### Post by IndigoMontoya on 2006-07-05
Are you using a toshiba as well - or is it a more general problem?  

I have certain USB drives that mount and umount fine when not plugged in at boot and others that only work if plugged in at boot.  I wish I knew more to be able to figure this out myself.

Oh well, I am getting a new laptop with school next month, so hopefully this wont be a problem then.  

Atleast I'm not alone on this ship ;)

Thanks!

---

### Post by Frizguru on 2006-07-08
Oh man... you have had this posted that long? I just made the swtich and suddenly my USB drives do not pick up anything. I can dual boot in windows and it works fine, but when I'm in Linux, nothing in my USB drives are registered or function. Glad to see I'm not alone, but am disappointed no one knows to how to fix it.:-({|=

---

### Post by cheuschober on 2006-08-03
NP.

It's the uhci (sorry off the top of the head, it might be the other  -hci module... whichever one controls usb 1.0 and 1.1 devices)

Something happens with how things are started / initialized during boot that allows this module to recognize and use these devices but it does not work after boot and I'm not genius enough to know how to troubleshoot that.

Same laptop. Same problem. Utterly frustrating.

Le sigh. Some things work much better in linux, some things I couldn't live without linux for, but there are many things that 'headache' does not well-describe.

Ahhh well. My belief in the concept is more important, for now, than my personal comfort or experience.

Best of luck,
~Chad

---

