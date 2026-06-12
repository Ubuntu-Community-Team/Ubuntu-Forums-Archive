---
title: "Help for a newbie"
date: 2010-07-23
forum: General Help
---

### Post by Vladimir Pavic on 2010-07-23
[FONT=Verdana]Dear friends, [/FONT]
  
  [FONT=Verdana]I have just downloaded Ubuntu 10.04 Desktop version and browsed the trial version without installing it onto my laptop. OK, I love it. I have decided to get rid of Windows 7 and install Ubuntu as the sole OS. However, I have got three questions before I do it. 1) Ubuntu couldn’t detect any wireless networks. Was that because I run only the trial version? I am really concerned about it as I am a frequent Internet visitor. 2) Ubuntu preloaded movie and audio players couldn’t play anything from my external HD. I got warning that plugin MPEG-2 System Stream demuxer was missing and couldn’t be found (as I couldn’t access Internet, I guess). [/FONT]
  [FONT=Verdana]When you help me to solve the first problem, I suppose I will be able to download the missing plugins. This leads to question 3) Once I download the necessary missing plugins, what am I supposed to do with them? How to install them?[/FONT]
  
  [FONT=Verdana]Thank you very much in anticipation.[/FONT]
  
  [FONT=Verdana]Greetings from Croatia![/FONT]
  
  [FONT=Verdana]Vladimir[/FONT]

---

### Post by watupgroupie on 2010-07-23
It would be helpful to know your wireless card info in order to help you with it. It may be like with my broadcom card that you need to install proprietary drivers. 

For your second question. There is a restricted drivers package you can install once you have internet. Ubuntu can't provide these by default because of legal issues.

For your third question, Ubuntu will download and install them for you. Once you learn about Synaptic and how to use it I think you will understand a lot more.

---

### Post by limestone on 2010-07-23
Ok, the Live CD is not a trail, it's the whole thing :) anyway, you first have to install drivers for your wireless card, it will pop-up after a while or you can access it through the system meny -> hardware drivers. 2) yes you can download the plugins after that, you'll need plugins for most formats. I recommend you to install all plugin using this command in the terminal:
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad flashplugin-installer
```

---

### Post by howefield on 2010-07-23
> **Vladimir Pavic said:**
> OK, I love it. I have decided to get rid of Windows 7 and install Ubuntu as the sole OS.

Firstly, just to mention that it doesn't need to be all or nothing, you can dual boot Ubuntu with your Windows installation, might be useful as you get used to how to make your way around Ubuntu.

> Ubuntu couldn&#8217;t detect any wireless networks. Was that because I run only the trial version?

It isn't because of running a Live CD, if you can connect with an ethernet cable, there may be a driver available via System > Administration > Hardware Drivers. What sort of wireless card do you have ?

> Ubuntu preloaded movie and audio players couldn&#8217;t play anything from my external HD.

Download the relevant codecs once you sort out your internet access.

> Once I downloahe necessary missing plugins, what am I supposed to do with them? How to install them?

Downloading and installing is usually part of the same process, eg, using Synaptic Package Manager you can select the software and mark it for installation, Synaptic will sort it all out for you.

There are other ways of installing software, eg if you download something outwith the repositories, but that's unlikely to be the case for what you need to do to achieve the above.

---

### Post by Vladimir Pavic on 2010-07-24
**[COLOR=#006600][FONT=Verdana]Thanks to all of you who offered your tips. So, here are the specifications of my Wireless card.[/FONT][/COLOR]**
  **[COLOR=#006600][FONT=Verdana]Software version: 5.30.21.0[/FONT][/COLOR]**
  **[COLOR=#006600][FONT=Verdana]Suplicant Version: Dell:EAP-TTLS 5.30.21.0[/FONT][/COLOR]**
  **[COLOR=#006600][FONT=Verdana]Board: Dell Wireless 1397 WLAN Mini-Card Rev 5.00[/FONT][/COLOR]**
  **[COLOR=#006600][FONT=Verdana]Chipset: BCM4315 / BCM22062000[/FONT][/COLOR]**
  **[COLOR=#006600][FONT=Verdana]I hope the provided data will help you to tell me what to do next. As you have already realised, I am not an advanced PC user (but, I could follow step-by-step guidance if it is not too complicated. [/FONT][/COLOR]**
  **[COLOR=#006600][FONT=Verdana]Oh, yes – my laptop model is Dell Inspiron 1545, 2.20GHz, 2GB RAM, HD 250GB[/FONT][/COLOR]**
  **[COLOR=#006600][FONT=Verdana]Thanks.[/FONT][/COLOR]**

---

