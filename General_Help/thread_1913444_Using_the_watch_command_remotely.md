---
title: "Using the watch command remotely"
date: 2012-01-22
forum: General Help
---

### Post by triunenature on 2012-01-22
What I am trying to do is use watch to see who is logging into my server and who is attempting to log into my server.  But do this all as part of a script.

(I omitted my server address and password for obvious reasons)
```

omega@desktop:~$ ssh SERVER "echo 'PASSWORD' | sudo -S watch 'netstat -nap | grep EST'"
[sudo] password for omega: Error opening terminal: unknown.

```

If i lose the watch command it works fine, the problem is, then I have to call the command every 2 seconds, including reloggin into the server via ssh.

Its the whole "Error opening terminal:unknown" that gets me.

Any idea?

---

### Post by sanderd17 on 2012-01-22
Can't you set up ssh with a passwordless key? That would be way safer than providing your password in a plain text file: [https://wiki.archlinux.org/index.php/SSH_Keys](https://wiki.archlinux.org/index.php/SSH_Keys)

But I don't think that's the way to execute commands remotely. You're not piping anything.

---

