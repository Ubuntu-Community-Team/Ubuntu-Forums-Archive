---
title: "PPPoe problems"
date: 2006-02-16
forum: General Help
---

### Post by Fubdub on 2006-02-16
Well, I'm running a freshly installed Breezy having taken a break from ubuntu since Hoary. Now, back on Hoary PPPoe was working smoothly starting up at boot with no problems, however I now find that it is no longer so. 
First I thought I had to run pppoeconf everytime I rebooted my box, but then I found out, after searching forums for similar problems, that I only have to do:

ifconfig eth0 up
pon dsl-provider

Which of course makes me believe that the problem lies in eth0 not being initialised during boot.

This however is where I'm stuck at.

I would be immensely happy if someone could help me fix it so I don't have to waste precious seconds getting my internet to work everytime I start my computer.

cheers
Leonard

---

### Post by dcstar on 2006-02-16
[QUOTE=Fubdub]Well, I'm running a freshly installed Breezy having taken a break from ubuntu since Hoary. Now, back on Hoary PPPoe was working smoothly starting up at boot with no problems, however I now find that it is no longer so. 
.......
I would be immensely happy if someone could help me fix it so I don't have to waste precious seconds getting my internet to work everytime I start my computer.

cheers
Leonard[/QUOTE]
Can't help with the specific problem, but I'm told the network-manager package helps with other issues like this, you may want to install it and see if it is of use to you.

---

### Post by MP3it on 2006-02-16
I just went through this, info was hard to find

From a terminal window run:
sudo pppoeconf

This worked for me and connects at boot however if not:
sudo gedit /etc/init.d/bootmisc.sh

Before final
: exit 0

Add the line
pon dsl-provider

Hope this helps.
Alan

---

