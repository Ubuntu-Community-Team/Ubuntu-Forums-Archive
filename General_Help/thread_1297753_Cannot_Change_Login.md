---
title: "Cannot Change Login?"
date: 2009-10-22
forum: General Help
---

### Post by GCoffee on 2009-10-22
Hi All,

I've got a Acer Aspire (couldnt stand its default OS) 1 with Ubuntu 9.10 With all the latest updates, and i've switched it to normal desktop mode.

I have 2 logins on the PC, for 2 different people.

However, when I logout from 1 user and try to login as another, it comes up with something along the lines of:

"Error initiating conversation with authentication system - general failure"

I just turned auto-login off and now i find that I can't login at all :S

Its using gnome at the moment, so I'm going to try switching the Sessions around.

I'll get back to you on that one.

Thanks,
GCoffee.

---

### Post by GCoffee on 2009-10-22
Hi All,

I've got a Acer Aspire (couldnt stand its default OS) 1 with Ubuntu 9.10 With all the latest updates, and i've switched it to normal desktop mode.

I have 2 logins on the PC, for 2 different people.

However, when I logout from 1 user and try to login as another, it comes up with something along the lines of:

"Error initiating conversation with authentication system - general failure"

I just turned auto-login off and now i find that I can't login at all :S

Its using gnome at the moment, so I'm going to try switching the Sessions around.

I'll get back to you on that one.

Thanks,
GCoffee.

---

### Post by adeypoop on 2009-12-09
did you find anything out? I have the same problem. I added a new user and changed  auto login. Next thing I can't login at all from the login screen. 

The error message is as follows.

> error initiating conversation with authentication system - general failure

If i change the session to login with a terminal i still get the error.

---

### Post by matbence on 2009-12-28
I was (JUST SOLVED IT A MINUTE AGO!!!) having the same problem. I saw on another post [elsewhere]("http://ubuntuforums.org/showthread.php?t=1271821") that the problem is due to trying to disable the keyring manager prompt. I'm a bit of a noob, but I really didn't want to have to reinstall ubuntu (I had spent ages getting it working perfectly for me).
Reversing changes caused by trying to disable the keyring prompt restored the login. For reference trying to access the /etc/pam.d/gdm file from my windows partition using installable ext2 file system didn't work.
I managed to delete the '@include common-pamkeyring' line through the terminal when booting from a live CD.
Then because I am such a newbie to linux I uninstalled the libpam-gnome-keyring package using my synaptic package manager instead of using a terminal.

Hope this helps you

---

### Post by kvelandia on 2010-05-26
how did you manage to delete it from the live session? did you browse your drive from terminal?

---

### Post by johnofthedead on 2010-06-08
I had the same problem but managed to figure it out on my own. There is a way to revert the changes to your /etc/pam.d/gdm without logging into a gnome live session by doing the following:

1. At login screen, press CTRL+ALT+F1
2. Type the following command: sudo nano /etc/pam.d/gdm and enter your password.
3. Use the arrow keys to scroll down to the last line that you added to the file and delete it.
4. Press CTRL+X to exit. You will be prompted asking you if you want to save. Press 'Y' for yes. You will now be prompted with where you want to save it. By default it is in the same location, so just press enter to overwrite the file.
5. sudo reboot


Worked perfectly for me. Good luck.

---

