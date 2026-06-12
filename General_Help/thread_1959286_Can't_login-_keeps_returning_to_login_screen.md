---
title: "Can't login- keeps returning to login screen"
date: 2012-04-15
forum: General Help
---

### Post by TheBigH on 2012-04-15
I'm having trouble logging in. When I type in my user name and password, the screen goes momentarily black and then I get dumped back at the login screen. I am running ubuntu 10.04.

Another thread I found on this forum suggested I go to a terminal with Ctrl-Alt-F1 and type "gdm". When I do that I get the following error message

```

** (gdm-binary:1699): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.37" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:1699): WARNING **: Could not acquire name; bailing out
```I have no idea what this means or even if it's relevant. Can anyone help me?

Cheers.

---

### Post by grahammechanical on 2012-04-15
I do not know if this will help but did you type sudo and then enter your password when asked?

It is just a thought.

Another idea. Do you get a Grub menu? If so, is there another (older/earlier) kernel in the list? Try booting into that one. It might get you to a desktop top.

Regards.

---

### Post by Toz on 2012-04-15
I don't think gdm is your problem if you're getting a graphical login screen. 
Here are a few other things to try or look at:

1. Do you have adequate free space? This might happen if you've run out of disk space.

2. When you log in at Ctrl-Alt-F1, have a look at the permissions of the files .Xauthority & .ICEauthority in your home directory. If they are not owned by you, change the ownership. You can also try deleting the files (they will be recreated).

3. Also when logged in at Ctrl-Alt-F1, have a look at the .xsession-errors file in your home directory. It might yield some clues as to what is happening.

---

### Post by TheBigH on 2012-04-15
> **Toz said:**
> I don't think gdm is your problem if you're getting a graphical login screen. 
Here are a few other things to try or look at:

1. Do you have adequate free space? This might happen if you've run out of disk space.


Free space is not an issue; still have over 100 gig.

> 
2. When you log in at Ctrl-Alt-F1, have a look at the permissions of the files .Xauthority & .ICEauthority in your home directory. If they are not owned by you, change the ownership. You can also try deleting the files (they will be recreated).
Both of these are owned by me, with permission strings
"-rw-------"

Deleting them does not help.

> 
3. Also when logged in at Ctrl-Alt-F1, have a look at the .xsession-errors file in your home directory. It might yield some clues as to what is happening.This file contains one error:
"/home/thebigh/.profile: 34: Syntax error: newline unexpected"

I don't remember touching .profile lately. Could this be the source of my problem?


Cheers

---

### Post by Toz on 2012-04-15
Can we have a look at your .profile file?

And maybe post back, if you can, the last 5 lines of ~/.xsession-errors.

---

### Post by TheBigH on 2012-04-16
I found the problem. There was a misformatted line in my .profile, and commenting it out fixed my problem.

---

### Post by Toz on 2012-04-16
Good to hear. Can you please make this thread as Solved from the Thread Tools link above?

---

