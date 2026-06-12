---
title: "How to run three monitors (ATI HD5770)"
date: 2011-04-24
forum: General Help
---

### Post by rockstar2577 on 2011-04-24
Hello All, 

I just started with Ubuntu today.  So I am extremely new to how the language and the codes work, etc, etc.

But from what I can see, in order for me to get three monitors to work, I have to go into terminal and input some lines of code?

Here is what I have:

1 monitor using on-board graphics (Currently the only one Ubuntu will recognize)

2 monitors on an ATI HD5770 (When I install Ubuntu's third party driver, the system can see an unknown graphics card device, but if I try to enable it in Catalyst, it gives me errors and I have to restart in low graphics mode.

Here is what I have tried so far:

Downloading ATI's actual Linux driver, found out how to unpack it by using the terminal.  Catalyst installs, but gives me "The graphics driver did not install or is not working properly" error.

Then if I try to uninstall that driver and use the third party one, the system basically wont let me uninstall it.  I get an error and it just stays there.


Bottom line, is there an easy way to do this?  I am noticing that others are entering some sort of config  via the terminal and inputing something.

Could someone baby step me through this please?

Thank you

---

### Post by Mark Phelps on 2011-04-25
You didn't mention if your PC has switchable graphics, but from what I've read in those situations, you have to disable the onboard graphics to get Ubuntu to work with the ATI card.

You might try that and see if you can get Catalyst working.

After that, you might then be able to re-enable the onboard graphics and get both working.

---

### Post by rockstar2577 on 2011-04-25
Ok I will give that a try. Thank you!

---

### Post by rockstar2577 on 2011-04-25
Thank you, that did the trick!  So there is no way to get the onboard graphics monitor working, at this point?

---

### Post by Mark Phelps on 2011-04-26
Not that I've read.

---

### Post by rockstar2577 on 2011-04-28
Confirmed as of today.  Version 11.04 supports this.  I am now running 4 monitors off of two cards - One is the on-board, and one is the HD5770.

How did it do it?  I dunno.  I just upgraded today and restarted and it all works :)

---

