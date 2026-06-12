---
title: "run a script"
date: 2011-10-20
forum: General Help
---

### Post by Big-G on 2011-10-20
Hello members,

I am working at a new project and having a problem with it.
My problem is that i have someway to run a script every time linux asks for the root password.
If anyone can tell me how to solve the problem, i would be grateful.
I also mention it won't be used for bad purpososes.

Best regards,
Big-G

---

### Post by tors on 2011-10-20
Hi,
maybe you can check out /var/log/auth.log and see if it can help you.

---

### Post by shubham1 on 2011-10-20
> **Big-G said:**
> Hello members,

I am working at a new project and having a problem with it.
My problem is that i have someway to run a script every time linux asks for the root password.
If anyone can tell me how to solve the problem, i would be grateful.
I also mention it won't be used for bad purpososes.

Best regards,
Big-G
[http://www.cyberciti.biz/faq/ubuntu-linux-root-password-default-password/](http://www.cyberciti.biz/faq/ubuntu-linux-root-password-default-password/)

---

### Post by Big-G on 2011-10-20
No, i think my explanations weren't very clear. 
I want, for example, when linux asks for root password, first to run a script (Ex: read 3 ints and print them) and then the user inserts the pass.

Ex:
```

user@home:~$ sudo apt-get update
insert 3 numbers: 2 3 4
the numbers are: 2 3 4
[sudo] password for user: 

```

---

### Post by drofart on 2011-10-20
> **Big-G said:**
> Hello members,

I am working at a new project and having a problem with it.
My problem is that i have someway to run a script every time linux asks for the root password.
If anyone can tell me how to solve the problem, i would be grateful.
I also mention it won't be used for bad purpososes.

Best regards,
Big-G
Check [this]("http://ubuntuforums.org/archive/index.php/t-1497966.html") otherwise we have other explicit things to do!

---

### Post by CharlesA on 2011-10-20
> **Big-G said:**
> No, i think my explanations weren't very clear. 
I want, for example, when linux asks for root password, first to run a script (Ex: read 3 ints and print them) and then the user inserts the pass.

Ex:
```

user@home:~$ sudo apt-get update
insert 3 numbers: 2 3 4
the numbers are: 2 3 4
[sudo] password for user: 

```
Why do you want it to do that? I cannot think of any reason to have a prompt before entering your sudo password. If someone shouldn't have sudo access, don't give them sudo access.

Read [here]("https://wiki.ubuntu.com/RootSudo") to read more about sudo.

sudo prompts for the userpassword, not the root password btw.

---

### Post by drofart on 2011-10-20
[HERE]("http://ubuntuforums.org/showthread.php?t=19236")

---

