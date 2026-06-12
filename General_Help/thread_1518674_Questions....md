---
title: "Questions..."
date: 2010-06-26
forum: General Help
---

### Post by MrMario on 2010-06-26
Okay. I have been running Ubuntu along side Windows XP for about two days now. An when I log on to Ubuntu, it all runs smoothly an all. Though I cannot figure out how to scan for a Wireless Network as you would on Windows. Any help?

---

### Post by cj.surrusco on 2010-06-26
Networks should just appear on the list when you click on the network icon on the panel, given that your wireless adapter is functioning properly.

---

### Post by MrMario on 2010-06-26
Nothing appears. An I don't want to go through the process of having to gather all those details to configure it. If I run firefox without internet, will it give me any options to scan for internet?

---

### Post by Revolutionary101 on 2010-06-26
To scan for a wireless network left click on the wireless bars on the top panel on the right side. It should be right next to the battery icon (or close to it). Once you left click on it, you will be show a list of wireless networks that you can connect to.

I hope it helps, and best wishes to you as you use Ubuntu.

Edit: Ugh someone was faster with the response, again.

---

### Post by MrMario on 2010-06-26
Okay [Revolutionary101]("http://ubuntuforums.org/member.php?u=856122"), Please don't leave off yet. You might be able to help me, I am switching over to Ubuntu now on my desktop an I have signed in on the forums on my iTouch to post here. :)


So what do I need to do?

---

### Post by Revolutionary101 on 2010-06-26
This may sound like a stupid question, but is your wireless switch in the on position on your laptop?

Also right click the network icon and check to see if "Enable Wireless" and "Enable Networking" are checked.

---

### Post by cj.surrusco on 2010-06-26
If nothing appears, then your network adapter may not be properly configured.

Post the output of 
```
sudo lshw -C network
```

---

### Post by MrMario on 2010-06-26
I am on a desktop an I believe they were. Ubuntu is starting up now.

---

### Post by MrMario on 2010-06-26
Cj, what do I do with that code. I just got ubuntu. Lol

---

### Post by Revolutionary101 on 2010-06-26
Go to Applications>Accessories>Terminal. Then put the code in there.

---

### Post by cj.surrusco on 2010-06-27
No problem. Just type it up in a terminal. 

From the menu: **Applications>Accessories>Terminal** 
That will open up a terminal for you and then type the code in there.

EDIT: Are we racing to help this guy, Revolutionary101?

---

### Post by MrMario on 2010-06-27
Okay. Hold on. Then what after that?

---

### Post by cj.surrusco on 2010-06-27
> **MrMario said:**
> Okay. Hold on. Then what after that?

Check the response of the command for anything like that says "Wireless Interface"

It would be good if you could post the output on this thread.

---

### Post by Revolutionary101 on 2010-06-27
> **cj.surrusco said:**
> 
EDIT: Are we racing to help this guy, Revolutionary101?

Haha I guess it is sort of a race, but I don't mean that as a competition. I just want this Ubuntu user to solve their problems asap.

---

### Post by bodhi.zazen on 2010-06-27
It is also helpful to show the output of 

```
iwconfig
```

---

### Post by MrMario on 2010-06-27
I see this in the end of the code. 

*-network DISABLED
Decription: Wireless Interface
Physical id: 1
Logical name: wlan0
Serial: 00:0f:66:1c:63:ce
Capabilities: Ethernet physical wireless
Configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


Also when I hover over the network thing it says: no network connection

When I right click it. All 3 are checked 

When I left click it. Both say disconnected

---

### Post by MrMario on 2010-06-27
> **bodhi.zazen said:**
> It is also helpful to show the output of 

```
iwconfig
```
When I did that command I get two things saying no wireless extensions. Then a few things saying :off an some other things.

---

### Post by cj.surrusco on 2010-06-27
> **MrMario said:**
> When I did that command I get two things saying no wireless extensions. Then a few things saying :off an some other things.

What exactly did it say to the right of "wlan0"?

---

### Post by MrMario on 2010-06-27
> **cj.surrusco said:**
> What exactly did it say to the right of "wlan0"?
wlan0: IEEE 802.11bg ESSID: off/any
Mode: managed Access Point: Not-Associated Tx-Power=0 dBm
Retry long limit: 7 RTS thr: off Fragment thr: off
Power management: off

---

### Post by cj.surrusco on 2010-06-27
I won't be able to help you for a while with this problem but check this page out for info. It should be pretty useful.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by MrMario on 2010-06-27
Why can't you help me for awhile?

---

### Post by cj.surrusco on 2010-06-27
> **MrMario said:**
> Why can't you help me for awhile?
 
I will be away on vacation. I am leaving soon.

---

### Post by MrMario on 2010-06-27
Is there anyone who can help me? I need help an that link isn't helping, way to confusing.

---

### Post by MrMario on 2010-06-27
Anyone?

---

### Post by MrMario on 2010-06-27
Please someone

---

### Post by Revolutionary101 on 2010-06-27
Do you know what the make and model of your wireless card?

If you don't know what it is type this into terminal
```
lspci
```
Then copy and paste the results here.

---

### Post by MrMario on 2010-06-27
How do I copy an paste them if I don't have internet on it lol

---

### Post by Revolutionary101 on 2010-06-27
> **MrMario said:**
> How do I copy an paste them if I don't have internet on it lol

Haha that is true. You could just write it down on a piece of paper and type it into your computer.

---

### Post by MrMario on 2010-06-27
Hmm okay.

---

### Post by gadolinio on 2010-06-28
> **MrMario said:**
> How do I copy an paste them if I don't have internet on it lol
Hahahaha we're all soooo used to Internet connection, that we can't even think that we can actually lack it, some day.
If you have any removable media (pendrive, diskette, CD-RW), you can copy and paste the output to a file stored there and then open it from the connected computer to then copy-paste it here. That way you would surely avoid spelling mistakes.

---

### Post by MrMario on 2010-06-28
> **gadolinio said:**
> Hahahaha we're all soooo used to Internet connection, that we can't even think that we can actually lack it, some day.
If you have any removable media (pendrive, diskette, CD-RW), you can copy and paste the output to a file stored there and then open it from the connected computer to then copy-paste it here. That way you would surely avoid spelling mistakes.
Okay. I just need to get Internet on it lol

---

### Post by MrMario on 2010-06-28
Can anyone help me? How do I run the window one on XP.

---

### Post by MrMario on 2010-06-28
Hmmm...anyone?

---

### Post by MrMario on 2010-09-26
Anyone haha

---

