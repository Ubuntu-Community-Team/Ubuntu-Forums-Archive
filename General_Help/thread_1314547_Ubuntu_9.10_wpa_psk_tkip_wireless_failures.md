---
title: "Ubuntu 9.10 wpa psk tkip wireless failures"
date: 2009-11-04
forum: General Help
---

### Post by supaman306 on 2009-11-04
HI ALL
 
DOES ANYONE HAVE A GUIDE TO SETTING UP **WPA-PSK TKIP** CONNECTIONS ON UBUNTU** 9.10**?
 
FOR ALL OTHER VERSIONS THE BELOW IS GOOD **BUT NOT** FOR 9.10!
 
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)
 
I DONT SEE WHY IT IS SUCH A PAIN, IT SEEMS LIKE ANY WIRELESS DEVICE CONFIGURATION CAUSES ISSUES ON UBUNTU.
 
I HAVE TRIED FOLLOWING INSTRUCTIONS INSTALLING NDISWRAPPER/NDISGTK (NOT SURE IF VERSIONS ARE CORRECT FOR 9.10, ALSO CHANGING THE INFTERFACES FILE. NADA!
 
SO I JUST WANT TO KNOW IF THERE IS A SIMPLE GUIDE FOR THIS ON 9.10.
 
THANKS

---

### Post by coffeecat on 2009-11-04
First: [SIZE=4]DO YOU HAVE A PROBLEM WITH THE CAPS LOCK KEY?[/SIZE] :wink:

Second: your question is meaningless without knowing which wireless chipset you are using. For four different wireless chipsets in my house, this is my guide to setting up WPA-PSK in Karmic:

1 - click on Network Manager applet.
2 - select wireless network.
3 - Enter WPA key where prompted.
4 - Enjoy the internet.

Perhaps you are unlucky with your wireless device, but no one will be sympathetic IF YOU SHOUT.

Have a look in the Networking and Wireless subforum. There are stickies there telling you what information you need to post about wireless issues.

---

### Post by supaman306 on 2009-11-04
ERR NO I DO NOT BUT IT WAS MORE FRUSTRATION RATHER THAN ISSUE WITH CAPS KEY...Apologies was not meant to sound like shouting.
 
And its not as easy as you described...If you see my post you will see that I have still not had the luxury of such an easy install.
 
Im using a BELKIN WIRELESS G USB...
 
here is my post:
 
[http://ubuntuforums.org/showthread.php?t=1311866](http://ubuntuforums.org/showthread.php?t=1311866) 
 
I have been on this for days....

---

### Post by coffeecat on 2009-11-04
Actually, two of my wireless NICs are...

> **supaman306 said:**
> BELKIN WIRELESS G USB...

.... and they work just fine with Karmic. Well - the Zydas chipsetted one works OK but Network Manager reports a weaker signal and slower connection strength than is true. But I can live with that. But herein lies the problem. Belkin - like many other manufacturers - use different chipsets at different times. What you need to do is to open a terminal and get the output of:

```
lsusb
```Look for the line with 'Belkin' in it. If that doesn't give the actual chipset (it usually doesn't unfortunately), google the complete ID number (4-digits colon 4-digits) and that will usually give you the information needed. Then, and only then, can you make a sensible decision on how to proceed. I'm really surprised and disappointed that no one in that thread has asked for that information. 

By the way - a friendly piece of advice. Just as it's considered rude to SHOUT, it's also considered rude to start a new thread or double-post before the first one has been resolved. I'll ask a mod to close this one, but I'll bookmark your other and mosey over there and see if I can help, **after** you've posted the output of lsusb and the other information.

---

### Post by ibuclaw on 2009-11-04
Thread closed in favour of [http://ubuntuforums.org/showthread.php?t=1311866](http://ubuntuforums.org/showthread.php?t=1311866)

Just a small note @OP though, as great guides may be here, and in despite of the number of people that report success, they are never always universally true in every situation.

Regards

---

