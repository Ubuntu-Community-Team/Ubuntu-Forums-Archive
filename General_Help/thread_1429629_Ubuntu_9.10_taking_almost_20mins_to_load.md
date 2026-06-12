---
title: "Ubuntu 9.10 taking almost 20mins to load"
date: 2010-03-14
forum: General Help
---

### Post by Samuraibuntu on 2010-03-14
Hi,  I've recently installed Ubuntu 9.10 (dual boot with Windows 7) and whilst the Live CD was a breeze, after installation, Ubuntu is taking close to 20 minutes sometimes to load.

I've dual booted before with 9.04 on other machines and haven't had a single problem, but this one is frustrating me.

I've attached my Bootchart below and would be extremely grateful if anyone can interpret and provide a workable solution.  Thanks in advance

[IMG]http://img.photobucket.com/albums/v343/dogleish/samuraibuntu-shuttle-karmic-2010031.png[/IMG]

---

### Post by DawieS on 2010-03-14
Your boot-chart is unreadable, even if zoomed in 800%.

I would suggest you look in System - Administration - Log File Viewer. Click the "Messages" tab.

Now look at the left-hand column showing the times of the last boot-session. Check at which process a lot of time lapsed (process got stuck). The total boot-time should take less than 20 seconds, depending on your hardware.

If you cannot resolve the problem yourself, then copy/paste those portions of the log file for interpretation of the forum (A small text is better readable than a massive graphics file).
:grin:

---

### Post by Samuraibuntu on 2010-03-14
Thank you very much for your reply.

Unfortunately, I think Sys>Admin>Log File>Messages is telling me lies!!  It says that it took 17 seconds to boot (21:42:18 to 21:42:35) but the actual time to boot was over 10 minutes.  In fact, I initiated the boot before 21:42 (roughly 21:30) and the actual time to a workable desktop was 21:44.

I'm at a loss :(

---

### Post by DawieS on 2010-03-15
Could you please elaborate more how you initiate the boot?
Do you use Grub, or Wubi?
Is there any network activity?
When you press enter on the menu, does the disk LED light up?
Are there any messages displayed on screen?

---

### Post by Samuraibuntu on 2010-03-15
> **DawieS said:**
> Could you please elaborate more how you initiate the boot?
Do you use Grub, or Wubi?
Is there any network activity?
When you press enter on the menu, does the disk LED light up?
Are there any messages displayed on screen?

I use Grub.  There is a LAN cable plugged in, if that's what you're asking re: the network activity.

Yes, when I hit enter on the grub menu, the disk led lights up and does something - the PC fans start spinning frantically for a long while.  The screen is blank; no messages until the Ubuntu splash screen.

---

