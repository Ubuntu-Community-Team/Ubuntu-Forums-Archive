---
title: "Ubuntu 10.10 really slow with google chrome and Firefox"
date: 2010-10-23
forum: General Help
---

### Post by linuxguy86 on 2010-10-23
I downloaded ubuntu 10.10 and both google chrome and firefox ran so slow. I run with Linux Mint 10 RC and Ubuntu 10.04 LTS both with those OS google Chrome and Firefox runs fast. Has anybody found anything to as why 10.10 runs so slow

---

### Post by haradeep on 2010-10-23
I want to know your root partition filesystem format.

In btrfs partition filesystem, I found problem with Google Chrome and Firefox while opening new tabs.

Change Partition to ext4.

---

### Post by Jebtrix on 2010-10-23
Sounds like your having the SQLite blues. 

One way to compare/verify on the different linux installs and filesystems:

```
sudo apt-get install phoronix-test-suite
phoronix-test-suite benchmark sqlite
```

Here is phoronix user uploaded test results for SQLite:
[http://global.phoronix-test-suite.com/index.php?k=category&u=sqlite](http://global.phoronix-test-suite.com/index.php?k=category&u=sqlite)

Here is mine in particular if your curious. (I've had SQLite performance problems in the past with my different machines, not so much with this rig)
[http://global.phoronix-test-suite.com/index.php?k=profile&u=anon-11522-30109-15479](http://global.phoronix-test-suite.com/index.php?k=profile&u=anon-11522-30109-15479)

---

### Post by piggyslasher on 2010-10-26
If your Firefox's download/network speed is slow, you might want to search around for IPv6 fixes.

However, mine (and a few others on this forum) was an all round slowness, and I upgraded the kernal as mentioned [here]("http://fb.me/we7tFztT"). Now the Meerkat is flying.

---

### Post by Scott Deagan on 2010-11-08
I too am having performance issues with Ubuntu 10.10 64-bit. The system is general is sluggish and laggy. Things like scrolling up and down a web page in Firefox is "jittery", moving a window around the desktop is laggy (i.e. you click on the titlebar, start dragging the window, the window will move about a second later), and typing text in a terminal window feels like you're SSH'ed into a remote server on the other side of the planet where the comms are slow.

I love Ubuntu, it's my OS of choice. Unfortunately this release is borderline unusable. I am running a Sony VAIO VPCF11S1E/B, Intel core-i7, 6GB DDR3 RAM, and an nVidia GT330M. I should point out that due to the nVidia 260.xx incompatibility with my hardware, I had to install the 256.53 driver. Initially I thought that this was the problem. While I can only assume that this is partly to blame, I found others reporting sluggish performance in 10.10 and blaming it on the kernel.

I tried to update my kernel from 2.6.35-22 to 2.6.37, but unfortunately I could not find an nVidia driver that would install after the kernel upgrade (complained about different version of GCC compiler used to build the nVidia driver).

I am hoping this issue is resolved soon as at present I can't exactly "show off" the latest build to colleagues (it's too embarrassing, something best kept in the dark for the time being).

---

### Post by Roasted on 2010-11-09
I'm in the same boat as above. Chrome is slower, but usable. Firefox is so slow it's non-functional. Problem is, Chrome is quite incompatible with a lot of very necessary things, so it's hard to use Chrome for day to day things. Example - can't log into wp-admin with Chrome. Why? I don't know! Firefox works though, yet Firefox = so painful to use...

And I'm not talking about those Chrome fanboys who are anti Firefox saying it's slow when it's 2ms behind Chrome. I'm talking about flat out non-usable. It's THAT slow it makes 56k look wicked fast...

Any fixes?

---

### Post by Nburnes on 2010-11-11
> **Roasted said:**
> I'm in the same boat as above. Chrome is slower, but usable. Firefox is so slow it's non-functional. Problem is, Chrome is quite incompatible with a lot of very necessary things, so it's hard to use Chrome for day to day things. Example - can't log into wp-admin with Chrome. Why? I don't know! Firefox works though, yet Firefox = so painful to use...

And I'm not talking about those Chrome fanboys who are anti Firefox saying it's slow when it's 2ms behind Chrome. I'm talking about flat out non-usable. It's THAT slow it makes 56k look wicked fast...

Any fixes?

I am having the same exact problem with Ubuntu 10.10 64bit :(

---

### Post by JaredNJames on 2010-12-05
Bump.  Me too. It's horrendously slow.

Also, on 10.04 I was getting 20mb/s to my USB stick, now I'm lucky to get 7.

At the moment, Windows 7 is running a lot better.

---

### Post by Spyderkid on 2010-12-05
If it's an old computer then that might be the problem not having enough ram or a REALLY old processor

also if you disconnect a lot then its a problem with your wireless not the accutaly device but something processing the device, if its a new device and the computers old the computer struggles to keep up ESPECCIALLY WITH USB'S

I switched to a different computer a bit newer and used the same usb and it worked it might be the computer thats the problem.



HOWEVER I DON'T HAVE A SOLUTION SORRY :D

---

### Post by Didjit on 2010-12-05
It has to do w/DNS lookup. I had the same issue and resolved. For the life of me I can't find the post I used and recall exactly what I did, duh... Anyway there are a few options out there people tried and worked, go down the path of changing the way your system resolves DNS I bet that is the issue.

Sorry I couldn't give you exact instructions :-(

---

