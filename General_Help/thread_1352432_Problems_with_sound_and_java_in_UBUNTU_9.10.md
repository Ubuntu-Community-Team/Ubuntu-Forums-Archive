---
title: "Problems with sound and java in UBUNTU 9.10"
date: 2009-12-11
forum: General Help
---

### Post by moninalexander on 2009-12-11
Hello, all. Recently, I installed UBUNTU 9.10 on my ASUS EEE 1005HA, I am new to linux. Now I am fighting with two problems, namely I can not watch video on youtube and can not use internal microphone. PLEASE, HELP!! I followed some threads, but there is no solution for me. I installed javascript and adobe-flashplayer, but still some web pages inform me that the java script is not turned on. ANY HELP WILL BE APPRECIATED THANKS

---

### Post by vgrisham on 2009-12-11
> **moninalexander said:**
> Hello, all. Recently, I installed UBUNTU 9.10 on my ASUS EEE 1005HA, I am new to linux. Now I am fighting with two problems, namely I can not watch video on youtube and can not use internal microphone. PLEASE, HELP!! I followed some threads, but there is no solution for me. I installed javascript and adobe-flashplayer, but still some web pages inform me that the java script is not turned on. ANY HELP WILL BE APPRECIATED THANKS

Hello. Welcome to Ubuntu. Are you by chance running 64-bit? Are you by chance running Ubuntu Netbook Remix? 

If you haven't done so already, you'll want to turn on the Canonical repository under software sources in Synaptic. 

In Synaptic, search on sun-java6-plugin. If it's not installed, you'll want to mark it for installation. Also search on flashplugin-installer. You'll want to install that too if it's not already.

---

### Post by vgrisham on 2009-12-11
Regarding your mic issue, please pull up your sound preferences (System>Preferences>Sound) and tell me what you see under the Input tab. Make sure the Input volume is cranked up and not muted. Also, you'll want to see what is available under the Connector dropdown menu. For example, I'm using a System 76 laptop that has a microphone just above the space bar. It also has a microphone port on the side for an external, plug-in mic. With my setup, the internal mic is called Microphone 2.

---

