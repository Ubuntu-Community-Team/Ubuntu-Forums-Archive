---
title: "notify-send isn't working in ubuntu 11.04 anymore!?"
date: 2011-05-08
forum: General Help
---

### Post by hakermania on 2011-05-08
Ok, I know that this is quite weird and I don't know why this is happening, but both me and my friend have the same problem:
notify-send isn't working.
I don't know if this is a cause of an update or something like this, but when i run
```
notify-send "Hello World"
``` the command exits normally but there's no notification...
The same problem to a friend of mine.....


Any suggestion?

---

### Post by pcapeluto on 2011-05-08
Hello hackermania, you have to install the libnotify-bin

sudo apt-get install libnotify-bin

Saludos...

---

### Post by hakermania on 2011-05-09
Hello, I've already installed this!
Im not a newbie one, if I were I'd have posted at the Newbie Section.
Thx

---

### Post by hakermania on 2011-05-10
bump....

I don't know....I am curious to see if other people have the same problem...
It hasn't to do whether there's an upgrade or a clean install, because my friend has a clean install and I an upgrade....
And it doesn't work :(

---

### Post by lotharmat on 2011-05-10
Clean install here and works like a charm!

---

### Post by kevinsu22 on 2011-05-15
Not working for me either.

On 11.04
Thinkpad T420
libnotify-bin installed

Got the OS a week ago or so, fairly clean. Mainly used for RoR.

Edit: Using 64bit natty

---

### Post by kevinsu22 on 2011-05-15
Tried installing notification-daemon from synaptic

Still doesn't work

---

### Post by infected?! on 2011-05-22
Are you using caffeine? I experienced the same issue while caffeine is running. It doesnt matter if the screensaver is enabled or not... After shutting down caffeine it's work like a charm.

---

### Post by Jean le Rond d'Alembert on 2011-05-22
> **infected?! said:**
> Are you using caffeine? I experienced the same issue while caffeine is running. It doesnt matter if the screensaver is enabled or not... After shutting down caffeine it's work like a charm.

Thanks for that, I shut it down and notifications started working again.
It would have taken me forever to make the connection. :/
It doesn't affect just notify-send though, seems to affect libnotify in general.
It was blocking Pidgin notifications for me.

---

### Post by Graipher on 2011-05-28
I had the exact same problem, tried a lot of stuff, but I, too, would never have made that connection...We should report this as a bug to caffeine.
But first, I'm gonna enjoy my slick notifications again :D

---

### Post by Graipher on 2011-05-28
Ok, the bug was already submitted. it seems to be a problem of the design of libnotify-bin, however there is a patch available for caffeine, which works for me
Here's the link:
[https://bugs.launchpad.net/caffeine/+bug/593649](https://bugs.launchpad.net/caffeine/+bug/593649)

---

