---
title: "Ekiga with different SIP provider?"
date: 2006-06-07
forum: General Help
---

### Post by sol77 on 2006-06-07
Hi there. I'm trying to get Ekiga 2.0.1 to work with my SIP provider MySecretary.
After having filled in all the information I can recieve calls were the caller can't hear me but I can hear them. Also when I dial out I get a "security check failed" error. 
I am not behind a router and I have successfully made calls from other software under windowsXP. 

Does anyone know how I can get it to work?

---

### Post by damu on 2006-06-07
I am using Ekiga everyday to give my phonecalls, using sipdiscount as a sip provider.

Here are my settings :

in Edit/Accounts, I have created a sipdiscount account, with the following:
Accountname :sip.discount
registrar : sip1.sipdiscount.com
username : 'login given by sipdiscount'
password : 'password given by sipdiscount'

in Edit/preferences :
    -Protocols/Network settings :
           - stun : stun.ekiga.net  (you might use another stun. I have notice that I had erratic results when using the sipdiscount one)
    -Devices/Audio devices :
            -make sure that you have selected the proper device for the input and output device. Pay a special attention on the input device, as it doesn't seem that you can be heard...

May the force be with you....once working, on a daily basis, Ekiga is just a pure joy to work with...very reliable

---

### Post by sol77 on 2006-06-08
Thanks for the help. 
I tried all those things and it still won't work. 
I can make calls with x-lite without any problems so I'm pretty sure it is something I have missed with Ekiga. 
Do I need to use OSS for Ekiga to work? Right now I'm using Alsa and I have my soundcard selected.
And do I need to sign up for a free sip account in order to call out with my own sip provider?

---

### Post by mko on 2006-06-11
> put the REGISTRAR field in your account IN NUMERCAL FORM!
read this: [http://www.mail-archive.com/gnomemeeting-list@gnome.org/msg03682.html]("http://www.mail-archive.com/gnomemeeting-list@gnome.org/msg03682.html")

---

