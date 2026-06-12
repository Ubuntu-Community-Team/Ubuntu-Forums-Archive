---
title: "File saved to mapped samba drive empty"
date: 2010-02-24
forum: General Help
---

### Post by OctPhil on 2010-02-24
Hey everyone -

I'm putting this in the General Help thread because I have no idea where the problem occurred.

I use a Windows desktop with Notepad++ to do my PHP scripting.  I use Samba to share my test server's /var/www/ directory, allowing me to map the drive on my Windows machine and use Notepad++ to directly edit files.  This has worked well until last night.

Last night, I was working on a script and was surprised when it suddenly stopped outputting anything, including errors.  It was the end of the day, so I saved the file and went home figuring I'd figure out the problem in the morning when I was fresh.

When I opened Notepad++ today, the file was empty.  I assume that if I had used vim on the server last night, I would have discovered an empty file, instead of the version Notepad++ was showing me (many, many lines of code).  I saw no indication from Notepad++ that the file was empty, or that the file had been changed (usually it will warn you if an open file is changed).

Has anyone seen anything like this happen before?  I'd really like to know what I can do to stop this in the future.

Some basics on my systems:
Windows XP SP3 64 Bit
Notepad++ v5.3.1

Ubuntu 8.04.4 LTS
Samba Version 3.0.28a

Thanks!

---

