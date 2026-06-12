---
title: "Logging in as Root?"
date: 2009-09-20
forum: General Help
---

### Post by chrispche on 2009-09-20
I remember how to enable this in Hardy, but I can't find it in Jaunty. How do I enable root login?

I only ask because if I sudo nautilus and delete archive and other files. I want to empty the trash in root.

Cheers.

---

### Post by NoaHall on 2009-09-20
Don't enable it. That's just silly to do :).

If you go to "/", press Ctrl + h, and then go into "/.trash"

---

### Post by chrispche on 2009-09-20
If do want enable it what do I do?

---

### Post by NoaHall on 2009-09-20
Can't tell you that, I'm afraid, it'd be against the forum's rules.

---

### Post by erilidon on 2009-09-20
sudo su - 

or you could always shift delete and then files wont be sent to trash.

---

### Post by m_duck on 2009-09-20
[Ubuntu docs on the root account and sudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jocko on 2009-09-20
[Read the forum rules]("http://ubuntuforums.org/showthread.php?t=885580"), specifically "don't" #12. It is not allowed to post instruction for how to enable root login. This may seem a little bit silly, but there are very good reasons for it. If you really know enough to understand the risks of allowing root login, you should also know how to find the information yourself. But most people who understand the risks would never activate root login.

As you already seem to know how to start a nautilus window as root, it should not be any problem for you to navigate that window to /home/.Trash-0/files and delete the files (you have to press shift+delete, otherwise the files will reappear).

---

### Post by chrispche on 2009-09-20
> **erilidon said:**
> sudo su - 

or you could always shift delete and then files wont be sent to trash.

Oh really? That's useful to know. Thanks.

---

### Post by chrispche on 2009-09-20
> **jocko said:**
> [Read the forum rules]("http://ubuntuforums.org/showthread.php?t=885580"), specifically "don't" #12. It is not allowed to post instruction for how to enable root login. This may seem a little bit silly, but there are very good reasons for it. If you really know enough to understand the risks of allowing root login, you should also know how to find the information yourself. But most people who understand the risks would never activate root login.

As you already seem to know how to start a nautilus window as root, it should not be any problem for you to navigate that window to /home/.Trash-0/files and delete the files (you have to press shift+delete, otherwise the files will reappear).

OK cheers anyway.

---

### Post by CatKiller on 2009-09-21
> **NoaHall said:**
>  If you go to "/", press Ctrl + h, and then go into "/.trash"

> **jocko said:**
> []("http://ubuntuforums.org/showthread.php?t=885580") As you already seem to know how to start a nautilus window as root, it should not be any problem for you to navigate that window to /home/.Trash-0/files and delete the files (you have to press shift+delete, otherwise the files will reappear).

These are both crazy. *The guy already has a Nautilus window as root*. All he needs to do is select File &#8594; Empty Deleted Items and it will delete root's trash. Unless he's using *sudo* instead of *gksudo*, in which case he needs a slap.

To the OP. Don't run nautilus with *sudo*. Don't run any graphical application with *sudo*. Use [**gksudo**]("http://www.psychocats.net/ubuntu/graphicalsudo") instead.

---

### Post by 3rdalbum on 2009-09-21
Run gconf-editor with gksudo, and enable "Allow Delete" in root's Nautilus.

---

### Post by grturner on 2009-09-21
I personally disagree with the no root login rule. There are uses for logging in as root, though not into X. If you know what you're doing logging in as root or using su can be much more convenient than simply sticking sudo before every command. With everything that gnome/kde does, it is alot easier to destroy your system.

---

### Post by t0p on 2009-09-21
> **grturner said:**
> I personally disagree with the no root login rule. There are uses for logging in as root, though not into X. If you know what you're doing logging in as root or using su can be much more convenient than simply sticking sudo before every command. With everything that gnome/kde does, it is alot easier to destroy your system.

You're right, there are good reasons why one might wish to log into a root console.  But there should be no need to tell that user how to do it, regardless of the forum's rule.  If "you know what you're doing", as you put it, then surely you must be acquainted with the **passwd** command.  Or at least know how to read and understand the passwd manpage.  If you know the passwd command, you don't need to ask in these forums how to enable root login.  The sacred rule will be obeyed, and you can use your computer as you see fit.  The end.

---

### Post by snowpine on 2009-09-21
> **grturner said:**
> I personally disagree with the no root login rule. There are uses for logging in as root, though not into X. If you know what you're doing logging in as root or using su can be much more convenient than simply sticking sudo before every command. With everything that gnome/kde does, it is alot easier to destroy your system.

sudo -i

---

### Post by fanglinyong on 2009-09-21
why did you use root account! if you want to run a software need the root authority, you can use ```
sudo
```
it can work correctly!

---

### Post by grturner on 2009-09-21
> **snowpine said:**
> sudo -i

well i found out a new thing about sudo. Thanks

---

### Post by FunkyRes on 2009-09-21
> **t0p said:**
> You're right, there are good reasons why one might wish to log into a root console.  But there should be no need to tell that user how to do it

Bottom line - with sudo, any admin password is a root password.
So a user sets up any kind of way to remote login into their account, and that password gets sniffed, their box is owned.

Or their password is brute forced, their box is owned.

Their are good reasons for a user wanting to disable sudo, and disabling sudo involves setting a password.

Maybe those reasons don't apply to everyone, many have no need or desire to enable remote access. But many do.

Some of us are of the school of thought that sudo should only be used to allow execution of commands that can not spawn a shell.

---

### Post by snowpine on 2009-09-21
> **FunkyRes said:**
> No. There aren't good reasons for it.

Locking the root account and using sudo instead is one of those special features that distinguishes Ubuntu from other Linux distros. I understand you have your reasons to disagree, but you might as well ask Canonical to drop support for the Gnome desktop, or stop using the color brown. ;)

---

### Post by FunkyRes on 2009-09-21
> **snowpine said:**
> Locking the root account and using sudo instead is one of those special features that distinguishes Ubuntu from other Linux distros.

Not really - all linux distros at this point ship with sudo, usually installed by default, it's a simple matter of changing a couple lines and any of those distros become just like ubuntu.

And they all (including ubuntu) have su --command

---

### Post by snowpine on 2009-09-21
> **FunkyRes said:**
> Not really - all linux distros at this point ship with sudo, usually installed by default, it's a simple matter of changing a couple lines and any of those distros become just like ubuntu.

And they all (including ubuntu) have su --command

Believe me, I understand exactly what you are saying, however, as far as I know, Ubuntu is the only distro that actively bans discussion of root login from their official forums. It is a "feature, not a bug" that we are not allowed to discuss it here. You can agree or disagree, but it is seen as a positive in terms of marketing the distro towards a wider audience.

---

### Post by chrispche on 2009-09-21
> **CatKiller said:**
> These are both crazy. *The guy already has a Nautilus window as root*. All he needs to do is select File &#8594; Empty Deleted Items and it will delete root's trash. Unless he's using *sudo* instead of *gksudo*, in which case he needs a slap.

To the OP. Don't run nautilus with *sudo*. Don't run any graphical application with *sudo*. Use [**gksudo**]("http://www.psychocats.net/ubuntu/graphicalsudo") instead.

Hi there in Sunny Southend from Leigh on Sea. ;-)

---

### Post by bodhi.zazen on 2009-09-21
I think this thread has run it's course.

If you wish information on how to use sudo see :

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo") 

For our policies please see :

[Forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=716201")

---

