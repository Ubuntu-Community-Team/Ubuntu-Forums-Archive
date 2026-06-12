---
title: "ubuntu 10.04 is without sip telephony in practice"
date: 2010-05-09
forum: General Help
---

### Post by ff1-ff1 on 2010-05-09
Looks like all steam of dev team was used to move buttons to the wrong place :) because main aim of distribution (one from many) was to improve social side of system .In result of their efforts sip telephony is impossible  in U 10.04 ( it is impossible to connect on voipcheap.com account using empathy which is horrible to configure, and ekiga -which is easy to configure but has serious problems to dial and connect).
For example in ubuntu 9.04 ekiga worked flawlessly . So question is &#8211; why in long term distribution they included software which simply dont work?
(in ekiga case even version with patch from :  [https://launchpad.net/~sevmek/+archive/ppa](https://launchpad.net/~sevmek/+archive/ppa) doesnt help. After restart of system again connection is impossible!!!)

---

### Post by murderslastcrow on 2010-05-09
Hm. That is definitely a serious bug that should be reproduced and reported, since I wouldn't accept it, either. It's too bad this one slipped through the cracks. Of course, we should make sure it's not just a server time-out or something of that nature.

However, you seem to have done some pretty extensive research, so far. You should definitely report this as a bug in Ekiga, and Empathy for that matter if this is supposed to be a supported feature. Perhaps there's a thread that describes a workaround for this issue.

Again, it's really too bad they missed this one- but it may be fixed, soon. Maybe you should give Debian a try if this is a crucial element to your desktop experience. Again, sorry for your trouble!

---

### Post by ff1-ff1 on 2010-05-10
after deeper investigation i was able to move the whole problem a bit ahead. Two mentioned earlier programs are fired now.I founded another one: linphone. After configuration it behaved as (again) useless software.But next day i started it and asked me about password to my voipcheap.com account (earlier it didn t -and even in interface there is no place where you could put password).But anyway after restart of system it asked me about passwword (showed me which account i want to use to call).And worked flawlessly. Don t expect functionality offered by software of voipcheap for windows: there is no phone book, history of calls is strange and it needs to used to but generally works.

---

### Post by Ms_Angel_D on 2010-05-11
This seems more like a support thread, so I moved it to general support from Testimonials & Experiences.

---

### Post by green69 on 2010-06-08
> **ff1-ff1 said:**
> Looks like all steam of dev team was used to move buttons to the wrong place :) because main aim of distribution (one from many) was to improve social side of system .In result of their efforts sip telephony is impossible  in U 10.04 ( it is impossible to connect on voipcheap.com account using empathy which is horrible to configure, and ekiga -which is easy to configure but has serious problems to dial and connect).
For example in ubuntu 9.04 ekiga worked flawlessly . So question is – why in long term distribution they included software which simply dont work?
(in ekiga case even version with patch from :  [https://launchpad.net/~sevmek/+archive/ppa](https://launchpad.net/~sevmek/+archive/ppa) doesnt help. After restart of system again connection is impossible!!!)

After some days of very extensive search I have to completely agree with you. In 10.04 no SIP seems to be possible. My previous OS was ubuntu 8.1 and with that I could use ekiga with my account in 12voip.com without problems. Now in 10.04 I can't connect with ekiga and nor with emapthy. I even tried Twinkle and QuteCom from the ubuntu softwre center but it seems that neither with those I can connect to my 12voip account. Really I don't know how to do. I feel like if I've lost my way to phone cheap.

Anyone has a suggestion?

---

### Post by YaPaY on 2010-06-11
Could somebody tell me how can I use my internetcalls.com account on Linphone?

thanks...

---

### Post by dzsobacsi on 2010-06-30
Any experience of Voipcheap software with wine?
I have tried it yesterday but wasn't able to connect.

---

### Post by Docaltmed on 2010-06-30
I'm using [Nomado]("http://www.nomado.eu") for my sip service, it works just fine with Qutecom and Ekiga on 10.04. Also freecall.com worked alright, too. 

I'm using an HP TX2500 for hardware, so YMMV.

---

### Post by dzsobacsi on 2010-07-14
I have managed to install X-lite under Ubuntu 10.04.
It is not the most user friendly software I have ever seen but it works pretty well with my VoipCheap account.
That's how I did it:

1./ Download Xlite from here:
[http://www.counterpath.com/x-lite-3.0-for-linux-download.html](http://www.counterpath.com/x-lite-3.0-for-linux-download.html)

2./ Download and install libstdc++5:
[http://packages.ubuntu.com/jaunty/i386/libstdc++5/download](http://packages.ubuntu.com/jaunty/i386/libstdc++5/download)

3./ Unpack Xlite

4./ Execute ./xtensoftphone

5./ To config use this guide
[http://www.voipcheap.com/en/sipp.html](http://www.voipcheap.com/en/sipp.html)

---

