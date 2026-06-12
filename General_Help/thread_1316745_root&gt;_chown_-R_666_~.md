---
title: "root&gt; chown -R 666 ~"
date: 2009-11-06
forum: General Help
---

### Post by veracity on 2009-11-06
Hey Guys!

```
root> chown -R 666 ~
```Problem: So i've accidentally gone and changed the permissions of all root commands to make them non executable. Including chown. Darn. What would you guys do in the same situation?
chown won't help me now! e.g. 
root> chown -R 777 ~
root> "Permission denied - chown"

Before you say anything, yes, yes, i shouldn't have been directly logged in as root.

(Why have i go this problem? Well, I'm pretty advanced and was trying to change the permissions of my normal user directory (e.g. /home/whatever) as was having permission problems with firefox, and completely forgot that '~' when logged in as root is the root home directory, not the normal users)

Right now, i'm going to try booting from CD, mounting then changing permissions that way... see if that works.

---

### Post by anaconda on 2009-11-06
> **veracity said:**
> 
Right now, i'm going to try booting from CD, mounting then changing permissions that way... see if that works.

That should work...

---

### Post by veracity on 2009-11-06
Hmm, permission change went well, but starting up didn't. I'll just reinstall (its ok, my home directory is on a separate partition) and do it that way...

*note to self, don't log in a root directly!*

Oh, and as someone else pointed out, i meant CHMOD all the way through that thread, not CHOWN.

---

### Post by Paddy Launch on 2009-11-06
Actually, I don't think you changed the permissions of all root commands at all!

As you correctly say "~" resolves to /root on the system, NOT "/". There are no commands in the /root directory! e.g. "chmod" is located in /bin.

I suggest the reason you were having problems is that you were trying to execute commands whilst actually in a directory for which you had no execute permissions. 

The simple solution would have been to have typed:

$ cd /
$ chmod -R 700 ~

Hope that helps for next time!

---

### Post by QLee on 2009-11-06
> **Paddy Launch]Actually, I don't think you changed the permissions of all root commands at all![/QUOTE]

+1

[QUOTE=veracity said:**
> 
Before you say anything, yes, yes, i shouldn't have been directly logged in as root.

Well, how did you login as root, a default system won't let you do that and, in my opinion *you* should not try defeat system security. The ways that people try to do this often leave a system in somewhat of a mess, it should only be attempted by experts. I advise using sudo as the system was designed to be used, it works well.

---

### Post by grizato on 2009-11-06
Try and get your files out of their and then reinstall your OS(get jaunty?).  Tat's what I did.

---

### Post by veracity on 2009-11-06
Thanks for your replies guys!

i got into root with ```
sudo -s
```It's ok, i've kept my /home directory partition, have removed the old settings kept in that directory and am installing now.

If you want to read more on how i got into this mess, i direct you to [this page]("http://www.linuxquestions.org/questions/linux-software-2/root-chown-r-666-767288/").

Thanks!
Si

---

### Post by QLee on 2009-11-06
[QUOTE=veracity]i got into root with ```
sudo -s
```It's ok, i've kept my /home directory partition, have removed the old settings kept in that directory and am installing now.
[/QUOTE]

Just so you know, that is not logging in as root as you said in your first post. I do understand how it might seem like that.

What that does is give you a root shell and as you have discovered this is, often, not actually what you want. Use sudo for commands and gksu to run a graphical app if you want to run it with root permissions, Ubuntu works very well when used as directed.

---

