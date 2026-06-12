---
title: "Loading/Initiating actual windows(super machine!)"
date: 2009-10-05
forum: General Help
---

### Post by TechMansoor on 2009-10-05
I have core 2 quad 3.06 processor, 8 gigs of ram with pae installed on the latest buntu. What could be making firefox and basic windows,dialog boxes, etc. take 4-5 seconds on average to start up?

Thanks for the help in advanced guys!! :)

---

### Post by XCan on 2009-10-05
I don't know about what you refer to with dialog boxes, etc, but firefox taking some time to start up most likely have to do with your hdd performance.

---

### Post by TechMansoor on 2009-10-05
crap!! you may be onto something..my 1.5tb drive is 5400 rpms.. :( :(. I didnt think it would be a noticeable difference like that.. crap!!!!

dialog boxes, I'm talking boxes that need or require my input such as gksudo, terminal prompts etc...these are forms of dialog boxes....

but I wonder if thats the culprit...are there any tests I can run to solidify this notion? Maybe ubuntu doesn't like my 5400 1.5rpm seagate....

---

### Post by XCan on 2009-10-05
I'm not too familiar with benchmarking on linux, but I know that there's the Phoronix test suite [http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/) , that includes tons of test, including hdd performance. However, it feels peculiar that your terminal prompts and such light stuff are taking so long time to load.

---

### Post by TechMansoor on 2009-10-05
Indeed. Thanks a billion Xcan! I will check out your reference. If anyone can give any insight that would be awesome. I actually just took that drive back to office depot and traded it in for a 7200 segate. I'm installing pae at the moment. I wonder if it is the culprit. 

Once pae is installed, it will regonize all 8 gigs of memory. But how don't see how in the world adding 8 gigs of memory would slow my workstation down at all? That's like reverse computing logic indeed.

Thanks for the help thus far everyone...

---

### Post by XCan on 2009-10-06
I think PAE can induce a performance hit depending on your drivers, sometimes it won't work at all. But I have to ask, why don't you simply use the 64-bit version of Ubuntu? :)

---

### Post by TechMansoor on 2009-10-06
> **XCan said:**
> I think PAE can induce a performance hit depending on your drivers, sometimes it won't work at all. But I have to ask, why don't you simply use the 64-bit version of Ubuntu? :)

Because I'm an idiot plainly put!  But nah, I'm trying to learn the intracicies of linux and ubuntu indeed. I saw a few errors in relation to architecture and I got scared. Plus this isn't a play around workstation, its my workstation at the office.  I'm even having, on this 32 bit version, problems troubleshooting my sound card. It takes a lot just for ubuntu to make it work as this reference dictates:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I really need to learn all the cli and things surronding each command and such..

So I'm working on it..and I think your original statement was right, it was the hdd. Ive installed pae, updated ubuntu, and firefox is zooming. I guess the 7200rpm vs 5400 played a difference indeed...

are you online often xcan? do you do any type of IM?

---

