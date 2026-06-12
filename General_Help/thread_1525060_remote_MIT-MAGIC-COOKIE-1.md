---
title: "remote MIT-MAGIC-COOKIE-1"
date: 2010-07-06
forum: General Help
---

### Post by Windy Peaks on 2010-07-06
Hello Ladies and Gentlemen of the Forum:

This is a remote ssh -X (ip address) question.

Here is how it goes, when using a 32bit 10.04 Ubuntu OS I can connected to my 64bit 10.04 Ubuntu OS computer through a ssh connection and use the GUI's on the 64bit computer by simply typing it's name (i.e. geany) and up it comes.

However, this is the problem section on of blog, when I try the same ssh -x (ip address) on the 32bit Ubuntu OS from the 64bit Ubuntu OS, I can connect a terminal interface however when I try to launch the GUI I get this error message.
" Invalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-COOKIE-1 keyError: cannot open display: localhost:11.0 "

Any thoughts ????

Regards
Windy

---

### Post by iponeverything on 2010-07-06
-X      Enables X11 forwarding.  
     -x      Disables X11 forwarding.

---

### Post by Windy Peaks on 2010-07-07
> **iponeverything said:**
> -X      Enables X11 forwarding.  
     -x      Disables X11 forwarding.

Thanks for that I will double check that one again

Windy

---

### Post by Windy Peaks on 2010-07-09
NO that didn't fix it.  :(

Anybody else with a thought or two ???

Thanks in Advance

Windy

---

### Post by Windy Peaks on 2010-07-09
To the Forum Folks:

I figured out that I needed to install vnc4server into the 32bit Ubuntu in order to launch the GUI's remotely using a ssh -X (ip address).

Try it for laughs if You want to start a garage computer with GUI's from the comfort of your warm home.

Windy

---

