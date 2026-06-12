---
title: "Can't Log in as Root"
date: 2006-04-15
forum: General Help
---

### Post by nakile on 2006-04-15
Hello.

I have yet antother problem here.

When I go to the KDE login screen and try to login as "root," I get the message "Root logins arn't allowed." Use the right password and everything. This happens with both KDE and Gnome.

Thanks in advance.

---

### Post by ComplexNumber on 2006-04-15
thats not a problem that you're descrivbing. you're not supposed to login as root. you can damage your system and render your account vulnerable if you are on the internet. ubuntu prevents that by disabling logging in as root.
when you are in your user account, use the command sudo on the commandline to perform adminstrator tasks
.

---

### Post by nakile on 2006-04-15
The only problem with your reply is that I could login as root before all of this. ](*,)

---

### Post by incubus on 2006-04-15
Can you do something like:
$ sudo passwd root

Is that how you activated the root password in the first place?

incubus

PS: But I agree with secondnumber: avoid having a root account if you can. I've seen many sad stories about it, mostly because the system won't ask you for confirmation.

---

### Post by nakile on 2006-04-16
I would just like to log in as the root under KDE. I don't want to use Konsole.

And I can handle root accounts, I have in the past.

---

### Post by incubus on 2006-04-16
nakile,

That command is to reset (recreate) your root password. You just need to run it once.

incubus

---

### Post by fdoving on 2006-04-16
To allow root logins to KDM you will need to edit /etc/kde3/kdm/kdmrc and change:
```

AllowRootLogin=false

```

To:
```

AllowRootLogin=true

```

AND you need to set a root password as the other posts in this thread explains.

- Frode

---

### Post by elamericano on 2006-04-16
ComplexNumber: "thats not a problem that you're describing."

You mean to say that it's not a bug, but it sure can be a problem for those who want to do it. It used to be that you had to recompile to do it, but now KDE and Gnome both have switches to allow it.

Personally, I prefer using sudo with the password disabled when I'm using a computer where security doesn't matter.

---

### Post by wanger123 on 2006-04-16
[QUOTE=nakile]I would just like to log in as the root under KDE. I don't want to use Konsole.

And I can handle root accounts, I have in the past.[/QUOTE]

LMAO
:-D :-D :-D

---

### Post by ComplexNumber on 2006-04-16
[quote=nakile]The only problem with your reply is that I could login as root before all of this. ](*,)[/quote] really? :confused:. you must have enabled it yourself, somehow. the root account is disabled by default in the ubuntu family of distros.

[QUOTE=elamericano]
You mean to say that it's not a bug[/QUOTE]
yes, i'm saying its not a bug.

---

### Post by nakile on 2006-04-16
[QUOTE=fdoving]To allow root logins to KDM you will need to edit /etc/kde3/kdm/kdmrc and change:
```

AllowRootLogin=false

```

To:
```

AllowRootLogin=true

```

AND you need to set a root password as the other posts in this thread explains.

- Frode[/QUOTE]
I can't edit that file because I'm not the root user.

---

### Post by aysiu on 2006-04-16
[QUOTE=nakile]I can't edit that file because I'm not the root user.[/QUOTE] Go to KMenu > System > Konsole and type ```
sudo cp /etc/kde3/kdm/kdmrc /etc/kde3/kdm/kdmrc_backup
sudo kwrite /etc/kde3/kdm/kdmrc
```

---

