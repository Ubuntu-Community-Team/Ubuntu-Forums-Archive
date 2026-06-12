---
title: "Shell script multiple log files"
date: 2011-10-10
forum: General Help
---

### Post by RonnieJ on 2011-10-10
Hey - not sure this is the right thread but couldn't fine any more appropriate. 

I have several webserveres running... with multiple log files on every one of them... I would like to be able ro run a shell script that went through my servers with ssh authetication and tail'ing all my log files (that I have choosen not all log files are interesting) and returning the output to me... that way I can very easy get a status from my serveren by looking at the output instead of going onto every server and doing it manually. 

Any idea how to do this? Or now something that can do this for me already out there?
I have no shell scripting experience... 

Best /Ronnie

---

### Post by papibe on 2011-10-14
I would do it like this:

- Install OpenSSH on all your server.
- Create Public Keys to connect password-less from your workstation.
- Use rsync over ssh to retrieve the files you need.
- Automate the process using crontab.

Just some thoughts,
Regards.

---

