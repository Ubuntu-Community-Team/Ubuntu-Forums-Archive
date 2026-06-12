---
title: "Issues with web browsers with kernel 2.6.38-11-generic"
date: 2011-09-28
forum: General Help
---

### Post by tonlika on 2011-09-28
Hi!

I have installed Ubuntu 11.04 32-bit on my HP machine.
I updated to the new kernel 2.6.38-11-generic and since then every time I open multiple
pages (especially 5 or more tabs of Facebook photos) in Google Chrome or Mozilla 
Firefox (they're both the last version in the repositories), the system starts slowing 
down, the mouse moves very slow and sluggish, that I can't even close the tabs 
manually.

I switched to the first console with Ctrl+Alt+F1, tried to login as both root and home user, 
but the login always timeouts and I never can get to enter the password so I can kill 
manually the processes. The only solution is to pull the plug. :)

I noticed that during this time there is high Disk I/O activity, because the LED in the PC 
blinks all the time and the hard disk is working noisily. Can't say much about RAM, Swap and 
CPU usage because I can't open top, but I'm guessing at least CPU usage must be high 
since the system nearly freezes.

Please help me, whats the issue here?

Thanks in advance!
Tony

---

### Post by heyandy889 on 2011-09-28
Huh. Here's what I would try.
[LIST]
[*]Run "Update Manager." In 11.04, found under Applications, Update Manager. If that doesn't help, maybe
[*]Run "Additional Hardware Drivers"
[/LIST]
If rebooting after those guys doesn't solve the problem, I'm kinda stuck. I've never experienced this problem, so I don't know why your problem is happening.

---

### Post by oldsoundguy on 2011-09-28
VERY good chance it is Facebook itself.  NOTORIOUS for having huge memory leaks.

I have memory problems with their pages often. ESPECIALLY when dealing with their internal hyperlinks. You have to remember, every page is awash with scripts.  One bad script an you get slowed down.

Install Ad-Block+ and Grease Monkey into FireFox and that will block all of the advertising scripts. (and it really speeds things up!)

---

### Post by tonlika on 2011-09-28
> **heyandy889 said:**
> Huh. Here's what I would try.
[LIST]
[*]Run "Update Manager." In 11.04, found under Applications, Update Manager. If that doesn't help, maybe
[*]Run "Additional Hardware Drivers"
[/LIST]
If rebooting after those guys doesn't solve the problem, I'm kinda stuck. I've never experienced this problem, so I don't know why your problem is happening.

I tried those but they didn't do anything. I don't see how they could help.

---

### Post by tonlika on 2011-09-28
> **oldsoundguy said:**
> VERY good chance it is Facebook itself.  NOTORIOUS for having huge memory leaks.

I have memory problems with their pages often. ESPECIALLY when dealing with their internal hyperlinks. You have to remember, every page is awash with scripts.  One bad script an you get slowed down.

Install Ad-Block+ and Grease Monkey into FireFox and that will block all of the advertising scripts. (and it really speeds things up!)

It could be that, and I think all the Disk I/O is mostly virtual memory swapping.

But definitely there must be something wrong with the new kernel,
because I just booted into the previous kernel version 2.6.38-10 and
everything just works fine. No slowing down nor in Chrome neither
in Firefox with more than 20 Facebook photos tabs open.

---

