---
title: "Jaunty freezes at login, crazy screen"
date: 2009-07-31
forum: General Help
---

### Post by radiodj55 on 2009-07-31
Hi all, 
 
i've just come back to Ubuntu after trying a MUCH earlier version a couple years ago...it really has come a long way. I installed Jaunty with the windows boot option on Monday, and in less than a week, was using it more than windows xp.
 
And just when I was about to convert...this happened. I was in a meeting at work and looked over and my laptop had frozen on the screen saver (the sliding tiles one). When I rebooted, I got all the way through the boot process, just when the Ubuntu splash goes away and begins to load the login screen, the screen kind of goes crazy...it looks like an old analog TV signal tuning out...sometimes I may see a portion of the screen saver that it froze on...other times it's just nonsense crazy colors and static. It will change twice before finally freezing completely. CTRL-ALT-F1 and CTRL-ALT-DEL do nothing.
 
I also tried booting from the CD, but get:

[INDENT][FONT=Courier New][ 4.248589] IO APIC resources could not be allocated.[/FONT]
[FONT=Courier New]Loading, please wait...[/FONT]

[FONT=Courier New]BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)[/FONT]
[FONT=Courier New]Enter 'help' for a list of built-in commands[/FONT]

[FONT=Courier New](initramfs)[/FONT]
[/INDENT]It's hard to say if any changes caused the problem, i'm still in that first week, where the OS is still updating itself with the latest packages, and i was just starting to explore adding packages. Last added before the crash were Wine and VLC. I hadn't used Wine yet, and had used VLC once.
 
I'm on a Thinkpad R40, with Windows XP and Ubuntu dual boot (the in-win install, not partitioned) XP boots just fine, with all hardware and software functioning properly.
 
I'm attaching a picture of what the screen is doing.
 
Thanks for your help!
 
--Dave

---

### Post by prshah on 2009-07-31
> **radiodj55 said:**
> the screen kind of goes crazy...

I also tried booting from the CD, but get:
[INDENT][FONT=Courier New][ 4.248589] IO APIC resources could not be allocated.[/FONT]
[FONT=Courier New]Loading, please wait...[/FONT]

[FONT=Courier New]BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)[/FONT]
[FONT=Courier New]Enter 'help' for a list of built-in commands[/FONT]

[FONT=Courier New](initramfs)[/FONT]




I had a similar problem ([attaching this link for screenshots]("http://ubuntuforums.org/showpost.php?p=7132514&postcount=2")), and it was in fact a resolution issue; Jaunty (beta) did not correctly detect the native resolution of my laptop screen. The link also contains a solution that worked for me.

For me too, the splashscreen displayed perfectly, but X had a problem.

As for the issue with the CD, I suggest you simply use another CD; preferably one burnt at the lowest possible speed.

---

