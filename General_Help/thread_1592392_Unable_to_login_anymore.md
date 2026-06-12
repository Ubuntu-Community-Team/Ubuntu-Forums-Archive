---
title: "Unable to login anymore"
date: 2010-10-10
forum: General Help
---

### Post by paulm2822 on 2010-10-10
I recently powered up my netbook... Selected my user log in, entered my password, and after a couple seconds I briefly see what looks to be the console and am returned to the login splash screen... I can Ctrl+Alt+F2 to get to the console and log in... but that is as far as I can get.  This is the case for Gnome, Remix, and Remix 2D.

I can sudo apt-get (update, upgrade, etc) as well.

It is the right password because if I type in a wrong one it presents an authentication failure dialog box. 

How can I fix my log in screen and get to my desktop?

I am Currently running 10.04.... waiting to get 10.10

---

### Post by JackNocturne on 2010-10-10
I had a similar but not exactly the same problem. 

Everytime i logged in , it did just like what you described. I got it to work by booting to console then i reinstalled Gnome

```
#apt-get install ubuntu-desktop
```

---

