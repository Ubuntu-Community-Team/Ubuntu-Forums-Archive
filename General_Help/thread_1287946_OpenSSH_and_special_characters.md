---
title: "OpenSSH and special characters"
date: 2009-10-10
forum: General Help
---

### Post by mocka on 2009-10-10
I have now tried to set up a backup system where the files are copied from one computer to a Ubuntu Server via sftp (ultimately openssh). As I am from a nordic country, many of my documents includes special characters like æ, ø and å. These filenames however, are converted to use normal characters instead of those special. Is there any way to avoid this?

---

### Post by diesch on 2009-10-10
It works for me:

```

$ touch /tmp/foo/æøå
$ sftp localhost:/tmp/foo/æøå /tmp/
Connecting to localhost...
Fetching /tmp/foo/æøå to /tmp/æøå
$ ls /tmp/æøå
/tmp/æøå

```

---

### Post by mocka on 2009-10-11
I see, thank you for testing. Then the problem must lie with the sftp sender.

---

### Post by StuartN on 2009-10-11
[I]"Make sure that /etc/ssh/ssh_config in the client includes the line
SendEnv LANG LC_*

and that /etc/ssh/sshd_config in the server includes the line
AcceptEnv LANG LC_*"[/I]

[http://www.linuxquestions.org/questions/linux-networking-3/locale-problem-with-ssh-641968/](http://www.linuxquestions.org/questions/linux-networking-3/locale-problem-with-ssh-641968/)

---

