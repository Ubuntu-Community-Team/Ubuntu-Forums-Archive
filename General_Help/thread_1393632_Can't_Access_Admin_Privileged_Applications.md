---
title: "Can't Access Admin Privileged Applications"
date: 2010-01-29
forum: General Help
---

### Post by Bushflyer on 2010-01-29
Whenever I try to do anything that requires administrative permissions, including Synaptic, the Update Manager, or installing something on the Software Center, the "Starting Administrative Application" task comes up on the window list, but then the window does not come up and whatever action was supposed to be taken does not happen; no error messages, nothing.  Also, whenever I use su or sudo in the command prompt, nothing shows up when I type my password; then when I hit Enter, it gives me an authentication error.

EDIT:  It seems that the "Add/Remove Applications" program as well as the Software center do not have this problem.  Synaptic and the Updates Manager, however, still do not work.

---

### Post by quixote on 2010-01-31
Your "sudoers" file may be corrupted.  That tells the system who has admin privileges.  The following is taken from the documentation on the [ubuntu wiki]("https://help.ubuntu.com/community/Sudoers").  There's only one way to edit that file: ```
sudo visudo
```

That'll bring up a file that looks like this: ```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
**root    ALL=(ALL) ALL**

# Members of the admin group may gain root privileges
**%admin ALL=(ALL) ALL
```**

Most of the lines are comments.  The two lines in bold are what you need.  If either is missing, carefully type it in.  (No typos!)  The editor it uses is just a command line thingy known as "nano".  No mouse, only arrow keys.  Backspace works, I'm not sure "delete" does.  when you're ready to save, hit ctrl-x, and "y" for yes.

If you look at it, and there doesn't seem to be anything wrong, then the trouble may be that your user (ie whatever you log in as) somehow got disconnected from the admin group. To add yourself back in:```
# sudo usermod -G -a admin <username>
```  Or, I think you can do it via the menu: System > Admininistration > Users and Groups, unlock, go to Manage Groups button, and make sure you're in the group "admin."

---

### Post by Bushflyer on 2010-02-12
The "sudoers" file is just fine.

However, I can't tell if I've been disconnected from the admin group because I can't unlock the menu (requires admin privileges) and I can't use sudo.

Also, sudo seems to be acting differently.  Instead of giving me an authentication error, it says, "must be setuid root".

---

### Post by jken146 on 2010-02-12
Typing ```
groups
``` will list the groups you're in.

---

### Post by jken146 on 2010-02-12
But hang on, if you could do **sudo visudo** then you must be a sudoer, and therefore a member of the group **admin** (unless your username is specified in sudoers). But in any case, if you can sudo at the command line, why can't you do things like run Synaptic?

Open a terminal and type ```
gksudo synaptic
``` and see if you get any error messages.

---

### Post by jken146 on 2010-02-12
> **Bushflyer said:**
> Also, sudo seems to be acting differently.  Instead of giving me an authentication error, it says, "must be setuid root".

Gah, I've just noticed this line. If you could post the contents of /etc/sudoers that might shed some light on the problem.

---

### Post by Bushflyer on 2010-02-13
I used the recovery console to do the visudo operation.  I can only do stuff requiring sudo from there.


As to gksudo synaptic, it just sits there for a moment, makes a blank new line, then puts a command prompt line in.  No error messages or anything else appears.

Now as to the sudoers file:

```

# /etc/sudoers
#
# This file must be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults         env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root      ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down.)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may not gain root privileges
%admin ALL=(ALL) ALL

