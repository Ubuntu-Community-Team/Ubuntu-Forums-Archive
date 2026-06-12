---
title: "no valid sudoers sources found, quitting"
date: 2012-02-10
forum: General Help
---

### Post by Jonners59 on 2012-02-10
I am trying to use stunnel, but getting the following error message when I try and start it:
```
$ sudo stunnel4
sudo: /etc/sudoers is owned by uid 1000, should be 0
sudo: no valid sudoers sources found, quitting

```

I had to change permissions on /etc/stunnel/ to add a stunnel conf file.

---

### Post by WorMzy on 2012-02-10
You'll have to boot into recovery mode to fix that.

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Look at case 3, but instead of the chmod command, you need to use
```
chown root:root /etc/sudoers
```

---

### Post by Rafterman414 on 2012-02-10
> **WorMzy said:**
> You'll have to boot into recovery mode to fix that.

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Look at case 3, but instead of the chmod command, you need to use
```
chown root:root /etc/sudoers
```

+1 that should do the trick I ran into that issue before. Also I know on my CentOS machine if /etc/sudoers is not read only it will also throw an error, not sure if it is the same for Ubuntu.

---

### Post by Jonners59 on 2012-02-10
> **WorMzy said:**
> You'll have to boot into recovery mode to fix that.

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Look at case 3, but instead of the chmod command, you need to use
```
chown root:root /etc/sudoers
```

I did try this just after I reported the problem, but it did not work.  I'll try again.

Yup, tried again....  said it changed ownership, but when I boot back in I get the same old message.

---

### Post by Jonners59 on 2012-02-12
Whatever I do it always says that it is wroned by 1000 and not 0.  It says it must be owned by 0.  I have tried all the links below and on other threads.  I have tried to open Accounts and Groups from Settings but it does not open.  I think something is wrong there.  The directory etc is owned by me and NOT root.  I need to change this back to root.  How?

---

### Post by Jonners59 on 2012-02-16
SOlved using
```
pkexec chmod 0440 /etc/sudoers
```

---

### Post by soodsse on 2013-02-03
> **Jonners59 said:**
> SOlved using
```
pkexec chmod 0440 /etc/sudoers
```

yes it works

---

### Post by Jonners59 on 2013-02-03
> **soodsse said:**
> yes it works

Good, glad all my work helped someone else...

---

