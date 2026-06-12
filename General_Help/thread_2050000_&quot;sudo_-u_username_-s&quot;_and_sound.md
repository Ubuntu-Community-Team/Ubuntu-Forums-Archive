---
title: "&quot;sudo -u username -s&quot; and sound"
date: 2012-08-29
forum: General Help
---

### Post by JasonFWard on 2012-08-29
I use XBMC as my main TV viewing platform.

However XBMC addons store passwords in plain text, including for Youtube, your Google password!

So I want to run XBMC as it's own user with its own permissions etc so that no one other than a super user and XBMC can see it's files and the passwords.

I can do this quite easily

```

xhost +local:
sudo -u xbmcuser xbmc
xhost -local:

```works perfectly all but for sound.

I've done some testing, and sound is just not available to the "sudo" session, anything running inside a sudo session thinks there are no sound cards.

So how do I get sound working inside a sudo session?

---

### Post by JasonFWard on 2012-08-30
Anyone?

Any ideas?

---

