---
title: "Eee PC Driver Issue"
date: 2009-09-21
forum: General Help
---

### Post by Soapy.Illusions on 2009-09-21
Ive been using my Eee PC with a full install of Ubuntu (not UNR) and well internet drops after about 30 mins of usage and I can only get it to work again with a full restart. 

So I tried using the proprietary drivers (the madwifi ones) and well then I could not connect to the internet at all, gnome-network-manager doesn't even see that I have wireless

Anything that i'm missing??

---

### Post by snowpine on 2009-09-21
Impossible to answer without knowing which model of eee pc you have. :)

I have had good luck on my eee 900ha using the custom kernel from array.org:

[http://array.org/ubuntu/](http://array.org/ubuntu/)

However, since the 9.04 release, my hardware is well supported by "regular" Ubuntu, and I find the custom kernel is no longer necessary.

---

### Post by Soapy.Illusions on 2009-09-21
I also have the 900 HA, and am using 9.04 (sorry for the lack of info) I didnt think the array kernel was necessary because of 9.04

Do you know what may be causing these drops and are you using the open source drivers or the madwifi ones??

---

### Post by Soapy.Illusions on 2009-09-21
Sorry to bumb, but these drops make my Eee quite unusable, any suggestions??

---

### Post by snowpine on 2009-09-21
> **Soapy.Illusions said:**
> I also have the 900 HA, and am using 9.04 (sorry for the lack of info) I didnt think the array kernel was necessary because of 9.04

Do you know what may be causing these drops and are you using the open source drivers or the madwifi ones??

Totally vanilla, out-of-the-box ath5k module. No extra steps necessary, no drops (for me).

Currently running Windows XP though (long story)...

---

### Post by Soapy.Illusions on 2009-09-21
Ya I have the ath5k ones but maybe because I am at University and we are using WPA Enterprise

But the madwifi ones don't work and the ath5k ones work, but drop... am I out of luck?

---

