---
title: "Skype, Openwengo, PhoneGaim, gizmo, SIP?"
date: 2006-04-18
forum: General Help
---

### Post by brallan on 2006-04-18
Which cross-platform voicechat client works best? I am not happy with Skype and would prefer something open source and truly cross-platform. I do not  necessarily need videophone, but I do need something like skypeout....

---

### Post by damu on 2006-04-21
I use Ekiga on a daily basis, and it just works fine. I have a sipdiscount account, so I only pay phone calls to mobile phones...great combination

You will find all the details in this forum with the key word sipdiscount

---

### Post by mulvila on 2006-04-22
[QUOTE=brallan]Which cross-platform voicechat client works best? I am not happy with Skype and would prefer something open source and truly cross-platform. I do not  necessarily need videophone, but I do need something like skypeout....[/QUOTE]

I had the same urge and for one week have been using sucessfully Twinkle voip software and VoipBuster SIP account for calling to land lines. It seems the VoipBuster is part of the sipdiscount family and the SIP calls to land lines in about 20 countries are almost free.

Probably because my VOIP phone (yealink usb-p1k) Ekiga does not give quite as good a sound.

Marko

---

### Post by Buffalo Soldier on 2006-04-22
using ekiga to talk with friends and relatives that uses opengizmo... sound quality a lot better than when i was using skype.

---

### Post by brallan on 2006-04-23
I am running breezy, and had errors with twinklephone & ekiga installs, and openwengo crashed. Further reading led me to believe that the software in breezy was outdated, but one atttempt at a dapper install led to a GRUB crash and video problems. MAybe I should give it another try. Are you all running Dapper?

Neither twinklephone or ekiga are cross-platform, although I suppose for skypeout type functionality they will work fine. But everyone I know uses msn, yah00, or AOL, so I wonder how to stay in touch with these folks. Perhaps I can use some kind of Instant Messenger/regular chat program like gaim which opens a p2p connection to their msn/yahoo program and lets me pass them a small windows/mac executable like openwengo which will enable cross-platform voice chat? Anyone have any ideas?

---

### Post by Typhoon on 2006-05-03
Ekiga is cross-platform.  I'm not sure where you find the Windows version, but it has been mentioned several times in the forums.

Typhoon

---

### Post by cvmostert on 2006-05-04
Hey,

How do you exactly call with ekiga using voipbuster? do I have to log out of ekiga.net?

My windows viopbuster works fine, i just wanted to get ekiga working with that..

any suggestions... ?

---

### Post by mulvila on 2006-05-11
[QUOTE=cvmostert]Hey,

How do you exactly call with ekiga using voipbuster? do I have to log out of ekiga.net?

My windows viopbuster works fine, i just wanted to get ekiga working with that..
[/QUOTE]

Ekiga supports multiple accounts, so you just need to set up your voipbuster account in the Ekiga Accounts-section. sip1.voipbuster.com is the SIP server, otherwise just fill your username and passwords.

When calling to land line numbers using the voipbuster account, you need to write the voipbuster sip-sever to the sip-address, ie sip:123456@sip1.voipbuster.com

Good luck,

Marko

---

### Post by deathbyswiftwind on 2006-05-11
[QUOTE=brallan]I am running breezy, and had errors with twinklephone & ekiga installs, and openwengo crashed. Further reading led me to believe that the software in breezy was outdated, but one atttempt at a dapper install led to a GRUB crash and video problems. MAybe I should give it another try. Are you all running Dapper?

Neither twinklephone or ekiga are cross-platform, although I suppose for skypeout type functionality they will work fine. But everyone I know uses msn, yah00, or AOL, so I wonder how to stay in touch with these folks. Perhaps I can use some kind of Instant Messenger/regular chat program like gaim which opens a p2p connection to their msn/yahoo program and lets me pass them a small windows/mac executable like openwengo which will enable cross-platform voice chat? Anyone have any ideas?[/QUOTE]


When was the last time you tried Dapper? Ive used dapper now for a while and it has become VERY stable and so forth. I use skype for all of my calling needs which runs perfect but Im sure you could use others

---

### Post by jvictor on 2006-05-27
I use OpenWengo 2.0 , found it to be pretty good audio-video wise. 
I tested it using Openwengo ng 2.0(Linux) <---> Openwengo ng 2.0(Windows XP)

---

### Post by potrick on 2006-05-28
Hey, can anyone let me know how these compare in sound quality with Google Talk? And does anyone have any idea when a client compatable with Google Talk will be out for Ubuntu? I'm using it in a viritual machine right now and have been really happy with the sound quality.

---

### Post by jvictor on 2006-06-03
Open wengo ng is prety good.. Try Tapioca for Gtalk its amazingly clear

---

### Post by brallan on 2006-06-27
I started this thread looking for a good crossplatform VOIP client, as I support 5 boxes (4 w/linux, 1 w/XP) in a social center with dozens of (account and non-account users) on any given machine. I was NOT able to find an easily configureable truly crossplatform softphone client to use with SIP.

I tried all of the following softphone products:
Skype
ekiga
Wengo
xtensoftphone
linphone
gaim
amsn & yahoo clone

and the following SIP providers:
sipdiscount skype voipcheap 

I have to say, this was a rather frustrating and unsuccessful foray into the field of software and SIP companies. I was disappointed with sound quality, ease of configuration, the variety of vocabulary used for each product, proprietary tendencies of many of theses companies, and a wide disparity in prices. On five computers with a variety of soundcards (all detected by ubuntu), I was only able to get very partial success with every piece of software I tried. Another major problem was figuring out a way to recieve VOIP-in calls, never knowing which machine would be up and running at any given time. All the VOIP software i tried required five different accounts on the five machines.

](*,) 

In the end i decided to get a sip device (linksys PAP2 w/voipcheap) for a landline phone. its much better for our needs than dealing with maintaining two sets of not really crossplatform software on five different machines. It also saves the trouble of having a computer on 24/7 in order to recieve calls.

---

