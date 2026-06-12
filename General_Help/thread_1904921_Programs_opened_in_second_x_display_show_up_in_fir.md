---
title: "Programs opened in second x display show up in first"
date: 2012-01-05
forum: General Help
---

### Post by Mahkoe on 2012-01-05
I've been experimenting with X, and after a lot of fighting, I finally managed to get a second x display open with wmii as the window manager. But, when I get wmii to open a program, it shows up on the first display, where I have gnome and compiz going. I'm guessing this has something to do with environment variables, but seeing as I don't know which, I thought I would ask the good people at these forums.

So, how do I run two xsessions, completely independently, where when I open a program in shows up in the display I'm using?

Thanks

---

### Post by imachavel on 2012-01-05
just got back from a wild journey
I ran this:

startx -- :1

from this reference:

[http://www.cyberciti.biz/faq/running-multiple-x-sessions/](http://www.cyberciti.biz/faq/running-multiple-x-sessions/)

and my computer remoted off to a screen that looked exactly like my desktop but with no icons home folder and no task bar start menu nothing. I think it's obvious I don't know the answer to your question. But I had fun booting into low res mode because whatever I did wouldn't let me boot normally. Oh well I had fun :popcorn:

---

### Post by bluexrider on 2012-01-05
I have done what you are attempting, but it take more than just switching sessions.

You need to set separate .Xsession commands then they will be able to segregate files.

[https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)

Start reading here


**How To Run Multiple X Sessions Without Virtualization**

[http://maketecheasier.com/run-multiple-x-sessions-without-virtualization/2009/07/11](http://maketecheasier.com/run-multiple-x-sessions-without-virtualization/2009/07/11)

---

### Post by Mahkoe on 2012-01-05
Thanks a lot! It works now

---

### Post by bluexrider on 2012-01-05
No problem. Please mark this one
(SOLVED)

---

