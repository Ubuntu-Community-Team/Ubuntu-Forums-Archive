---
title: "Shut Down doesn't turn off my computer - please help :)"
date: 2006-06-05
forum: General Help
---

### Post by Pat_Primate on 2006-06-05
Hello Everybody, ever since I installed ubuntu 6.06 on my LG LW40 Express laptop, my computer doesn't fully turn off when I tell it to shut down from the shut down menu (or pressing the power button). The screen goes blank, but doesn't turn off, the power button light stays on, and the fan keeps blowing. I can power it off by holding the power button for 4 or 5 seconds (only a mild inconvenience) but I was wondering if anyone had a fix for this.

Thank you very much :)

Pat

---

### Post by _simon_ on 2006-06-05
This is just a guess.

in terminal enter gconf-editor

apps -> gnome-power-manager

There is an item that says "action_button_power" maybe that needs to be set to "shutdown"?

---

### Post by Pat_Primate on 2006-06-05
[QUOTE=_simon_]This is just a guess.

in terminal enter gconf-editor

apps -> gnome-power-manager

There is an item that says "action_button_power" maybe that needs to be set to "shutdown"?[/QUOTE]

Thanks for the suggestion Simon. I changed my "action_button_power" setting from "interactive" to "shutdown" and tried to shutdown my comp again, but alas, it had the same problem as before :(

But I appreciate your quick reply :)

Pat

---

### Post by ubuntu27 on 2006-06-05
*bump*

---

### Post by Kobalt on 2006-06-05
That's wierd... It's the kind of problem I usually saw with windows and bad motherboeard drivers... Is your Dapper alone on the hard drive or is there a dual boot ? 
Also - quite a long shot but who cares - did you (or do you still have) a blank screen when you turn on your laptop, when you installed ubuntu ? Did you use some command line like vga=771... ?

Cheers !

---

### Post by Pat_Primate on 2006-06-05
[QUOTE=Kobalt]That's wierd... It's the kind of problem I usually saw with windows and bad motherboeard drivers... Is your Dapper alone on the hard drive or is there a dual boot ? 
Also - quite a long shot but who cares - did you (or do you still have) a blank screen when you turn on your laptop, when you installed ubuntu ? Did you use some command line like vga=771... ?

Cheers ![/QUOTE]

Hey Kobalt, thanx for the reply :)

I do currently have Windows on my system still, on another partition of course, but Im not sure how that could effect my ubuntu operating system (I'm still quite new to linux). This is my first laptop, and It is a recent purchase, so I haven't had any of the older Ubuntu releases on it and am unsure if it would do the same thing with 5.10

As for the blank screen question, Im not really sure what you mean, when I turn on my computer I get the standard boot up screen, and I didn't use any command line options when I installed ubuntu 6.06

Let me know if any of this gives you any suggestions :)

Thanx again

---

### Post by Eversmann on 2006-06-05
It's a well-known problem and it will be fixed in a near future. The problem is inside kernel 2.6.15-23.

I'm having the same problem actually.

Someone at launchpad.net said that one of the kernel developers posted at irc that the fix will be release in the next security revision.

---

### Post by Pat_Primate on 2006-06-05
I have found a bug report on what seems to be the same problem over at launchpad - [https://launchpad.net/distros/ubuntu/+bug/43961](https://launchpad.net/distros/ubuntu/+bug/43961) - and I have added my info and logs to the report.

Is that all that I can / should do as a ubuntu/linux novice with no programming skills? Or are there more things that an average comp user can do to help out?

Pat

---

### Post by Pat_Primate on 2006-06-05
[QUOTE=Eversmann]It's a well-known problem and it will be fixed in a near future. The problem is inside kernel 2.6.15-23.

I'm having the same problem actually.

Someone at launchpad.net said that one of the kernel developers posted at irc that the fix will be release in the next security revision.[/QUOTE]

Thanx for the reply Eversmann, I guess that solves this issue :)

I must admit that I was quite impressed with the speed of and number of responses, thank you all very much. You people are the real beauty of open source (well..... and the free 'beer' & 'speech' part :P)

---------------------------

just out of curiousity, what does Ubuntu27's "bump" message mean? Does that just mean he wanted to bump the thread to the top of the list again to see if there were any more commentaries? (if so thanx ubuntu27)

---

