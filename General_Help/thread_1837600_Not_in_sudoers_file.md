---
title: "Not in sudoers file"
date: 2011-09-02
forum: General Help
---

### Post by community on 2011-09-02
I have a doubt regarding the sudo command.Whether I can install any packages via terminal on running apt-get with sudo??? I asked because I got an error message as depicted below

anil is not in the sudoers file.  This incident will be reported.

where anil is one of the user.Can anyone give a solution for this???

---

### Post by dodo3773 on 2011-09-02
> **community said:**
> I have a doubt regarding the sudo command.Whether I can install any packages via terminal on running apt-get with sudo??? I asked because I got an error message as depicted below

anil is not in the sudoers file.  This incident will be reported.

where anil is one of the user.Can anyone give a solution for this???


You have a file on your computer called a sudoers file. It is usually somewhere like /etc/sudoers. The problem is that you will need sudo to read or edit the sudoers file. Are you the only user on the system? I ask because Ubuntu usually sets all this stuff up for you.

---

### Post by community on 2011-09-02
anil is only one of the users on my Ubuntu.The two users are 'anil' and 'anoop'.'anoop' was the only user before.Recently I created the user 'anil'.But now nothing can be done by logging into anil's account.It always display the same error message.What might be the reason???

---

### Post by sisco311 on 2011-09-02
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by community on 2011-09-02
Look, my recovery mode is protected with root password.But the problem is that I forgot my root password.
Therefore please tell me a method through which I can gain the root access and perform the actions listed in the above url...

---

### Post by WorMzy on 2011-09-02
Ubuntu doesn't have a root password (unless you set one for some reason).

All you need to do is add "anil" to the admin group. You can do that after logging in as "anoop", then running:
```
sudo usermod -a -G admin anil
```

---

### Post by dodo3773 on 2011-09-02
> **community said:**
> anil is only one of the users on my Ubuntu.The two users are 'anil' and 'anoop'.'anoop' was the only user before.Recently I created the user 'anil'.But now nothing can be done by logging into anil's account.It always display the same error message.What might be the reason???

Does sudo work for anoop? If so, then use anoop to fix sudo for anil.

---

