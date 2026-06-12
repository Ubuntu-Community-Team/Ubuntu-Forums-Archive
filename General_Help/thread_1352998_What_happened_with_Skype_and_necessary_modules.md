---
title: "What happened with Skype and necessary modules?"
date: 2009-12-12
forum: General Help
---

### Post by 6205 on 2009-12-12
On fresh Ubuntu Karmic install, with Medibuntu enabled, is not anymore possible to install Skype (in the past available from Medibuntu) Second problem is, that essential for Skype to work (or my microphone to work) is needed backport module alsa, which is also not anymore available for current kernel. Synaptic error >>>

[COLOR="DarkRed"]linux-backports-modules-alsa-karmic-generic:
 Depends on: linux-backports-modules-alsa-2.6.31-17-generic  but it is not installable[/COLOR]

My question is what the hell is going on? I need to use Skype. I can always download *.deb file from skype website, but what about that kernel module?

---

### Post by Leppie on 2009-12-12
I installed Skype from the medibuntu repo and didn't need to install extra alsa modules.

---

### Post by handaxe on 2009-12-12
There is of course [http://www.skype.com/intl/en/download/skype/linux/choose/]("http://www.skype.com/intl/en/download/skype/linux/choose/")

Not as convenient as synaptic/apt but another avenue nonetheless.

HA

PS  MY bad, I now see the OP mentioned the Skype website.... (sigh!)

---

### Post by handaxe on 2009-12-12
Got curious, 'cos for me skype also is not present in Medibuntu... But there is something odd.

It is not there looking at: [http://packages.medibuntu.org/karmic/index.html]("http://packages.medibuntu.org/karmic/index.html")

However, it is there looking at:
[http://packages.medibuntu.org/karmic/]("http://packages.medibuntu.org/karmic/")

So Medibuntu has some or other issue.

And I can confirm the OPs issue with the alsa backport modules- not installable.  Needs a bug report against backports. Not a problem for me as I do not need those modules.  Something about the OPs hardware?

HA

---

### Post by Leppie on 2009-12-12
Not sure what's going on, but skype (2.1.0.47-medibuntu) appears in my synaptic and installed normally without the use of backports.

---

### Post by handaxe on 2009-12-12
Clarity:

[https://bugs.launchpad.net/medibuntu/+bug/494564]("https://bugs.launchpad.net/medibuntu/+bug/494564") and [https://launchpad.net/medibuntu/+announcement/4539]("https://launchpad.net/medibuntu/+announcement/4539")

Skype is officially gone from Medibuntu.  Use the Skype site *.deb

HA

---

### Post by 6205 on 2009-12-12
Without that alsa module it's useless..

---

### Post by handaxe on 2009-12-12
@6205

I believe you probably have proposed updates (Karmic-proposed) enabled in synaptic / sources.list. Disable that and you should be able to install that needed alsa module.  Works for me.

HA

---

### Post by 6205 on 2009-12-12
That is working, but only if i install also older version of kernel 2.6.31-16 what is not acceptable for me..

---

### Post by handaxe on 2009-12-12
Assuming you have a solid technical reason for using the proposed kernel (ie. it solves some or other hardware issue that the current kernel does not, because 2.6.31.17 is not officially released to Karmic yet (and comes from the karmic-proposed repo too)) you are stuck.  

Take way the karmic-proposed repo and then the current kernel (2.6.31.16.29) and your the current alsa module are in harmony, which is what Canonical would argue counts...

HA

---

### Post by 6205 on 2009-12-12
mmm

---

### Post by Linuxforall on 2009-12-13
Skype from the site doesn't work with my microdia cam, all I get is green stripes whereas it works fine in Cheese and Skype from Medibuntu.

---

### Post by kostkon on 2009-12-13
> **6205 said:**
> That is working, but only if i install also older version of kernel 2.6.31-16 what is not acceptable for me..
Yeap, the current kernel is 2.6.31-16. Please, don't complain, it was your choice to enable the Proposed repo, which is only for testing reasons by people who really want to test packages before they come out.

If you want a fine tuned system, you will need to disable that repo.

---

