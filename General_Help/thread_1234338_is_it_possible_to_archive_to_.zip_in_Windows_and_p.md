---
title: "is it possible to archive to .zip in Windows and preserve Unix file permissions?"
date: 2009-08-07
forum: General Help
---

### Post by zo3adams on 2009-08-07
Greetings,

I'm trying to find a procedure to create a zip file in Windows and preserve Unix file permissions on the files...

I have a set of bash scripts to be archived, originally created on a linux machine with file permissions 755. Some people in our group are using Windows and if they archive the files then pass them back to a Linux user, the file permissions are lost, unzip creates files with 644 permission, so an additional step is needed to execute them.  No problem if the archival is preformed on linux, but not all members of our group are comfortable with it.

Situation is the same whether using the default XP "Send to compressed", or something like winRar or 7-zip,  I can't find any option that will respect / preserve the UNIX permissions, anyone know of a way?

---

### Post by dcstar on 2009-08-07
> **zo3adams said:**
> Greetings,

I'm trying to find a procedure to create a zip file in Windows and preserve Unix file permissions on the files...

I have a set of bash scripts to be archived, originally created on a linux machine with file permissions 755. Some people in our group are using Windows and if they archive the files then pass them back to a Linux user, the file permissions are lost, unzip creates files with 644 permission, so an additional step is needed to execute them.  No problem if the archival is preformed on linux, but not all members of our group are comfortable with it.

Situation is the same whether using the default XP "Send to compressed", or something like winRar or 7-zip,  I can't find any option that will respect / preserve the UNIX permissions, anyone know of a way?

Files on a Windows filesystem can have no Linux credentials - you lose them the instant the files exist on a foreign filesystem which has its own credentials (and vice versa).

You can preserve Linux credentials inside a **tar** archive, but the archive file itself will have whatever credentials the filesystem is exists on supports.

---

### Post by zo3adams on 2009-08-10
Thanks for the info David!

If it's of any use to people finidng this thread in the future, we ended up using the first of the two work-arounds below:

> when decompressing on the linux machine, after unzip use chmod to restore execute bit. Created the two line shell script to make it seamless, ideally we would preserve the exact file permissions and this can't be done, but at least scripts can execute again with:
unzip NAME.zip
chmod +x *.sh

> install cygwin and have windows users zip from the cygwin terminal

---

