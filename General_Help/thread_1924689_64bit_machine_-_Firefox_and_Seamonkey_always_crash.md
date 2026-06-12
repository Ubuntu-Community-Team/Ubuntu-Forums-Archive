---
title: "64bit machine - Firefox and Seamonkey always crashing"
date: 2012-02-13
forum: General Help
---

### Post by missmoondog on 2012-02-13
is it possible to use a 64bit machine and a mozilla based browser without it CONSTANTLY crashing?

2 machines i've had now in the last week WILL NOT work with either firefox or seamonkey, after installing seamonkey. obviously firefox is already installed, but IMMEDIATELY after installing seamonkey, they BOTH do nothing but crash!

gmail crashes every single time and yahoo mail crashes 99.9% of the time, and those are just 2 examples. it crashes so frequently, both browsers are virtually useless, which makes this entire OS useless, on a 64bit machine useless also, IMO.

not seeing anyone having similar issues, for some reason, but 2 out of 2 64bit machines have bitten the dust as far as using xubuntu on them.

edit:
fwiw, i now see a TON of complaints about firefox, [https://crash-stats.mozilla.com/products/Firefox](https://crash-stats.mozilla.com/products/Firefox) [https://crash-stats.mozilla.com/report/index/bp-53d79a8a-c753-4fce-9847-7132f2120207](https://crash-stats.mozilla.com/report/index/bp-53d79a8a-c753-4fce-9847-7132f2120207) and the last update crashing everybody's stuff!!

---

### Post by missmoondog on 2012-02-14
wow! not a single reply? cripe! i've even gotten some replies in a couple other forums that are not even remotely ubuntu/linux related.

this is most definitely a 64bit, firefox 10 and above issue though. any 32bit machine works perfectly.

---

### Post by kc1di on 2012-02-14
Not noticing any problem here on my 64 bit machine with FF and yahoo or Gmail. 

All seems to be working Haven't tried seamonkey in a long time though.
Sorry see your using xubuntu - I think the problem may be in that edition only as I've seen some
post in other xfce forums about ff 10 also.  I was using Ubuntu when I tested it

---

### Post by muteXe on 2012-02-14
Seems to be working for me, on one desktop and one laptop.
(10.04 lts).
p.s. i should also mention i pretty much keep gmail open in ff 100% of the time when i'm on my ubuntu partition.

---

### Post by philinux on 2012-02-14
> **missmoondog said:**
> wow! not a single reply? cripe! i've even gotten some replies in a couple other forums that are not even remotely ubuntu/linux related.

this is most definitely a 64bit, firefox 10 and above issue though. any 32bit machine works perfectly.

I've got three 64 bit installs. Two are 11.10 ,a netbook and a desktop and the other is 12.04 testing desktop. I've not experienced anything like you describe.

It could be an addon to firefox that's causing the trouble. Try running it in safe mode from a terminal and look for any errors reported.

```
firefox -safe-mode
```

---

### Post by Gremlinzzz on 2012-02-14
but IMMEDIATELY after installing seamonkey, they BOTH do nothing but crash!
maybe you should remove the monkey are you using the latest version

We strongly recommend that all SeaMonkey users upgrade to this latest release. 

[http://www.seamonkey-project.org/news](http://www.seamonkey-project.org/news)
:popcorn:

---

### Post by missmoondog on 2012-02-15
latest version of seamonkey in the repository is 2.7, which i have. i can uninstall both ff and sm and use one or the other (ff still crashes sometimes though) but i'm hard headed and want BOTH to work like they should!

i haven't come across any posts or reports of issue with xubuntu and xfce, but glad to know some one has. quite a few posts about ff crashing in the crash reports [https://crash-stats.mozilla.com/products/Firefox](https://crash-stats.mozilla.com/products/Firefox)

thanks folks  :)

---

### Post by missmoondog on 2012-02-18
now have newest (supposedly) stable versions of ff and sm and STILL crashing like there's no tomorrow!!

crashes in safe mode also.

not a total loss anyway as at least chromium and opera work perfectly still, although i didn't use chromium until this started happening and don't particularly like it either.

---

### Post by missmoondog on 2012-02-20
> **kc1di said:**
> Not noticing any problem here on my 64 bit machine with FF and yahoo or Gmail. 

All seems to be working Haven't tried seamonkey in a long time though.
Sorry see your using xubuntu - I think the problem may be in that edition only as I've seen some
post in other xfce forums about ff 10 also.  I was using Ubuntu when I tested it

well, i just sent about 4+ hours trying to install mythbuntu, using wubi, on a 64bit machine and i see why it's called that. upon restart, it couldn't find it's own dang iso that it had just downloaded! told me to run a chkdsk /r, which i did although i knew it was going to be a waste of time. restarted in windows and let it FULLY load. restarted again to finish mythbuntu installation and got same error. went back to windows and removed that garbage. 

next i installed ubuntu, using wubi. it installed just fine, but wow, is that ubiquity (?) thing a total disaster!! that is one total POS desktop!!

although it has to be the worlds dumbest desktop, i went ahead and played with it for a bit. took a little while how to figure out getting seamonkey 2.7.2 installed, but immediately after doing so, seamonkey and firefox both crashed instantly when going to gmail!!

that's enough of this thing on any 64bit machine i get a hold of again and DEFINITELY the last time i use ubuntu with that crappy desktop! who's dipstick idea was that?!! :idea:

so, obviously it's not a xfce thing either, but some really crappy software writing by someone!

might try 12.04 when it comes out on a 64bit machine, but until then ii sure am glad windows 7 is as great as it is!!  :)

---

### Post by philinux on 2012-02-20
Wubi is just meant to try out ubuntu. Definitely not for long term use. I would investigate a proper dual boot.

---

### Post by missmoondog on 2012-03-03
oops! i now see why mythbuntu screwed up. should've done more research on that one!

my very first attempt on a 64bit machine WAS a proper dual boot setup! no difference there and part of why i'm experimenting with wubi on 64bit now.

what the heck are you talking about wubi is just meant for trying out ubuntu? i have almost never used anything but and never had a problem like i am now!! in fact, using wubi, i even had a totally awesome experience upgrading from 11.04 to 11.10 and that has NEVER happened for anyone, as far as i know, by reading posts on here.

my issue is TOTALLY a mozilla/flash/64bit issue as i have absolutely no issues of any kind on 32bit machines, and that's even using beta versions of firefox!

i had a 64bit laptop here a couple days ago that i tried a very basic install of xubuntu on. nothing more than the basic updates. no issues until installed flash, then poof, instantaneous crashes up the wazoo, especially loading gmail!!

fwiw and as far as i'm concerned, this issue is closed. am deleting this topic from my subscriptions and simply NOT installing any version of ubuntu on 64bit machines again, or at least until 12.04 comes out!

thanks to all who replied  :)

---

