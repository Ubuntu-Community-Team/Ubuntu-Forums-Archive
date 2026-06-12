---
title: "How to fix messed up locale setting"
date: 2010-12-22
forum: General Help
---

### Post by zerubbabel on 2010-12-22
Somehow my language/locale setting has gotten messed up, and I don't know how to fix it. Several applications complain with a message like: "No matching locale found for 'C'."

The contents of /etc/default/locale is:
LANG="en_US.UTF-8"

But when I type "locale" in a terminal, it lists:

LANG=C
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_PAPER="C"
LC_NAME="C"
LC_ADDRESS="C"
LC_TELEPHONE="C"
LC_MEASUREMENT="C"
LC_IDENTIFICATION="C"
LC_ALL=

How can I fix this?

(I'm running 64-bit Ubuntu 10.10 with all updates applied.)

---

### Post by zerubbabel on 2010-12-23
bump...

---

### Post by karthick87 on 2010-12-23
Try,
```
sudo dpkg-reconfigure locales
```

---

### Post by zerubbabel on 2010-12-23
Thank you for responding. I did try that, but it didn't change anything.

---

### Post by karthick87 on 2010-12-23
Try reinstalling the locale package,
```
sudo apt-get install --reinstall locales
```

---

### Post by zerubbabel on 2010-12-23
Alas, still no change after trying that...

---

### Post by karthick87 on 2010-12-23
Try to export it in your ~/.profile if nothing else helps..

---

### Post by zerubbabel on 2010-12-23
I'm not quite sure what you mean by that.

---

### Post by karthick87 on 2010-12-23
Edit  profile and add the following lines at the end of your file,
```
gedit ~/.profile
```
Add this line at the end of your file,
> export LANG="en_US.UTF-8"
Logout and then login back..It may help you,but i am not sure..Just try it...

---

### Post by zerubbabel on 2010-12-23
Ok, tried that, but it still didn't fix the problem. Very odd...

---

### Post by karthick87 on 2010-12-23
Final try,
```
locale-gen en_US.UTF-8
```

---

### Post by zerubbabel on 2010-12-23
Here's the result:

zerubbabel@dz:~$ locale-gen en_US.UTF-8
Generating locales...
  en_US.UTF-8... up-to-date
Generation complete.
zerubbabel@dz:~$ locale
LANG=C
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_PAPER="C"
LC_NAME="C"
LC_ADDRESS="C"
LC_TELEPHONE="C"
LC_MEASUREMENT="C"
LC_IDENTIFICATION="C"
LC_ALL=
zerubbabel@dz:~$

---

### Post by karthick87 on 2010-12-23
Alright..Some other user might help you..Be patient :)

---

### Post by zigzag77 on 2010-12-23
A quick workaround for a single user / single shell session would be to execute:

```
# locale -a
```to see, which locales are available on your system. Then set LC_ALL for your current shell.

```
export LC_ALL=en_US.UTF-8
```I would check whether the whole system is affected, or only a specific user account.
Try adding a new user and check the language settings of the new user.

---

### Post by zigzag77 on 2010-12-23
Are you using Gnome?

System --> Administration --> Language Support

is probably be the right place to change this setting system-wide.

---

### Post by zerubbabel on 2010-12-23
Yes, I've tried resetting it there too, but to no avail. It still reverts to "LANG=C"

It is bizarre. I've tried putting "export LANG=en_US.UTF-8" as the last line in ~/.profile, but still when I login and type "locale" in a terminal, it says LANG=C.

---

### Post by zigzag77 on 2010-12-23
Try** LC_ALL**, not **LANG**.

If .profile does not work, try [B].bashrc
[/B]
Did you change any of the global scripts like /etc/profile or /etc/bash.bashrc ?

Did you try a fresh different login user?
Is only the GNOME desktop affected? 
What happens to locale settings if you login on a virtual console, e.g.  Ctrl-Alt-F1 ... F7

-------------------------
You could also try to temporarily move all dot-files and directories out of your home directory:

```
$ cd
$ mkdir SAVE-DOTS
$ mv .??* SAVE-DOTS/
```Then logout and login again.

If it does not change anything, move everything back

```
$ cd
$ mv SAVE-DOTS/.??* .
```

---

### Post by zerubbabel on 2010-12-23
Setting LC_ALL=en_US.UTF-8 in either .profile or .bashrc makes no difference.

Moving all the dot-files made no difference in the locale.

In a virtual console, the locale is correct: LANG=en_US.UTF-8

When logging in to a new user account, the locale is correct.

---

### Post by zigzag77 on 2010-12-24
Your wrote:
> When logging in to a new user account, the locale is correct.

Then it must be a user specific configuration issue just for your account. In my understanding all local config settings should reside in some dot-file or dot-directory. I am not a Gnome expert, but I would expect to find all user specific local Gnome settings in some of the .g* directories.

Try the following steps:

[LIST=1]
[*]End the graphical desktop session
[*]Login on a virtual ASCII console
[*]Move the dot-files and dot-directories, especially .g*
[*]Login on the graphical desktop
[*]Now the default deskop should appear with the default language settings.
[*]After log out you should find the new default Gnome config in new config files/directories
[*]Now you need to find the difference that affects your locale setting.
[/LIST]
**Is some Gnome expert reading this** and can enlighten us, where user specific Gnome settings are stored? (In ASCII files or in a database?)

---

### Post by zigzag77 on 2010-12-24
Try to find a config line with LANG or LOCALE setting of "C"
```

# find .gconf/desktop -type f -size +0 -print | xargs grep C
# find .gconf/desktop -type f -size +0 -print | xargs egrep -i 'locale|lang'

If grep does not find anything, you might need to read all config lines by yourself:
# find .gconf/desktop -type f -size +0 -print | xargs more


```

But I am not sure whether .gconf/desktop is the correct config directory for the user specific locale setting.

---

### Post by zerubbabel on 2010-12-24
Well, none of those searches yields anything, but I really appreciate your suggestions. I'll have to try the steps in your previous post later, when I have the time.

Anyone else have any ideas?

---

### Post by zerubbabel on 2010-12-28
Putting "export LANG=en_US.UTF-8" in ~/.gnomerc solved my problem.

---

### Post by karthick87 on 2010-12-28
Glad it worked :) Mark it as [COLOR=Red][SOVED][/COLOR]

---

