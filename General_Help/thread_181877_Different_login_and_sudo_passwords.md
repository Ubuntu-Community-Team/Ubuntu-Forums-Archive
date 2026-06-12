---
title: "Different login and sudo passwords"
date: 2006-05-24
forum: General Help
---

### Post by elamericano on 2006-05-24
I'm surprised a search didn't find this. I know it's possible to make a sudo password that is different from the user password, but I don't know how.

If there is another thread, or something in the wiki, maybe someone can just point me to that.

Thanks

---

### Post by zhoux on 2006-05-24
i think the code is something like:

sudo passwd

---

### Post by elamericano on 2006-05-25
sudo passwd is to create or change your root password. I'd be careful recommending sensitive configuration changes without knowing what they do.

---

### Post by aysiu on 2006-05-25
From the [Wiki](https://wiki.ubuntu.com/RootSudo):
> **Let sudo ask for the root password**

You can make sudo ask for the root password instead of the user password, you can do this by adding the keyword rootpw to the line in /etc/sudoers that starts with Defaults.

<!> Make certain that you don't do this if you intend to lock the root account

---

### Post by simonn on 2006-05-25
See rootpw in man sudoers.

Note that in Ubuntu you will need to give root a password to do this, thus enabling the root account.

If you enable the root account, you may as well just use su -c [command] instead of sudo.

---

### Post by elamericano on 2006-05-25
Sadly, I knew about this option, although I thought the keyword was runaspw. I was looking to give unique passwords to administrators. If everyone uses the root password, then when I remove an administrator I have to change the root password and send it out to everyone. It would be better if I can just disable that account.

Has anyone heard about creative use of the PAM file to allow each admin to have their own unique sudo password? I've seen it mentioned, but there were no details given.

Sorry for the inexact question.

---

### Post by aysiu on 2006-05-25
What you want is exactly Ubuntu's default.

If you add each user to the *admin* group, each user will have *sudo* privileges with her own unique password.

If you have *sudo* use the root password instead, you will have to keep changing the root password every time you want to deny a particular user root access.

The way Ubuntu is now, you take away someone *sudo* ability by just removing her from the *admin* group.

---

### Post by elamericano on 2006-05-25
The only difference is that I would have each admin's sudo password be different from their login password. It seems to me that two levels of access should have two different passwords. Some people won't agree, but I was just focusing on how to do it.

---

### Post by aysiu on 2006-05-25
[QUOTE=elamericano]The only difference is that I would have each admin's sudo password be different from their login password. It seems to me that two levels of access should have two different passwords. Some people won't agree, but I was just focusing on how to do it.[/QUOTE] Oh, I see! So instead of having three users with three passwords or three users with four passwords (their own and then one root), you'd have three users with six passwords...

I have no idea how to set that up.

---

### Post by elamericano on 2006-05-25
Exactly :-) Although in the beginning it will just be 1 user with 2 passwords and root disabled.

I'll post here once I figure it out.

---

### Post by elamericano on 2006-05-25
OK, here is my solution. First I create another root user to be the sudo password for user "fred":
```
sudo useradd sudofred -c sudo\ password -d /root/sudofred -m -o -u 0 -g 0
```

Then I change the defaults in /etc/sudoers:
```
Defaults:fred  runaspw, runas_default=sudofred

fred   ALL=(ALL) ALL
```

Admin user fred now sudo's under the priviledges of this line rather than using the %admin line.

There you are. I like this. Now if freds account is compromised, root access isn't automatically given along with it.

I would disable all remote access to sudofred. When you want to remove sudo priviledges from fred, you just disable or remove sudofred. I'll have to experiment with putting expiration on that account, maybe a user could be granted sudo access for a set period of time.

Any comments or suggestions?

---

### Post by uzi09 on 2006-07-20
i was hoping we could get something like this working (please see section "Back to SUDO"):
[http://linuxboxadmin.com/articles/sudo-vs-root.php](http://linuxboxadmin.com/articles/sudo-vs-root.php)

i'd rather not have another user added, just different password asked for by sudo.

i apologize if this way was already mentioned. i'm still sort of new and some of the things you were talking about went over my head.

---

### Post by michaelzap on 2008-01-14
I was also looking for a way to do what elamericano is doing (although ideally I'd like it to be able to do it without enabling the root account).

The way that I use and share my PC this seems like it would be a very useful option. I am usually the only one who uses my computer, and I want to be able to install updates and do other sudo tasks without logging out (of a non-sudo account) and logging back in again. But sometimes I allow other people to use my PC for a while, and I don't always want to log out and close all of my open programs and whatnot when they do. My screensaver is set to ask for the password, so sometimes people need to ask me for it (and I try not to be rude while typing it in myself). But I don't want these people to be able to make changes to my system...

So I guess I could create a separate guest account without sudo permissions, but that would sometimes be an inconvenience (making me close my open apps and login/out again). Or I could remove sudo permissions from my regular account and create another one for that, but that would have the same disadvantages. Two passwords per admin user (regular and sudo) would be the porridge that Goldilocks chose.

---

