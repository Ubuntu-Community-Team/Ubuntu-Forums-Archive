---
title: "Disable login sounds"
date: 2010-10-12
forum: General Help
---

### Post by MrNatewood on 2010-10-12
How can I disable login sounds in maverick without completely disabling the ubuntu sound theme?

I just want it to not make sounds on startup\login but still make the ubuntu sounds when new mail is received, etc.

Any ideas on how to do this?

---

### Post by TheAnachron on 2010-10-12
In Ubuntu you go to:
Settings -> Sounds -> Sound Theme -> Startup Sound -> Change it to none -> Save -> Close -> Restart.

That should fix the issue!

---

### Post by MrNatewood on 2010-10-12
Where are these "settings" you are referring to?

I tried System->Preferences->Sound
But it doesn't have the options you are referring to.

---

### Post by TheAnachron on 2010-10-12
Hm I am using 10.04, maybe that is the reason.

Look for an option to select the sound theme. (In the sounds tab)
You can edit the theme and save it.

---

### Post by JOHNNYG713 on 2010-10-12
Go to System>Preferences>startup Applications un-check GNOME Login sounds!

---

### Post by MrNatewood on 2010-10-12
Thanks, that worked :)

---

### Post by MrNatewood on 2010-10-12
This does remove the log-in music, but how do I disable the sound played before logging in? When the login screen comes up there is also a sound and this does not disable it.

---

### Post by JOHNNYG713 on 2010-10-12
If you are speaking of the little "bump-diddly-bump" at the log in screen, You can rename the system-ready.ogg  to sytemready.ogg take out the "-" or change it as you wish, This is a link to dialog-question.ogg just open a terminal, and," sudo nautilus " to usr/share/sounds/ubuntu/stereo and rename that link, you wont have the sound at login but you will still have dialog-question.ogg. There might be an easier way, but this will work.

---

### Post by MrNatewood on 2010-10-12
Thanks. I wish they had included a way to edit the theme through the sound menu or something like that.

---

### Post by sendblink23 on 2010-10-12
> **JOHNNYG713 said:**
> Go to System>Preferences>startup Applications un-check GNOME Login sounds!

randomly asking...  can you share me your theme ;)

---

### Post by JOHNNYG713 on 2010-10-12
> **sendblink23 said:**
> randomly asking...  can you share me your theme ;)
  Not a problem! the icon theme is Buttonized found here! Enjoy!
[http://gnome-look.org/content/show.php/Buttonized?content=129217](http://gnome-look.org/content/show.php/Buttonized?content=129217)

---

### Post by sendblink23 on 2010-10-13
> **JOHNNYG713 said:**
> Not a problem! the icon theme is Buttonized found here! Enjoy!
[http://gnome-look.org/content/show.php/Buttonized?content=129217](http://gnome-look.org/content/show.php/Buttonized?content=129217)

Thank you very much!
Odd I couldn't reply to your private message =P
> JOHNNYG713 has chosen not to receive private messages or may not be allowed to receive private messages. Therefore you may not send your message to him/her.
lol

---

