---
title: "Want to make a small network storage computer."
date: 2010-07-22
forum: General Help
---

### Post by Captain Smiley Pants on 2010-07-22
Like the title says, I want to use this computer that's been lying around the house for a network storage computer, basically files that other Windows computers can throw at it for backups or just if a user wants to save a file on their share of the network.

I'm wondering if it's possible to create three users, make three folders for them, and then assign those folders with permissions for only those users to see and use (so they wouldn't be able to mess with other people's stuff in their folder).

I'd prefer using Debian, but I'd bet this can be done with Ubuntu as well, right? I mean if it's proven to be easier than using Debian.

ANWAY, the machines connecting to this Linux box will all be using Windows (I have my Win7 netbook, another has a Win7 laptop and the last is an XP desktop) and I'm sure if an Apple user ever needed it (unlikely) it wouldn't have too much of a problem finding this.

I guess you could think of this as acting like a domain controller for the Windows machines, since I'd like to make them user credentials to access their folder share.

Am I going in way over my head here?

---

### Post by bigfatgooglefat on 2010-07-22
If you wanted to do this simply, you could setup your box with an FTP server and create the users with passwords. This gives only the correct user access to the files as well as allowing all the computers access without extra software or effort.  If you wanted to be more advanced you could use Samba for more secure, faster transfers and better features, but I only have a basic Samba setup on my home server, without logins.

---

### Post by Captain Smiley Pants on 2010-07-22
That's actually a good idea. I'm really only familiar with the Filezilla server and it's Windows exclusive, can you recommend me a good FTP client that an idiot like me can understand through it's GUI?

Are you running Ubuntu desktop? Because right now I'm downloading Ubuntu server but if I could use a GUI this machine is capable of running the desktop version just fine, and I could manage FTP from there.

You would still be able to mount this server as a drive on Windows, right? And I'm sure I could set up user accounts and passwords there.

Wow now my head doesn't hurt so bad, I should have thought of this before. Thanks man.

---

### Post by Captain Smiley Pants on 2010-07-22
EDIT: Oh wow this is exactly what I was looking for:

[http://yourubuntulinux.blogspot.com/2007/08/how-to-setup-file-sharing-using-samba.html](http://yourubuntulinux.blogspot.com/2007/08/how-to-setup-file-sharing-using-samba.html)

I'm wondering, is this way too old to work now, something I can only do through Ubuntu, or should I go ahead and install Debian (it's literally ready to go) and give it a shot since Ubuntu is based from Debian anyway?

Good lord I was going to set up so much crap for something so simple, lol.

---

