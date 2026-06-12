---
title: "Require Password at Login"
date: 2011-03-24
forum: General Help
---

### Post by fliphkd23 on 2011-03-24
A few months ago I decided that I was sick of typing in my password at login, and since I'm the only user of the computer I decided to set it to auto-login.  Unfortunately I did not realise that the I would need to type in my password to unlock the keyring after login anyways.

Now instead of typing in my password once at login I have to type it in multiple times after login to unlock everything that accesses the keyring.  This was certainly not helping my situation so I set my preferences back to normal login, but now it doesn't require a password at login and I still have to unlock the keyring multiple times after login.

After poking around on my computer for a while and some extensive use of google, I still cannot find a way to set it back to requiring the password at login.  If anyone could help me get it back to just typing in my password once right away instead of multiple times later it would be much appreciated!!!

---

### Post by Another Monkey on 2011-03-24
That's the Gnome keyring thing.

"System"/"Administration"/"Login Screen".
Then select "Show the screen for choosing who will log in".
Should sort it.

I ran into the same issue when trying to use VNC from a remote machine (I needed to use Wake-On-LAN then login etc).  Got it sorted by having VNC come up at boot rather than the auto-login (as VNC wouldn't even work until someone local had typed the password in multiple times).
Worked great until the capacitors on the motherboard blew!

---

### Post by fliphkd23 on 2011-03-24
That's the weird thing, I already have that selected.  When I get to the login screen I have to select my user name, but it doesn't require a password until after I login and have to unlock the keyring like four times for all the separate things that require access.  

So virtually I have to select the user, can login without a password, but can't do anything after that until I unlock the keyring multiple times!

---

### Post by Another Monkey on 2011-03-24
Right.  That is truly hat-stand.

Have you tried changing your password, in case that causes something to reset?

Sorry, I really wish I could help more.

---

### Post by Krytarik on 2011-03-24
- go to "System -> Administration -> Users and Groups"
- select your user
- right of "Password" click at "Change"
- untick "Don't ask for password on login"

Greetings.

---

### Post by fliphkd23 on 2011-03-24
Absolutely fantastic.  Thank you. I wonder why that option isn't contained in the login screen preferences though...

---

### Post by Krytarik on 2011-03-24
> **fliphkd23 said:**
> Absolutely fantastic.  Thank you. I wonder why that option isn't contained in the login screen preferences though...
Because it's user specific.

You're welcome!

---

### Post by fliphkd23 on 2011-03-24
Of course, that was foolish of me.  Being the sole operator of this computer for so long has almost made me forget about the need for an OS to support multiple users.

---

