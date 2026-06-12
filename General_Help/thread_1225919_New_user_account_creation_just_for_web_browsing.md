---
title: "New user account creation just for web browsing"
date: 2009-07-29
forum: General Help
---

### Post by gwyddyon on 2009-07-29
I'd like to know if is there any way to create a limited / restricted user account (similar to 'guest' account) just only for web browsing purposes. I mean:

The new user could log into the system, then he can only use a web browser (i.e. firefox). He couldn't navigate through the file system structure, launch any terminal, text editor, etc.

I'll appreciate any help about it.

(Sorry, if my english is not good enough)

Thanks in advance.

<< Gwyddyon >>

---

### Post by credobyte on 2009-07-29
Create a new group, set permissions ( applications, etc. ) and finally, create a new user. Haven't done this by myself, however, you can change which applications the group should have access to.

---

### Post by magh-87 on 2009-07-29
If you're using Ubuntu, go to System -> Admin -> Users & Groups

From here unlock the application if necessary, select "Manage Groups"
This is where you can pick and choose existing groups or create your own. For a user that browses the web, I would personally provide the Office tools to them :) Means they can do their research and their home work at the same time.

When you create a new user that can only do that, specifically your guest account, make sure they're in that "web" group or whatever you call it.

---

### Post by gwyddyon on 2009-07-31
I'am testing it right now...

---

### Post by magh-87 on 2009-08-01
Let us know how it goes, if there's anything not working right I'll do my best to help you out.

---

### Post by gwyddyon on 2009-08-03
Unfortunately the changes I did were not enough. The user can log in but he works like a common desktop user in Ubuntu. How can I change the group ('internet') properties to allow it only to run network-manager, firefox and power on/off the system?

Thanks to all in advance.

---

### Post by credobyte on 2009-08-03
Hm, Unprivileged account ( when you add a user, check "type" field ) would have no access to system files and internet - basically, user can only login ! Give him the rights to connect to the internet and you should be fine :)

---

### Post by CatKiller on 2009-08-03
There are a bunch of lockdown keys in GConf, although I don't know exactly how they work. It's been done before though; look for "kiosk," since that's how such things are generally known.

---

### Post by amac777 on 2009-08-03
Here is a very quick and dirty way of doing what you want:

1. Create a 'guest' account by going to SYSTEM->ADMINISTRATION->USERS AND GROUPS. The guest user should be a regular desktop user so they can get sound in flash. To prevent this user from logging in to a shell via text mode, on the Advanced tab, change the shell from '/bin/bash' to '/dev/null'.

2. Create an .xsession file for the guest account by doing:

```
sudo nano /home/guest/.xsession
```

with this contents:

```
/usr/bin/metacity &
/usr/bin/firefox
```

and make it executable by running:

```
sudo chmod +x /home/guest/.xsession
```

3. Logout and then login as guest. You should be presented with only firefox open and when you close firefox, the user will be logged out automatically.

---

### Post by mike555 on 2009-08-03
OK, i just tried this and got as far as putting in 
/usr/bin/metacity &
/usr/bin/firefox   , but how do I save this ??

---

### Post by CatKiller on 2009-08-03
It's written at the bottom.

Ctrl-O saves. Ctrl-X exits.

---

### Post by mike555 on 2009-08-03
OK, got it....... now to log in "guest" without a password.........any ideas how?

---

### Post by amac777 on 2009-08-03
You can set your computer to automatically login the 'guest' account user after something like 10 seconds of inactivity (no password will be required to be entered):

SYSTEM -> ADMINISTRATION -> LOGIN WINDOW

Go to the SECURITY tab, select: ENABLE TIMED LOGIN, and pick the 'guest' user. You can set the pause before login time to anything you like... maybe 10 seconds is a good choice to give yourself a chance to login using another account if you like.

By the way, about security and preventing the guest user from seeing other users' files on your computer, you should make sure you set the permissions on the home directories for all users so that other users can't see in those directories. Otherwise, the 'guest' user could do something sneeky like use a website upload function to access those files from the other users.

To secure all user's home directories, use this command:

```
sudo chmod go-rwx /home/*
```

That will make each user's files only visable to the user himself and not to others.

---

### Post by mike555 on 2009-08-03
OK, got it working , except the fast user switching doesn't show the guest , and when using the guest Firefox if I minimize it the screen goes black and I can't do anything to bring it back up.

---

### Post by renkinjutsu on 2009-08-03
don't minimize it.. or you can add 
gnome-panel &
before firefox

or you can use something more lightweight if you want..

---

### Post by amac777 on 2009-08-03
You can use Alt-Tab to bring firefox back from being minimized.

I'm not sure why the fast user switcher doesn't show the guest account. My computer is like that too. Maybe the username 'guest' is filtered by the fast user switcher? Switching the user name might solve the problem.

---

### Post by rraj.be on 2009-08-03
Ctrl + o will make you save the file with a name in nano.

You can use gedit instead of nano if you feel GUI is more comfortable than CLI.

Try this 

```
 sudo gedit /home/karthik/.xsession
```

It should be more convenient than nano.

---

### Post by mike555 on 2009-08-03
Thanks Amac777 , I'm trying to set up a Ubuntu machine for my local lodge, but need it to be bullet prof as possible ...

---

### Post by amac777 on 2009-08-03
Yeah, I understand making things as bullet proof as possible. Using a proper Kiosk program as suggested by another user at the beginning of this thread would actually be a better way of doing this. My solution was the DIY version, but as you can see, sometimes that ends up being more complicated than learning how to use a proper tool.

Anyway, here's what I figured out:

1. FAST USER SWITCHER

The fast-user-switcher applet only shows users who have their shell set to /bin/bash. That is how it seems to be hard coded. So if you want the guest account to appear in the fast-user-switcher, you need to change the shell for the guest account back to /bin/bash. So basically undo that part from my original instructions. The trade off is now the guest user could login via text mode (by pressing Alt-F2 for example) and get shell access. You need to decide if the convienence is worth the loss of security.

2. BLACK SCREEN AFTER MINIMIZING

If you feel that using Alt-Tab would be too much trouble for your users (maybe they don't even know this is possible), one simple fix is you can not even use a window manager and then it will be impossible for the user to move/resize/minimize/adjust firefox's window in any way. This might not be what you want but you can try it by doing:

```
sudo nano /home/guest/.xsession
```

and change the contents to simply:

```
/usr/bin/firefox
```

If that is too ugly and not user friendly for you, you can also try removing the minimize button so it would be that much harder (although it's still possible) for users to minimize firefox. Here's how to remove the minimize button for the guest account:

Make a temporary change to the .xsession file for the 'guest' user by doing:

```
sudo nano /home/guest/.xsession
```

change the contents to:

```
/usr/bin/metacity &
/usr/bin/gconf-editor
/usr/bin/firefox
```

Now login to the guest account and you should presented with the gconf-editor for the guest user. Navigate to "apps->metacity->general->button layout" and double click the button layout and change it to:

```
menu:maximize,close
```

Close gconf-editor, and then close firefox.

Finally, change the .xsession file back to its original contents:

```
sudo nano /home/guest/.xsession
```

```
/usr/bin/metacity &
/usr/bin/firefox
```

Now the guest user won't be able to minimize firefox with that button because the button is gone. (There still might be other keypresses or ways to minimize it though so using a proper Kiosk program would be the better way to do this.)

---

### Post by amac777 on 2009-08-03
deleted because not true.

---

