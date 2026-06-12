---
title: "Two different systems using same /home"
date: 2010-04-28
forum: General Help
---

### Post by TheNessus on 2010-04-28
Possible?

I currently use Ubuntu with both lxde and KDE. I wish to install on a seperate partition a #!, the latest one, that is Debian-based. And I want them to share the same /home. Don't know if it's possible...

---

### Post by Leppie on 2010-04-28
yes, it's possible. i had xubuntu and #! share the same home partition.

---

### Post by bodhi.zazen on 2010-04-28
It is possible and works best if you use a unique user name for each OS

If you want to use the same user name it usually works, but sometimes you will have problems either with permissions or conflicting config files.

I suggest you simply use a shared data partition.

---

### Post by TheNessus on 2010-04-28
> **bodhi.zazen said:**
> It is possible and works best if you use a unique user name for each OS

If you want to use the same user name it usually works, but sometimes you will have problems either with permissions or conflicting config files.

I suggest you simply use a shared data partition.

Thank you :) and to Leppie too.

Problem is my Home folder *is* my data partition, but I might work around that and fix things. Different user names is a good idea.

---

### Post by Leppie on 2010-04-28
which windows manager are you going to use in crunch?
normally it uses openbox, which doesn't have a lot of config files in common with lxde and kde...
or just use it with lxde.

---

### Post by TheNessus on 2010-04-28
> **Leppie said:**
> which windows manager are you going to use in crunch?
normally it uses openbox, which doesn't have a lot of config files in common with lxde and kde...
or just use it with lxde.

Mighty good question. I figure openbox as well.

---

### Post by bodhi.zazen on 2010-04-28
> **Leppie said:**
> which windows manager are you going to use in crunch?
normally it uses openbox, which doesn't have a lot of config files in common with lxde and kde...
or just use it with lxde.

Well, LXDE does use openbox ...

---

### Post by Leppie on 2010-04-28
> **bodhi.zazen said:**
> Well, LXDE does use openbox ...
so what does this change? that the config files are already there?

---

### Post by srs5694 on 2010-04-28
First, I'd like to flag a potential area of miscommunication: /home refers to a specific directory on a Linux system. On most Linux installations, including normal Ubuntu installations, /home contains at least one user subdirectory, such as /home/ebrown. If the system has multiple users, normally each one gets a different subdirectory, such as /home/ebrown, /home/jsmith, and /home/kjones. These directories are the individual users' home directories (some people capitalize "home" in this context, as in "Home directories"). The distinction between *the* /home directory and users' *individual* home directories is very important, especially for this discussion.

Many systems have /home on a separate partition, in which case users' home directories are directories on this partition's root -- so if /home is /dev/sda5, /home/ebrown is the ebrown directory on /dev/sda5. Another possible configuration is to create /home/ebrown as its own partition, whether or not there are other users and whether or not /home is its own partition. (So /dev/sda6 could be /home/ebrown and /dev/sda5 could be /home, with /home/jsmith and /home/kjones.) It's critical that you understand how your system is configured along these lines for purposes of this discussion.

One more point: Users' home directories are conventionally named after usernames, so /home/ebrown belongs to a user whose username is ebrown. This isn't necessary, though; ebrown's home directory could be /home/e, /home/eb, /home/smelly72, or whatever. It could also reside somewhere odd, as in /home/e/ebrown or /foo. This can be configured via the usermod command, as in "usermod -d /home/smelly72 ebrown" to change ebrown's home directory to /home/smelly72.

If you've got /home on its own partition, you can certainly use different usernames in your different installations, or even the same username but different home directories, to provide separate sets of configuration files in the two installations. If you're careful to give your users the same user ID (UID) numbers in both installations, you can share files pretty easily in this way, without risking one installation doing something weird to another's user configuration files. If you've got /home/yourusername on its own partition, you can do the same thing, but you'll need to adjust the mount point and restrict how many files you create in /home/otherusername on your second installation. In either case, you can also use symbolic links to simplify access -- for instance, /home/smelly72/ebrown could link to /home/ebrown, to enable slightly easier access to your regular files in /home/ebrown when you log into the account that uses the /home/smelly72 home directory.

---

