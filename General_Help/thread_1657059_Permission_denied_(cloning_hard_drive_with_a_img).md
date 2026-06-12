---
title: "Permission denied (cloning hard drive with a img)"
date: 2010-12-31
forum: General Help
---

### Post by Keypel on 2010-12-31
```
user01@ubuntu:~$ sudo gunzip -c /media/xbox/xbox_image.gz | dd  of=/dev/sdc
dd: opening `/dev/sdc': Permission denied

[sudo] password for user01: 

user01@ubuntu:~$

user01@ubuntu:~$ sudo gunzip -c /media/xbox/xbox_image.gz | dd  of=/dev/sdc
dd: opening `/dev/sdc': Permission denied
user01@ubuntu:~$
```

I'm getting Permission denied even though I'm putting sudo in front of the command but, instead of asking me for a pass word it just says Permission denied "then" it askes for a pass. I enter the pass and it just takes me to the 

user01@ubuntu:~$ 

prompt. I enter the command a second time and it says Permission denied again.

---

### Post by noah++ on 2010-12-31
The problem is that with your syntax, *dd *runs unprivileged. Try *su *to enter a root shell, then run the command there.

---

### Post by Keypel on 2010-12-31
> **noah++ said:**
> The problem is that with your syntax, *dd *runs unprivileged. Try *su *to enter a root shell, then run the command there.

OK I logged in with root using su and it works. Marked Thread as solved but can you please explain to me why sudo does not work? I don't understand what you mean syntax?

---

### Post by noah++ on 2010-12-31
By "syntax" I just mean the order in which you put the terms in your command. When you start a program with *sudo *and then pipe its output to another program, *sudo *can only elevate the privileges of the first program.* dd *needed root privileges to do what you asked it to do. But since it came after the pipe, it ran as your regular user. Naturally, if you are logged in as root (by using *su*, for instance) the entire command runs with root privileges.

Theoretically this could work too,
```
sudo gunzip -c /media/xbox/xbox_image.gz | **sudo** dd of=/dev/sdc
```but I've never tried it like that.

---

### Post by Keypel on 2010-12-31
Thank you for the extra explanation. I now understand what you were trying to tell me.

---

