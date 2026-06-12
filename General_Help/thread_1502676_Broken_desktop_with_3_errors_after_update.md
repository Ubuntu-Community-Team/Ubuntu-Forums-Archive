---
title: "Broken desktop with 3 errors after update"
date: 2010-06-05
forum: General Help
---

### Post by napi on 2010-06-05
Hey all,

I'm running UNR 10.04 on a Samsung NC10.

Every thing has been working great for the last few weeks since I downloaded and installed - almost everything worked great out of the box! Only 'problem' I was having was pants flash performance but that's a bit of a given I guess.

However, this afternoon I did an update + upgrade, then did the required restart.

Booted fine to login screen, but it then took a looong time for any thing to happen - before any panels/UNR interface appear, I get 3 errors, one after another.

They are:

1. Could not update ICEauthority file /home/matt/.ICEauthority
2. Problem with configuration server /usr/lib/libgconf-sanity-check-2 exited with status 256
3. Nautilus could not create the following required folders /home/matt/Desktop, /home/matt/.nautilus

(I think the third one asked me to create the folders myself and then give it correct permission but not certain)

I tried loging into standard Gnome desktop, same errors, same problem. Same with the gnome safe thing.

After a while however, I do get one panel, in the top left corner - rather than stretching full width, it's about 2 inches across. On it are some buttons (mail, sound, chat, power, time) but not some that should be (guake, wireless etc)

I brought up the run dialogue (Alt + F2) and tried a variety of programs but nothing happened with any (tried firefox, chromium, xchat, terminal)

If any one could offer any advice/help it would be greatly appreciated. I don't know where to start!

Thanks,

Matt

---

### Post by ikonia on 2010-06-06
you're going to need to boot into safe mode and check the permissions on the /home and /home/matt directory, make sure they are read/writeable for your user. From the errors you've suggested it looks like write permissions has been removed.

---

