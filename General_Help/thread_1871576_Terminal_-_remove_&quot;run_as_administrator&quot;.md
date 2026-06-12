---
title: "Terminal - remove &quot;run as administrator&quot; text at the top on default"
date: 2011-10-29
forum: General Help
---

### Post by altjx on 2011-10-29
Now that I've deleted my user account, logged in as root and created another user account, every time I run terminal, I get this at the top of the terminal session.

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

```

Here's a screenshot:

[IMG]http://dl.dropbox.com/u/2526790/Screenshot%20at%202011-10-29%2004%3A06%3A42.png[/IMG]

---

### Post by deloquencia on 2011-10-29
Did you check the file .bashrc in your home directory?

---

### Post by altjx on 2011-10-29
> **deloquencia said:**
> Did you check the file .bashrc in your home directory?

What am I looking for in here?

---

### Post by deloquencia on 2011-10-29
The .bashrc is used for non-login shells and there it could be possible that the lines about "To run a command as administrator (user "root")...." are echoed. Look for that, perhaps it's there.

---

### Post by haqking on 2011-10-29
> **altjx said:**
> Now that I've deleted my user account, logged in as root and created another user account, every time I run terminal, I get this at the top of the terminal session.

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

```

Here's a screenshot:

[IMG]http://dl.dropbox.com/u/2526790/Screenshot%20at%202011-10-29%2004%3A06%3A42.png[/IMG]

After the first time you run a sudo command the message will go away

example

```
sudo apt-get update
```

---

