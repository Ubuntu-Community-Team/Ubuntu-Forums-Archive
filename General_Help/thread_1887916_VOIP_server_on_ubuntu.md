---
title: "VOIP server on ubuntu?"
date: 2011-11-28
forum: General Help
---

### Post by jlparsons on 2011-11-28
Hi folks,

I'd like to set up a system on a ubuntu home server which;

Connects to my incoming SIP phone line (provided by a 3rd party)
Answers all calls with a short recorded message then passes the call to the deskphone/softphone
Records all calls and saves the audio
Forwards calls to my mobile if not answered in the house
Takes voicemails if I am not there to answer.

I'm thinking some sort of SIP server package would do it, however I'd need something with a GUI that's reasonably intuitive.  Any ideas?  Otherwise I'm going to have to use a third party provider which might get expensive.

Anyone have any experience with this?  Couldn't find a linux SIP/VOIP forum to post in, suggestions welcome!

---

### Post by jonobr on 2011-12-02
Hi there,

IMO ,  your asking for a good few features there in one,
what you require involves

Inbound calling which is ok
Auto attendant / autoplay
call transfer
IVR
Find me/ Follow me
Voicemail

There are services out there that offer this kind of stuff for you, but if you wanted to handled it on your own then Im thinking you should maybe look at something like [PBX in flash]("http://pbxinaflash.com/"), 
This is really a small IP PBX but again, what your looking for is complex.

If it were not that complex, Ie call transfer with voicemail or Find me follow me,
you could install a sip solution like opensips, kamailio or asterisk but its all CLI and not what you want.

Installing something like PIAF installs a Linux core and a pbx from the cd, its a simple install and  gives a full featured GUI which allows you to provision extensions however you like,
again though, the machine will be wiped and the PBX will take up the machine,
If you want to get documentation to help you set it up, there is a PIAF without tears manual which is really good

Again, if you want this for your home for one or a couple of phones, I would consider using an external service

---

