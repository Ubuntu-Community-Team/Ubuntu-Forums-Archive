---
title: "Acrobat Reader 9 won't open on Ubuntu 9.10"
date: 2010-09-03
forum: General Help
---

### Post by tripwire45 on 2010-09-03
Tech support installed a new computer for me at work yesterday and it's running 64-bit Ubuntu 9.10. I succeeded in installing Adobe Reader 9 (I need to review PDF documents in a number of PDF readers including Adobe as part of my job) but I can't open any PDFs using Reader. I ran "acroread" in the shell and it rendered this output:

```
(acroread:17035): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (1179128842)
```

I've tried Googling all this, but nothing helpful has been forthcoming. Any ideas? Thanks.

-Trip

---

### Post by tripwire45 on 2010-09-17
*bump*

Anyone?

---

### Post by mkvnmtr on 2010-09-17
You might ask your IT dept if your account has permission to install apps.

---

### Post by llamabr on 2010-09-17
I don't know why, but it's expecting a different UID.  Is this a fresh install?  Or did you keep your old home dir?

Sometimes it's just a weirdness in a config file.  Try:

```
rm -rf ~/.adobe/Acrobat
```

Which will wipe out your old config files, and create new ones when you restart acroread

---

### Post by tripwire45 on 2010-09-17
@llamabr Tried your suggestion. Unfortunately, it didn't work out. Same result.

@mkvnmtr I've installed a number of other applications and they've worked out fine (Kile, GIMP, and so on). 

Two things: This is on a 64-bit machine and from what little I can tell from Googling, this error seems to be associated 64-bit but not 32-bit machines.

Also, this computer authenticates to an Active Directory Domain Controller (I work in a mixed Linux/Windows environment).

EDIT: Forgot to say that this is a fresh install. I only backed up the contents of my home directory from the previous install (8.10) so I could retain my data.

---

### Post by gregport on 2010-09-27
FYI... I'm tripwire45's IT guy :)

We are using Likewise Open to authenticate against Active Directory on our Ubuntu 9.10 64 bit desktops.   While googling, I'd found [similar problems]("http://forums.adobe.com/thread/395558") with users authenticating using LDAP and NIS, which were resolved by installing 32 bit versions of the required libraries.    This doesn't appear to be an option as the Likewise lsass library for user lookup is already 32 bit.

Then I found a workaround for the problem in this post:   [http://allaboutfedora.blogspot.com/2009/02/f10-how-to-fix-getpwuidr-failure.html]("http://allaboutfedora.blogspot.com/2009/02/f10-how-to-fix-getpwuidr-failure.html")

So we installed nscd (name service caching daemon, which caches authentication and dns lookups locally):

```

apt get install nscd

```

... and it fixed the problem, Acrobat Reader works!

---

### Post by tripwire45 on 2010-09-27
Thanks, Gregport. It's alive! :D

-Trip

---

### Post by andrewthomas on 2010-09-27
> **gregport said:**
> . and it fixed the problem, Acrobat Reader works!
Could the OP then use the thread tools menu to mark the thread as solved?

---

### Post by senor_smile on 2010-12-07
> **gregport said:**
> FYI... I'm tripwire45's IT guy :)

We are using Likewise Open to authenticate against Active Directory on our Ubuntu 9.10 64 bit desktops.   While googling, I'd found [similar problems]("http://forums.adobe.com/thread/395558") with users authenticating using LDAP and NIS, which were resolved by installing 32 bit versions of the required libraries.    This doesn't appear to be an option as the Likewise lsass library for user lookup is already 32 bit.

Then I found a workaround for the problem in this post:   [http://allaboutfedora.blogspot.com/2009/02/f10-how-to-fix-getpwuidr-failure.html]("http://allaboutfedora.blogspot.com/2009/02/f10-how-to-fix-getpwuidr-failure.html")

So we installed nscd (name service caching daemon, which caches authentication and dns lookups locally):

```

apt get install nscd

```

... and it fixed the problem, Acrobat Reader works!

Thank you very much.  This solved my problem too!

---

