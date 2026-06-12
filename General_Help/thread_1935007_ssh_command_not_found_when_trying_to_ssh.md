---
title: "ssh: command not found when trying to ssh"
date: 2012-03-03
forum: General Help
---

### Post by R.Bucky on 2012-03-03
I have a clean install of Ubuntu 10.04.4 on my laptop. When trying to ssh or sftp in Nautilus, I keep getting the **ssh: command not found**. I have purged ssh, autoremove, autoclean, clean then reinstalled with the same results. 

any ideas on what is happening?

[IMG]http://cdn1.nwlinux.com/ssh-not-found.png[/IMG]

---

### Post by codemaniac on 2012-03-03
Hello .

Please check the executable permissions on ssh binary .

```
ls -l /usr/bin/ssh
```

---

### Post by R.Bucky on 2012-03-03
the command returns

---------- 1 root root 339712 2011-06-16 22:54 /usr/bin/ssh

What should they be?

---

### Post by codemaniac on 2012-03-03
Hello ,

turn required x bits on .

```
sudo chmod +x /usr/bin/ssh
```

Cheers
Codemaniac

---

### Post by R.Bucky on 2012-03-03
I changed permissions and made it executable. All is well. I never even thought about permissions or making ssh executable on a clean install. 

I appreciate the help with this one. It's always the simple tasks... 

Mark

---

### Post by codemaniac on 2012-03-03
Please never forget to mark the thread as SOLVED .

Best Regards
Codemaniac .

---

### Post by R.Bucky on 2012-03-03
> **codemaniac said:**
> Please never forget to mark the thread as SOLVED .

Best Regards
Codemaniac .
done - and thank you

---

