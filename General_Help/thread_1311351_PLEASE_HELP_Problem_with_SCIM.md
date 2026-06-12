---
title: "PLEASE HELP: Problem with SCIM"
date: 2009-11-02
forum: General Help
---

### Post by Tapas Bose, India on 2009-11-02
Hallo everybody.
I want to write in Bengali. I installed scim-avro found in [http://omicronlab.com/forum/Avro-Phonetic-for-Linux-scim-avro-has-been-released-t2029.html. ]("http://omicronlab.com/forum/Avro-Phonetic-for-Linux-scim-avro-has-been-released-t2029.html")According to that site I have scim icon in my pannel. But I do not have any scim icon. I checked System->Preferences->SCIM Input Method Setup->Panel->GTK and found that the "Show tray icon" option is marked. I googled and found various methods. I tried all of those methods and logout and login several times. But still in the dark. When I try to launch scim from terminal I got the following output:
> 
tapas@My-Child:~$ scim
Smart Common Input Method 1.4.9

Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
Failed to load x11 FrontEnd module.
SCIM has exited abnormally.
tapas@My-Child:~$ 

I also searched google to get the solution of "Failed to load x11 FrontEnd module." but can not found any suitable solution.
Please help me to get the scim icon in my sys-tray. At least any method to type in Bengali easily.
Waiting for reply.

---

### Post by SnappyU on 2009-11-05
try scim -d instead :)

But you may need to put it into the "Startup" section if it works.

---

### Post by Tapas Bose, India on 2009-11-05
> **SnappyU said:**
> try scim -d instead :)

But you may need to put it into the "Startup" section if it works.
I have done everything. scim -d also give the same output.

---

### Post by Irihapeti on 2009-11-05
It's quite usual to get an error message when trying to start Scim manually. It simply means that it's already running. You can check that by looking in the System Monitor, but make sure that "all processes" is checked in the "View" menu.

It sounds as though there is some other setting up that needs to be done. See [http://ubuntuforums.org/showthread.php?t=1267584](http://ubuntuforums.org/showthread.php?t=1267584) (second message) for further details.

---

### Post by Tapas Bose, India on 2009-11-05
> **Irihapeti said:**
> It's quite usual to get an error message when trying to start Scim manually. It simply means that it's already running. You can check that by looking in the System Monitor, but make sure that "all processes" is checked in the "View" menu.

It sounds as though there is some other setting up that needs to be done. See [http://ubuntuforums.org/showthread.php?t=1267584](http://ubuntuforums.org/showthread.php?t=1267584) (second message) for further details.
I did it. But nothing different. Same as previous. :icon_frown:

---

### Post by Irihapeti on 2009-11-05
That system tray shown on the Avro website appears when you press control-space, once you have a document open.

I notice that it mentions that the .deb is for 9.04 only. I'm going to install it and see if it can work on 9.10 That will take a few minutes, probably.

---

### Post by Tapas Bose, India on 2009-11-05
> **Irihapeti said:**
> That system tray shown on the Avro website appears when you press control-space, once you have a document open.

I notice that it mentions that the .deb is for 9.04 only. I'm going to install it and see if it can work on 9.10 That will take a few minutes, probably.
Okay. But I had installed it. but nothing happened.

---

### Post by Irihapeti on 2009-11-05
Yes, it does work in 9.10, which is good news.

Do you have scim-bridge installed as well as scim? My experience is that it's easier to work with.

Then open System -> Administration -> Language Support and check that scim-bridge appears in the keyboard input method system box.

After logging out and in again, it should work. If not, I'm not sure what's happening.

---

### Post by Tapas Bose, India on 2009-11-05
> **Irihapeti said:**
> Yes, it does work in 9.10, which is good news.

Do you have scim-bridge installed as well as scim? My experience is that it's easier to work with.

Then open System -> Administration -> Language Support and check that scim-bridge appears in the keyboard input method system box.

After logging out and in again, it should work. If not, I'm not sure what's happening.
I did every possible things. but nothing changed. Thank you for what you have done for me. I got another two software viz., BONGOLIPI and MUKTOLEKHA for bengali writing and found a website where I can use online keyboard for bengali typing.
Thank you once again.
Bye.
Goodnight.

---

### Post by Matt G Dalian on 2009-12-07
Hi,
 
 I just put Ubuntu Netbook Remix on my Asus eee pc 900 and I had a similar problem:
 SCIM just wouldn't work for me (or I couldn't figure out how to use it!)
 
 I wanted SCIM to input Pinyin (Simplied Chinese characters).
 
 But now my SCIM is &#27809;&#38382;&#39064;&#20102; (no problems!)
 
 Here's what I did: (maybe some details are missing)
 
 First, go to System --> Language Support and install the language you need (I installed Simplified Chinese).
 
 Then I used Ubuntu Software Center to download SCIM (and some related packages).
 
 But when I went to use SCIM Input Method Setup (under the System menu),
 there was no sub menu for Chinese input under the "IMEngine" tab on the left- all it said was "Global Setup" (now that it works I also have a Smart Pinyin menu).
 
 The problem was that when SCIM downloaded it didn't automatically download the packages required for Mandarin Chinese.
 
 So I opened up Synaptic Package Manager and searched for "SCIM" and downloaded some related packages- the ones that had "Pinyin" or "Chinese" in the description.
 
 Now when I opened up SCIM there was an additional option under IMEngine- Smart Pinyin.

But SCIM still wasn't available for use in Firefox.

So under SCIM's Panel --> GTK menu, set Toolbar to show: always.

Now in the lower right corner of any program I see the SCIM icon, and when I click on it I can switch input methods.

Hope that helps.

---

### Post by kaustavdm on 2010-05-05
> **Tapas Bose, India said:**
> I did every possible things. but nothing changed. Thank you for what you have done for me. I got another two software viz., BONGOLIPI and MUKTOLEKHA for bengali writing and found a website where I can use online keyboard for bengali typing.
Thank you once again.
Bye.
Goodnight.
In Ubuntu 10.04, try switching your keyboard input method to **scim-bridge** from scim. It solved the problem for me. I had tried all the methods, including tips mentioned in the bug reports at [https://bugs.launchpad.net/ubuntu/+source/scim/+bug/475800](https://bugs.launchpad.net/ubuntu/+source/scim/+bug/475800), but they didn't work.

---

### Post by Matt G Dalian on 2010-05-06
> **kaustavdm said:**
> In Ubuntu 10.04, try switching your keyboard input method to **scim-bridge** from scim. It solved the problem for me. I had tried all the methods, including tips mentioned in the bug reports at [https://bugs.launchpad.net/ubuntu/+source/scim/+bug/475800](https://bugs.launchpad.net/ubuntu/+source/scim/+bug/475800), but they didn't work.

Also, since I first commented on this post several months ago, I have stopped using SCIM altogether and use **iBus** instead.

I find that iBus is better (easier to setup, easier to use).

---

