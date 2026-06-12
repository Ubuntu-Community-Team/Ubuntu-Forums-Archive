---
title: "Can someone please help me with my actiontec DSL modem?"
date: 2006-06-21
forum: General Help
---

### Post by theduke11 on 2006-06-21
I know this is a boring topic but trust me ive searched these forums for at least a week now and still cant find an answer. The problem is that my internet is slow on dapper drake 6.06. Yes it works but on every new site i go to it takes a good minute beofre firefox starts loading the page. Ive tried turning that ivp6 option off but that didnt help either. I dont think i had a problem with version 5.10 so if all else fails and i cant get it working is version 5.10 ok to use?

Thank you very much. Oh and i tried editing that config file for your router that you find in the etc folder to change the DNS numbers because they are not the right ones but i couldnt do it because i didnt have root access and i tried for hours and figured out to log in to root but it still said i couldnt edit the damn file. Ive also had problems with random crashing in dapper drake. specs:

athlon xp 2500
512 mb ram
ati radeon 9600 pro
80 gig wd hd

Not look for answers why its crashing on me but i thought why not mention it.

---

### Post by Jasper Houtman on 2006-06-21
You prob couldn't edit the file because it was in use.
Did you try booting with just the command line? (safe mode).
and then editing it?
Use sudo nano /directory/file

---

### Post by theduke11 on 2006-06-21
no i didnt try going in safe mode. Did you just tell me how to do it? sorry i dont know any of this talk but thanks.

---

### Post by theduke11 on 2006-06-21
Jasper, to save everyone getting pissed off at me who are trying to help because i dont know what im doing what do you think my chances are of reinstalling dapper drake finding out how to do what you said and get it working right? is it possible that this release just does not support my DSL modem?

Thanks.

---

### Post by Pnut on 2006-06-21
theduke11 I use a actiontec dsl modem and i have no problems with  my speed of browsing web pages.  this is after a normal install.  Im running dapper on my laptop wirelessly and my desktop hardwired.  I have not experienced what you claim is being caused by your actiontec modem.  If you would like some more indepth help with your issue, feel free to contact me using the information listed below.

[email]pnut@nutzogames.com[/email]

---

### Post by eth on 2006-06-21
you may try editing your **/boot/grub/menu.lst**, adding after the kernel name, and right before the **quiet splash** token, the following 

> noapic nolapic

I found exactly the same problem on a HP, a full minute to load every single page, but still working and now it's full speed.

---

### Post by Pnut on 2006-06-21
oh yea...one more question.  are you connecting your actiontec dsl modem to some sort of router/firewall?  and if so, are they both acting as dhcp servers?  I have seen an instance in which a friend of mine who was new to ubuntu thanks to me :)  was double natting his lan.  typically you really cant notice this...but in his case he was experiencing serious degradation of his connection speed.  Let me know some more information about your network infrastructure and maybe we can solve this problem your having.  Dapper Drake is really a great operating system because everything just works.

[email]pnut@nutzogames.com[/email]

---

### Post by theduke11 on 2006-06-21
Pnut, mine is not wireless its a dsl/router combo. And really thanks for offering to help like that but trust me i wouldnt leave you alone haha. 

eth, im going to go try that now big thanks for that info.

to add. pnut going to go install it again and ill be back reading this again. And yes i for sure see getting this to work worth the hassle because minus the crashing ans the slow dsl i really like this OS.

---

### Post by eth on 2006-06-21
let me know if it helped

---

### Post by Fred Doolie on 2006-06-21
I have an actiontec and had the same problem. Here's what worked:

Enter "about:config" in the firefox address window. In the filter window enter "ipv". You will see something about " ipv6 disable". Change that to "true".

The enter "pipe" in the filter window. Change all of them to "true" and change the number to 999 or something.

That sped up my firefox a LOT!

---

