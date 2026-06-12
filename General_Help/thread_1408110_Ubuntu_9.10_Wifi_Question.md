---
title: "Ubuntu 9.10 Wifi Question"
date: 2010-02-16
forum: General Help
---

### Post by unrealdustin on 2010-02-16
I have been experiencing slight problems while attempting to connect to the internet via a wireless router. 
I can connect to my router perfectly fine on Vista and I could connect to my friends router while I was in Ubuntu, but I can't connect to my router while on Ubuntu. I've been entering the same code that will work when I'm in Vista, but it wont work while in Ubuntu. 
Any help would be greatly appreciated because I am completely lost at this point.

I will gladly go more in depth if I wasn't clear enough.

---

### Post by JCG3 on 2010-02-16
WiFi card? router encryption?

---

### Post by unrealdustin on 2010-02-16
It's just a wireless router connected to a modem. It is password protected, but the password doesn't seem to work when trying to connect and I can't figure out why.

---

### Post by SeaJayEmm on 2010-02-16
What kind of encryption are you using?

---

### Post by unrealdustin on 2010-02-16
I just tried again so I figured I would try to explain again what is going on. 
When I try to connect to my wireless router "Homenet" a box comes up asking for me to input a code to connect. Something like WEP 40/120 is selected in the drop box. I have a 10 character code that lets me connect to my router on vista, but it says there are too many characters when I use it for Ubuntu. 
I'm not too computer savvy so I'm sorry if this is a stupid question.

---

### Post by bcbc on 2010-02-16
Some network cards don't have driver support in linux - in that case you may need to use a windows driver (using ndiswrapper). Certain types of router encryption may also not work depending on the card - I had to change my router to WEP because an old wireless card doesn't support wpa/psk in linux, even though it works in windows.

You need to figure out what type of network card you have:
```
sudo lshw -C network
```

Also what encryption the router is using. It sounds like it's likely not WEP (I kept getting prompted by Network Manager to enter a WEP key on a WPA/PSK connection). Try connecting to it in Windows and check the connection properties - it will probably tell you what encryption it is using.

Here's a link to a troubleshooting guide:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

Take a look through that and post back with more information and then maybe someone here can you help out.

---

### Post by switch10 on 2010-02-16
Try the other WEP option.  Is your password random letters and numbers, or is it a pass phrase that you picked out???

---

### Post by rrnwexec on 2010-02-16
There is a large, lively, and friendly community of Ubuntu users in Vancouver that can help you with this... much easier than using forums if you are nearby. (Try-this-try-that is tiring).

Check us out:
[http://meetup.com/ubuntuvancouver](http://meetup.com/ubuntuvancouver)

I recommend our events on Feb 22 and Feb 27th.

Cheers,
Randall
Ubuntu Vancouver Buzz Generator

---

