---
title: "Evolution - The road ahead"
date: 2009-07-03
forum: General Help
---

### Post by swappa on 2009-07-03
Greetings. 
I recently replaced my Vista install with a x64 ubuntu jaunty install on my work laptop. It is working great, albeit with a few annoying things here and there. 

My company is on a Exchange 2007 server and that, from what I can tell, rules out Evolution. I have used Evolution on and off for a few years. I have never been happy with it with regards to Exchange (like all emails in the in-box disappearing), but after our upgrade I cant use it at all. This is not a big deal, I run my Windows Vista as a Virtual machine so I have my Outlook,  but I would really like to use Open Source apps where I can...I have seen a few suggestions pointing at Imap, but I need my calendar. 

I dont except anyone to tell me what the problem is. I know Evolution doesn't support Exchange 2007, but can anyone shed some light on the Evolution road map maybe? Will they ever support Exchange 2007? I have been looking at their home page but I only see stuff from 2008 with regards to future plans.

Thanks

---

### Post by blueridgedog on 2009-07-03
I can't tell you the road ahead, but here are two points:

1.  Crossover office runs outlook 2003 great under Linux
2.  Some companies are moving away from exchange and toward Zimbra, so you should "bring the mountain" to you so to speak.

---

### Post by swappa on 2009-07-04
> **blueridgedog said:**
> I can't tell you the road ahead, but here are two points:

1.  Crossover office runs outlook 2003 great under Linux
2.  Some companies are moving away from exchange and toward Zimbra, so you should "bring the mountain" to you so to speak.

I am aware of the crossover alternative but then I am better of using my Outlook 2007 on my virtual machine. Zimbra looks exiting but convincing my IT dept to move away from Exchange...hmm, maybe in a million years :-) 

Thanks for your input.

---

### Post by PmDematagoda on 2009-07-04
Have you tried version 2.26 of Evolution? According to the Gnome 2.26 release notes:-
> 2.3.&#8195;Evolution Evolves its Migration from Windows

GNOME's e-mail and groupware suite, Evolution, has gained two important features for helping users who are migrating to GNOME from Microsoft Windows environments.

First is the ability to import Microsoft Outlook Personal Folders (PST files) directly in Evolution. E-mail, contacts, appointments, tasks and journal entries are supported. Previously, the files had to be imported via a third-party utility, such as Thunderbird on Windows.

Second is support for Microsoft Exchange's MAPI protocol. This is the protocol that Microsoft Outlook uses to communicate with Exchange. Previously, Evolution only supported Exchange's SOAP protocol, which is not available on all Exchange servers. This support significantly improves Evolution's integration with Exchange servers.
so you probably may have better luck now.

---

### Post by swappa on 2009-07-04
> **PmDematagoda said:**
> Have you tried version 2.26 of Evolution? According to the Gnome 2.26 release notes:-

so you probably may have better luck now.

Haven't tried it myself but by crawling the various forums out there I can tell that some people did make it work by spending a lot of time tampering with various settings, while the mainstream reports that it is not working. I dont really wanna spend a lot of time on something that would or wouldn't work. I need this to work more or less out of the box. 

Thanks for your input

---

### Post by txcrackers on 2009-07-04
The last I tried Evolution produced at least being able to (barely) do e-mail (threading conversations is horribly broken). Calendar is completely shot. At this point, I'd classify Exchange support as "extremely experimental" -- but at least it's partially working. That's kinda huge for having to reverse-engineer the protocols.

Personally, at work I'm using Outlook 2007 in Crossover. Works well enough except for the fact that it's Outlook (which, IMHO, sucks).

---

