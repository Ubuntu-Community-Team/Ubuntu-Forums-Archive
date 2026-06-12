---
title: "ekiga / voipstunt.com"
date: 2006-04-10
forum: General Help
---

### Post by Marc Higgins on 2006-04-10
ekiga / voipstunt.com

Has anyone been able to get ekiga working with voipstunt? if so, can you please telling me what I am doing wrong?

Account Name; voipstunt
Registrar; stunt.voipstunt.com
User; myusername
Password; mtpassword

more options

Authentication Login; myusername (it added this auto)
Realm/Domain; voipstunt.com
Registration Timeout; 3600

really use the free call to landlines. at the moment I need to keep a windows box up & running just so i can use this service.

If anyone knows of another service similar service that i can get running on dapper or breezy that will allow me to call a whole bunch of landlines FOC & mobiles cheaply I would be very interested

---

### Post by damu on 2006-04-10
I use sipdiscount which is the same company than VoipStunt. Actually, I started to use Voipbuster which is also another name for the same company. I used it on WinXp and when I switched to linux I started to use it with Ekiga...works great! and can't be cheaper really, as all my phonecalls to landline are free!

Your settings look allright. Did you check under preferences/Network settings, what stun you use? 

I personaly use > stun.ekiga.net . I had some issues with this stun settings at the beginning...

---

### Post by Marc Higgins on 2006-04-10
1st I tried 

stun.ekiga.net

& then

stun.voxgratia.org

& then

stun.fwdnet.net

---

### Post by damu on 2006-04-11
and it still doesn't work?...bugger!

In my Ekiga here are the settings :

Account Name; sipdiscount.com
Registrar; sip1.sipdiscount.com
User; myusername
Password; mypassword

Authentication Login; myusername (it added this auto)
Realm/Domain; sip1.sipdiscount.com
Registration Timeout; 3600

May the force be with u!

---

### Post by kwyjibo on 2006-04-16
did you (or anyone else) manage to get their voipstunt working under linux?  It's the only reason why i still have XP on this machine

---

### Post by SirKillalot on 2006-04-16
try
Registrar voipstunt.com

---

### Post by patrickfromspain on 2006-04-16
[http://www.ubuntuforums.org/showthread.php?t=161282&highlight=ekiga](http://www.ubuntuforums.org/showthread.php?t=161282&highlight=ekiga)

Although I did it with voipbuster, should be pretty much the same.

Hope it helps

---

### Post by malachakla on 2006-08-28
Works just fine for me.
My settings:
Registrar: sip.voipstunt.com
Username: (voipstunt username)
Password: (voipstunt password)
Realm/Domain: voipstunt.com
Timeout: 3600

---

