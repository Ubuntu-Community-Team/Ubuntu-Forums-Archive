---
title: "System freezes ONLY for the duration of no keyboard or mouse input"
date: 2012-02-06
forum: General Help
---

### Post by gjwebber on 2012-02-06
Hi all,

I've just installed 11.10 on an old Toshiba A30, but am having a very strange problem.

The laptop seems to work perfectly, except I can't leave it running and expect it to resume whatever it was doing before. When I stop touching the mouse or keyboard, it freezes. When I move the mouse, it resumes as normal.

I can see this using the system monitor tool, the graph stops moving entirely when I stop moving the mouse. The same for the ping command. If I set it going and move the mouse, all is good. As soon as I stop moving the mouse, it stops pinging. When I move it again, it continues pinging as if nothing ever happened. Ping time doesn't increase or anything. It's as if EVERYTHING just stops.

Any ideas what could be causing this?
What can I do to try and fix it?

It's really hard to search for, everything comes back as the mouse freezing on peoples systems. Mine is sort of the opposite of that. My system "freezes" when I'm not moving the mouse.

Thanks for any help,
Gareth

---

### Post by HiImTye on 2012-02-06
that is such a strange problem, I am at a complete loss

---

### Post by aasdfasdfg on 2012-02-06
> **gjwebber said:**
> Hi all,

I've just installed 11.10 on an old Toshiba A30, but am having a very strange problem.

The laptop seems to work perfectly, except I can't leave it running and expect it to resume whatever it was doing before. When I stop touching the mouse or keyboard, it freezes. When I move the mouse, it resumes as normal.


Has this happened throughout your entire experience with Ubuntu? Because I have a hard time believing that you were constantly moving mouse/keyboard during the install process, for instance...

Personally, I would do some more tests to ensure the problem is as you describe it. For instance, I would open a terminal and run
```
apt-get update
apt-get upgrade
```with proper permissions. As I'm sure you are aware, this is just going to update and install recent packages. I am suggesting this because after you press enter on each command, you will not be giving the computer any keyboard or mouse movement, whereas it should continue running with verbose output.

If you run these commands and STILL observe the same issue as you have described, then we may well be stumped.

---

### Post by gjwebber on 2012-02-06
Not exactly. I had a few issues with the install freezing up on me, so it didn't go smoothly from the start. I have done an md5sum on the .iso and the CD I used to install it, everything is fine in that respect.

It's really hard to explain when it does it. It's not quite as straight forward as I first thought. I did the updates last night, and yes I did sit there moving the mouse the whole time, just in case, so I can't do that as you ask.

From what I can see now, having certain background threads running causes the problem to go away. By this, I mean the computer works PERFECTLY when I have a Firefox download running in the background (clock seconds update as expected, for another example). As soon as the download is done, the clock freezes until I move the mouse again.

Could this be something to do with interrupts? What about ACPI?

Thanks for any more help,
Gareth

---

### Post by aasdfasdfg on 2012-02-07
This is a very puzzling issue and your guesses are as good as mine.

Now let my speculation run wild. When you mention interrupts/ACPI at the end of your last post, you are getting quite low level. I don't think it is a low level issue, because something like a firefox download running in the background is at the software level, and should not make a difference to low level stuff. However, if it seems to fix the problem, maybe we could experiment with what other background process solve the problem. For instance, open a terminal and type ```
zenity --progress &
```
This should fork a progress bar window into the background. Does this background process change anything? What about hooking up the progress bar to a script that slowly increases?

---

### Post by gjwebber on 2012-02-08
SUCCESS!

I finally managed to fix the problem last night. After countless lock ups, I decided to try reinstall one more time. If that didn't work I was going to throw in the towel for this machine.

So at the boot screen, I decided to turn off the top 3 options (ACPI, I forget the other two) just to see what happens. Everything worked great in the LiveCD. Reboot and leave them all on, I get the usual problem. Finally, I feel like I'm getting somewhere. Reboot once more, turning just ACPI off. Everything works great.

So yeah, I reformatted the machine and then edited GRUB to permanently disable ACPI. Everything is working great now. Only took two and a half days to work it out, haha.

I'd love to know how certain processes running seemingly made the issue go away temporarily.

Thanks for helping me out :).

Regards,
Gareth

---

### Post by sergioperr on 2012-03-03
I had the same problem with a Toshiba Satellite and Ubuntu 11.10.
I coudn't even run Synaptic because 2 or 3 minutes after starting up, system hunged down.
It was impossible start Ubuntu in secure mode, so the only way to update/upgrade was turning ACPI to OFF.
Other people asked me how I did it, so I'll try to  explain here.
1.  Boot your system but keep on Grub menu (the first one with options to boot different operative systems) simply typing any cursor key up/down;
2. Highlight the line with normal Ubuntu system;
3. Press 'e' key to enter "Edit mode"
4. Look for the line with boot options like "vga=off" and add "acpi=off"
5. Press 'F10' to boot

You are done! Ubuntu will run endlessly as usual.
After updating/upgrading you could make this change permanent or not. It it is the case, you can download a grub edit tool like "Grub customizer" or "StartUp manager" to do it without to mess with grub menu directly.
:D

---

