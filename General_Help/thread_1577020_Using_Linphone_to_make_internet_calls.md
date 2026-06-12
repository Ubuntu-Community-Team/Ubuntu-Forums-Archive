---
title: "Using Linphone to make internet calls"
date: 2010-09-18
forum: General Help
---

### Post by DeMus on 2010-09-18
Hi,
We still use a Windows PC, with problems (what else is new?) Now I also want to install Ubuntu on that computer, making us use only Linux.
There is one program we use in Windows which does not have a Linux variant and that is the program we use to make internet phonecalls with. We use Voipbuster because of the low prices.
I read on the Voipbuster.com website that Linphone can be used to do the same on Ubuntu. I installed it but after starting it form the menu I get nothing.
I started it from the terminal and got this:
```
linphone-3

(linphone-3:7053): libglade-WARNING **: Radio button group video_item could not be found
ALSA lib conf.c:4600:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:902:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib conf.c:4600:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default:0
ALSA lib conf.c:4600:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default:0
*** stack smashing detected ***: linphone-3 terminated
Segmentation fault
```
Can somebody please explain in simple terms what is wrong and what I have to do to make it work? I have no idea what these codes mean.
Thanks in advance.

---

### Post by saad khalid on 2011-01-26
i need help to configure my linphone to get all the other clients ip address from SIP server it is connected?
Can it be done?
aur i would need to write my own code.
thanks for help in advance

---

### Post by gordintoronto on 2011-01-26
I'm sorry, I don't know what to do about those error messages. It might help if you mentioned what version of Ubuntu you use, and what audio device is in the computer.

Have you looked at Skype? I think it is a competitor of voipbuster.

---

### Post by DeMus on 2011-02-04
> **gordintoronto said:**
> I'm sorry, I don't know what to do about those error messages. It might help if you mentioned what version of Ubuntu you use, and what audio device is in the computer.

Have you looked at Skype? I think it is a competitor of voipbuster.

It is, but the reason I use voipbuster is it is much cheaper. Using Skype to make calls to actual phones is way too expensive. I live in Holland and we can make calls to 25 countries for absolutely nothing. As long as we want. Try that with Skype. No way. It'll cost you a small fortune.

---

### Post by Zill on 2011-02-04
> **DeMus said:**
> ...Can somebody please explain in simple terms what is wrong and what I have to do to make it work? I have no idea what these codes mean...
Unfortunately it looks like you have found [Bug #573722]("https://bugs.launchpad.net/ubuntu/+source/linphone/+bug/573722") in Linphone :-(

Hopefully, the bug will eventually be fixed but in the meantime you may like to try a different SIP client.  I understand from their website that Voipbuster.com does use normal SIP protocols so you should have a good choice.

[SIP Communicator]("http://www.sip-communicator.org") is a Java VoIP client that is progressing steadily, although it is still officially an "alpha" release as it has nightly updates.  Just download and install the Ubuntu deb of the latest release from the website, along with the signing key.

You should then be able to configure SIP Communicator with the Voipbuster [configuration info]("http://www.voipbuster.com/en/sipp.html") for for your account.

---

