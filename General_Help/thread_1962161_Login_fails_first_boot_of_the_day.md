---
title: "Login fails first boot of the day"
date: 2012-04-20
forum: General Help
---

### Post by MoebusNet on 2012-04-20
I leave my notebook off at night. Lately I've noticed that about 50% of the time when I cold-boot the first time of the day (Ubuntu 11.10), the login fails and goes back to the login screen. So far I can login the second time around, but I worry that this will get worse not better. This morning, anticipating the login problem, I was particularly careful when typing in my password. I wanted to make sure that this was not an issue of operator error. Sure enough, the login failed.

How can I dignose what's going on to correct this? Under Gnome I might have been able to come up with some ideas, but Unity has disposed of what little I knew about error messages, log files, etc.

Suggestions welcomed.

---

### Post by MoebusNet on 2012-04-22
Happened again this morning. While I was typing in my password, I noticed a keyboard light illuminate briefly. It shouldn't have, because I wasn't locking/unlocking caps, or the number keypad or any other function.

The keyboard light is the lowest light in the upper-left corner of my System76 Serval Pro 7 notebook, and is labelled with a symbol resembling a padlock with a vertical line or numeral on it. It looks just like the number lock/unlock keyboard light at the upper-left corner of the keyboard, but does not respond to the "Num Lk" function. I don't know what that light does.

Anybody have any ideas, or know what that keyboard light is for?

---

### Post by dino99 on 2012-04-22
unity is installed as the actual default frontend, but you still can get the old look by installing gnome-session-fallback, then login as gnome-classic. That way its easier the view your logs as you are used to, etc. (and install synaptic too, as its not installed by default)

sudo dpkg-reconfigure -phigh -a

(can take a while, dont stop it)

---

### Post by MoebusNet on 2012-04-22
Well I must say, this was interesting... not necessarily in a good way. I installed gnome-session-fallback through Synaptic (already installed) then ran 'sudo dpkg-reconfigure -phigh -a' in Terminal. Terminal issued a bunch of warnings, but continued on to the end. After a shut-down and restart, I do not have the option to log in under Gnome, when I click on the password box of the login page I am immediately logged in without entering a password, and all of my files, folders, etc. are missing.

I guess now I'd be grateful to get back to where I started from. Before I break out a Live-CD to attempt a file recovery session, is there anything I can do first?

EDIT: Somehow I got logged into the Guest account (which I've never used). Scared me to death until I figured that out. When I'm logged in as my normal user account, I do have all my files, folders etc. (Whew!) I'll play with the Gnome desktop to see if I can come up with some error logs for when/if my login issue strikes again. I'll mark this as "Solved" for the present.

Dino99, thanks for the gnome-seesion-fallback advice, I was just being hard-headed trying to figure this out under Unity. I guess what they say about old dogs and new tricks applies here.

---

