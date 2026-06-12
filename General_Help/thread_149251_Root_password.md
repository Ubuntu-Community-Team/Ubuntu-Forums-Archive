---
title: "Root password"
date: 2006-03-23
forum: General Help
---

### Post by brandoncolorado on 2006-03-23
Hello,
As this is the beginners forum I assume I won't get made fun of for asking this.

I changed my password on the about me preferences section.

Now my updates won't update because it says my root password is wrong.  How can I change my root password?

---

### Post by taurus on 2006-03-23
You can use sudo to run root's programs
```

sudo apt-get update
(Type in the password that you use to log into your regular account...)

```
Otherwise, if you REALLY need to assign password for root, do this from a terminal,
```

sudo passwd root

```

---

### Post by brandoncolorado on 2006-03-23
like this?

sudo password root oldpassword newpassword
???

Because I want the automatic updater thing in the top right to work.

---

### Post by taurus on 2006-03-23
Yes...

sudo passwd root <return> <-- means hit Enter key!!!
<password> <return>
<retype same password> <return>

---

### Post by brandoncolorado on 2006-03-23
Here's a stupid question,

If someone is at my computer and I don't log out, could they just go in and sudo my password like this to something else?

---

### Post by aysiu on 2006-03-23
[QUOTE=brandoncolorado]
If someone is at my computer and I don't log out, could they just go in and sudo my password like this to something else?[/QUOTE] Yes. Well, she'd have to know your *sudo* password first in order to change the root password... unless she boot into recovery mode.

The fact of the matter is, though, that anyone who has physical access to your computer *and* a little know-how can compromise just about anything and do just about anything (delete your important files, change your password, etc.).

General physical access security tends to be this by default:

1. Most people don't have physical access to your computer--it's in a house or apartment that only you and family members have a key to.

2. Your family members and friends are generally people you can trust (they're well-intentioned, anyway), so as long as you tell them, "Don't touch this," they'll generally listen.

3. Most people who generally have physical access to your computer don't know enough to do irreparable damage to your important files.

Of course, those three act as general safe-guards, but if you're truly paranoid, you'd lock up your computer (including your CD-ROM drive) in a box that cannot be moved and cannot be opened without your key or combination lock. You'd log out or lock your session every time you left the computer. You'd encrypt all your files. You'd disconnect from the internet every time you weren't using it. In fact, you'd have a separate computer--one that connects to the internet, one that doesn't, with the one that doesn't have all the important file connecting.

---

### Post by brandoncolorado on 2006-03-23
[QUOTE=aysiu]Yes. Well, she'd have to know your *sudo* password first in order to change the root password... unless she boot into recovery mode.

[/QUOTE]


Ok, I think I see my confusion now.

So there is a root password and a sudo password?

Is my sudo password the one that I use to login and the one I changed in the "about me" page?

---

### Post by aysiu on 2006-03-23
[QUOTE=brandoncolorado]Ok, I think I see my confusion now.

So there is a root password and a sudo password?

Is my sudo password the one that I use to login and the one I changed in the "about me" page?[/QUOTE] The default Ubuntu installation has no root account you can log into and no root password.

There's only one account to begin with--one user who can use *sudo* (and the user's password) to temporarily gain root privileges.

Read more here:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

