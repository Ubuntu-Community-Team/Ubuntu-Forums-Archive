---
title: "Verifying a user's permissions."
date: 2010-11-20
forum: General Help
---

### Post by Side.Step.Society on 2010-11-20
Hi all,

I just started dual booting Ubuntu 10.10 on my mini 10v with OS X a couple days ago, so I'm still pretty new to Linux.

But anyhow, I was attempting to change my User ID number so I could access the files in my User folder on my OS X partition.  So, I tried entering the following commands:

sudo usermod -u 501 yourusername
sudo chown -R 501 /home/yourusername

Of course, smart me should've realized I should've been logged out and on a different administrative account to do this.  But I didn't, and I believe the second command didn't work.  So, whatever, I thought I'd try logging out and logging in as root.

So, I logged out, tried logging in as root, and of course, no dice because I didn't know the password.  So then I tried logging onto my account and upon logging in, I got two errors.  One was about ".ICEauthority" and I didn't keep track of what the other one was.

Great.  So I did a quick google for the error, then tried entering these codes:

$ sudo chown user:user home/user/.ICEauthority
$ sudo chmod 664 /home/user/.ICEautority
$ exit

$ sudo chown user:user /home/user/.ICEauthority
$ sudo chmod 644 /home/user/.ICEauthority
$ sudo chown -R /home/user
$ exit

And again, I think the last one didn't work.  So, I looked up how to login as root, changed the password and logged in as root successfully.  Then, whilst in root, I entered:

/usr/sbin/usermod -u 12345 joeuser
/usr/bin/find / -user 701 -print | xargs -t chown joeuser
/usr/bin/find / -user 701 -exec chown joeuser {} \;

Upon entering those, I logged out and logged back into my account and everything was a complete success.  No error messages anywheres AND I could access the files in my Mac user folder.

So, here's my question.  How can I make sure I have all the right permissions I need?  Or do I already have the all of the permissions I had before changing my user id?

Did those last three lines of code I entered "override" all of the codes I had entered previously?
I just want to make sure verify I have all the correct permissions necessary so I don't run into any issues later on.

Thanks in advance,
Chris.

---

### Post by kidders on 2010-11-21
Hi there,

> **Side.Step.Society said:**
> So, I looked up how to login as root, changed the password and logged in as root successfully.Just for future reference, creating a temporary unprivileged account is preferable to logging in as root. Enabling root login compromises your box's security.

> **Side.Step.Society said:**
> How can I make sure I have all the right permissions I need?The first thing worth checking is that everything in your home directory belongs to you. The easiest way to be sure is to re-run ...```
sudo chown -R 501 ~
```Secondly, since your old UID may have owned files stored elsewhere ...```
sudo find / -nouser 2> /dev/null
```This'll give your disks a good thrashing, but should produce no output. It's worth mentioning that you should never execute anything as root unless you're sure you know what it does, so if in doubt ... :P

Anyhow, I hope that helps.

---

### Post by Side.Step.Society on 2010-11-21
I was actually thinking about making a new, unprivileged account, but then I thought I would just kill two birds with one stone and change the ownership whilst I was still in the root account.  I'm not too worried about security right now, but I'll definitely keep that tip in mind for the future.

Upon entering that first code in terminal, I get the following error:

"chown: cannot access `/home/chris/.gvfs': Permission denied"

Any ideas on that?

The second command showed me:

/var/cache/gdm/chris/face

And then a load of files on my Mac partition, which I assume would be expected.

Thanks a ton for your help! :D

---

### Post by kidders on 2010-11-21
> **Side.Step.Society said:**
> "chown: cannot access `/home/chris/.gvfs': Permission denied"If that's the only error, you're doing ok. Check to see who owns it at the moment ... chown-ing it *might* be unnecessary.

It's bizarre that root can't access that file though. Just in case, I assume your X server wasn't running at the time, right?

> **Side.Step.Society said:**
> /var/cache/gdm/chris/faceYou might as well run **sudo chown chris /var/cache/gdm/chris/face** just so everything's clean & neat.

Incidentally, you're right ... The unrecognised UIDs on your Mac partition are to be expected.

---

### Post by Side.Step.Society on 2010-11-21
Regarding that .gvfs file, would that be an invisible file?  I know in OS X files starting with a period are hidden.  I imagine the same goes for Linux, right?  How would one check the owner without showing hidden files?

Also, what do you mean by X server?

Once again, thank you very much!

---

### Post by WorMzy on 2010-11-21
May I recommend using ```
sudo -i
``` next time you need to execute successive commands as root, rather than setting a password for the root account then logging in as it.

May I also recommend that, once you've finished, disable the root account again with
```
sudo usermod -p '!' root
``` with Ubuntu, the root account really doesn't need to be enabled, and only serves as a security risk.

---

