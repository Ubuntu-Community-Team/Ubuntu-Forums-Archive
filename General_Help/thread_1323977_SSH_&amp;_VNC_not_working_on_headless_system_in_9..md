---
title: "SSH &amp; VNC not working on headless system in 9.10"
date: 2009-11-12
forum: General Help
---

### Post by tribin on 2009-11-12
After replacing my Ubuntu 9.04 install with a fresh 9.10 install, I'm unable to connect to my SSH and VNC servers without a monitor connected. It had worked in 9.04.

So I started over with a clean install of 9.04 and a clean install of 9.10 alongside it, to test both Ubuntu releases without any variables. The result was the same: after setting up OpenSSH and enabling Vino, 9.04 allowed me to login to both when the system was started without a monitor connected, while with 9.10 it wasn't possible to connect.

Any ideas why? The system is an Asus Eee Box B202, with its DVI>VGA dongle left plugged in when running headless. The Ubuntu variant is desktop i386.

---

### Post by denarced on 2009-12-04
I have the same problem
I guess it's easier to install jaunty server then

---

### Post by coolfiretech on 2009-12-05
I am also having this problem.  I have found that it can be resovled using a dummy connector.  Put 3 68-75 ohm resistors between pin 1-6, 2-7 and 3-8. See instructions [here]("http://www.xtremesystems.org/forums/showthread.php?t=200444").

Although this solution worked for me, I was hoping that there was a easier way via software or config file.

Anyone have any suggestions?

---

### Post by yeehaw on 2009-12-10
Have you tried to configure a 'virtual monitor' with the /etc/X11/xorg.conf file?

Source: [http://ubuntuforums.org/showthread.php?t=1297815](http://ubuntuforums.org/showthread.php?t=1297815)

[INDENT]Section &#8220;Device&#8221;
[INDENT]Identifier &#8220;VNC Device&#8221;
Driver &#8220;vesa"[/INDENT]
EndSection

Section &#8220;Screen&#8221;
[INDENT]Identifier &#8220;VNC Screen&#8221;
Device &#8220;VNC Device&#8221;
Monitor &#8220;VNC Monitor&#8221;
SubSection &#8220;Display&#8221;
[INDENT]Modes &#8220;1280×1024&#8243;[/INDENT]
EndSubSection[/INDENT]
EndSection

Section &#8220;Monitor&#8221;
[INDENT]Identifier &#8220;VNC Monitor&#8221;
HorizSync 30-70
VertRefresh 50-75[/INDENT]
EndSection[/INDENT]

I just configured my headless box with Ubuntu 9.10 with VNC and SSH, here are my notes on my configuration: [http://scotttyee.com/blog/2009/12/09/linux-headless-ubuntu-with-vnc/](http://scotttyee.com/blog/2009/12/09/linux-headless-ubuntu-with-vnc/)

---

### Post by coolfiretech on 2009-12-11
Yeehaw, thanks.  That is exactly the kind of solution I was looking for.  I will give that a try next time work on the box (its at a clients location).  

Thanks again.

---

