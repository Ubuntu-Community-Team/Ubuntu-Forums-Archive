---
title: "Tor - Firefox - Hulu - Adobe Flash Plugin Issues"
date: 2010-04-10
forum: General Help
---

### Post by atomicben on 2010-04-10
As you can see by the title of this thread, there are multiple things at play here so I didn't know exactly which category to put this in.  Sorry if it's in the wrong place.

Here goes:
I'm in Canada and I want to use Hulu.  When I go there I get the standard message telling me that I can only use Hulu if I'm in the states. 

So I installed Tor to get around that restriction.  However, when I go to Hulu with Tor Enabled i get a message that says I must use Adobe Flash 10.0.22 or higher.

If I disable Tor again and go back, I'm back to the other message about being in the US.

I've done some searching and I see people reporting problems with Hulu saying they need a certain version of flash, but I don't see anything about Tor in those threads.  That's why I'm starting this new one.

Here's some version info:
32 bit Ubuntu:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
Linux 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

Torbutton version: 1.2.4

Tor version: 0.2.1.25-2~karmic+1

Polipo version:  not sure but I just downloaded and installed it yesterday.

Flash plugin Shockwave Flash 10.0 r45:
File name:  libflashplayer.so Shockwave Flash 10.0 r45   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes

Firefox: 3.5.8

---

### Post by keithg67 on 2010-04-16
You need to go to the settings for tor defualt it disables flash completly if your using firefox the little tor button at the bottom right (right click it) and change the settings for it. this will get rid of the message to upgrade your flash I had the exact same issue.

Btw I am trying to install tor could you please give me the directions you used to install it on ubuntu 9.10.

---

### Post by atomicben on 2010-04-16
I followed the instructions right from the tor website [http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)
 
they worked great.  I couldn't beleive how smooth it was.  And the Torbutton add-on to firefox is sweet, you click it to toggle tor on and off.  
 
Have you tried those instructions?  They tell you to use Polipo instead of Privoxy.  I didn't really know what the major differences were so I didn't have a preference.  I figured it Tor reccomended it, I should use it.
 
I have one tip.  
 
The instructions at one point tell you to reboot polipo
[FONT=Courier New]/etc/init.d/polipo restart[/FONT] 
before you continue.  
 
I followed the instructions to the letter and it didn't work until I rebooted my machine.  It was very frustrating because the instructions don't call for a machine reboot but I tried it and it worked.

---

### Post by lovinglinux on 2010-04-16
Just an advice....using Tor for bandwidth intensive stuff (like torrents) is not considered polite, since Tor relies on  donated bandwidth. I'm not sure how much bandwidth Hulu requires, because I can't access it, but I'm sure Tor wasn't designed for that. Most important, bypassing Hulu geo restrictions with Tor is certainly not legal, at least in the US, which is the country of origin of Ubuntu forums and Canonical. So it is not allowed to talk about this on the forums.

I'm not a moderator or anything related to the forum staff. I just thought you should be aware of this.

---

### Post by keithg67 on 2010-04-16
I personally set mine as a relay on my computer at home so I am not taking away anything I personally dont already donate to tor. as far as it being illegal that would depend on the country the person is in and what that countries laws are. And no I am not trying to start a arguement but he is using tor for the ability of anonymity and that is specifically what tor was designed for. he asked a question I answered it in fact if you search it on the tor forums you will see that even mods there answer these same questions they dont advise it but they dont banish it either.

---

### Post by lovinglinux on 2010-04-16
> **keithg67 said:**
> as far as it being illegal that would depend on the country the person is in and what that countries laws are.

You are correct, but the forums are in the US, so we should follow the board rules.

> **keithg67 said:**
> And no I am not trying to start a arguement but he is using tor for the ability of anonymity and that is specifically what tor was designed for.

No, he is not. The OP might also be using Tor for anonymity, nothing wrong with that, but this thread is specifically about using Tor to bypass Hulu restrictions. 

> **keithg67 said:**
> he asked a question I answered it in fact if you search it on the tor forums you will see that even mods there answer these same questions they dont advise it but they dont banish it either.

Recently they are even closing threads about how to download from YouTube, which does not use any kind of tool to restrict user access, but does not allow to download according to their terms of service.

Anyway, I have reported this thread, so let the moderators handle it.

---

### Post by Iowan on 2010-04-16
Closed for review.

> I'm in Canada and I want to use Hulu. When I go there I get the standard message telling me that I can only use Hulu if I'm in the states. Consensus suggests a legal limitation in Canada.  You're welcome to appeal in the [Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123").

---

