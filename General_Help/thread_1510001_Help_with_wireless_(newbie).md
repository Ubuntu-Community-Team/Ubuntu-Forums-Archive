---
title: "Help with wireless (newbie)"
date: 2010-06-15
forum: General Help
---

### Post by OpressedCalamity on 2010-06-15
Hey guys, Just installed ubuntu 10.04, Must say I am very displeased
My wireless doesen't work.
And I can't use a wire
Please help.
Hoping to resolve this issue tonight, the laptop i'm on goes back tomorrow and i don't have a windows cd
Thanks in advanced!!!

wireless usb 150n adapter.

---

### Post by OpressedCalamity on 2010-06-15
If i can't get it working..
I have a windows 98 ME cd around here somewhere..Atleast the internet will work on that.

---

### Post by OpressedCalamity on 2010-06-15
ALSO, wireless worked without installing anything in ubuntu 9.04

---

### Post by 3rdalbum on 2010-06-15
What wireless card, and what is the exact problem (for instance, are any networks detected?)

---

### Post by OpressedCalamity on 2010-06-15
Wireless 150n usb adapter
And yes it does not detect any wireless networks.

---

### Post by Bucky Ball on 2010-06-15
Easy: Reinstall 9.04 and try 10.04 in six months when most of the problems are ironed out. If you need your machine to be stable why did you fix something that wasn't broken? Any particular reason?

---

### Post by OpressedCalamity on 2010-06-15
Because 9.04 is outdated..
Odd
Linux can't connect wirelessly, Vista can <:0
and the latest wine is supported only in 9.10 or later.
And wireless doesen't work in ubuntu 9.10 neither
:(

---

### Post by Bucky Ball on 2010-06-15
Didn't really answer my question. 10.04 is extremely buggy for a lot of people but good luck. Your efforts at fixing the bugs are appreciated by the whole community. Posting bug reports will also be helpful. Consider yourself 'Testing'. :)

---

### Post by OpressedCalamity on 2010-06-15
But it doesen't work in 9.10 either..
is 9.10 buggy as well?

---

### Post by NiCopy on 2010-06-15
I just had the same problem myself using a wireless adapter on my computer.
I started off installing Ubuntu 9.04 and everything worked like a charm, but once I upgraded to 9.10 my wireless connections didn't work. :s
 
So now I've re-installed version 9.04, updated the software and everything is running smoothly. I know this isn't an answer for you problem, but perhaps someone else reading this thread might find it helpful.
 
/NiCopy

---

### Post by OpressedCalamity on 2010-06-15
I would stay with 9.04 
If the latest version of wine worked with it..

---

### Post by OpressedCalamity on 2010-06-15
Is there a console command to connect wirelessly?
I it sees my wireless network just won't let me connect to it.

---

### Post by Bucky Ball on 2010-06-15
Open Network Manager and check you have the correct DNS address(es) under the DNS tab. Check in there that you are a DHCP client or you have assigned a static IP address. Also, what have you got in /etc/hosts file?

When you run:

ifconfig

in a terminal, is it saying 'AP: disassociated'?

---

### Post by OpressedCalamity on 2010-06-15
will do

---

### Post by Bucky Ball on 2010-06-15
It can be a problem if you have set a static IP address on the local machine and the router is acting as a DHCP server. They both try to send each other an IP and Crash! But they can see each other. If you can see the router but can't get to the internet, though, that is usually a gateway problem, DNS IPs generally.

---

### Post by OpressedCalamity on 2010-06-15
Didin't seem to work.
I've found a opensuse cd
I may use that if all else fails, I have a pc-bsd 8 cd.. But wireless doesen't work on that

---

### Post by OpressedCalamity on 2010-06-15
RAGE quit..
Just going to install opensuse, if that works with my wireless i'll be happy <:0
If not i'll just install 9.04 again.

---

