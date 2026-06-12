---
title: "set up a Finarea voip service (e.g. voipbuster, voipstunt, voipcheap) on a softphone?"
date: 2006-06-13
forum: General Help
---

### Post by hanzj on 2006-06-13
I used to use X-Lite Sotware phone (xtensoftphone) to make PC-to-phone calls.But now, my X-Lite doesn't work, so I'm looking to see what alternative softphones I can use. Do you have any suggestions?

I tried setting up  Ekiga with this Finarea VOIP. If anyone is using a Finarea VOIP service (e.g. VoipBuster, VoipCheap, VoipStunt, InternetCalls, etc) please tell me what to input into Ekiga's Edit-->Accounts window.


It asks for the following info:

Account Name
Registrar
User
Password

What do i put in the above 4?

I tried:
AccounName: Voipstunt.com
Registrar: sip.voipstunt.com
User: my username
password: the password

but it didn't work.  What exactly should I put in the registrar blank? and in username blank?
---------
In XLite program,
I had the following settings:
Username: my username
Authorization user: my username
Password: ****
Domain/Realm: sip.voipstunt.com
SIP Proxy: sip.voipstunt.com

-----------------

[COLOR="Red"]**Or, if you have successfuly set up a Finarera VOIP service on any other softphone, please let me know.**[/COLOR]

Thank you for your help.

---

### Post by kubuntux on 2006-06-13
I found a solution that worked for me at the following page ( reply #8 thanks to mulvila)
[http://www.ubuntuforums.org/showthread.php?t=162355](http://www.ubuntuforums.org/showthread.php?t=162355)

I set up ekiga as follows (for my voipbuster.com account):
Account Name: voipbuster [you can use whatever you want]
Registrar: sip1.voipbuster.com
User: myusername
Password: mypassword

When calling a phone number (landline or mobile) write: 
sip:111@sip1.voipbuster.com (in the place of "111" use the landline or mobile number you are colling to)

ByeZ! :)
- Paolo -

---

### Post by hanzj on 2006-06-13
Since I'm using voipstunt, I put the following into the blank in registrar:sip1.voipstunt.com. But I get "Registration Failed". Then I tried "sip.voipstunt.com". And this works. Thanks, kubuntux, for your post. It encouraged me to keep trying.

---

### Post by hanzj on 2006-06-13
So if I want to call north america, should I have sip:16323333456? or sip:001632333456?


EDIT: Found out the answer: it's 00 + country code + area code+ local number.

---

### Post by Noiano on 2007-02-16
> **hanzj said:**
> Since I'm using voipstunt, I put the following into the blank in registrar:sip1.voipstunt.com. But I get "Registration Failed". Then I tried "sip.voipstunt.com". And this works. Thanks, kubuntux, for your post. It encouraged me to keep trying.

Hi,
i am using twinkle and I can't make it work: always timeout error...can you tell me the parameters you use?

---

