---
title: "cant compose message in thunderbird??"
date: 2011-05-23
forum: General Help
---

### Post by nerdy_kid on 2011-05-23
For some reason thunderbird randomly decided to stop letting my dad reply to emails with attachments.  He can reply to normal emails, but as soon as he tries responding to an email with an attachment thunderbird just shows this:  [IMG]http://ubuntuone.com/p/vAy/[/IMG]

Note the cutoff toolbar -- that might be a seperate issue though.

It will then show the above for all emails he tries responding to until I restart thunderbird.

I have tried:

1.  Running Ubuntu classic with no effects.
2.  Moving ~/.thunderbird
3.  Changing the theme to clearlooks.
4.  Resizing/maximizing/moving the window.

I have not installed or removed anything, the last upgrade I did was a few days ago, a bunch of qt libs were upgraded, along with firefox and openoffice.

Can anyone please help?  My dad really likes thunderbird, and he needs to be able to reply to emails.  I suppose I can set him up with Evolution if I have to, but he probably won't like that.

---

### Post by nerdy_kid on 2011-05-24
bump...

---

### Post by linuxinstalledfromhdd on 2011-05-24
Did he just upgrade from 10.10 to 11.04? I'd roll it back and see if that helps for right now.

---

### Post by nerdy_kid on 2011-05-24
> **linuxinstalledfromhdd said:**
> Did he just upgrade from 10.10 to 11.04? I'd roll it back and see if that helps for right now.

No, clean install.  Everything has been working great for several weeks.  A totally random issue.

---

### Post by linuxinstalledfromhdd on 2011-05-24
Hmm...  You can try this:

In Terminal:

sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get upgrade

Did anything upgrade?

---

### Post by nerdy_kid on 2011-05-27
There are no thunderbird packages in that ppa, so I didn't add it.  I'm going to try reinstalling thunderbird.

---

