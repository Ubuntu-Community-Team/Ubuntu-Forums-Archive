---
title: "How do I get to lightdm screen with autologin"
date: 2011-11-04
forum: General Help
---

### Post by gandaran on 2011-11-04
How do I get to lightdm screen with autologin enabled before booting unity or is there any way  with autologin that can also display the lightdm screen, I wouldn't mind the extras seconds needed to boot.

---

### Post by haqking on 2011-11-04
> **gandaran said:**
> How do I get to lightdm screen with autologin enabled before booting unity or is there any way  with autologin that can also display the lightdm screen, I wouldn't mind the extras seconds needed to boot.

LDM is what displays the login screen.

So you want a login screen with autologin enabled ?

---

### Post by gandaran on 2011-11-04
> **haqking said:**
> LDM is what displays the login screen.

So you want a login screen with autologin enabled ?
right, just wondering if it's possible or is there any key to press  
to show LDM before booting unity.

---

### Post by haqking on 2011-11-04
> **gandaran said:**
> right, just wondering if it's possible or is there any key to press  
to show LDM before booting unity.

I am confused, sorry.

You want to show the login screen with autologin enabled ?

that is an oxymoron isnt it ;-)

---

### Post by gandaran on 2011-11-04
> **haqking said:**
> I am confused, sorry.

You want to show the login screen with autologin enabled ?

that is an oxymoron isnt it ;-)
why not? lets say the screen was displayed for about 5 seconds then if no action taken it would login automatically, I think this would be useful now with all the choices to login not just unity and still autologin working.

---

### Post by Vaphell on 2011-11-04
check /etc/lightdm/lightdm.conf
internet says that you can find appropriate settings
- autologin-user
- autologin-user-timeout

---

### Post by haqking on 2011-11-04
> **Vaphell said:**
> check /etc/lightdm/lightdm.conf
internet says that you can find appropriate settings
- autologin-user
- autologin-user-timeout

oh i get what he is after now.

Yeah perhaps looking at the TimedLoginDelay value may do what you are after.

---

