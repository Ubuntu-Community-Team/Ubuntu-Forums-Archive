---
title: "Invalid password for Active Directory user"
date: 2011-12-14
forum: General Help
---

### Post by lmorel12 on 2011-12-14
I am running 11.10 x64 on my HP. I installed Centrify to join my Active Directory at the office. Everything was fine once I got the right syntax, etc. I rebooted, logged in as my AD user and no issues. If I leave my PC unattended for a while (can't tell you how long exactly - it does NOT go to standby or sleep, just screen saver)) and I try to unlock it, I get an invalid password message. Yes, I checked that I entered the right password several times. I ended up rebooting the system. Thinking it was a fluke. Later, same issue. Next day, same issue as well. Is my 11.10 "losing" its connection back to my DC (for lack of better terms)? If I try switching to a local user, everything is fine.

---

### Post by lmorel12 on 2011-12-14
Guys,
 
Just wanted to add that I decided to unplug the ethernet cable, which made the password window disappears on the screen, waited 20 seconds, and plugged it back in. The password window reappeared and I entered my password and it took it! So it seems that when the system is idle for a long enough period of time, the connection to my DCs is "broken" and the password authentication process is immediately affected. Is that like an expiration issue? I am SO sorry for my lack of appropriate jargon. I am a Windoz user and big time noob in linux. Thank you for understanding.

---

### Post by polki@mac.com on 2011-12-15
I use likewise-open (and likewise-open-gui, because I'm lazy) and I haven't run into that problem (yet?). Try it and see if that works better.

---

### Post by lmorel12 on 2011-12-16
Thanks!
 
Interestingly enough things have been ok, meaning I am not running into that issue again. I have the feeling I have some lingering issues with my AD and never really ran into problems when dealing with Windows based systems. I guess even if this doesn't work out, it surely didn't hurt to know about it, right? :)

---

### Post by sumana.annam on 2011-12-16
Its great you no longer see this issue. But in future if it reappears and need help with troubleshooting from Centrify support, please post the question into our forums as well.

[http://community.centrify.com/](http://community.centrify.com/)

Good luck
Sumana

---

### Post by lmorel12 on 2011-12-16
Thanks!

I spoke too fast. But there is now an interesting twist to this. I think there is a "broken" link between my DCs and my 11.10 system. Today I managed to get Evolution working when connecting to my mailbox residing on an Exchange 2010 server. Within 20 minutes my account was locked out because my DCs believed my password was submitted wrong more than 5 times (I set the AD policy that way). The only other PC logged in with my name is a Windows 7 system and that's how I noticed that my account was locked out.

Now, I'm thinking that IF I would have insisted to enter my password more than 5 times with my initial situation, that probably would have resulted with the same issue (locking out my password). So I'm guessing here: when I try to unlock my account on 11.10 with he right password, it hit one of the DCs with a wrong password/encrypted translation of that password. (man, that would be nice that someday I speak the jargon......).

Sumana, I will go to the Centrify site and start posting the same stuff as soon as I get a chance. Just wanted to update everyone. I think I am going to give Likewise a try though.

Here a quick question to all Linux gurus though: are Centrify or Likewise tools that only help to join active directory but are not necessarily needed after that to handle any security handshakes between the client and the DCs? I guess I'm wondering if the authentication mechanism alone is at fault. I can see that my 11.10 joined the AD, I didn't get any error messages so I'm thinking the operation of my 11.10 within the AD is what is problematic. Not the implementation process.

---

