---
title: "Keyring password"
date: 2009-11-16
forum: General Help
---

### Post by Rikii on 2009-11-16
Hi, I installed Gnome-do and now I have a problem with a pop up box saying the application 'Do' (/usr/bin/mono) wants access to the default keyring, but it is locked.  As a newbie to Ubuntu this week, I'm asking for a little help from you to guide me to removing this annoying thing that is appearing on startup. Thank you for your help in advance.

---

### Post by P4man on 2009-11-17
You probably enabled autologin. If you do that, then the keyring (which stores passwords for things like wifi, email, etc) is locked for secutiry reasons, and gnome-do or any other app can not access it. Either disable the autologin or if you dont give a hoot about your security and identity set a blank password on your keyring at your own risk. Do realize that means anyone with physical access to your machine can read your unencrypted passwords on your drive.

---

### Post by Rikii on 2009-11-18
Thanks for your help. I will set a password.

---

### Post by Pjotr123 on 2009-11-18
A keyring password is in most cases an exaggeration; only people with physical access to your computer can see your keyring passwords, when all three following conditions are present:

- someone is already active in your user account (you let him use your computer, or he has used a LiveCD for access to the hard drive), AND

- he knows where to look for the stored wireless keys, AND

- he has bad intentions.

Now, how likely is that (all three conditions at the same time) to happen?

When you have already set a password for the keyring and you want to get rid of it (for example when you use automatic login), you can do it as follows:
[http://sites.google.com/site/easylinuxtipsproject/tips](http://sites.google.com/site/easylinuxtipsproject/tips)
(number 15)

---

### Post by Soul-Sing on 2009-11-18
Pjotr I don't think security is about how likely conditions are to be secure or insecure. Security isn't ambiguous, security is about secure or insecure, yes or no.

---

### Post by Pjotr123 on 2009-11-18
> **leoquant said:**
> Pjotr I don't think security is about how likely conditions are to be secure or insecure. Security isn't ambiguous, security is about secure or insecure, yes or no.

I disagree with you here... :)

It's all to do with *acceptable* risks, in my opinion. Otherwise no one should ever connect to the internet, for instance. Because there is absolutely no way of being 100 % secure when you're connected to the net.... And driving a car would be impossible too, for the same reason. That's not how we would want to live.....

As it says on the front of an old house, I think somewhere in Voorburg: De waerelt is vol gevaer. ;)

So, one has to weigh practical usability on the one hand, and security on the other hand. You'll want to choose some sort of an optimal balance there.

---

### Post by dobelden on 2010-05-27
i this keyring an annonniying thing :(

---

