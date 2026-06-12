---
title: "Ekiga phone numbers"
date: 2009-11-19
forum: General Help
---

### Post by lewmur on 2009-11-19
I just installed Ekiga and want to get a local phone number.  The default provider, Diamondcard, doesn't have numbers in my areacode. Can anyone tell me how to find a provider for numbers in the 504 areacode?

---

### Post by chmac on 2009-12-01
I just started playing with [Localphone]("http://www.localphone.com/") and I'm loving them. Incoming numbers in the UK are 33c a month! I think they're $1 a month in the US. They seem to have a load of incoming number locations. I haven't quite gotten the settings right for Ekiga yet, but I think it's close... :-)

---

### Post by chmac on 2009-12-01
Ok, just got it working when I have a public IP (no NAT / firewall). Settings are as suggested by [localphone]("http://support.localphone.com/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=57"). Then to call phone numbers the sip address is sip:+12345678901@proxy.localphone.com. I was able to make a call.

Now I'm trying to figure out the NAT issues...

---

### Post by suyog on 2011-04-08
@chmac , good to know that you got localphone.com account working in Ekiga. If you can share settings that will be great !

I am not able to configure it , though I did it in linphone easily.

Following are settings I am trying :-
In Ekiga on Ubuntu 10.10 , Add SIP account

1) Name - Localphone (I assume this can be anything)
2) Registrar - localphone.com
3) User - sip:xxxxxxx@localphone.com ( xxxxxx is my sip username)
4) Authentication user - ????? (I just dont have any clue about it)
5) Password - my VOIP pwd
6) Timeout - 3600

Please let me know your settings since its working for you !

---

### Post by chmac on 2011-04-08
I believe it used to work, but now doesn't seem to. I fired it up recently when having issues with SIP on Android and couldn't get it to work. I installed Linphone in the end, which worked like a charm. Since then I've added a second monitor (might be unrelated) and now neither Linphone or Ekiga works. But my Android Nexus One does work, albeit incoming and outgoing through different apps, what a mess!

---

