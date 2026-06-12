---
title: "Help!  Thunderbird hangs"
date: 2011-07-15
forum: General Help
---

### Post by msp3k on 2011-07-15
Hi all,

I'm getting desperate.  I backed up my user directory, did a fresh install of 11.04 (old version was 9.10), and then restored my user directory.  (User account information, UID, GID, and file permissions have remained the same.)

Thunderbird hangs w/:
futex(0x7f91c3b02640, FUTEX_WAIT_PRIVATE, 2, NULL) = ? ERESTARTSYS (To be restarted)

The Thunderbird window never appears.

I have tried removing ~/.thunderbird/ and ~/.mozilla-thunderbird/, to no avail.

I have tried creating a new dummy account and running Thunderbird -- that works okay.  So this has to be something in my user home area, I just can't figure out what.

While I can wipe my home area and start over, I have about 60 other users who are going to face this same issue when I upgrade their machines, so I am desperate to resolve the issue some other way.

---

### Post by msp3k on 2011-07-15
I have filed a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/811063](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/811063)

---

### Post by Habitual on 2011-07-15
> **msp3k said:**
> ...I have tried removing ~/.thunderbird/ and ...I have tried creating a new dummy account and running Thunderbird -- that works okay...

I'm confused, removing .thunderbird is essentially creating a dummy account.

Have you tried starting Tbird in safe-mode? Terminal > 
```
thunderbird --safe-mode
``` 

What Tbird version?
```
thunderbird --version
```

You could start with Profile Manager, make a new profile and copy the broken account to the new...?

---

### Post by msp3k on 2011-07-15
Version 3.1.10

```
thunderbird -safe-mode
``` hangs on the futex() call

```
thunderbird -ProfileManager
``` also hangs on the futex() call

---

### Post by msp3k on 2011-07-15
I have also tried -migration, -no-remote, and -options, just to see if I can get thunderbird to do anything other than hang.

---

### Post by Habitual on 2011-07-15
Replace a copy of the b0rked .thunderbird to your home directory but name it something else. say .thunderbird.1st

Fire up Tbird and create a new profile manually using the same settings as the b0rked account. **DO NOT Retrieve any email or connect to the mail server** after setting up the new account.

(Try to get back to the state where "tried creating a new dummy account and running Thunderbird -- that works okay")

Shut down| exit Tbird.

Terminal >
```
cd .thunderbird.1st
find `pwd` -iname "*\.default" -type d

```

my default directory looks like this, yours will be differently named (but still have ".default" in it's directory name)

/home/jj/.thunderbird/rkgkaw42.default/
I illustrate yours with xxxxxxxx.default here...
Still in terminal...
```

cd .thunderbird.1st
cd xxxxxxxx.default
nautilus .
```

Press Ctrl+H to show hidden files and directories.
Press Ctrl+A to highlight all.
Press Ctrl+C to copy all.
Navigate to your home/.thunderbird directory and find the .default directory that is unique for your system and open it in nautilus.

Press Ctrl+V to paste contents into it. Overwrite/merge all.

Close nautilus.
fire up Thunderbird. see what happens.

Please let us know...

---

### Post by msp3k on 2011-07-18
No dice.  Same behavior.

On an additional note.  If I delete ~/.thunderbird all together, and let Thunderbird re-create it, the re-created ~/.thunderbird directory does not contain any *.default sub-directory.  It only contains a Crash\ Reports directory.

I notice that there is an updated release of Thunderbird available.  I will upgrade and see what that does.

---

### Post by msp3k on 2011-07-18
Nope.  Updated thunderbird (3.1.11) still has a problem.

---

### Post by msp3k on 2011-07-18
New information:
1) New local user accounts: work
2) Existing LDAP user accounts: don't work
3) New LDAP user accounts (with home areas created directly from /etc/skel/): don't work

---

### Post by msp3k on 2011-07-18
LDAP information:
LDAP server is running Ubuntu 9.10
LDAP service is via slapd 2.4.18-0ubuntu1.2

---

### Post by msp3k on 2011-07-18
Confirmed that this is a problem between Thunderbird and LDAP by reproducing it on another machine.

Created a local user via useradd: works

Deleted local user

Created LDAP user w/ same UID/GID/HOME_DIR (not NFS or autofs mounted): doesn't work

---

### Post by msp3k on 2011-07-18
I finally found this post:
[http://www.funkynerd.com/thunderbird-segfault-with-ldap-user/]("http://www.funkynerd.com/thunderbird-segfault-with-ldap-user/")

A workaround is to install the nscd package:

```
sudo apt-get install nscd
```

Then Thunderbird will operate normally.

I still do not understand why Thunderbird would not run for LDAP users.  And since many organizations rely on LDAP for user authentication, I would still consider this a serious bug that warrants investigation.

---

### Post by msp3k on 2011-07-18
Update: Not Solved

Thunderbird hangs indefinitely while trying to look up hostnames.

---

### Post by msp3k on 2011-07-19
Received this reply from Mozillazine:
[http://forums.mozillazine.org/viewtopic.php?f=39&t=2256323&p=11039807#p11039807]("http://forums.mozillazine.org/viewtopic.php?f=39&t=2256323&p=11039807#p11039807")

I was on the right track by installing nscd, but there's more to it than that.  The package to install is libnss-ldapd, which will automatically include nscd and one other dependency.

Thunderbird has been tested and now appears to work.

---

