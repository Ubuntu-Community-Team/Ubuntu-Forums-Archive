---
title: "vipw, couldn't lock file: interrupted system call"
date: 2010-02-17
forum: General Help
---

### Post by bender1234 on 2010-02-17
Hey. 

I was trying to set up a svn server on my server, follwing this tutorial [http://www.subversionary.org/howto/setting-up-a-subversion-server-on-ubuntu-gutsy-gibbon-server]("http://www.subversionary.org/howto/setting-up-a-subversion-server-on-ubuntu-gutsy-gibbon-server")

I'm not used to vi/vim, and I quit the app with ctrl-z when using the vipw command.

Before that I just used nano to alter /etc/passwd setting altering the last line
svn:x:1001:1001:,,,:/home/svn:/bin/false 
as stated in the article.

However now I get the following error when trying to run vipw, vigr or adduser.  "Couldn't lock file: Interripted system call"

Or variations of the same error depending on the command I use.

What's going on? The box is located at a remote location, and it takes me couple of hours to get there. When I cat the original file it is correct.

---

### Post by rnerwein on 2010-02-17
hi
that looks for me that nano is not secure (and not made for this to alter passwd or group).
i just looked at my box whats going on with vipw ...
i use lsof -p PID of vipw and saw:
vipw    3844 root    3wW  REG    8,8        0    264[COLOR=Red] /etc/.pwd.lock[/COLOR]

vipw creates ( for security that no one else is doing the same thing as you at the same time ) a lock file in /etc.
you said you try to edit the file on a server and i guess there you have no permission to "create" a file.
hope this help
ciao

---

