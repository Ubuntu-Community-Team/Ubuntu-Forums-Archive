---
title: "Wireless Not working Atheros AR5001"
date: 2010-04-22
forum: General Help
---

### Post by Edge-1337 on 2010-04-22
Hello everyone. I am 100% new to Linux and know nothing of it, and Ubuntu is my first Linux OS. I upgraded I guess from Windows Vista Home Premium 32Bit.

I have a Atheros AR5001 card in my Compaq Presario C700. I need to know how to get it working. It worked on Vista, but once I installed Ubuntu it stopped working.

I can't get it enabled. So how do I go about getting it enabled to detect my wireless?

Says Wireless is disabled but the terminal can detect the card.

rfkill list

I ran this in Terminal after some searching and found this...

0: phy0: Wireless LAN
Soft blocked: no
[COLOR=Red]Hard blocked: yes[/COLOR]


So I keep pressing the WiFi Switch and nothing happens.

---

### Post by Edge-1337 on 2010-04-22
Sorry for the bump, but noone has any ideas?

---

### Post by squid1230 on 2010-04-25
I understand your wifi card needs to be turned on. I can't be specific but it is f2, or f6 or one of the function keys. Play around with it - you may get lucky.

---

### Post by eqisow on 2010-05-29
I'm in the same situation with the same chipset. Thing is, the wireless was working for a long time, but seems to have just stopped recently (no updates) and is now hard locked, as the OP said.

The hardware wireless button has no effect, just as the OP said.

---

### Post by nmaster on 2010-06-06
i just upgraded (clean install) to lucid yesterday.  i have the same problem (same laptop, same chipset).  the weird thing is that my wifi worked at first.  then i hit the button to manually turn it off.  that didn't do anything at the time, but the next morning i had no wifi.

if anyone figures out some magic that would be great.  this is a really stupid problem.  i have the card, but i can't use it :(

---

### Post by nmaster on 2010-06-06
actually, i remember that the hardware switched worked in jaunty.  i'm going to try installing jaunty to another partition and try turning the switch there. i'll let you know what happens.

---

### Post by nmaster on 2010-06-06
> **neal.m.master said:**
> actually, i remember that the hardware switched worked in jaunty.  i'm going to try installing jaunty to another partition and try turning the switch there. i'll let you know what happens.

SUCCESS!!!  OP, if it worked for me then it'll probably work for you too.  just go ahead and install jaunty alongside lucid.  in jaunty, once you get wifi working (just install the backport modules) you can turn on your wifi card.  then just reboot into lucid. if you want/need more details.  i can help :)

EDIT:after you have the card unblocked, it is still possible to reblock it.  if you hit the button, the wifi card will be blocked when you restart.  also, when in jaunty you need to call "sudo ifconfig wlan0 down" after you hit the button.  

sorry for the sloppiness of this post, i'm just excited to have figured it out :)

---

### Post by nmaster on 2010-06-10
update: you don't actually need to install jaunty. i made a persistent live usb and used that.

---

### Post by 5BallJuggler on 2010-06-10
I had a similar problem with an Atheros Card. When I fixed it I made this to help others, give it a try it may work for you too.

[http://ubuntuforums.org/showthread.php?t=1054629](http://ubuntuforums.org/showthread.php?t=1054629)

---

### Post by nmaster on 2010-06-11
> **5BallJuggler said:**
> I had a similar problem with an Atheros Card. When I fixed it I made this to help others, give it a try it may work for you too.

[http://ubuntuforums.org/showthread.php?t=1054629](http://ubuntuforums.org/showthread.php?t=1054629)

this is a slightly different problem.  for lucid, i didn't even need to install the backports (i did on jaunty though). the card works.  the issue was turning it on after accidentally turning it off. 

in any case, i'm relatively happy with how things work now.

---

### Post by d4nny_d on 2011-05-11
try to start your laptop with the wireless button set to "on" (not the Fn+F2).
for me it worked (on an Asus pro31)
It seems that Natty it's reading the (hardware) button status on boot

---

