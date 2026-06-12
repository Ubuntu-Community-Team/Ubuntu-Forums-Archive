---
title: "$PATH not matching /etc/environment"
date: 2011-10-05
forum: General Help
---

### Post by Ranko Kohime on 2011-10-05
Running Xubuntu 11.04 Natty Narwhal.

Let me first start off with this: I've Googled this issue, and nothing I came across has helped, as .bashrc & .bash_profile DO NOT accomplish what I'm trying to do, which is get the GUI to recognize the path, not the CLI.

I am experiencing a problem with my $PATH.  Specifically, /etc/environment lists all of the paths that I want to have in my $PATH, like so:

```
ranko@yggdrasil:~$ cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

However, my $PATH ends up being this:

```
ranko@yggdrasil:~$ echo $PATH
/usr/local/bin:/usr/bin:/bin
```

And I can't figure out why.  This behavior is breaking many of the shortcuts in the Apps menu, which as created by the package manager have no paths, just the command of the executable.

I am under the impression that /etc/environment sets the initial paths system-wide on boot, are there any other system-wide areas that define the $PATH as it relates to the GUI?

---

### Post by hwttdz on 2011-10-05
I'm pretty sure the .bashrc (and probably .profile, and .bash_profile) affect this as well.  I'd check that in these files when you add something to the path you aren't resetting the path, i.e. use
export PATH="newstuff:$PATH"
not
export PATH="newstuff"

---

### Post by mcduck on 2011-10-06
If I remember right, ~/.profile is the one that gets executed when you log in, while ~/.bashrc and ~/.bash_profle only affect Bash shell (meaning that they get executed when you open a terminal).

Keep in mind that only the *user shell* is Bash, the system shell is Dash. So all the scripts executed when you log in to desktop, as well as all the system scripts, are executed using Dash.

---

### Post by Ranko Kohime on 2011-10-06
> **hwttdz said:**
> I'm pretty sure the .bashrc (and probably .profile, and .bash_profile) affect this as well.  I'd check that in these files when you add something to the path you aren't resetting the path, i.e. use
export PATH="newstuff:$PATH"
not
export PATH="newstuff"
That's what I have done, adding "newpath:$PATH".  However, it does not seem to carry over to the GUI from .bashrc and .bash_profile.

At the moment, I've deleted the latter, (which did not exist prior to my creating it), and reverted the former to a saved version.

I have not edited .profile at all, and it's sole default command to add ~/bin has no effect on the GUI.

ETC: ~/bin is not being referenced by the GUI, and any shortcuts to an executable there (even with executable bit set) don't start unless they have the full path, so I'm guessing that whatever is breaking the paths from /etc/environment is also breaking ~/.profile.

---

### Post by Ranko Kohime on 2011-10-06
Around the same time I noticed the issue of the $PATH, I had another sign of something off: Every time I open a new terminal window I get this message:

```
non-network local connections being added to access control list
```
Anything I Google seems not to be related to my present issue.

---

