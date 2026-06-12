---
title: "Am I puting myself at risk?"
date: 2010-11-26
forum: General Help
---

### Post by Mindswap1 on 2010-11-26
Hi guys! I'm fairly new to Ubuntu ( Used it for 3 days now ), and I'm confused. I've been told that giving yourself root privileges puts yourself in danger. I always type into the terminal  "Sudo Apt-get install *program name*". Does this mean I'm using root privileges and putting myself at risk. How can I make sure I have VERY limited Root privileges on my account.

---

### Post by Lone_Joker on 2010-11-26
No you are not putting yourself at risk. What would put you at risk is if you used the account named 'root' to login.

---

### Post by WorMzy on 2010-11-26
Using sudo is the "correct" way of doing things, at least on Ubuntu. It means that you're elevating yourself to the root user for a short amount of time, rather than being the root user for a prolonged period of the time, or indefinitely.

In other distributions of Linux, "su" is the encouraged way of elevating yourself to the root user, and this method is *indefinite*. Meaning that, if you were to use su, then walk away from your machine without ending your su session, your computer would be vulnerable. Ubuntu disables this method by disabling the root account. This means that, by default, you are root for a short period of time; long enough to install a few programs and nothing more. You can emulate the su environment by running sudo -i, but this is discouraged, since you rarely ever need to be root for more than a few seconds.

---

### Post by Lone_Joker on 2010-11-26
Also wanted to add that if you ever did need to login as root you would have to run this to set root's password:
```
sudo passwd root
```
then use this to switch to root, using the password you just set:
```
su
```


It is recommended to not use root privileges because you could screw up your system. You also have to be careful when you run the *sudo* command, because sudo runs a command as root.

In case you're wondering what root is, it's just a user that can do **anything**.

I hope I haven't complicated things for you. Short answer to your question: what you're doing is fine.

---

### Post by dcstar on 2010-11-26
> **Mindswap1 said:**
> Hi guys! I'm fairly new to Ubuntu ( Used it for 3 days now ), and I'm confused. I've been told that giving yourself root privileges puts yourself in danger. I always type into the terminal  "Sudo Apt-get install *program name*". Does this mean I'm using root privileges and putting myself at risk. How can I make sure I have VERY limited Root privileges on my account.

[LIST=1]
[*]Why are you using the command line when there are perfectly good GUI tools?
[*]If you are concerned, do not use the command line as it is basically unnecessary for a new user.
[/LIST]

---

### Post by The Cog on 2010-11-27
You are not putting yourself in danger. The point is that you shouldn't be running with root privilege all the time, because of the danger of making mistakes or running malware that then has full write access to the system. But of course, you do need root privilege to do system admin work. You use the sudo command to gain those privileges for just the commands you need them for.

Do not set a root password like Lone_Joker suggests. If you want a root command prompt to do a whole series of commands, use the command **sudo -i** to raise that terminal session to root, and close it when you've finished.

---

