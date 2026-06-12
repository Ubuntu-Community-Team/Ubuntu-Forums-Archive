---
title: "ssh local browsing"
date: 2010-01-25
forum: General Help
---

### Post by stonebergftw on 2010-01-25
I can't find this on the net anywhere, but I know there is a command...

I'm ssh'ing into a server, and I KNOW there is a command to run commands from the local machine, in the same terminal window as the ssh.

For instance,

ls lists the directory on the server, but something like:

!ls lists my local directory.  It's a precommand modifier or something.  Anyone know what I'm talking about?  I can't remember it and it's so frustrating! ](*,)

---

### Post by Puck7 on 2010-01-25
It seems to me you are confusing this with the ftp commands (:
When you ftp to a server you can still run commands on your local machine, but when you do the ssh, it doesn't really work like that. You just connect over and you're there.

---

### Post by stonebergftw on 2010-01-25
:lolflag:

Uh yea.  Oops!

---

### Post by ibuclaw on 2010-01-25
> **stonebergftw said:**
> :lolflag:

Uh yea.  Oops!

Now now, you could always install [gnu screen]("http://www.gnu.org/software/screen/"), that should do what you want. ;)

---

### Post by hwttdz on 2010-01-25
Or you could alias something like

echo $SSH_CLIENT|awk '{print $1}'|xargs -I{} ssh {} command

of course I'm sure you could be more elegant, and unless you're clever about it it's going to perform the action in your home directory instead of the directory from which you initiated the ssh session.  Of course there's always ls ~/Desktop instead of just ls.

---

