---
title: "what happened to the Security tab that used to be located in System/Administration/Lo"
date: 2010-01-15
forum: General Help
---

### Post by C.S.Cameron on 2010-01-15
what happened to the Security tab that used to be located in System/Administration/Log in Window 
I'm trying to figure out how to get a Live USB to boot to my user name and password.

---

### Post by C.S.Cameron on 2010-01-16
Bump

---

### Post by jamesisin on 2010-01-16
I would not recommend doing that on a USB live build as this will mean that if you lose it anyone who finds it will be able to log in as you without any hindrance.

That being said, you'll have to tell us which version of Ubuntu you are running so we can best help you de-secure it.

---

### Post by C.S.Cameron on 2010-01-16
Well I would of course use a password which is more secure than a persistent thumbdrive without a password. Without it you have to make a new user  in Users and Groups and then switch users after log in.

9.04 still had the Security tab in System/Administration/Log in Window, 9.10 does not.

---

### Post by jamesisin on 2010-01-16
I am able to select users from a menu at the login screen in 9.10 (all user accounts have been created using System --> Administration --> Users and Groups).

What do you see at your login screen?

---

### Post by C.S.Cameron on 2010-01-16
I think that is what I was looking for , it just did not seem to be working the same as it did with 9.04. It still logs in as ubuntu.
Thanks

---

### Post by jamesisin on 2010-01-16
Oh, I see.  You want to turn *off* automatic login.

You might be able to simply edit this:

gksu gedit /etc/gdm/custom.conf

(AutomaticLoginEnable=true change to false?)

If that doesn't work out for you I found this post with more complicated instructions (which they claim work):

[http://ubuntuforums.org/showthread.php?t=1309554](http://ubuntuforums.org/showthread.php?t=1309554)

Let me know how that goes.

(On a side note, I would prefer doing a full installation as described in the other post rather than a live install; but the other post does describe how to deal with this in a live install.)

---

### Post by efflandt on 2010-01-16
Take it from me, simply changing autologin for ubuntu user from gnome or editing /etc/gdm/custom.conf does not work because it uses its default custom.conf on reboot.  Although, strangely you can still see your edited custom.conf if you loop mount casper-rw on a different system.

I have not tried the more complicated method yet.  Although I have installed a regular system on 4 GB USB flash (using tmpfs for /tmp like the USB live iso does).

---

### Post by C.S.Cameron on 2010-01-16
Yes, I was starting to get afraid it was going to be more complicated than I remember.

My only problem with Full installs is that I start fooling with stuff like restricted drivers and pretty soon my thumbdrive only works on one computer.

When I travel I take both.

---

### Post by dcstar on 2010-01-16
> **C.S.Cameron said:**
> what happened to the Security tab that used to be located in System/Administration/Log in Window 
........

The whole X login section changed from 9.04 to 9.10, and there are no tools yet to manage it in 9.10.

---

### Post by C.S.Cameron on 2010-01-16
I tried installing 9.04 again and it was possible to require passwords on a persistent thumbdrive install without messing with filesystem.squashfs. 
I hope they add the tools soon.

---

