---
title: "Voice and Video Chat in Ubuntu lucid lynx 10.04"
date: 2010-09-18
forum: General Help
---

### Post by promish on 2010-09-18
Hello Everyone, I am a linux and mostly Ubuntu newbie. Since the day when i first used ubuntu I have become a total fan of it. Please help me with this problem.

I want to voice and [video chat[IMG]http://images.intellitxt.com/ast/adTypes/mag-glass_10x10.gif[/IMG]]("http://www.neowin.net/forum/topic/939170-voice-and-video-chat-in-ubuntu-lucid-lynx-1004/#")  with my friends on yahoo and msn in ubuntu. The default IM client i.e.  Empathy on ubuntu 10.04 suppots only google and the other famous IM  client pidgin has also the same disadvantage. I have used wine to  install yahoo messenger but every now and then the messenger quits  itslef or gets hanged. Is there any other IM client for ubuntu that  supports voice and video chat on ubuntu for yahoo and msn, 

Please help

---

### Post by Lateralis on 2010-09-18
I have never used Yahoo in my life, so I cannot help you with that.  I do know that there used to be a Linux-specific Yahoo client, but that was an .rpm as opposed to a .deb package.  Whether a Debian package now exists I don't know.  

As for MSN, I use aMSN which is in the Ubuntu universe repository.  To enable the universe, go to System -> Administration -> Software source.  Then check the universe tab and save.  You'll be asked to reload your package database which is fine.  Then:

```

sudo aptitude install amsn

```

I've never used the web/voice on aMSN (normally use Skype for that) but aMSN is the best MSN client I have come across for MSN.

---

### Post by Lateralis on 2010-09-18
Additional.  I've just found this: [Ubuntu forums thread on Yahoo for Ubuntu]("http://ubuntuforums.org/showthread.php?t=81895")
 
Enjoy!

---

