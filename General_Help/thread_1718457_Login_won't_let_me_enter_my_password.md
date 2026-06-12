---
title: "Login won't let me enter my password"
date: 2011-03-31
forum: General Help
---

### Post by rickcjmac on 2011-03-31
I had auto-login setup. I tried to disable keyring login by following instructions on a thread that I can't find now, go figure :). I had to enable the login screen for it to work, as per instructions on the thread. Then I installed pam-something and added a line to the end of a file. 

Upon reboot I get to the login screen and my user name shows up, but there is no box to put my password in. I click on my user name and the login box bounces but doesn't give the password area. Same when I click on "Other".

This is a weird error and I have no clue how to fix it. Any help is MUCH appreciated. 

Richard

---

### Post by p110011 on 2011-03-31
Are you able to use the terminal? If you hit the arrow up key it should show your last few commands. Maybe you can undo that pam something?

I had the keyring popping up on my systems, was a bug and I just left the password blank to stop it from popping up.

---

### Post by rickcjmac on 2011-03-31
Someone had a similar problem as me:

[http://ubuntuforums.org/showthread.php?t=1699774&highlight=login]("http://ubuntuforums.org/showthread.php?t=1699774&highlight=login")

I had to boot Linux in recovery mode (or at the normal login screen hit ctrl + alt + f1)

Then navigate to ect/pam.d

Then open "gdm" as root (sudo vim gdm)

In the vim text editor I removed the last line which read:

"@include common-pamkeyring"

Saved it, rebooted now we're back to normal :) YEAH!!!

---

