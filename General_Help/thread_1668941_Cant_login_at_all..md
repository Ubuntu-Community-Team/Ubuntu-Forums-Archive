---
title: "Cant login at all."
date: 2011-01-17
forum: General Help
---

### Post by Shadowgamon on 2011-01-17
After logging out a few minutes ago, I decided to go back in to send an email. unfortunately whenever I enter the password(correctly) it shows the *console* that appears before logging in, and it brings me back to the account selection (all accounts) 
Something I noticed before losing access was that startup applications was missing from the Gnome menu. Maybe that has something to do with it?
Please help! 



*posting from windows vista partion*

---

### Post by Shadowgamon on 2011-01-17
bump

---

### Post by CryptSphinx on 2011-01-17
have you tried logging in via a virtual terminal to see if there's any errors?

do:

At the login screen try ctrl-alt-f6 , this should bring you to tty6 
then login using your user name and password

if it gives an error of some variety that would be a start

then just exit

it would then be ctrl-alt-f7 to get back to your normal login screen


also - you haven't recently installed kde/gnome or any other window manager or anything like that?

---

### Post by Shadowgamon on 2011-01-17
I installed xfce a while back but there were no problems. I'll try and find errors in the tty now. I cant believe I didn't think of that :o



RE: Ok I logged in easily enough from the TTY, but I still cant get in :X

---

### Post by CryptSphinx on 2011-01-17
I would assume you all ready have ,but it is worth asking

have you both gnome and xfce installed at the moment or just xfce - if you have both have you tried logging in with either.

and obviously does either show any error message or just nada when you try log in.

I had a similar problem a while ago while trying out xfce when I still used gnome - the problem didn't occur immediately if I remember correctly.

---

### Post by Shadowgamon on 2011-01-17
> **CryptSphinx said:**
> I would assume you all ready have ,but it is worth asking

have you both gnome and xfce installed at the moment or just xfce - if you have both have you tried logging in with either.

and obviously does either show any error message or just nada when you try log in.

I had a similar problem a while ago while trying out xfce when I still used gnome - the problem didn't occur immediately if I remember correctly.

I removed xfce in excess of a week ago so I don't believe is the problem.

I was messing around the the PPAs though if I recall correctly ppa:erik-b-andersen/rgba-gtk this one specifically. Maybe I deleted something important along side it.


RE :I've come to the conclusion that gnome itself was compromised somehow. Can anybody give me a commandline guide to reinstallation of gnome?

---

