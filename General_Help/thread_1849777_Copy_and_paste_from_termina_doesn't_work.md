---
title: "Copy and paste from termina doesn't work"
date: 2011-09-25
forum: General Help
---

### Post by semsaudade on 2011-09-25
Hi to everybody. In my Ubuntu Netbook Edition 10.04.02 I can't use copy and paste from terminal. 

I tried every possible way (right clicking with mouse and selecting copy, using ctrl-shift-v, using menu in terminal) but when I try to paste the text in gedit (or any other place) the content is always empty.

Is there any way to solve or to investigate this problem? Thanks a lot for your help!
Giancarlo

---

### Post by CatKiller on 2011-09-25
Not closing the Terminal window before you try pasting is the only thing I can think of.

---

### Post by semsaudade on 2011-09-25
I do not close terminal window! The most strange thing is that copy and paste does function just after booting PC. But it works just once: after first copy and paste from terminal, next attempt always fails.

It could be some sort of conflict in memory allocation?

---

### Post by patryk77 on 2011-09-25
Does copy/pasting with middle click work?

Simply highlight the text to copy, and click the middle mouse button (or both left and right at the same time if you don't have a mouse with a scroll wheel) in the application you want to copy to.

---

### Post by raja.genupula on 2011-09-25
Hey man , actually its a bug.You can find more information on this at the given link & solution for this is simply getting this package gnome-terminal version 2.32.1-0ubuntu3.

[http://askubuntu.com/questions/7189/why-does-pasting-sometimes-not-work-in-gnome-terminal](http://askubuntu.com/questions/7189/why-does-pasting-sometimes-not-work-in-gnome-terminal)


all the best

---

### Post by semsaudade on 2011-09-26
Thanks raja.genupula. I read the bug report. So I hope it will be solved in future...

---

### Post by raja.genupula on 2011-09-26
Hi the solution is also in my post. please check your gnome-terminal with version i have given ,gnome-terminal version 2.32.1-0ubuntu3.


All the best

---

### Post by raja.genupula on 2011-09-26
> **linux2001 said:**
> SHIFT+Ctrl+C to copy selected text
SHIFT+Ctrl+V to past selected text

Hi actually both things work . Ctrl+Shift+C & Shift+Ctrl+c both we can use for copying and similarly that paste command also. But he is facing a Bug & Due to that he was unable to do copy an do paste from the terminal.

---

### Post by tgwilt on 2012-09-24
When I used to use FreeBSD and other *nix varients 4 or 5 years ago, all I had to do was highlight text then press the middle button of the mouse, or both buttons if you didn't have a middle button to paste said text.

Now it seems I have to highlight the text, right click and choose Copy, then right click again to paste.

Is there any way to have the mouse revert to this behavior? I am currently using XUbuntu 12.04 LTS, but the behavior extends to the gnome-terminal (3.4.1.1-0ubuntu1) and xterm.

I know I can use the keyboard shortcuts of Ctrl-Shift-c and Ctrl-Shift-v, but sometimes it is just easier to use the mouse. Maybe I have to just accept the current behavior?

Or am I living in the past?:P

---

