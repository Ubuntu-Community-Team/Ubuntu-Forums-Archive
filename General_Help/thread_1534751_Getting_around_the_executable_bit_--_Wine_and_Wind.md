---
title: "Getting around the executable bit -- Wine and Windows 95"
date: 2010-07-20
forum: General Help
---

### Post by beezum88@gmail.com on 2010-07-20
So I have a copy of "Riven" for Windows 95 still laying around, and I decided to see if I could run it in WINE just for the hell of it.  I got the following error when I tried to run the "Setup.exe" file (or any other executable on the CD-ROM, for that matter) using WINE: 

> The file '/media/Riven1/Setup.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

I read about the executable bit, and while I understand the security reasons for it being there, I would still like to know if there's a way to circumvent it, or even a workaround.  I tried chmod on the exe file, but since it's on read only media, that didn't work.  Any ideas would be appreciated. 

By the way, I'm running Lucid.

---

### Post by robsoles on 2010-07-20
Does the installer break if you run it after copying to your harddrive and setting the executable bit on it there?

If it does break then you can use playonlinux to get around the executable bit problem - check it out a bit and post back to this thread if you can't seem to find what to do to get your CD/DVD based executable (installer!) to run for you.

---

### Post by Vaphell on 2010-07-20
wine /path/to/exe/file.exe should work, similar to how you can make .sh script executable or pass it as an arg to sh

as a bonus - you can see warning and error messages in case something goes wrong

---

### Post by tarps87 on 2010-07-20
How are you trying to run it?

---

### Post by beezum88@gmail.com on 2010-07-20
> How are you trying to run it?
I was right clicking and selecting "Open with the Wine Windows Program Loader", as well as simply double-clicking the file.

> wine /path/to/exe/file.exe should work
Yes it does, thanks.  

Also, copying all the files to my hard drive and then changing the permissions did get the same result, except now I get the error (from Wine itself this time) "This program is not compatible with Windows 3.1.x", even though I've set Wine to open all programs as Windows 98, since those are the only Windows programs I own.  And it opens other programs in the correct version of Windows, (though they have their own problems).  But maybe I should start a new thread for this.

---

### Post by tarps87 on 2010-07-21
Some times that happens with launching it, usually running it from the command line is more successful.
Have you tried specifically setting the exe to run in 95 mode? Just as your first post says it is designed for 95. There is not usually a problem between the two but who knows

---

### Post by beezum88@gmail.com on 2010-07-24
It gives me the same error whether or not I run it from the command line or run the copy I put on my hard drive and changed the permissions on.  I did try changing the settings in the wine setup dialog to specifically open that executable in 95 mode, but it doesn't seem to have any effect.

---

### Post by robsoles on 2010-07-24
sounds like you will need to do it in a VM - [www.virtualbox.org]("http://www.virtualbox.org") is what I recommend myself.

[www.google.com/search?q=use+xp+vm+in+virtualbox+under+ubuntu]("http://www.google.com/search?q=use+xp+vm+in+virtualbox+under+ubuntu") (1st result is opposite of idea but I saw a couple of ok results in the list Google return.)

---

### Post by chmegr on 2011-09-15
I am having the same problem...is there a way to do it using WineHQ?

---

### Post by holycow131415 on 2011-09-15
You right clicked on the file, and in the permissions tab enabled for execution?

---

