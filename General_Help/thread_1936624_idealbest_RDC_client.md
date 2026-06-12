---
title: "ideal/best RDC client?"
date: 2012-03-06
forum: General Help
---

### Post by RememberWhenItRained on 2012-03-06
I'm not sure if this is in the right section, but here goes:
 I am looking for an app that will allow me to access my Ubuntu linux system from another (any) computer. I know there are several RDC clients for Ubuntu, but which one is ideal? Also, can i turn my system on remotely, or do I need Wake On LAN (WoL)) & Magic Packets for that?

I used LogMeIn back when I was big on Win7, that was alright, but it was annoying at times how you couldn't access if your system was turned off or on standby..

Thanks in advance.

Regards,
Collin

---

### Post by Paddy Landau on 2012-03-07
This is a perennial question, unfortunately with no simple answer.

LogMeIn is a great product, but sadly does not work when accessing Linux.

Have a look at [Yuuguu]("https://www.yuuguu.com/"). It has a free version (or did when I last looked), but it's nowhere as good as LogMeIn.

You can use VNC, but beware that security is nonexistent, so use it only over a secure local network. (RealVNC provides security, but again not for Linux.)

 There's also the built-in Remote Desktop, which I have never tried, because (as I understand) again there is no security.
 
 You can access one machine from another using SSH, but that is rather a lot more complex; and you may have to fiddle with your router to ensure that the requests go through cleanly, especially if more than one device is connected. Once successful, you'll need something like xnest or Xephyr X (Google xephyr for more information). I have not managed to get this to work, but I understand others have.

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

### Post by RememberWhenItRained on 2012-03-11
> **Paddy Landau said:**
> This is a perennial question, unfortunately with no simple answer.
 
LogMeIn is a great product, but sadly does not work when accessing Linux.
 
Have a look at [Yuuguu]("https://www.yuuguu.com/"). It has a free version (or did when I last looked), but it's nowhere as good as LogMeIn.
 
You can use VNC, but beware that security is nonexistent, so use it only over a secure local network. (RealVNC provides security, but again not for Linux.)
 
There's also the built-in Remote Desktop, which I have never tried, because (as I understand) again there is no security.
 
You can access one machine from another using SSH, but that is rather a lot more complex; and you may have to fiddle with your router to ensure that the requests go through cleanly, especially if more than one device is connected. Once successful, you'll need something like xnest or Xephyr X (Google xephyr for more information). I have not managed to get this to work, but I understand others have.
 
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
 
Thank you, Landau.
 
Unfortunately, Yuuguu seems to be only a week trial, so that will not really fit the bill. 
I have looked at both the built-in RDC client, and installed Remina - and have not been able to (properly) configure those yet. (I'm not the brightest Linux user out there, clearly.)
 
Also, with regards to security - while it is nice, I'm not sure how much that really matters. I am using university internet, so i don't have my own wireless and router, so that will probably affect security from the get-go.
 
 
SSH is a thought, but it looks like it has a bit of a learning curve (which i don't particularly mind.) Even accessing a ttyl kind of terminal for my linux machine would work too (so long as I could use lynx on there.)
 
Obtaining the necessary info for my computer should not be an issue (a simple ifconfig, right?) But if i do not have one specific, set, physical machine that i use to access my own computer, that would ruin the chances of SSH, right (or am I misunderstanding this?) If I have the credentials for my own computer, can i log on to it via any computer (so long as I have an SSH client?) Most of the university computers are windows, so I suppose I could run Putty via a flash drive? 
 
Thoughts?
 
Thanks!

---

### Post by Paddy Landau on 2012-03-12
> **RememberWhenItRained said:**
> Also, with regards to security - while it is nice, I'm not sure how much that really matters.
It matters plenty. You don't want other people logging into your computer!

> **RememberWhenItRained said:**
> SSH is a thought, but it looks like it has a bit of a learning curve (which i don't particularly mind.)
SSH will work, and I know it's possible to use the GUI interface (look at Xephyr X and xnest; use Google and YouTube). Also look at VPN and OpenVPN. I have not used it for a very long time and have completely forgotten how, but I think there are instructions on these forums somewhere.

> **RememberWhenItRained said:**
> Obtaining the necessary info for my computer should not be an issue (a simple ifconfig, right?) But if i do not have one specific, set, physical machine that i use to access my own computer, that would ruin the chances of SSH, right (or am I misunderstanding this?) If I have the credentials for my own computer, can i log on to it via any computer (so long as I have an SSH client?) Most of the university computers are windows, so I suppose I could run Putty via a flash drive?
Look at using a free DNS server. Sorry, I have lost my list of those, and in fairness I don't even remember if I have the terminology correct :confused:.

More links:
[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)
[http://openvpn.net/index.php/open-source/documentation/howto.html](http://openvpn.net/index.php/open-source/documentation/howto.html)

---

