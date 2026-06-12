---
title: "Locked out"
date: 2009-09-28
forum: General Help
---

### Post by Tearaft on 2009-09-28
Hi everyone,

I've got a bit of a problem that I can't resolve. I can no longer open and run the program "Users and Groups". Here's how I got there. I wanted to make my computer more secure so I was thinking (or maybe not thinking) that I would enable root and restrict the other accounts (three total) by denying them admin status. So, I used "Users and Groups" to enable root and restrict my other accounts. It worked just fine. But here's my problem. I wanted to use "Update manager" to download some software updates but it wouldn't allow me. So, I went to "Users and Groups" to give myself admin permission but now I can't get in.The box pops up and says "that I am not allowed access to system configuration". I restarted and tried logging in as root but it won't allow me too from the login screen. I can't remember (haven't used Linux as my main os since 2000) how to grant sudo permission to a user from the command line. I have tried su adduser myname and sudo adduser myname when I was root but they don't work. So how can I fix this? 

PAX

Tom

---

### Post by Iowan on 2009-09-29
Hopefully, [this]("http://www.psychocats.net/ubuntu/fixsudo") one will help.

---

### Post by admelfo on 2009-09-29
That's a great tutorial.

---

### Post by Vunutus on 2009-09-29
What you've done is essentially the opposite of the Ubuntu security philosophy. Ubuntu aims to secure itself by disabling the root account (or more accurately, preventing anyone from logging into it), and give sudo privileges to users that require root access.

I'm not entirely sure, but I believe that sudo is configured to give sudo access to users in the "admin" group. It sounds like you've removed yourself from this group. 

To add yourself back to this group, you should be able to run the following command (which you most be logged in as root for this to work):

```
usermod -a -G admin **YOURUSERNAMEHERE**
```

---

### Post by undecim on 2009-09-29
> **Vunutus said:**
> What you've done is essentially the opposite of the Ubuntu security philosophy. Ubuntu aims to secure itself by disabling the root account (or more accurately, preventing anyone from logging into it), and give sudo privileges to users that require root access.

I'm not entirely sure, but I believe that sudo is configured to give sudo access to users in the "admin" group. It sounds like you've removed yourself from this group. 

To add yourself back to this group, you should be able to run the following command (which you most be logged in as root for this to work):

```
usermod -a -G admin **YOURUSERNAMEHERE**
```

If you set a password for the root user, you should be able to go to a terminal, type "su" and get root access with that password.

If you haven't set a password for the root user, you need to reboot, press escape when grub comes up with its timer, and select "recovery mode" from your boot options. When your recovery mode loads, choose the "root" option from the menu, and you will have root access (type "reboot" after you are done fixing your system)

Once you get root access from one of those ways I've mentioned above, run the command that Vunutus suggested:
```
usermod -a -G admin **YOURUSERNAMEHERE**
```

---

