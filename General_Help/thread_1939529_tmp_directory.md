---
title: "/tmp directory"
date: 2012-03-11
forum: General Help
---

### Post by hwttdz on 2012-03-11
Does the operating system ever clean up files that are put in the /tmp directory? If so when does this happen?  Is it a safe assumption that there is a directory named /tmp that is writable by any user?  Is there such a thing as a per user tmp directory?

---

### Post by houseworkshy on 2012-03-11
Don't know the full answer but I'm sure that not all of tmp is cleared anyway.  The reason being that if one installs bleachbit, which is a junk cleaner similar to ccleaner for windows, then don't use it for a while, when one does run it ( even after several reboots ) it clears things from tmp which have obviously persisted since bleachbits last use.

---

### Post by pqwoerituytrueiwoq on 2012-03-11
pretty sure /tmp is emptied at shut down
shut down and boot a live cd and see if anything is in there
my /tmp is a ram disk so checking it rather pointless here

---

### Post by ankman on 2012-03-11
> **hwttdz said:**
> Does the operating system ever clean up files that are put in the /tmp directory? If so when does this happen?  Is it a safe assumption that there is a directory named /tmp that is writable by any user?  Is there such a thing as a per user tmp directory?

I guess at least Debian has an option implemented to clear /tmp but I couldn't find one in Ubuntu.

Yes, /tmp is writeable worldwide, and there is no other directory for every user. But files can get permissions there that not everybody can write or even read them.

For example I find a directory /tmp/orbit-root which I cannot read or write (root can of course). But a file /tmp/orbit-username (if my name was "username") I can read and write.

What this script is supposed to do is checking if files or directories in /tmp are 8 days or older (by default) and clears those files matching, leaving others untouched.

In /etc/default/rcS there is TMPTIME=8 here (although not working) where you can set up how old files shall be before they get deleted.

---

### Post by VH-BIL on 2012-03-11
Applications that use the tmp directory should remove the files after using them or when the application is closed.

---

### Post by dcstar on 2012-03-12
> **ankman said:**
> I guess at least Debian has an option implemented to clear /tmp but I couldn't find one in Ubuntu.

Yes, /tmp is writeable worldwide, and there is no other directory for every user. But files can get permissions there that not everybody can write or even read them.
...........

/tmp is set up to be writeable by all but only readable by the user that does the writing.

---

### Post by Paqman on 2012-03-12
> **pqwoerituytrueiwoq said:**
> pretty sure /tmp is emptied at shut down


It's actually at boot, but the effect is the same.

---

### Post by WorMzy on 2012-03-12
Create a tmpfs entry in fstab if you want it to be truly temporary.

```
tmpfs /tmp tmpfs nodev,nosuid 0 0
```

I'm surprised that Ubuntu/upstart doesn't do that by default tbh.

---

### Post by hwttdz on 2012-03-13
I should have been more specific in saying that I'm writing a program that needs to write a temporary file.  In a spectacular example of what not to do I am not checking if such a directory exists or if it is readable or if the file name I want to use exists or if it is readable (these all seem reasonably likely to be true).  I am cleaning up after myself though.  I feel like I should get partial credit for that.  

In any case I think it's clear that I (one) should check for these things, but they're all likely to work out even without checking.

---

### Post by dcstar on 2012-03-14
> **WorMzy said:**
> Create a tmpfs entry in fstab if you want it to be truly temporary.

```
tmpfs /tmp tmpfs nodev,nosuid 0 0
```

I'm surprised that Ubuntu/upstart doesn't do that by default tbh.

Use valuable RAM for /tmp - which can require sufficient space to match the contents of a DVD if you want to copy one of them - are you **insane**?

---

### Post by WorMzy on 2012-03-14
Only legally. :-\"

It's been common for /tmp to be tmpfs for a while now though, Ubuntu's aparently just behind the times.

[https://en.wikipedia.org/wiki/Tmpfs#Semantics](https://en.wikipedia.org/wiki/Tmpfs#Semantics)

---

### Post by dcstar on 2012-03-14
> **WorMzy said:**
> Only legally. :-\"

It's been common for /tmp to be tmpfs for a while now though, Ubuntu's aparently just behind the times.

[https://en.wikipedia.org/wiki/Tmpfs#Semantics](https://en.wikipedia.org/wiki/Tmpfs#Semantics)

Until things like the CD/DVD copying stop using /tmp (and where else would they write temporary files?) then using tmpfs will only cause problems.

Many other apps assume the /tmp has more than enough space for their purposes, telling people to use tmpfs in Ubuntu without any caveats is irresponsible as it will directly lead to problems with many common uses.

---

### Post by WorMzy on 2012-03-14
I sincerely doubt it.

The rest of the Linux world seems to coping fine with a tmpfs /tmp. If your CD/DVD ripper is creating a huge amount of temporary files, I recommend that you look into finding a better CD/DVD ripper.

dd works fine for me.

---

