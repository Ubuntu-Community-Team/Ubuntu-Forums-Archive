---
title: "How To Syncronize Files Automatically Across LAN"
date: 2009-11-13
forum: General Help
---

### Post by umechanism on 2009-11-13
I use a password manager (KeePass) to manage all my passwords.  I use the program on four different machines - three on my LAN and one at my office.  The KeePass data file has to be stored locally on each machine so it is a constant chore of keeping the data bases synchronized.  I would like to know if there is an automatic way to keep these files sync'd between XP and Ubuntu machines.  Here's my thought on how it should work:
[LIST]
[*]Each computer has the same KeePass file on it.
[*]I add a password entry in KeePass on my Windows XP machine for a new website I joined.
[*]That entry is saved on the hard drive on the XP machine.
[*]Later, I sit down at my Ubuntu desktop and wish to visit the same site.
[*]The password is not stored on the Ubuntu machine so I must sync it with the XP machine.
[*]I execute a "sync" command and the XP file is copied over (this is where the magic happens).
[*]The sync should work both ways.
[/LIST]

Any thoughts on how to achieve this? (too bad Ubuntu One does not work with XP).

---

### Post by cyberbuff on 2009-11-13
Why don't you try Dropbox? [https://www.dropbox.com/referrals/NTEyNDI5Njk](https://www.dropbox.com/referrals/NTEyNDI5Njk) the dropbox client is available in the repos, too.

---

### Post by umechanism on 2009-11-13
That looks awesome but I'm hesitant about sync'ing with an outside service.  I mean, these are ALL my passwords so I'm concerned about the integrity of the security of the outside services.  I would feel more secure being able to sync behind my LAN and, at times, remotely from my office computer.  Any other options?

---

### Post by Calmor on 2009-11-13
I'd imagine there are a couple options.  There are synchronizing programs for both Windows and Linux.  I've used Toucan in Windows with some success, it allows two-way synchronization of files.  Both Toucan and KeePass can be run as portableApps directly from a USB drive also, adding to its portability... but it doesn't help much for your Ubuntu machines at home.

For Linux, I'm sure there are scripts using rsync that will do what you want.  rsync typically only synchronises one direction, but in your case, you know the file name, so you could run it twice - one from the source to the destination (copying only if newer), then destination to source (again copying only if newer).  This will make sure you've got the latest in both locations.  If you wanted to get fancy and had a machine that's always on, you could set up a cron job to automatically sync at whatever interval you like - hours, days, weeks, etc.

The only issue I can see is how you'll get it out to the one at your office - unless you have internet-accessible network storage on your LAN, synchronization will be somewhat difficult or require manual efforts (like the USB drive).

I don't recommend making your KeePass file accessible via the internet, though, for security reasons... possible exception is if you're running a VPN server.

---

### Post by kjohri on 2009-11-13
Try Unison. 

[http://www.softprayog.in/tutorials/synchronize-files-primer.shtml]("http://www.softprayog.in/tutorials/synchronize-files-primer.shtml")

---

### Post by skotos on 2009-11-13
I have been running Unison 2.57 for over a year to keep 300 GB synchronized among two USB hard disk drives and three workstations and a server.
It is a bit harsh to set up and initialize, but - in the mid and long term - it really works great.
As kjohri has underlined: it is crossplatform indeed. I have recently dismissed my last Windows box, but till that time Unison has worked well with it.

---

### Post by OwnSurname on 2009-11-13
I would recommend rsync; it will be something like:

sudo rsync -av --progress --delete --log-file=<path>/$(date +%Y%m%d).log <path_source> <path_destination>

and you can also do it over ssh:

sudo rsync -av -e ssh --progress --delete --log-file=<path>/$(date +%Y%m%d).log <path_source> <path_destination>

now, what you should keep in mind, is that I suggest the delete option, so if you add a password and then forget to rsync immediately, and the next day you will rsync from another machine, that password will be lost. Of course you can decide not to use the delete option. Man rsync will help you, it's well done.

---

### Post by bilderbuchi on 2009-11-13
re the security concerns with dropbox, there's a similar service called Spideroak, and they use a "zero knowledge privacy" policy, they say they can't look at your data even if they wanted. :-)
[https://spideroak.com/download/referral/5892fe7295103f7296057acb9f8a3250](https://spideroak.com/download/referral/5892fe7295103f7296057acb9f8a3250) (this is a referral, gives both of us +1GB space)

---

### Post by umechanism on 2009-11-13
Thanks for the tip but trust me...they can view any data on their servers should the need arise.  Perhaps they don't make it a standard policy to do so but the means is there.

---

### Post by bilderbuchi on 2009-11-14
yeah well, then they lie in their faq: [https://spideroak.com/faq/is_spideroak_really_zero_knowledge_could_you_read_a_users_data_if_forced_at_gunpoint](https://spideroak.com/faq/is_spideroak_really_zero_knowledge_could_you_read_a_users_data_if_forced_at_gunpoint)

---

