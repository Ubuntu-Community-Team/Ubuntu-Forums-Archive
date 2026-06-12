---
title: "Quick question about my quick question...lol"
date: 2009-08-30
forum: General Help
---

### Post by rmp5s on 2009-08-30
[http://ubuntuforums.org/showthread.php?p=7873019#post7873019](http://ubuntuforums.org/showthread.php?p=7873019#post7873019)

No prob and all.  I didn't know that.

But, out of curiosity, why not?

---

### Post by uylug on 2009-08-30
Always running commands as root makes it possible to accidentally delete essential files. If you run every application as root, you will be giving them the right to do anything to your system.

That is why we dont use root :)

---

### Post by Bachstelze on 2009-08-30
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by LzBy1 on 2009-08-30
I would guess when you log in a root it's too easy to mess things up. It would be like finding malpractice insurance for a surgeon who uses a chainsaw instead of a scalpel.

---

### Post by uylug on 2009-08-30
> **LzBy1 said:**
> I would guess when you log in a root it's too easy to mess things up. It would be like finding malpractice insurance for a surgeon who uses a chainsaw instead of a scalpel.

:lolflag:

---

### Post by rmp5s on 2009-08-31
Roger that.

But, aren't some things only possible as root?

---

### Post by credobyte on 2009-08-31
> **rmp5s said:**
> Roger that.

But, aren't some things only possible as root?

[COLOR=RoyalBlue]sudo -i[/COLOR] can do the same as if you would have been logged in as [COLOR=RoyalBlue]root[/COLOR].

---

### Post by rmp5s on 2009-08-31
Thank you.  I'll try that out.

Again, out of curiousity, why can that be on here but nothing about root if they both do the same thing?

---

### Post by SoftwareExplorer on 2009-08-31
Because if you login as root that means that you most likely gave root a password. All linux computers have the root user. If someone is trying to break in to your computer, and root has a password, all they have to do is guess roots password, not which user and password. If root doesn't have a password, then they can't login as root, no matter what password they try. Basically, if root has a password and the computer has something like ssh, people can get into your computer remotely and do basically anything on your computer just by guessing a password.

The main thing is that if root has a password, the don't have to guess what user to try to login as.

---

### Post by SoftwareExplorer on 2009-08-31
Also, if your browser was to have a vulnerability for example, and someone gains control of it, they can make system wide changes. For example deleting all the files on your computer. If you are running as a 'normal' user, they might be able to cause problems with your user, but they wouldn't be able to change anything system wide unless they correctly guess the password for sudo. 
Also, if you want to run a single command as root from the terminal, just add 'sudo<space>' before the command. If you are running a graphical application, just add 'gksudo<space>' before the command.

---

### Post by rmp5s on 2009-08-31
Love the avatar!  I'm a Chrome fan, myself but have grown to like Firefox.  ANYTHING is better than IE...great avatar.

Anyway...this all makes perfect sense...the power root has is a problem.  Except for one thing:  if root = total access and root = security problem (just guess a password), then why would sudo be any different?  I just put a password in for that too...???  Again...just trying to learn about this whole Kernal, root, superuser, Linux thing...I have root access on my phone (Android G1) and haven't really used it much cuz I don't know how.  Just in the quest of knowledge for lack of a better way to put it.

Oh...and "sudo -i" or whatever it was worked like a charm.  My speakers work now!  Thank you!

---

