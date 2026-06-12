---
title: "Unison - Archive locked but no lock file"
date: 2011-05-19
forum: General Help
---

### Post by iclestu on 2011-05-19
Hey folks.

Wonder if you can help with this one. I use Unison to synch files between my netbook and desktop. Have done for a while without issue. I hadnt used it for a while and now, when doing so, i cannot get it to work.

I get the following error message:

```

Looking for changes
Fatal error: Warning: the archives are locked.  
If no other instance of unison is running, the locks should be removed.
The file /home/stewart/.unison/lk09e2944d6161a81c9630d960bc290077 on host stewart-desktop should be deleted
Please delete lock files as appropriate and try again.
```No such file exists!

This comes up AFTER connecting through ssh (password, etc)

I get this message regardless of whether i run unison from command line or from gui and also when doing ```
sudo unison netbooksynch.prf
```It works fine for a different profile which synchs to a pendrive.

I have tried:
a: creating the above file as a blank text document, running unison then deleting it and rerunning. (the same error came up with the file name repeated twice whilst my file was there but no change on deletion)
b: deleting all the archive files (nothing - just went to same error message)
c: temporarily removing the entire .unison/ directory and replacing it with an entirely blank one and trying to set up a new default profile to access my netbook. (again, just the same error). 

I have used this before many many times to synch files to the same netbook! i dont know why it suddenly stopped working.

Anyone got any ideas?

---

### Post by iclestu on 2011-05-24
Bump....

anyone got any ideas?

---

### Post by iclestu on 2011-05-29
Ok - this was nothing to do with Unison.

I had set up the prf file using the ip address of the netbook rather than name (which is ok as my router assigns persistant ip's) but having reset the router software my desktop had ended up with the ip that my netbook had previously held. Unison was trying to synch to the same directory therefore the lockfile was being created at runtime and deleted on termination hence why I could not find it.

My fault entirely. Unison's only fault is a bit of an ambiguous error message.

Have posted resolution in case anyone else finds themselves in the same boat.

---

