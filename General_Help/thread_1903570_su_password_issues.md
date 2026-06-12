---
title: "su password issues"
date: 2012-01-02
forum: General Help
---

### Post by scholzilla on 2012-01-02
well, here's a weird problem i've never had before. I'm running 64 bit lucid and am getting authentication errors whenever I try to use su from term. I'm certain I'm typing in the correct password correctly. Ummmm...what do I do? I need this access in order to allow a remote server to install a networking java app.

---

### Post by fdrake on 2012-01-02
> **scholzilla said:**
> well, here's a weird problem i've never had before. I'm running 64 bit lucid and am getting authentication errors whenever I try to use su from term. I'm certain I'm typing in the correct password correctly. Ummmm...what do I do? I need this access in order to allow a remote server to install a networking java app.

"su" is used to switch user and for that you need sudo so it should be "sudo su ". only root can use only "su"
note:
"sudo su" and "sudo su -" is to switch to root
"sudo su username" is ro switch to the user "username"

---

### Post by sisco311 on 2012-01-02
By default, the root account password is locked. su prompts for the target user's password, hence you can't use it log in as root. Use sudo instead: [uhelp]community/RootSudo[/uhelp]

---

### Post by fdrake on 2012-01-02
> **sisco311 said:**
> By default, the root account password is locked. su prompts for the target user's password, hence you can't use it log in as root. Use sudo instead: [uhelp]community/RootSudo[/uhelp]
i do know that but on my fresh install ubutu 10.04 even if my /etc/shadow says:
> 
root:!:15339:0:99999:7:::

the ":!:" should stand foe account we no password, not for locked account :!<hash code>:  or :*: 

I am still able to login using "sudo su" or "sudo su -" or "sudo su root". Why ? I mean I know with this option I should be able to login but why do they say is locked instead?

---

### Post by sisco311 on 2012-01-02
> **fdrake said:**
> "su" is used to switch user and for that you need sudo so it should be "sudo su ". only root can use only "su"
note:
"sudo su" and "sudo su -" is to switch to root
"sudo su username" is ro switch to the user "username"

su and sudo are very similar commands. They both allow a user to run a command (shell or other application) as another user (including root).

By default, any user who is in the wheel group is allowed to use su. The user also has to know the target user's password, because su will prompt for it, if it's invoked by a non-root user. So, if the root account password is locked and you aren't logged in as root, you can't use su to switch to root. 

By default, sudo allows any user from the admin group run a command as another user. sudo will prompt for the invoking user's password (if needed). 

I'd not recommend to mix the two commands. The preferred method, in Ubuntu, for starting a root shell is: **sudo -i**. Please check out the link I posted.

---

### Post by scholzilla on 2012-01-02
ok, but the aforementioned remote java install pops up a term that says "root/su password required" and typing my normal password gives me the authentication error. So it would seem I actually need root access. It's not a matter of typing sudo and then some command. I'm only prompted for a password.

And btw, sudo -i doesn't do it for me either

---

### Post by sisco311 on 2012-01-02
> **fdrake said:**
> i do know that but on my fresh install ubutu 10.04 even if my /etc/shadow says:

the ":!:" should stand foe account we no password, not for locked account (:!<hash code>:)

I am still able to login using "sudo su" or "sudo su -" or "sudo su root". Why ? I mean I know with this option I should be able to login but why do they say is locked instead?

![whatever] stands for a locked account. From **man passwd**:
```
       -l, --lock
           Lock the password of the named account. This option disables a
           password by changing it to a value which matches no possible
           encrypted value (it adds a '!' at the beginning of the password).

           Note that this does not disable the account. The user may still be
           able to login using another authentication token (e.g. an SSH key).
           To disable the account, administrators should use usermod
           --expiredate 1 (this set the accounts expire date to Jan 2, 1970).

           Users with a locked password are not allowed to change their
           password.

```

Invoked as root su won't prompt you for a password. That's what you do when you run *sudo su*. You use sudo to run the su command as root. 

HTH

---

### Post by sisco311 on 2012-01-02
> **scholzilla said:**
> ok, but the aforementioned remote java install pops up a term that says "root/su password required" and typing my normal password gives me the authentication error. So it would seem I actually need root access. It's not a matter of typing sudo and then some command. I'm only prompted for a password.

And btw, sudo -i doesn't do it for me either

Try to run the installer as root (with sudo):
```
sudo path/to/command
```

If it still prompts you for the root password, then you will have to set up a root password, then lock it after the application is installed.

---

### Post by scholzilla on 2012-01-02
that worked. Thanks!

---

### Post by sisco311 on 2012-01-02
You are welcome!

---

