---
title: "Ssh"
date: 2010-11-22
forum: General Help
---

### Post by Party on 2010-11-22
Hello!I have one pc and one laptop in my house.I have installed windows 7 in the laptop and ubuntu in my pc.I want to share my terminal from my pc to the laptop.I asked my teacher and he told me to use SSH but i really have no idea how to do that.So i've spent like 4 hours trying to find out about shh and how you forward ports and i still have no clue.Can you give me any babysteps on how to do that?Any help is very much appreciated.Thanks!

---

### Post by lmarmisa on 2010-11-22
This page explains the basic topics of ssh:

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

An important question: do you wish to share a text-only terminal (Applications -> Accessories -> Terminal) or the graphical full screen?.

---

### Post by mrnelson1986 on 2010-11-22
You might be making this more complicated than you need to.

1.  Are you trying to connect to your home CPU's from outside of your house?

2.  Are both of your CPU's connected to a local network? With or without internet?

If #1 is true, then you need to do port forwarding, etc, it is much more complicated.  If only #2 is true, and you are trying to connect just from your desktop to your laptop, then all you need is your local IP address of the computer you are trying to connect to (for example, 192.168.1.1XX is the format most linksys routers assign local networks, where XX is dependent on how many CPU's you have hooked up at once).  For connecting to a Windows machine, however, you may need to download and install "cygwin" on your windows computer, and run it as an ssh server, I'm not sure if windows has "ssh" functionality built in.  

If it has it built in, or after you set up cygwin, all you need to do is type in "sudo ssh LOGIN_NAME@192.168.1.1XX" in a terminal, where "LOGIN_NAME" is your windows login name.  Also, enter all commands without the quotes.

---

### Post by Party on 2010-11-30
I finally got it to work thanks to you! Thanks a lot guys!I really took it more complicated than i should have. :)
Oh and #2 was true :P

---

