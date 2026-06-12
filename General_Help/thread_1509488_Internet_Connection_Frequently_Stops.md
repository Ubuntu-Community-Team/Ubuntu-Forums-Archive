---
title: "Internet Connection Frequently Stops"
date: 2010-06-14
forum: General Help
---

### Post by OxentroT on 2010-06-14
Hello!
      I have recently upgraded from Ubuntu9.04 to 10.04 and A couple of days after that I opened FF browser and it said 'Offline Mode. So I then click on 'File' and un check 'Work Offline' radio button and reload. It then says 'Cannot Find Server'. After trying a few things to no avail I insert live CD(9.04) and reboot, then the internet connects and works fine with no problem. I then search for resolves to this issue which I copied down for use. I then take out live CD(9.04) and reboot. To my surprise the internet now works again! However, this morning it happened again, as I am using the live CD(9.04) to be able to visit these forums and seek out possible cause and solution.

Any information will be great!

Thank You.

:guitar:

---

### Post by wojox on 2010-06-20
I would try

```
mv ~/.mozilla/* ./mozilla .old
```

Also read this [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by Revolutionary101 on 2010-06-20
Does the computer say that it is connected to a network when the browser can't surf the web?

---

### Post by OxentroT on 2010-06-20
When I input 'ifconfig' it does show active connection as does the dos prompt within WinXP on Vbox. But nothing that relies on a network connection works at all. But when I place live cd of ubuntu8.04 it works. I leave live cd runnign for a few min and reboot, take out live cd and when it boots back up to my desktop it works again :confused:
Not sure what could be causing this. 

Just thought someone would have an idea?

Thank you for replies, it is much appreciated.

):P

---

### Post by Revolutionary101 on 2010-06-20
> **OxentroT said:**
> When I input 'ifconfig' it does show active connection as does the dos prompt within WinXP on Vbox. But nothing that relies on a network connection works at all. But when I place live cd of ubuntu8.04 it works. I leave live cd runnign for a few min and reboot, take out live cd and when it boots back up to my desktop it works again :confused:
Not sure what could be causing this. 

Just thought someone would have an idea?

Thank you for replies, it is much appreciated.

):P

I sometimes have this problem with my computer. My laptop will say that I am connected, but I can't go to any websites. The next time this happens to you right click on the network icon on your panel. When you right click it disable networking, let it disconnect, then enable networking. Thats what I do to fix similar problems that I have.

---

### Post by OxentroT on 2010-06-20
OH YEAH! I forgot all about that thing ](*,) I accidentally removed it and forgot to replace it.. d*****! 
Got It!

Thank You very much!

I will be sure and spend an hour or so on here tomorrow to see if there is anyone that I may be able to assist with any problems that I may be familiar with.

have a good evening

:guitar:

---

### Post by Revolutionary101 on 2010-06-20
I am glad I could help.

> **OxentroT said:**
> 
I will be sure and spend an hour or so on here tomorrow to see if there is anyone that I may be able to assist with any problems that I may be familiar with.

This is what the forum is all about. If you gain knowledge about a problem share it with everyone. I am glad to hear that you will spread your knowledge.

---

