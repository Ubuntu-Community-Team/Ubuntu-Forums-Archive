---
title: "No sound in Realplayer 10"
date: 2006-04-29
forum: General Help
---

### Post by karigna on 2006-04-29
I just installed RealPlayer 10 Gold in Dapper but am not getting sound. I tried files from a couple of different sites with no luck. The video portion looks great though.

Kevin

---

### Post by jamesrw on 2006-06-05
"Re: No sound from realplayer

You can install the "alsa-oss" package, and then run "aoss realplayer" rather than "realplayer" - that will make realplayer use alsa's OSS emulation, which should work regardless of how many programs are using the soundcard. To make this work when launching it from a menu you'll need to edit the menu item."

---

### Post by lixy on 2006-07-08
Thanks Jamesrw! Just made my day :D

---

### Post by vulpes on 2006-07-14
On Dapper, I edited the startup script (/usr/lib/realplay-10.0.7/realplay) and changed line 73 from

$REALPLAYBIN "$@"

to

aoss $REALPLAYBIN "$@"

and that worked great.

---

### Post by fk4n on 2006-09-02
thank you. this is sooooo helpful!!!!=D>

---

### Post by yorkshiremies on 2006-10-17
I got things happily working by doing both, so installing the "also-oss" package using:

System --> Administration --> Synaptic Package Manager
Search: "alsa-oss" then click the package "Mark for installation"


..and then go and edit (you will need su rights to edit this) the startup script (/usr/lib/realplay-10.0.8/realplay) and changed line 73 from

$REALPLAYBIN "$@"

to

aoss $REALPLAYBIN "$@"

//Craig

---

### Post by domer on 2007-01-11
I am new to the Linux world. So may be my question will be very silly. 

How do I edit the  /usr/lib/realplay-10.0.8/realplay file. I changed line 73 as mentioned, but it does not allow me to save the change. I do have su rights (as it is my desktop) but I dont know how to use that right to edit the startup script. 

Can someone help me out? 

Thanks :)

---

### Post by domer on 2007-01-11
I figured out how to edit the realplay file

at terminal I typed:

**sudo gedit /usr/lib/realplay-10.0.8/realplay**

This opened the realplay file in gedit and changed line 73 as discussed above. Real Player works. 

Thanks for posting the above solution !!

---

### Post by falela on 2007-01-16
I am having similar problem with realplay10Gold.  It plays video nicely.  but for sound, I need to quit and restart <realplay> several times before it can play any sound.   And I can't sees any pattern in it, all random.  Sometime, I get sound the 1st time, sometime get it after many restart. 
My config is:

Kubuntu 6.10 amd64
using Asus M2N-E onboard sound

anyone have similar issue?

---

### Post by ntlam on 2007-12-24
> **vulpes said:**
> On Dapper, I edited the startup script (/usr/lib/realplay-10.0.7/realplay) and changed line 73 from

$REALPLAYBIN "$@"

to

aoss $REALPLAYBIN "$@"

and that worked great.

Thank you,

that works great

---

### Post by dondad on 2007-12-24
> **domer said:**
> I figured out how to edit the realplay file

at terminal I typed:

**sudo gedit /usr/lib/realplay-10.0.8/realplay**

This opened the realplay file in gedit and changed line 73 as discussed above. Real Player works. 

Thanks for posting the above solution !!

Be careful. When using gedit, you need to use gksudo rather than sudo. (That is true with any graphical application). Sometimes if you use sudo with a graphical app, it messes with the permissions of your home directory and you will have problems booting. (as in .drmc has the wrong permissions... error at bootup.) DAMHIKT ;-)

---

### Post by divali on 2007-12-31
Thanks. That worked for me using Gutsy.

---

