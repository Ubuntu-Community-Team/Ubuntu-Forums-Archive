---
title: "Move files from Linux to Windows"
date: 2009-11-10
forum: General Help
---

### Post by Cardale on 2009-11-10
I have a web server that is running Linux and it hosts a website where people can upload files for a game server which is running Windows XP well atleast ideally it would do this. I did host them both on the same server at one point and time and it was easy to move these documents from one location to the next. How would I do this on a windows(XP) machine from a linux machine(Ubuntu)?

Thanks for the help.

---

### Post by Giblet5 on 2009-11-10
Install CygWin on the XP box, including ssh and rsync.

Install openssh-server on the linux box.

Set up ssh keys for cygwin and the linux box.

Use rsync and scp to copy the files around.

---

### Post by Cardale on 2009-11-10
That sounds good but with Cygwn would I beable to use the mv command or something of the sort.  I am letting PHP run the mv command or has this been tested?

---

### Post by Giblet5 on 2009-11-10
> **Cardale said:**
> That sounds good but with Cygwn would I beable to use the mv command or something of the sort.  I am letting PHP run the mv command or has this been tested?

Cygwin provides a native Windows bash shell and pretty much every command that you have under Ubuntu.

So ... yeah.

You'll probably need to do an scp command, followed by an rm if the copy succeeded, but that's all mv does anyway (cp && rm).

A sample shell script for CygWin on Windows:
```
#!/bin/bash

cd /cygdrive/d/release/files

scp *.dat remotehost:/home/www/release/files && rm *.dat

exit 0
```

---

### Post by darkksyde on 2009-11-11
have you tried cygwin, there should be some tutorials if you google it

---

### Post by Cardale on 2009-11-11
Didn't even know such a thing existed thanks.

---

### Post by Cardale on 2009-11-11
How fast is this?  Will this hang up either computers?  Is there a way to automate the login?

---

### Post by Cardale on 2009-11-11
I generated my keys and everything, but for some reason I can't get the darn thing to login without a password.  I can get my desktop to login to my server and my game server without a password, but neither one wants to work on each other.  Is there anything else I should know about?

---

