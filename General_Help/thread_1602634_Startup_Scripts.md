---
title: "Startup Scripts"
date: 2010-10-21
forum: General Help
---

### Post by zangderak on 2010-10-21
I'm having trouble with the rc.local file.  So I tried the suggestions on this page:

[https://help.ubuntu.com/community/RcLocalHowto](https://help.ubuntu.com/community/RcLocalHowto)

I could run the script ok through the terminal.  But it doesn't run on startup.  Has anyone got this to work in the way explained in the link above?  I'm using Ubuntu Lucid.

---

### Post by sisco311 on 2010-10-21
[Upstart]("http://upstart.ubuntu.com/") often executes rc.local (and the System V style init scripts) too soon. Either put a sleep before the command:
```
sleep 6
command
```
or write an Upstart job. What script are you trying to run at startup?

---

### Post by zangderak on 2010-10-21
I tried the sleep command already.  Here's my script.  It's just something to see if I could get a simple script working at all:

```
#!/bin/bash
PATH='/bin:/usr/bin'
sleep 10
touch ~/file
exit 0

```

I used update-rc.d and now see it in the /etc/rc#.d directories.  But it's still not running on startup.

---

