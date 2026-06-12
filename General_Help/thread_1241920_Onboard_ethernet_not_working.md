---
title: "Onboard ethernet not working"
date: 2009-08-16
forum: General Help
---

### Post by Magma828 on 2009-08-16
Last week I turned my server off when I went on holiday, I just got back and turned it back on to find ubuntu can't connect to the network. I'm using ubuntu home edition, too.

These is exactly what happens:
1. I turn the computer on and it goes through all the post stuff, shows the ubuntu load bar thing, then prints the status on some services which have been started. The last one is *avahi-daemon* and the system just stops there. I thought the problem could be with *avahi-daemon* so I disabled it and now the last service is the one above - *cupsd*.
2. tty7 cannot be accessed (just ignores me) so something graphical is running (i think). I'm still a real noob with linux so don't take my word for it.
3. I open tty2 and type *sudo gdm* (just *gdm* gives operation not permitted errors). This loads the login screen and lets me login, but pops up the error ***Internal error** failed to initialize HAL!*
4. The little lan connection icon in the top right has a warning symbol by it and on hover says *No network connection*. I've tinkered with all the network settings but it just doesn't seem to find the onboard lan interface, because it's only showing *lo* not *eth0*.
5. If I click the shutdown icon everything freezes and I have to hard reset. If I push the reset button, type reboot or ctrlaltdel while in prompt mode it starts some shutdown scripts but then just freezes.

Also, there were installed updates awaiting reboot before I shut the server down which may have caused the problem on next boot. I don't remember what the updates were, but my systems pretty standard and they only installed just over a week ago (could have downloaded a few weeks back) so any drastic updates should be well known in the community.. right?

I'm sorry this problem is so damned complicated, I'm just trying to give as much detail as possible. If you want some specific info just ask but I can't go returning massive results of diagnostic commands because of obvious reasons (ie, the server does not have network access).

---

