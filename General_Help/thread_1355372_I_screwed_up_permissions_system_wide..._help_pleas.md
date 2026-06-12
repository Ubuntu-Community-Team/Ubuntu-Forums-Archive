---
title: "I screwed up permissions system wide... help please..."
date: 2009-12-14
forum: General Help
---

### Post by carolynmarenger on 2009-12-14
I screwed up!

I meant to type "sudo chmod *.* 770" in one of my home/user directories.  I realised after typing the requested password, that I had actually typed "sudo chmod .* 770"

Obviously, there is a very big difference between the two.  The system will no longer complete the GUI log in process for any user.  I can get in via a command line, however I am at a loss as to how to solve this dilema.

I remember that Mandriva's default configuration included a scan and reset of file/directory permissions for the whole system.  I am hoping Ubuntu has one as well, and that when I awaken in the morning, the system will have repaired itself.

This message, however, is posted by the more pessimistic portion of my cerebrum.  What do I need to do to reset the permissions across the whole system?  Is there a list somewhere of what the 'default' permissions are on a directory by directory basis?

Your assistance is greatly appreciated,

Carolyn

---

### Post by kitten16 on 2009-12-14
Is the error something like this?

> User's $home/.dmrc file is being ignored.  This prevents the default session and language from being saved...

---

### Post by Vaphell on 2009-12-14
when you log in text mode, what does ls -al say? who is the owner of the dotfiles/config directories (starting with .) and what are the permissions?

if you want some kind of gui to navigate stuff in text mode, install mc (sudo apt-get install mc)
when you run mc, use f9 to get upper menu, set one of the panels to info mode, it will show properties of the highlighted item.

---

### Post by john newbuntu on 2009-12-14
That should have affected all your filesystems!  I am assuming that you do not have a backup just before you ran the command.  Sorry, I do not know of a tool either to fix permissions.

Edit: Nevermind. I thought you recursively changed permissions.  So what you dir would not affected all your filesystems.

---

### Post by llamabr on 2009-12-14
Note that *.* is identical with * -- you don't need to trick linux over that dot.

it looks like you just 770'd all your dot files.  What directory did you do this in?  Go back there, and try this:

```
sudo chmod 755 .*
```

Also, if you did this in a user dir, try making a new user.  log in as that user.  See if the new user has the same problem.

---

