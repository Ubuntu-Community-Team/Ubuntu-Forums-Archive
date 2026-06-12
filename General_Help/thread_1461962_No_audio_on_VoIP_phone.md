---
title: "No audio on VoIP phone"
date: 2010-04-24
forum: General Help
---

### Post by arashiko28 on 2010-04-24
It's a bit complicated, but I'll try to make it easy...

I have installed 2 VoIP programs, skype and xten softphone (X-Lite), skype works well and no problem but on the xten softphone not so lucky, I get to hear the tone before dialing like any phone but can't receive calls and if I call, there's no sound, other side can hear me, but I can't hear a thing.

I need both, skype it's my personal account and xten softphone is for work. I would really appreciate a solution rather than installing windows in double boot.

Any ideas?

---

### Post by arashiko28 on 2010-04-25
[size="7"][color="red"]***_bump!_***[/color][/size]

---

### Post by jkxx on 2010-04-25
Disclaimer: I run my own Asterisk PBX so I've had to deal with some VoIP-related woes. That said, I'm trying to figure out if X-lite is even using SIP.. aaand from looking at its manual it looks like it does.

In a nutshell, dealing with SIP-based VoIP you'll need to have a number of ports open and forwarded to the computer running the VoIP software or have a PBX running on your router (or computer with a WAN/public IP address) to have calls working properly. An alternative is to use a STUN server which some VoIP providers will give you.

So a couple of things to try might be

1) Look to see if your work-based VoIP provider has a STUN server listed anywhere. If they do add that to your X-lite and try running it again. Usually this will fix the problems (caused by NAT) and allow things to work and is the easiest. 

Edit: Similar to STUN you might be able to use uPnP, if your router supports it. If it does then you could try to look for that option in X-Lite - generally you just have to enable it and it doesn't require entering any IP addresses or other info.

2) If you can't do the above then you'll have to forward ports manually. Make sure your router gives you a static local IP on your lan. Then find out which ports you need to forward:

- SIP uses 5060 (and sometimes 5061) so these two are a given
- a separate protocol called RTP is used for audio; different
programs and devices use different port ranges. Find out which ports X-lite uses for RTP and forward those to your internal IP as well.

Too confusing? Just post exactly where you got stumped if you get stuck trying to get it work.

---

### Post by arashiko28 on 2010-04-25
> **jkxx said:**
> Disclaimer: I run my own Asterisk PBX so I've had to deal with some VoIP-related woes. That said, I'm trying to figure out if X-lite is even using SIP.. aaand from looking at its manual it looks like it does.

In a nutshell, dealing with SIP-based VoIP you'll need to have a number of ports open and forwarded to the computer running the VoIP software or have a PBX running on your router (or computer with a WAN/public IP address) to have calls working properly. An alternative is to use a STUN server which some VoIP providers will give you.

So a couple of things to try might be

1) Look to see if your work-based VoIP provider has a STUN server listed anywhere. If they do add that to your X-lite and try running it again. Usually this will fix the problems (caused by NAT) and allow things to work and is the easiest. 

Edit: Similar to STUN you might be able to use uPnP, if your router supports it. If it does then you could try to look for that option in X-Lite - generally you just have to enable it and it doesn't require entering any IP addresses or other info.

2) If you can't do the above then you'll have to forward ports manually. Make sure your router gives you a static local IP on your lan. Then find out which ports you need to forward:

- SIP uses 5060 (and sometimes 5061) so these two are a given
- a separate protocol called RTP is used for audio; different
programs and devices use different port ranges. Find out which ports X-lite uses for RTP and forward those to your internal IP as well.

Too confusing? Just post exactly where you got stumped if you get stuck trying to get it work.

:shock::shock::shock:Thanks for your answer... I am pretty sure any IT would understand that... but, I'm just a regular user.

I do know it uses SIP and my boss told me to use the port 5070, all the other I know it's english... but don't understand a word! :oops: what is a STUN server? ... Nevermind, I'll google it... but why the default configuration is different from the one in windows, we installed it in a windows computer and worked right away. 
(I want to convince my boss Linux is better :P and now, just for pride I want to make this thing work!)

---

### Post by arashiko28 on 2010-04-25
Ok, so I changed a couple of thing but now got even more lost... I changed the 5070 for 5060 and now get a message of nor being able to connect. :confused: I'll wait until tomorrow and compare between both configurations, how is that?

---

### Post by jkxx on 2010-04-26
That's probably a good idea. In fact, take screenshots of the windows configuration and save them for when you boot up later in Linux.

Basically, STUN is a hack of sorts to allow VoIP to work for people behind routers, such as most of us at home. Since your home router only reports 1 IP address to the Internet, the STUN is used to tell the software which computer inside your LAN to connect to.

In this I'd say the software working has nothing to do with Windows vs Linux on your PC other than that maybe the Windows version is getting the STUN part right at the moment.

[http://www.voip-info.org/wiki/view/STUN]("http://www.voip-info.org/wiki/view/STUN") A good explanation of STUN. That particular site has plenty of other info related to VoIP.

Good luck with replicating your config from windows!

---

