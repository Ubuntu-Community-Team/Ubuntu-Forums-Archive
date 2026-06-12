---
title: "Xorg, Mouse, Hardware fail... what is this??"
date: 2012-02-16
forum: General Help
---

### Post by lepusfelix on 2012-02-16
Hi all. I've run into a massive problem. Last night I logged out of Lubuntu because some element of my desktop environment had disappeared (quite usual for me, as it generally happens when openbox or emerald or whatever else is running suddenly stops), and I was hoping to just log back in immediately and everything would be back to normal. While it was logging out, I noticed an unusual wall of text. I don't remember exactly what it said, but it was one line repeated over and over and over, and I know "port 8" was mentioned.

Anyway, I went to log back in, and after my desktop had appeared, and I went to get back to work, the screen went black briefly before the login screen reappeared. Now, after a full day of experimentation and investigating, I'm no closer to finding out why this happens, but I have found out that it's basically my X server being killed every time I move my mouse, even slightly.

I've ruled out a USB problem, because other peripherals that use USB are working fine. I've ruled out the mouse itself, because I replaced the mouse today, thinking it might have been the mouse itself. The brand new one does the same thing. Xorg logs seem all fine and normal to me, but without a mouse, there's near enough no chance I'll be able to copy and paste outputs here.

This problem affects me no matter what way I log in. If I use kdm, lxdm, gdm or lightdm, and no matter which DE I'm selecting to start, I always get the same thing. This presents a problem for a clean install, too, as downloading and burning a LiveCD is (as far as I know) practically impossible with only keyboard input. Not only that, but I wouldn't trust my CD-RW drive as far as I could throw it.

I should mention that I made another user account to try logging in with that. My own account at least logs in and brings up a desktop, even if I can only use it with a keyboard. The extra account doesn't get past the login screen at all.

Please help :(

---

### Post by lepusfelix on 2012-02-17
I managed to work around the issue by upgrading from Oneiric to Precise alpha. I still don't know where the problem came from, or indeed what it was, but that seems to have worked. I can now move my mouse without killing my x session. Leaving the thread open for future exploration, though.

---

### Post by Rodney9 on 2012-02-17
Good luck, don't forget 12.04 is still in alpha and will have rough edges.

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

