---
title: "slmodemd"
date: 2006-04-25
forum: General Help
---

### Post by cssutto on 2006-04-25
I am trying to follow the instructions for my modem given by scanModem.

When I enter the following command, I get the not found message.

I have downloaded slmodemd into the Gnome archives and used archives to extract it.

What am I missing?

 sudo slmodemd --alsa -c YOUR COUNTRY modem:1
sudo: slmodemd: command not found


CSSJR

---

### Post by Toxicity999 on 2006-04-25
well where did you extract it? if it wasn't put into a default bin directory then you need to cd to where the Binary file is to run the command. I don't remember where I got mine... but I actually have a Deb which daemonizes (is that even a word? *shrug*) slmodemd so you don't need to run the command. Since I dont remember where it is originally from I could forward it to you, It's still on my gmail. Whatever you want to try. Just remember after running the slmodemd command to point wvdial, gnome-ppp or what have you to /dev/modem or /dev/ttySL0 (the first may be easier to remember but all in all it points to the second.) contact me if you need help, It took me forever to figure it out when I was new. If I can simplify anything just ask.

---

### Post by Raoul Duke on 2006-04-25
See
[https://wiki.ubuntu.com/DialupModemHowto?highlight=%28modem%29]("https://wiki.ubuntu.com/DialupModemHowto?highlight=%28modem%29")

The key command for me was:
$ sudo module-assistant auto-install sl-modem

Thought I'd never get the effing winmodem working, but it does now...

---

