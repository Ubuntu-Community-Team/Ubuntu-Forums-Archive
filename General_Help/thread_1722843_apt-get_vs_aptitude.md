---
title: "apt-get vs aptitude?"
date: 2011-04-06
forum: General Help
---

### Post by gunit888 on 2011-04-06
I've been doing a lot of reading about installations lately, and more and more frequently I run across "sudo aptitude install <package>" rather than "sudo apt-get install <package>", which previously had been standard.  I've tried both and find no practical difference, the package gets installed correctly and it seems to work right in terms of dependency tracking.  

Can someone help me understand the difference?  Why should I use one over the other?  I've read a few people's opinions that using aptitude is the better way to go, but those opinions were unsubstantiated.

If I happen to have used both different ways for installing different packages, will it lead to any issues or problems later on?

---

### Post by KegHead on 2011-04-06
Hi!

I've only used aptitude for:

sudo aptitude install linux-image -f.

Aptitude doesn't seem to work in 11.04.

KegHead

---

### Post by steevven1 on 2011-04-06
I'd also appreciate an answer to this one.

---

### Post by matt_symes on 2011-04-06
Hi

IIRC, Aptitude will uninstall all of a packages dependences if no other package is using that dependency. 

With apt-get you have to use *sudo apt-get autoremove* to achieve the same thing.

I belive this is correct. Others will pipe up if i am mistaken.

Kind regards

---

### Post by Frogs Hair on 2011-04-06
Aptitude is supposed to do a better job of removing package dependecies , but I think Matt  is correct as far auto remove is concerned , I can't find any infomation that suggests otherwise. Aptitude is no longer installed by default in newer vrsions of Ubuntu and can be installed from the synaptic package manager in 10.10 . but I don't know about Natty beta.

---

### Post by Morpholinux on 2011-12-29
the best and probably the most updated stuff to read that I found >>>

"apt-get or aptitude?

First I want to make it clear that you can use both and mix them without problems. It used to be annoying when apt-get did not track which packages were automatically installed while aptitude did, but now that both packages share this list, there’s no reason to avoid switching back and forth.

I would recommend apt-get for the big upgrades (i.e. dist-upgrade from one stable to the next) because it will always find quickly a relatively good solution while aptitude can find several convoluted solutions (or none) and it’s difficult to decide which one should be used.

On the opposite for regular upgrades in unstable (or testing), I would recommend “aptitude safe-upgrade“. It does a better job than apt-get at keeping on hold packages which are temporarily broken due to some not yet finished changes while still installing new packages when required. With aptitude it’s also possible to tweak dynamically the suggested operations while apt-get doesn’t allow this. And aptitude’s command line is probably more consistent: with apt-get you have to switch between apt-get and apt-cache depending on the operation that you want to do, aptitude on the other hand does everything by itself.

*Take some time to read their respective documentation and to try them*."

I copy & paste from last paragraphs in [http://raphaelhertzog.com/2011/06/20/apt-get-aptitude-%E2%80%A6-pick-the-right-debian-package-manager-for-you/]("http://raphaelhertzog.com/2011/06/20/apt-get-aptitude-%E2%80%A6-pick-the-right-debian-package-manager-for-you/")

---

