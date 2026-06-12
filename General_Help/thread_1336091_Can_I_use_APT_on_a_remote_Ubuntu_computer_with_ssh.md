---
title: "Can I use APT on a remote Ubuntu computer with ssh"
date: 2009-11-24
forum: General Help
---

### Post by lightningfox on 2009-11-24
Hello

Can I use APT on a remote Ubuntu computer with ssh, meaning can 
I install and update software on a remote Ubuntu computer with
ssh.

---

### Post by amauk on 2009-11-24
yes

ssh into the remote machine
```
ssh user@machine
```

To sync the repos
```
sudo apt-get update
```

To install any updates
```
sudo apt-get upgrade
```

To install a new package
```
sudo apt-get install foo
```

---

### Post by blazemore on 2009-11-24
When you SSH into a remote machine, it is literally is if you are sitting at the physical computer.
As far as the computer knows, you are, so you can do anything.
To prove this, when you're at the machine, do ssh localhost, to ssh into itsself. You'll see there's no difference in privelages.

---

### Post by renkinjutsu on 2009-11-24
The answer is yes, but you should use it with nohup or use it in a screen session, so that even if your client drops out or disconnects, apt won't be terminated (which causes problems)

---

