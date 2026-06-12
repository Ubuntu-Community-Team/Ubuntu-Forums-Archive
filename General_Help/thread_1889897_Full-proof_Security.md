---
title: "Full-proof Security"
date: 2011-12-02
forum: General Help
---

### Post by hpon on 2011-12-02
Hi,

I need a full-proof security solution for my desktop.  

My first inclination is to have two different computers; one that is not connected to anything (Internet or network), and one that is connected but does not contain any confidential info.

What do you suggest?  Could I have one completely isolated "sandbox" for Internet stuff, and another "sandbox" for confidential data, all within the same computer?

Best Regards,
hpon

---

### Post by haqking on 2011-12-02
> **hpon said:**
> Hi,

I need a full-proof security solution for my desktop.  

My first inclination is to have two different computers; one that is not connected to anything (Internet or network), and one that is connected but does not contain any confidential info.

What do you suggest?  Could I have one completely isolated "sandbox" for Internet stuff, and another "sandbox" for confidential data, all within the same computer?

Best Regards,
hpon

No such thing as fool-proof security in a networked world i am afraid.

And in case you didnt know Linux is upon equal par with Windows and other end-user OS from a security standpoint.

Read here to get a some foundation for Ubuntu Specific information a few of of use here have been working on:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

It will link to other sources of information about browser security and safer surfing and the like.

Enjoy

---

### Post by alphaamanitin on 2011-12-02
You best option would be a full HD encryption using AES.  If you don't mind using windows, you could make a hidden operating system with TrueCrypt.  Here is Bohdi.zazen's page on doing full HD encryption with the ubuntu alternate cd [http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs).  No matter what you do though, if anyone can get you to run their program on the your machine, or gets physical access to your computer you have zero security.  Also, since most people never need the level of security you are talking about, unless they have a real threat of people using keyloggers and the like to steal their data, professionals who do this do not even need physical access.  It is possible to detect what keys are being used via high tech analysis of the sound of the keys being typed, and in the case of the FBI, monitoring the electronic and electromagnetic changes in the computer while typing.  In the former, the device does not even need to be attached to the computer but can merely be nearby.  

Basically, if you just want to keep financial info safe, buy a new HD and encrypt it with TrueCrypt.  If you have more serious reasons, I would say the best option would be a hidden OS with Truecrypt or a hidden TrueCrypt encrypted volume.  It is easy to prove an HD is encrypted, it is impossible to prove how many encrypted volumes are on an HD.  Basically you Encrypt a HD then make a new encrypted volume inside the original encrypted volume.  If you are ever forced to give the passphrase you give the passphrase to the outer volume and as the people work on that they damage the info on the inner volume, destroying the very data that they wanted.

AlphaA

---

### Post by collisionystm on 2011-12-02
> **hpon said:**
> Hi,

I need a full-proof security solution for my desktop.  

My first inclination is to have two different computers; one that is not connected to anything (Internet or network), and one that is connected but does not contain any confidential info.

What do you suggest?  Could I have one completely isolated "sandbox" for Internet stuff, and another "sandbox" for confidential data, all within the same computer?

Best Regards,
hpon



Use virtualbox to make a virtual machine.
Store the virtualmachine on a usb drive inside of a locked case bolted to your desk. Hide it from view. you can get very small usb hard drives now-a-days
Turn off networking in the virtualmachine
Or. Keep your machine on a micro sd card and just plug it into your computer when you want to run it. Keep the card in a safe when not using it

---

### Post by |{urse on 2011-12-02
A good proxy + opensolaris livecd running under virtualbox, using the latest tor-browser bundle. Not foolproof but any further than that and you're just getting fancy.

---

