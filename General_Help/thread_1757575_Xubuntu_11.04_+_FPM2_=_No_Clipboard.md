---
title: "Xubuntu 11.04 + FPM2 = No Clipboard"
date: 2011-05-13
forum: General Help
---

### Post by imbrian on 2011-05-13
I'm a big fan of Xubuntu and use FPM2 (Figaro's Password Manager 2) as a lightweight way of managing all my passwords.  It's intended use is for you to enter items with URLs (if applicable), your username and your password.  If you click on the URL, it can launch your browser with the username and/or password saved in the clipboard for quick and easy input.  Perfect!  Till 11.04, anyway...

I believe
I may have found a bug - either with fpm2 or with the default
clipboard.  I'm unsure how to determine which.

Software:
* Xubuntu 11.04 64-bit, unaltered
* FMP2 0.78

Steps to verify:
* Download the Xubuntu 11.04 iso and boot onto the "live" version
* apt-get install fpm2
* within fpm2 create a test entry
* attempt to copy the username or password
* unless "clear target after paste" is not selected, fpm2 will not copy

Expected behavior:
* values should be copied and the clipboard should be immediately
cleared

Any thoughts?  Anyone else experience this?

[http://packages.ubuntu.com/natty/fpm2](http://packages.ubuntu.com/natty/fpm2)

---

### Post by Wobblybob on 2011-05-13
I don't use this app but have you tried opening fpm2 from a terminal then checking the output to the terminal as you try the copy paste actions.

---

### Post by imbrian on 2011-05-13
I did try executing from terminal - but it doesn't echo anything out.  It also doesn't appear to have any -v option:

Usage: fpm2 [-f filename] [-t]
	-f filename		Open filename passwords file
	-t			Start in tray icon

Also, I should state that it worked as expected in 10.10.  I did a fresh format and install (not upgrade).

---

