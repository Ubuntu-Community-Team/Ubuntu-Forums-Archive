---
title: "Remove GUI permissions"
date: 2009-11-15
forum: General Help
---

### Post by Poyntz on 2009-11-15
Hi folks,

I want to make this window:
[ATTACH]136269[/ATTACH]

Look more like this window
[ATTACH]136268[/ATTACH]

The dilemma is, that this account has root access (this is how I want it)
but, root access means that you can set permissions via the GUI as can be seen in the first screenshot. I don't want this. I want root access (ie, so I can sudo x, and still do stuff, but I don't want random people that don't know my root password to be able to aimlessly mess with files just by right clicking and changing the permissions, when I've deliberately eliminated execute,read,write access 

How can I set Ubuntu up it to disable GUI access from this window? If I use chmod, I have to use sudo, likewise, when I'm changing permissions via the GUI, I'd like to have to type in some sort of password.

Free GUI access is a huge security flaw, so please help me disable it!

(I know you're all going to give me the command: **Ctrl + Alt + L** to lock the screen when I leave my laptop unattended but sometimes I forget... and the permissions window gives anyone permission access to all my files, even if I don't want them to)

Thanks in advance!

---

### Post by aysiu on 2009-11-16
If you forget to lock the screen, you can set up your screensaver to automatically lock the screen after a certain number of minutes of inactivity.

Linux and Unix both use users and permissions, so if you're logged in as a user, you can do whatever that user can do. The solution is always to log out or lock the screen if you don't want people having access to what your account has access to.

---

### Post by undecim on 2009-11-16
If you don't want people messing with permissions of random files, don't leave an account with root access out in the open. Better yet, don't log in as root at all!

Anyone with access to your GUI can still drag and drop files around, edit files, add files to /etc/*.d directories, etc. That's a bigger problem than the permissions!

If you just want to be able to use sudo without a password, try this: Type "sudo visudo" in a terminal. Find the line that looks like this and uncomment it by removing the # from the beginning:
```
# %sudo ALL=NOPASSWD: ALL
```

Then, add yourself to the "sudo" group by typing "sudo gpasswd -a username sudo"

That way, you should be able to run sudo commands without a password (you may need to log out and then back in before the changes take effect)

That is a thousand times safer than logging in with root privileges!

---

### Post by aysiu on 2009-11-16
> **undecim said:**
> Better yet, don't log in as root at all! From what I can make out from the original post, it sounds as if the user is an *admin* (able to *sudo*) but not root. I could be mistaken.

---

### Post by Poyntz on 2009-11-16
> **aysiu said:**
> If you forget to lock the screen, you can set up your screensaver to automatically lock the screen after a certain number of minutes of inactivity.

Thanks for the tip :). I'm also aware of this feature, but I often leave my computer for a while (even at home), and constantly retyping my password every time I come back to the screen is annoying. I know it's a way around the predicament, but there should be another option...

> **undecim said:**
> If you don't want people messing with permissions of random files, don't leave an account with root access out in the open. Better yet, don't log in as root at all!

I still want to be able to use sudo, just don't want GUI access for permissions.

> **undecim said:**
> Anyone with access to your GUI can still drag and drop files around, edit files, add files to /etc/*.d directories, etc. That's a bigger problem than the permissions!

I know that's a problem, but that's not my concern. I view permissions as a bigger problem because in that instance I've actually tried to deny execute/read/write access and people can still tamper with stuff. I accept liability for files without access protection.

> **undecim said:**
> If you just want to be able to use sudo without a password, try this: Type "sudo visudo" in a terminal. Find the line that looks like this and uncomment it by removing the # from the beginning:
```
# %sudo ALL=NOPASSWD: ALL
```

Then, add yourself to the "sudo" group by typing "sudo gpasswd -a username sudo"

That way, you should be able to run sudo commands without a password (you may need to log out and then back in before the changes take effect)

Thanks for the tip :D. But I would never use this, because ```
sudo su
``` works fine and it's easier to type.

> **undecim said:**
> 
That is a thousand times safer than logging in with root privileges!

I'm a bit confused. Logging in requires a password which others don't have. I wouldn't log in to an account without sudo access because it means if I want to do anything administrative (which I practically do every day), I'd have to restart. Think of how many times you use **sudo** in a given day.

> **aysiu said:**
> From what I can make out from the original post, it sounds as if the user is an *admin* (able to *sudo*) but not root. I could be mistaken.

You're on the money. Definitely not root and happy about it. 

-----------

If there really is no way to ensure that a password pop-up box appears when permissions are being set, is there somewhere I can see the code pertaining to the permissions tab? (if it's not in C++/Java it wouldn't make much sense to me, tho). I can see a case for an extra feature that should be implemented. If necessary I'd be even happy to contribute to see that this feature is implemented. I think it's important

---

