---
title: "TeamSpeak 3 Problems"
date: 2011-06-06
forum: General Help
---

### Post by Aashiq on 2011-06-06
Hey there,
recently installed the client for Teamspeak 3 on Ubuntu. To be precise, TeamSpeak3-Client-linux_x86. 

Any how, when I connect to a server I can get in but before I hear anything; or before long; it crashes.

I ran it through terminal and I'm not sure if this is of any help but this was what I was getting. 

```
2011-06-07 02:51:09.664498|INFO    |MPSingleton   |   | Detected local codeset to be: UTF-8
2011-06-07 02:51:09.665598|INFO    |              |   | Logging started, clientlib version: 3.0.0-rc1 [Build: 14345]
2011-06-07 02:51:09.679124|DEBUG   |PulseAudio    |   | connected to pulse audio server
2011-06-07 02:51:09.725038|INFO    |              |   | Registering plugin command id: {ef2290f2-0709-4d3c-a2d9-71ca8d4e06f2} appscanner_plugin
PLUGIN: registerPluginID: {ef2290f2-0709-4d3c-a2d9-71ca8d4e06f2}
2011-06-07 02:51:09.726837|INFO    |Query         |   | listening on 127.0.0.1:25639
2011-06-07 02:51:09.727129|INFO    |              |   | Registering plugin command id: {a5dcf6a6-58d3-4a1f-8bc3-a783e8bfa0c9} clientquery_plugin
2011-06-07 02:51:10.000716|INFO    |ClientUI      |   | Failed to init text to speech engine
2011-06-07 02:51:10.000938|INFO    |ClientUI      |   | TeamSpeak 3 client version: 3.0.0-rc1 [Build: 14345]
2011-06-07 02:51:10.001019|INFO    |ClientUI      |   | Qt version: 4.7.2
2011-06-07 02:51:10.001077|INFO    |ClientUI      |   | Using configuration location: /home/aashiq/.ts3client/ts3clientui_qt.conf
2011-06-07 02:51:10.784135|INFO    |ClientUI      |   | Last update check was: Tue Jun 7 02:44:32 2011
2011-06-07 02:51:23.490018|INFO    |              |   | No TSDNS found at "runeraiders.guildts.com"
2011-06-07 02:51:26.181415|INFO    |PreProSpeex   |  1| Speex version: 1.2rc1
QFSFileEngine::open: No file name specified
2011-06-07 02:51:33.990753|CRITICAL|GenericPlayback|   | Assertion "samples * sizeof(short) <= maxRequestSize" failed at client/clientlib/sound/genericplayback.cpp:710; 
 
```Not sure what any of that means however around the latter parts was when it crashed. I should mention that A) I'm not too experienced with Ubuntu just yet, and B) I'm running Ubuntu 11.04.

Any help would be brilliant and I thank you in advance.

---

### Post by Aashiq on 2011-06-07
Bump

Anyone? I really can't figure this one out ;/

---

### Post by Aashiq on 2011-06-07
Another bump? ;/

---

### Post by dargaud on 2011-06-07
Can you change your playback master channel to some other device and see if you still have the issue ?

---

### Post by Aashiq on 2011-06-07
Lol, shows me how silly I am. 
That worked, thank you very much.

Thought it may have been a bigger problem considering that there's quite a few people with the same error as me on the Teamspeak official forums.

Cheers.

---

