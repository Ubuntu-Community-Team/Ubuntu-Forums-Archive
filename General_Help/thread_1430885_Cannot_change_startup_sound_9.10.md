---
title: "Cannot change startup sound 9.10"
date: 2010-03-15
forum: General Help
---

### Post by pcdctor on 2010-03-15
I cannot find where i can change the startup sound for 9.10.  Everywhere that i have read so far has me go to System->Preferences->Sound and there was supposed to be a tab there for logon and logout sounds.  I do not have that tab in my sounds screen.

---

### Post by dcstar on 2010-03-15
> **pcdctor said:**
> I cannot find where i can change the startup sound for 9.10.  Everywhere that i have read so far has me go to System->Preferences->Sound and there was supposed to be a tab there for logon and logout sounds.  I do not have that tab in my sounds screen.

The sounds setup post 9.04 is totally different, the sounds are all in a "Theme" package and there are no GUI tools to make changes (even in 10.04!).

Do a search for instructions on how to manually change the sounds - but it is messy!

---

### Post by CLEARviewF on 2010-04-22
At least until Karmic 9.10, Ubuntu system sound themes are only customizable through the command line or manually as root moving and replacing files and directories. There is not a GUI to configure system sound themes.

If you want to change the default Login sound you must replace that file in /usr/share/sounds/ubuntu/stereo/desktop-login.wav

For example you could have a sound file for you new login sound in /home/your_user_name/your_personal_login_sound.wav

So you will change your login sound with the next command:

#sudo mv /home/your_user_name/your_personal_login_sound.wav /usr/share/sounds/ubuntu/stereo/desktop-login.wav

and done!

Bye.

---

### Post by towheedm on 2010-04-28
> **pcdctor said:**
> I cannot find where i can change the startup sound for 9.10.  Everywhere that i have read so far has me go to System->Preferences->Sound and there was supposed to be a tab there for logon and logout sounds.  I do not have that tab in my sounds screen.

Check out the link at the beginning of this thread:
[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

Customizing the login sound starts at page 41 of the pdf file.

---