```

Also, I found an old post with someone saying that you should never chown the /usr/ directory to anything other than root, or sudo would give this error.  However, when I booted into the recovery console, typed in "chown -Rv root /usr/", and rebooted normally, sudo still didn't work.

---

### Post by jken146 on 2010-02-13
The last line seems ok, but the comment in the penultimate line is strange. :s

---

### Post by Bushflyer on 2010-02-13
Well, that's the comment that was there.
Unless there's a default sudoers file available online, I don't know what to think of it.

UPDATE: When trying to do things on the Software Center and Synaptic, the authentication dialog box momentarily shows up, wagging side to side rapidly and showing "Authentication failure" and then disappears after 1-2 seconds.

---

### Post by Bushflyer on 2010-02-21
Umm...this is still a problem.  The comment in the sudoers file was a misspelling when I retyped it into the Vista laptop I posted it on.  I can't do anything that requires sudo without going to the recovery console.  Interestingly, I can use an installation of Webmin that I set up prior to having these problems.  This is the only way that I've been able to do anything whatsoever with packages, including updates.  Also, the GUI authentication dialog box is still acting weird.

By the way, does anyone know how to run GNOME from the recovery console so that I can use stuff like Network Administration as root?

---

### Post by quixote on 2010-02-21
To add yourself back to the admin group from the recovery console, it's the same command, but without sudo since you're already root:```
usermod -G -a admin <username>
``` It's interesting that webmin will work even when your user no longer has sudo privileges.  Bit disturbing, actually.  I'd use that as sparingly as possible, since it *shouldn't* be working, and god only knows what it's breaking as it goes about its business!

Be super-careful running from a graphical interface as root.  One stray click, and your whole system can be unrecoverable.  That said, "startx" or "restartx" (I can never remember which) should start up the graphical desktop from the command line.  If it still gives you grief about passwords, it is possible to enable the root account.  Instructions here: [http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html](http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html)

---

### Post by Bushflyer on 2010-02-23
> **quixote said:**
> It's interesting that webmin will work even when your user no longer has sudo privileges.  Bit disturbing, actually.  I'd use that as sparingly as possible, since it *shouldn't* be working, and god only knows what it's breaking as it goes about its business![l]("http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html")

It doesn't have its own user that the daemon runs under/is owned by, like "www-data" for apache or "mysql" for MySQL?  I'll have to look into this.

---

### Post by quixote on 2010-02-23
The apache or mysql users have privileges relevant to those programs, as I'm sure webmin does.  But nothing, except root, should be letting you do general system-type things that root normally does.  As far as I know.  Which may not be far enough :).

---

### Post by Bushflyer on 2010-02-25
> **quixote said:**
> The apache or mysql users have privileges relevant to those programs, as I'm sure webmin does.  But nothing, except root, should be letting you do general system-type things that root normally does.  As far as I know.  Which may not be far enough :).

I really don't know much more than a few inches or more, but, out of common sense, shouldn't webmin simply use sudo to do system-related stuff?

That reminds me.  I wonder if making a new user and transferring the desktop configuration (or manually recreating it) and then switching all the Unix-user syncs in Webmin to use it instead of the old one...then removing the old one...might fix it, if only my user is affected...I will have to find out whether new users are broken.

---

### Post by quixote on 2010-02-25
If it seems like this is something Webmin-related, any chance their forums might have some useful info?

---

### Post by Bushflyer on 2010-02-26
> **quixote said:**
> If it seems like this is something Webmin-related, any chance their forums might have some useful info?

Their forums are apparently so outdated that they don't have a search function(it is a SourceForge forum).  Anyway, I do not think it is related to Webmin because I am still in the admin group and, as far as I can tell, everything else is fine.  Also, new users created manually seem to have this defect as well.

EDIT: I am beginning to wonder if this is possibly related to AppArmor.  Does "must be setuid foo" happen when a user that is blocked by the AppArmor tries to access the application or command?  Or, for that matter, does it happen with SELinux?

---

### Post by quixote on 2010-02-27
I know zero about AppArmor.  Seems like it might block access in the situation you mention.  I wonder.  Any AppArmor geeks out there?

---

### Post by Bushflyer on 2010-02-28
Well, I removed AppArmor and sudo now works.  Thank you for your help, quixote.

EDIT:  OK, for some reason, the Software Center, and every other administrative application except Synaptic is still messing up.

---

