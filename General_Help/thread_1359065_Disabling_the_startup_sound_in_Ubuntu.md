---
title: "Disabling the startup sound in Ubuntu"
date: 2009-12-19
forum: General Help
---

### Post by freestyleren on 2009-12-19
I'm trying to disable that little annoying drum sound when you boot ubuntu. I've tried disabling it in startup apps, I've tried removing it from startup apps, and I've even deleted the sound file itself but it won't go away.

---

### Post by keplerspeed on 2009-12-19
You can go to system>preferences>sound and change "sound theme" to "no sounds".

---

### Post by audiomick on 2009-12-19
I think that is included it system sounds in system> administrations or system> options. I am not too sure exactly where, as I have all my system sounds off and have had for ages. Anyway, I don't think it is a startup option, but rather a system option related to the GUI. It comes when the GUI starts on a computer that I look after for a friend of mine.

---

### Post by freestyleren on 2009-12-19
> **keplerspeed said:**
> You can go to system>preferences>sound and change "sound theme" to "no sounds".

That doesn't change anything.

---

### Post by audiomick on 2009-12-19
Pity. :(
But it is there somewhere. Mine doesn't do it. I will have a look when I get home, but that will be a few hours yet.

---

### Post by philinux on 2009-12-19
These sounds are stored and picked up by the system from here.

/usr/share/sounds/ubuntu/stereo

Rename the offending file as xxxxxxx.sav to stop it being picked up. Just tried it and this works.

---

### Post by pbrane on 2009-12-19
If you want to disable it completely do what philinux says. If you want to change that to something else you can simply change what the symolic link points to.

I changed mine like this.

[B]1. cd /usr/share/sounds/ubuntu/stereo
2. sudo -s
3. rm system-ready.ogg
4. ln -s service-login.ogg system-ready.ogg[/B]

You can use any sound you want in place of service-login.ogg.

---

### Post by joes7 on 2009-12-19
Download StarUp Manager

---

### Post by vaiocomputer on 2009-12-19
Just go to 'System > Preferences > Startup Applications' and if you scroll down the list, you can uncheck "GNOME Login Sound" to disable it.

It'll still be there later just in case you want to recheck it again.

---

### Post by carolinason on 2010-10-07
i downloaded startup manager and it is cool. it lets me choose my default os on my dual boot. however, it does nothing to manage those annoying drums or sound for that matter, thanks for the misinformation. it is utilitarian. 

also the login sound (the most annoying sound created by man) is different from the startup sound so startup applications does nothing to fix this problem.

wth is the login sound doing in startup applications? i can actually even see the startup sound being in startup applications, but the login sound?  what einstein, thinks that the login sound (and the startup sound) doesn't belong in the SOUND control panel. i thought conanicoinaoncinaoncal's big contrib is supposedly putting it's efforts into the user experience.

well one thing is for sure, ubuntu's config is as annoying as a mac all right. *ubuntu also has many good points, but that's not fun right now.*

just do it the debian way... which is what pbrane posted.

---

### Post by Calcipher on 2011-01-14
I know that this thread is likely long since abandoned, but, as it shows up as the first Google result for searches on how to disable the Ubuntu startup sounds, I thought I would post the correct instructions.  For reference, these instructions apply to Ubuntu 10.04 and 10.10; if you have a different version, some steps might be different.

There are actually two sounds which people might be referring to when they say 'startup' sound, the sound you get when Ubuntu boots to the login screen (sounds like a short drum roll to me) and the sound you get when you login.  

To disable the former (startup sound):
[LIST=1]
[*] Go to **System -> Administration -> Login Screen**
[*] Click the **Unlock** button and enter your password if prompted
[*] Un-check the **Play login sound** box 
[*] Hit **Close** to save your settings
[/LIST]
(Note: I have seen people say that the box is already unchecked but that they are getting the sound anyways.  If this is the case, try checking the box, hitting close, and starting the process over again.  

To disable the latter (login sound)
[LIST=1]
[*] Go to **System -> Preferences -> Startup Applications**
[*] Find **GNOME Login Sound** and un-check its box
[*] Hit **Close** to save your settings
[/LIST]

I hope that this helps someone out there.

---

