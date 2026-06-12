---
title: "Default Keyring is gone!? And now I can't connect to wifi."
date: 2011-06-22
forum: General Help
---

### Post by Cr125f150ba on 2011-06-22
I am not a newbie to Ubuntu but I'm definitely  not an expert. Anyways I had ubuntu on a Dell Inspiron B130 for about two years with no problem. When I started my laptop it would log me in and then ask me for a password to unlock the default key ring. If i did not type the password in i couldn't connect to my wireless network. Now the problem occured yesterday and it is that every time ubuntu starts up now it won't ask me for the password now. And I can't connect to my wireless. The wireless icon is in the upper right of the screen but when i click on it there are no networks. Im almost positive it has something to do with my default key ring problem. I tried to look for the hidden file that people delete so they don't have to type a password in but my default key ring file is gone. Please help

---

### Post by haqking on 2011-06-22
> **Cr125f150ba said:**
> I am not a newbie to Ubuntu but I'm definitely  not an expert. Anyways I had ubuntu on a Dell Inspiron B130 for about two years with no problem. When I started my laptop it would log me in and then ask me for a password to unlock the default key ring. If i did not type the password in i couldn't connect to my wireless network. Now the problem occured yesterday and it is that every time ubuntu starts up now it won't ask me for the password now. And I can't connect to my wireless. The wireless icon is in the upper right of the screen but when i click on it there are no networks. Im almost positive it has something to do with my default key ring problem. I tried to look for the hidden file that people delete so they don't have to type a password in but my default key ring file is gone. Please help

system>preferences>passwords and encryption keys.

you should see your keyring here where you can edit it, unless of course you dont have one at all.

i suspect there was a recent password change ?

---

### Post by gizmo720 on 2011-06-22
This sounds like a hardware (or kernel) problem. What is the output of ifconfig and iwconfig.

---

### Post by haqking on 2011-06-22
sometimes if the keyring does not pop up on login you can force it to appear by trying to edit  your connections, i know you cant see any but if you choose edit connections or connect to hidden network etc it sometimes invokes the keyring.

this is a shot in the dark though ;-)

---

### Post by Cr125f150ba on 2011-06-22
Thankyou all for your quick response. I couldn't respond cause I was downloading the newest version of ubuntu. Anyways after I installed the new version and then tried pushing the on off button for the wireless card (located on the keyboard) and now it works. For some reason that on off button for the wireless card didn't work with the old ubunut version I was running (don't know how it got turned off in the first place). But now it works. My wireless card was turned off for some reason, and because of that, ubuntu didn't ask for my password to unlock the default key ring. All is good now. Thank you for your info everyone!

---

