---
title: "Administrative Password"
date: 2011-03-15
forum: General Help
---

### Post by rcopley on 2011-03-15
First off, apologies if this has already been answered elsewhere in the forum. I've searched the forum and googled around and there are plenty of people asking this question but I can't find a good answer. What I did find is quite a few responses that missed the point of the question, so forgive the long post, but I want to try to make it clear.

I have used Ubuntu before and I know that the root password is locked by default and that sudo (and the GUI equivalents) are used instead when admin privileges are required.

When I had Intrepid Ibex installed at home I could launch (say) Synaptic from the System/Administration menu. I would be asked "enter your password", I would enter my password, and the program would be run under sudo.

Now with Maverick Meerkat, instead I am asked "enter the administrative password", and if I enter *my *password, the response is "incorrect password". (Let's say for the sake of argument that I'm 100% sure that I've entered *my* password correctly.)

I'd be grateful if someone could acknowledge that this is not the intended behaviour of an Ubuntu system. Even more so if you have a fix!

---

### Post by wojox on 2011-03-15
Have you looked here [Fix Broken Sudo]("http://www.psychocats.net/ubuntu/fixsudo")

And no that's not normal. Something got clobbered somewhere along the line. :P

---

### Post by coffeecat on 2011-03-15
Press Alt-F2 and run "gconf-editor". Now apps> gksu. Is sudo-mode ticked? If not, tick it and you'll find that your password will be accepted. If sudo-mode is not enabled, then the system is prompting you for the root password when you run a command with 'gksu' (which is what is happening with Synaptic). And, of course, you don't have a root password...

That box should be ticked in a default install, but somehow the tick goes awol on occasion.

---

### Post by WorMzy on 2011-03-15
It is still asking for your password. If it's telling you that you've entered it incorrectly, then chances are, you have.

If, for sake of argument, you're 100% sure that you entered your password correctly, then there's a slight possibility that your password is being wrongly interpreted due to it containing characters that aren't yet included in unicode. If this is the case, try changing your password.

---

### Post by rcopley on 2011-03-15
Nice one, thank you wojox for the acknowledgement, coffeecat for the solution, and WorMzy

---

