---
title: "need an ivr soulution"
date: 2006-06-02
forum: General Help
---

### Post by nephish on 2006-06-02
lo there,

we are running a server at work and now find the need to implement an IVR (interactive voice response) system to call our customers with a pre-recorded message when their machines change and let them dial in with their phones for an update.

i think i need something like bayonne or asterisk, but i am not sure about the hardware.

can anyone point me in the right direction for a good solution here, what card, what platform.
i would prefer to do this in ubuntu or debian.

anyone have much experience with this ?

thanks

---

### Post by garyng on 2006-06-02
Personally, I would go asterisk using a VOIP provider rather than digium card. But I believe your question would get better answer from the asterisk guys, they have forums for it.

Installing asterisk on ubuntu is pretty easy though. They only thing that is needed(in addition to asterisk) is the zaptel module which provides the timer thing that is very essential for telephony apps.

---

### Post by nephish on 2006-06-02
thanks for the tip, just registered the asterisk forums.

by voip provider, do you mean another piece of software, or another piece of equipment ?

sorry, i am just starting to research this out

---

### Post by garyng on 2006-06-02
What you want is to call PSTN(old phone line network) from asterisk. You can either :

1. use digium board and order old phone line trunks from the local telco(more expensive and harder to play with) Or

2. find a local company that do (1) for you and you interface them using pure IP(SIP or IAX2).

(2) is cheaper, easier to manage, scales better(usually handles more active lines with the same hardware).

There are lots of VOIP providers around the world, just find one that is local to you and with good experience and support. This is in particular true in north america(and why SKYPE can offer free dialout).

---

### Post by nephish on 2006-06-02
cool, thanks very much, 
think i'll take door number 2.

appreciate your time !

---

