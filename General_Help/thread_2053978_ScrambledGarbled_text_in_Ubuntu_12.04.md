---
title: "Scrambled/Garbled text in Ubuntu 12.04"
date: 2012-09-06
forum: General Help
---

### Post by Tiit_Helimut on 2012-09-06
Hi!

After upgrading to Precise Pangolin (12.04), I've been getting garbled text every now and again. Although it's not a serious problem, it's a tad annoying and slows down my work.

The problem only seems to occur with text in text editors, text in nautilus and in the terminal. The text remains garbled until I press any button on the keyboard (this even includes the "print screen" key, which has made this problem hard to capture) and then immediately reverts to normal.

I've attached cropped screenshots to show you what I actually mean by scrambled/garbled. It happens roughly several times an hour (in batches) and seems to happen regardless of how much "uptime" I have.

I've had a search around and people appear to have had similar problems but nothing that really looks like this.

If anyone can help me with suggestions or point me in the right direction regarding fixing this problem then that would be really useful.

Thanks!

---

### Post by Tiit_Helimut on 2012-09-06
Additional couple of screenshots just in case...

---

### Post by andyridesbikes on 2012-09-26
Hi,

I'm having the exact same problem in the terminal and occasionally in emacs. As you said it's annoying but some combination of scrolling, mousing over the text, or typing seems to temporarily fix the problem.

I occasionally have similar problems in both Chrome, Firefox, and adobe acrobat if I'm scrolling through a very large PDF.

Like you I haven't been able to find much information about this problem, let alone a solution, so if you come up with a fix I'd love to hear it!

Thanks!

---

### Post by funicorn on 2012-09-26
try to use the closed source driver

---

### Post by leona on 2012-11-02
I am seeing this problem too, Nvidia graphics card, using nvidia drivers.

---

### Post by moma on 2012-11-02
Hello,
I had the same thing with the free [Nouveau]("http://nouveau.freedesktop.org/wiki/") driver. Try install NVidas or AMD/ATIs official driver via [Software Sources dialog]("https://launchpadlibrarian.net/120799793/Screenshot%20from%202012-10-23%2016%3A32%3A42.png").

Or from command line (for Nvidia):
Open Terminal (Ctrl+Alt+T)
$ sudo apt-get install linux-headers-generic
$ sudo apt-get install --reinstall nvidia-current nvidia-current-dev nvidia-settings
$ sudo reboot

[Bug# 1070427...]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1070427") may have struck/stricken some of you. I think it has been fixed and packages updated. So the bug is history? 
But make sure you've installed "linux-headers-generic" package first, then the display driver (Nvidia or AMD/ATI). Ok?

---