### Post by collisionystm on 2011-12-02
> **|{urse said:**
> A good proxy + opensolaris livecd running under virtualbox, using the latest tor-browser bundle. Not foolproof but any further than that and you're just getting fancy.

No way would I ever use 'tor'

any kind of proxy that does not belong to you and is not running on your own network is just plain scary. You never know what information is being cached on the other end

---

### Post by |{urse on 2011-12-02
Really the only worry is that someone could potentially sniff exit nodes from what I understand, I'd trade that up for anonymity. Please tell me more about why tor is dangerous, I've never heard that until now.

Forgot to add a decent hardware firewall to my comment above.

---

### Post by Basher101 on 2011-12-02
> **|{urse said:**
> Really the only worry is that someone could potentially sniff exit nodes from what I understand, I'd trade that up for anonymity. Please tell me more about why tor is dangerous, I've never heard that until now.

Forgot to add a decent hardware firewall to my comment above.

was tor not kind of the "only" browser to actually hide information and thus be the safest browser avaiable? not sure tho, but thats what i heard/read over the interwebz.

---

### Post by Habitual on 2011-12-02
> **collisionystm said:**
> ...You never know what information is being cached on the other end


"Tor cannot and does not attempt to protect against monitoring of traffic at the boundaries of the Tor network, i.e., the traffic entering and exiting the network." [...]("http://en.wikipedia.org/wiki/Tor_proxy#Weaknesses")

---

### Post by haqking on 2011-12-02
Tor has a few vulnerabilities as does anything in a networked world

[ESEIA Hack Tor Network]("http://thehackernews.com/2011/10/tor-anonymizing-network-compromised-by.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+TheHackersNews+%28The+Hackers+News+-+Daily+Cyber+News+Updates%29")

Also all traffic goes throughs relays, do you trust those relays ?

It is also pretty slow whether you use it with polipo or privoxy.

Personally i only use it for a cloak in IRC other than that is too slow.

Either way its the Internet, your privacy and anonymity is limited ;-)

---

### Post by |{urse on 2011-12-02
Lol so all in all, fool-proof security == nonexistant. Btw haqking , irc is where I first used tor with znc. And it is way too slow, for everyday web use.. agreed. Are there any pro-privacy networks anyone is aware of that may be a little faster (maybe even safer?)? Also, the eisa hack you mentioned, It's been recently added to metasploit framework so I'm sure every "kewldood" in town has it by now.

---

### Post by hpon on 2011-12-03
Thanks for the replies.  From what I understand from them, there is no way to guarantee the security through the use of software or hardware solutions.  So, if I want to keep some files completely separate from the Internet I must ensure there is never a physical connection between my desktop and the Internet.

How would I update Ubuntu if I never connect the computer to the Internet?  Can I download updates to a USB-stick or CD through another computer and install the updates from such media?

/hpon

---

### Post by haqking on 2011-12-03
> **hpon said:**
> Thanks for the replies.  From what I understand from them, there is no way to guarantee the security through the use of software or hardware solutions.  So, if I want to keep some files completely separate from the Internet I must ensure there is never a physical connection between my desktop and the Internet.

How would I update Ubuntu if I never connect the computer to the Internet?  Can I download updates to a USB-stick or CD through another computer and install the updates from such media?

/hpon

aptonCD or keyrx

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by hpon on 2011-12-05
> **haqking said:**
> aptonCD or keyrx

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
[http://keryxproject.org/](http://keryxproject.org/)

Very cool.  I'll try it out.  

Thanks for all the valuable information!

/hpon

---

### Post by collisionystm on 2011-12-05
I like my idea about a virtual machine on a micro sd card =) 

You can disable any and all internet communication to a virtual machine. Not to mention its a heck of alot easier than burning apt databases to a cd

---

### Post by Megaptera on 2011-12-05
hpon,
Not sure what your needs are but you may be interested in:

Ubuntu Privacy Remix "The goal of Ubuntu Privacy Remix is to provide an isolated working environment where sensitive data can be dealt with safely. The system installed on the computer running UPR remains untouched, UPR is not intended for permanent installation on hard disk" [https://www.privacy-cd.org/en](https://www.privacy-cd.org/en)

or quantOS which "is a hardened Linux distribution, based on Linux Mint 11, for secure daily use as a desktop operating system.
quantOS leverages AppArmor application security profiles, Arkose Desktop Application Sandboxing and Vidalia for creating secure Tor connections to enhance online privacy." [http://linux.softpedia.com/get/Syste...OS-70412.shtml](http://linux.softpedia.com/get/Syste...OS-70412.shtml)

---

### Post by |{urse on 2011-12-06
THANKS megaptera, both of those distros are awesome!!!

---

### Post by Megaptera on 2011-12-06
> **|{urse said:**
> THANKS megaptera, both of those distros are awesome!!!

You're welcome!

---

