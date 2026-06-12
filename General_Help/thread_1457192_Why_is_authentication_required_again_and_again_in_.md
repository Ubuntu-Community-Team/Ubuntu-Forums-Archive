---
title: "Why is authentication required again and again in Ubuntu"
date: 2010-04-18
forum: General Help
---

### Post by nbulchandani on 2010-04-18
hello,
if the wifi network gets disconnected why is the wireless authentication key needed again and again...cant ubuntu store and retrieve it...its really frustrating..
Thanks

---

### Post by cogier on 2010-04-18
Is it the Wi-Fi key it is asking for or your password?

---

### Post by 3rdalbum on 2010-04-18
> **nbulchandani said:**
> hello,
if the wifi network gets disconnected why is the wireless authentication key needed again and again...cant ubuntu store and retrieve it...its really frustrating..
Thanks

Yes, it can, but only within a keyring. You can create a keyring, I believe, by going to Applications > Accessories > Passwords And Encryption Keys. Normally the first time you input your wifi key you'll be asked if you want to create a keyring; you probably hit Cancel at this step.

If what you describe is that you are constantly being asked for the wifi key over and over again without a successful connection, then what's happening is not that the key is being forgotten - it's rather that something is going wrong with the connection. More precisely, usually the wifi device is in an inconsistent state, or the driver is.

Try unplugging the device if it's connected through USB, and plugging it back in. If it's not USB, then try shutting down the computer the whole way, and turning it back on.

---

### Post by nbulchandani on 2010-04-18
yes ,i saw in applications->accesories ->passwords and keys....it has stored the wifi authtntication key....but the problem is if the wifi gets disconnected it keeps on asking the key....more frequently than that asked in windows frequently
Thanks

---

### Post by impact on 2010-04-18
This happens to me every now and then, too. As odd as it may sound, I am able to fix this by rebooting my router.

---

### Post by The Cog on 2010-04-18
It's another reason for replacing network manager with wicd. Having to give my password again immediately after logging in just to get the wireless working is anti-user. I don't have the patience for that kind of silliness.

---

### Post by qamelian on 2010-04-18
> **The Cog said:**
> It's another reason for replacing network manager with wicd. Having to give my password again immediately after logging in just to get the wireless working is anti-user. I don't have the patience for that kind of silliness.

Wicd is no panacea either though. It has never worked reliably any time I have tried it on my laptop, but network manager has always worked flawlessly.

---

### Post by Scunnered on 2010-04-18
It is possible for you to both login into Ubuntu and to have your wireless connection open automatically.  There are however insecurities by doing so.

If you go to the login screen you will see that you can be logged in automatically and there is an option to give time to others to pick their own login. Having done that go to the Wireless network connection on the panel right click and edit connections. Select wireless, highlight the entry and edit where you will see at the foot of the page available to all users.  Tick this and this will let you connect at login without the need of a password.

I use this at home but if I take my laptop from home then I disable the autologin and wireless connection for safety.  

Trust this assists you.

---

### Post by The Cog on 2010-04-19
I'll stick with wicd thanks. 
* It works even before anyone logs in, and even if X is broken, and even after the GUI logs out.
* It doesn't want another password again immediately after I log in.

Frankly, I think a system where networking doesn't work until someone logs in, and dies as soon as they log out (regardless of what else is running in the background) is laughable. I don't think even Windows is that stupid.

---

### Post by dcstar on 2010-04-19
> **The Cog said:**
> I'll stick with wicd thanks. 
* It works even before anyone logs in, and even if X is broken, and even after the GUI logs out.
* It doesn't want another password again immediately after I log in.

Frankly, I think a system where networking doesn't work until someone logs in, and dies as soon as they log out (regardless of what else is running in the background) is laughable. I don't think even Windows is that stupid.

That is not a "system", that is one component (Network Manager) that can easily be replaced by alternatives that do not have this issue.

This particular component works in one way, other components (as you have found out) work in another way, and Linux gives you the choice to use whichever of these that suit you - how many choices do you get in Windows?

---

### Post by mcduck on 2010-04-19
> **The Cog said:**
> 
* It works even before anyone logs in, and even if X is broken, and even after the GUI logs out.
So does the Network manager, if you just enable the "Available to all users" option in your network connection's settings.

