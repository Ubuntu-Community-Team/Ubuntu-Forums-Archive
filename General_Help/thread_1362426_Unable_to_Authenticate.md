---
title: "Unable to Authenticate"
date: 2009-12-23
forum: General Help
---

### Post by RichardGv on 2009-12-23
**Environment:**
Ubuntu 9.10 Desktop i386
policykit 0.9-4ubuntu1
policykit-1-gnome 0.94-1+1git.270873
policykit-gnome 0.9-1ubuntu3

**Problem:**
In some applications, I simply cannot authenticate to do some task requiring higher permissions. I can use the same password to authenticate with "sudo" and enter Synaptic, but the password does not work in some other places like Ubuntu Tweak, and "Authorizations" in "System" menu -> "Administration".
Any idea where the problem is? Thanks in advance.

Some content in auth.log:
```

Dec 23 16:06:27 richard-desktop polkit-grant-helper-pam[1947]: pam_unix(polkit:auth): conversation failed
Dec 23 16:06:27 richard-desktop polkit-grant-helper-pam[1947]: pam_unix(polkit:auth): auth could not identify password for [richard]
Dec 23 16:07:33 richard-desktop polkit-grant-helper-pam[1963]: pam_unix(polkit:auth): conversation failed
Dec 23 16:07:33 richard-desktop polkit-grant-helper-pam[1963]: pam_unix(polkit:auth): auth could not identify password for [richard]
Dec 23 16:12:06 richard-desktop polkit-grant-helper-pam[2106]: pam_unix(polkit:auth): conversation failed
Dec 23 16:12:06 richard-desktop polkit-grant-helper-pam[2106]: pam_unix(polkit:auth): auth could not identify password for [richard]

```

---

### Post by theDaveTheRave on 2009-12-23
RichardGV,

I'm no guru, but some thoughts, that others may be able to answer and may lead to a solution...

I assume this is a "fresh" system, and you've only created a single user. Hence < sudo > should be working fine, and any occurance of a demand for admin permissions should function.

However...

Is it possible that you can have "limited" admin permissions? to allow a general user to configure most of their system settings, but not change others ?

Also what exactly are you trying to do??

I know from experience that when I try to use the mysql admin gui interface I may make changes in the settings, but because I started it fom my own personal area I do not have "write permissions" to the correct file on the disk for any changes to actually take place. to be able to do this with mysql admin I need to < gksudo mysql-admin >.

Is this possibly somehow similar to your situation (are you trying to edit the settings of an underlying system) ??

if so you may need to call that system with sudo (or gksudo) to write to the config file.

David

---

### Post by reiki on 2009-12-23
There are now several threads about authentication problems in 9.10. I'm having them myself. I can't use the administration -> Users and Groups to manage groups. I get an authentication dialogue, I enter password, the dialogue stays but the text area to enter password disappears and the button that says Authenticate does nothing. If I dismiss the box, the "keys" show up in the notification area, but if I try to manage groups, the list comes up empty as though I am not authenticated.

There is an issue here and it seems to manifest in different ways.

---

### Post by RichardGv on 2009-12-23
In auth.log, I found an extra line when executing polkit-gnome-authorization:
```

Dec 23 22:39:57 richard-desktop polkit-grant-helper-pam[2900]: pam_unix(polkit:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=richard rhost=  user=richard
Dec 23 22:41:02 richard-desktop polkit-grant-helper-pam[2910]: pam_unix(polkit:auth): conversation failed
Dec 23 22:41:02 richard-desktop polkit-grant-helper-pam[2910]: pam_unix(polkit:auth): auth could not identify password for [richard]

```**@theDaveTheRave**

David,

Thanks for your fast reply.
My Ubuntu is actually not a fresh system. I installed it 2 months ago, just after the release of Karmic Koala.
I don't think it's the problem of "limited permission". 2-3 weeks before Ubuntu Tweak works properly, with same password, however all a sudden it stopped working. I've updated my system so many times so I'm not sure which update caused this problem. Today I changed my password, hoping to solve this problem, but unfortunately it did not change anything.
Ubuntu Tweak requires authentication when it changes source.lst or removes packages, and in both situations it fails in authentication with correct password.  polkit-gnome-authorization fails in every authentication as well.
When running these software from a terminal, there's no output.

Thanks,
Richard Grenville

**@reiki**
Thanks. Would you mind giving me a link of bug report with a same/similar problem, if it has been reported right now?
Also, are there any workarounds so far?
Now I started realizing the reason they say Karmic Koala is Vista in Ubuntu... :( I was really puzzled by that PPPoE bug when I just installed a fresh Karmic.

---

### Post by RichardGv on 2009-12-25
I've reported this as a bug: [https://bugs.launchpad.net/ubuntu/+source/policykit-gnome/+bug/500354](https://bugs.launchpad.net/ubuntu/+source/policykit-gnome/+bug/500354)
Some additional information:
> I found if I enter the correct password when the authorization fails, there's no new log in auth.log. If I enter the wrong password, I will get an error like this in auth.log:
```

Dec 25 22:54:29 richard-desktop polkit-grant-helper-pam[2512]: pam_unix(polkit:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=richard rhost=  user=richard

```
There's no terminal output when authorization fails.
It's not related to my password. I tried changing my password, but the problem persists.


---

