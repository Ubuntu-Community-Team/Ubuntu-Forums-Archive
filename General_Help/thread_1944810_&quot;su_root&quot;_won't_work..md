---
title: "&quot;su root&quot; won't work."
date: 2012-03-21
forum: General Help
---

### Post by Zoaruki on 2012-03-21
For some reason I can't get this command working. The Terminal always rejects my password, when with "sudo" does not.
There is only one user in the system.

---

### Post by uRock on 2012-03-21
When you want to run a command as super user, you need to enter sudo in front of the command. For more info on root and sudo look here, [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Zoaruki on 2012-03-21
That's what I did when I was installing a program, but I thought it could work alone, lol.
Thank you!

---

### Post by HiImTye on 2012-03-21
the root user is disabled by default, use sudo to run any commands as an administrator or use one of the methods in [RootSudo]("https://help.ubuntu.com/community/RootSudo#Special_notes_on_sudo_and_shells")

---

### Post by Spewed on 2012-03-21
> **HiImTye said:**
> the root user is disabled by default, use sudo to run any commands as an administrator or use one of the methods in [RootSudo]("https://help.ubuntu.com/community/RootSudo#Special_notes_on_sudo_and_shells")

I'm going to be as simple minded as I can here, as maybe this helps, because I had issues and people overcomplicated it. 

Are you actually typing "Sudo root"? 

If so, there is your problem. Just simply type "Sudo su" and it will prompt you for your password that you used to log-in everyday. Enter that, and you're in root.

---

### Post by jerome1232 on 2012-03-22
> **Spewed said:**
> I'm going to be as simple minded as I can here, as maybe this helps, because I had issues and people overcomplicated it. 

Are you actually typing "Sudo root"? 

If so, there is your problem. Just simply type "Sudo su" and it will prompt you for your password that you used to log-in everyday. Enter that, and you're in root.

shouldn't use sudo su, instead
```
sudo -i
```

---

### Post by Spewed on 2012-03-22
> **jerome1232 said:**
> shouldn't use sudo su, instead
```
sudo -i
```

Whats the difference?

---

### Post by mcduck on 2012-03-22
> **Spewed said:**
> Whats the difference?

"sudo -i" loads root user's environment correctly, working exactly as if you had logged in as root.

"sudo su" and "sudo -s" give you root's permissions, but still use your normal user's environment, which can cause all kinds of unexpected problems, like the ownership of config files for your user becoming owned by root (and thus making the normal user unable to change the settings any more).

Same kind of thing as with the recommendation to always use gksudo for graphical applications, as sudo doesn't load the graphical environment variables correctly.

---

### Post by Subidubi32 on 2012-03-22
"sudo su" is working for me to be root, with an "exit" you can get back to your user

---

### Post by letoasty on 2012-03-22
you can't use ```
su root
``` because the 'su' command changes the active user to whichever you specify, in this case the 'root' user. Ubuntu by default locks the root user and only allows you to temporarily gain root priviledges with ```
sudo COMMAND
``` this is for security purposes because if you were to start a full terminal session as the root user there's a possibility of you breaking something if you are unfamiliar with the BASH shell.

---

### Post by Cheesemill on 2012-03-22
> **Subidubi32 said:**
> "sudo su" is working for me to be root, with an "exit" you can get back to your user

Yes, it works. But it might lock your normal user out of it's own configuration files.

'sudo -i' is the preferred method.

---