> **The Cog said:**
> 
* It doesn't want another password again immediately after I log in.
Neither does Network manager if you either use a login password, or remove the keyring password.

The first solution is clearly visible if you just bother to look at the settings, and the second solution has been discussed over and over again in these forums and other web sites, so finding it shouldn't be a problem. It's pointless to rant about the program if you haven't even tried to look for the simple, existing solutions to the problems you are having with it.

---

### Post by nbulchandani on 2010-04-19
buT THE PROBLEM WITH ME IS THAT IF THE WIFI GETS DISCONNECTED IT KEEPS ON ASKING FOR THE KEY MORE THAN ASKED IN WINDOWS....OFCOURSE IT TAKES IT AUTOMATICALLY AT SYSTEM START..BUT IF THE WIFI GETS DISCONNECETD..THEN...
aRE YOU TELLING THAT WICD IS AN ALETRANTIVE TO THIS THING??
tHANKS

---

### Post by The Cog on 2010-04-19
> **mcduck said:**
> So does the Network manager, if you just enable the "Available to all users" option in your network connection's settings.

I don't remember seeing that. I wonder how long it's been there.  I've been installing wicd as part of my post-install procedure for a few years now. I'll try to make time for a test install this evening.
> 
Neither does Network manager if you either use a login password, or remove the keyring password.

On a couple of occasions, I've been stuck with the situation where NM insists on me telling it a password that I don't know. It's very persistent and won't take "I don't know what f*** password you're on about!" as an answer. You can neither change nor remove the keyring password (even once you have figured out that's what NM wants) if you don't know what the flaming password is in the first place. And in those circumstances, faced with being nagged for a password I don't know every time I want to use wireless or installing wicd instead, the choice is easy.

Like I say, I'll try and have another go with it to see if it's any better than my recollection of it being extremely user hostile.

---

### Post by mcduck on 2010-04-19
> **The Cog said:**
> I don't remember seeing that. I wonder how long it's been there.  I've been installing wicd as part of my post-install procedure for a few years now. I'll try to make time for a test install this evening.

On a couple of occasions, I've been stuck with the situation where NM insists on me telling it a password that I don't know. It's very persistent and won't take "I don't know what f*** password you're on about!" as an answer. You can neither change nor remove the keyring password (even once you have figured out that's what NM wants) if you don't know what the flaming password is in the first place. And in those circumstances, faced with being nagged for a password I don't know every time I want to use wireless or installing wicd instead, the choice is easy.

Like I say, I'll try and have another go with it to see if it's any better than my recollection of it being extremely user hostile.

The option  to enable a network connection for all user's has been in Network Manager as long as it has been available in Ubuntu (so it was there even before it started to be included by default).

What comes to keyring password, network manager never asks for that. The Keyring Manager will, if you use automatic login, when Network manager tries to access the keyring. Anyway, unless you have changed the keyring password yourself it's (depending on the Ubuntu version) either the same as the login password you set when you installed Ubuntu, or whatever you set it to be when the Keyring Manager asked you if you wanted to create a keyring. In either case, the answer was always available in these forums if you just did a search for "keyring password" or just asked.

---

### Post by The Cog on 2010-04-19
Well, there's a thing!

I just tried NM with the "Available to all users" option, and as you say, it makes the wireless work for all users, even when no user is logged on. That's the feature I always installed wicd for. And with the "Available to all users", you don't keep getting pestered for the keyring password. An auto-connect network that's not "all users" does make nm ask for the password.

I'll give nm a longer spin and see how I get on with it.

Thank you, mcduck. I have been educated.

---

### Post by nbulchandani on 2010-04-19
Well,i never did anything with my keyring passwords and all..
$ whenever i login the wifi gets connected automatically
$ now suppose if the wifi gets disconnected it aks me for the WIFI AUTHENTICATION KEY AND not the keyring passwd....I am saying why cant ubuntu remember this passwd...
Please guide me....M a noob YEt
Thanks

---

### Post by The Cog on 2010-04-19
That beats me (of course). But it seems that if you choose the available to all users option, it asks you your sudo password and then saves the setting as a system setting. Then it doesn't ask again. At least, that's how it's now behaving for me.

---

### Post by nbulchandani on 2010-04-20
hmm...lemme try it for a while....lets c

---

