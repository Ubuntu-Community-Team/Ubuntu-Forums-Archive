---
title: "CANT become root!!!!!"
date: 2010-08-02
forum: General Help
---

### Post by adikris02 on 2010-08-02
I'm currently using a hpdv61111au laptop. Installed ubuntu 9.10 recently,but i'm not able 2 become root.And i'm not able to install windows.When i try to install windows,i get an error msg saying,operation halted.run CHKDSK and shows an error msg.Is it possible that this is a hard drive problem?? I've formatted the whole drive and then installed ubuntu. Still have the same problem. I'd really appreciate help on both the issues.

---

### Post by lisati on 2010-08-02
> **adikris02 said:**
> Installed ubuntu 9.10 recently,but i'm not able 2 become root.

Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by deathadder on 2010-08-02
How are you trying to become root? What error messages, if any, are you getting? The only way to "become" root in Ubuntu is using the sudo command. Normally you'll use the command to run individual commands as the root user, however if you pass the '-s' argument you can invoke a root shell.

---

### Post by Smart Viking on 2010-08-02
but there are many ways you can enter as root in a terminal session, you could become root in the same terminal with doing this:
```
sudo su
```

which can sometimes be handy, or launch a a new terminal with root privileges:
```
gksudo gnome-terminal
```

:)

---

### Post by rockager on 2010-08-02
this worked for me:
in the terminal type the following
"passwd root" (without quotes)
then follow the prompts and log on as root with the password you typed earlier in the terminal ( the UNIX password).this will make a new root account.

---

