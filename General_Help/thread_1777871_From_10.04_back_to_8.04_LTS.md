---
title: "From 10.04 back to 8.04 LTS ?"
date: 2011-06-08
forum: General Help
---

### Post by You bunt to? on 2011-06-08
Everything was working fine in 8.04 LTS Ubuntu, but I decided to upgrade to 10.04. Now, I can't send mail in Evolution (it just sits
there in the Outbox), and secondly, there is no sound in Firefox when playing e.g. YouTube videos.

I have the CD for 8.04 LTS. Is it possible to go back to 8.04 and retain my data?

Secondly, I live in Scarborough, Toronto, Canada and would gladly pay for a Linux/Ubuntu expert to instruct me in Linux. I can be reached at 416 438 0338.

My system is a PC, dual boot into Windows XP or Ubuntu.

---

### Post by Chrissd on 2011-06-08
Hi,

Personally, I'd be looking at trying to fix the two problems you have rather than going backwards. Easiest way to completely undo the upgrade is to restore a backup.

The following is my experience, not so much advice, since I'm no expert.

I'd check to see if you have Firefox4 installed as well. If not, [here is a FireFox4 Megathread](http://ubuntuforums.org/showthread.php?t=1712247), follow the instructions in that and see if that fixes the problem.

[This is my thread](http://ubuntuforums.org/showthread.php?t=957586) when I had a similar problem. The answer was resolved with this:
```

sudo apt-get install libflashsupport

```then restart firefox browser

Afraid I use web mail, so I can't help with regards to why your mail isn't disappearing. I'd certainly be looking at double checking the SMTP settings with your mail provider.

---

### Post by seawolf167 on 2011-06-08
I would definitely try to resolve the issues rather than downgrading.

For flash and other restricted formats:

```
sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh
```For Evolution, ensure that all your smtp settings, username, password, encryptions, ports, etc. are set up properly first.

---

### Post by mörgæs on 2011-06-08
Before paying people for solving the problem: 

Do you get sound in a live boot of 10.10?

---

### Post by Frogs Hair on 2011-06-08
Resolving your problems may be best thing to do rather than reinstalling an unsupported release.

---

### Post by mastablasta on 2011-06-08
you can get Cannonical support.
 
you can also seek faster support on irc channel for free.

---

### Post by seawolf167 on 2011-06-08
> **Frogs Hair said:**
> Resolving your problems may be best thing to do rather than reinstalling an unsupported release.

3 year support for LTS versions, 5 for the server LTS. [See here]("https://wiki.ubuntu.com/LTS")

---

