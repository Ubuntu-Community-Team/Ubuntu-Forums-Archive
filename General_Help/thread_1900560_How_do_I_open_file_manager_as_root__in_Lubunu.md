---
title: "How do I open file manager as root?  in Lubunu"
date: 2011-12-26
forum: General Help
---

### Post by pretty_whistle on 2011-12-26
How?

---

### Post by RedRat on 2011-12-26
Open a terminal and then use:
```
sudo nautilus
```

Can you do this, it works in Ubuntu.

---

### Post by benteveo on 2011-12-26
Generally, you can achieve this for any command, by prefixing the command with **sudo**. e.g. assuming your file manager is nautilus you would open a terminal and type:

```
**sudo** nautilus
```

Replace 'nautilus' above by your favorite file manager program name.

sudo would ask you for a password unless configured otherwise, type your password (not root) and the file manager should run with superuser privileges.

You should be able to do a similar thing in the GUI by prefixing the command launch config, wherever it is, with 'gksu' e.g.

```
**gksu** nautilus
```

(If you use kde, use **kdesudo** instead of **gksu**, YMMV.)

There are some more **lubuntu** specific hints here:

   [http://askubuntu.com/questions/86393/how-can-i-add-root-privileges-in-lxpanel-launcher](http://askubuntu.com/questions/86393/how-can-i-add-root-privileges-in-lxpanel-launcher)

---

### Post by WorMzy on 2011-12-26
You should never use sudo for graphical applications; at least not in that manner.

Use gksu, gksudo or kdesudo. If none of these are available to you, and you don't want to install them for whatever reason, then use sudo -i, followed by the command name. e.g.

```
sudo -i
<enter password>
nautilus
```

---

### Post by RedRat on 2011-12-26
> **WorMzy said:**
> You should never use sudo for graphical applications; at least not in that manner.

Use gksu, gksudo or kdesudo. If none of these are available to you, and you don't want to install them for whatever reason, then use sudo -i, followed by the command name. e.g.

```
sudo -i
<enter password>
nautilus
```

Why? I am curious. I have used both 'sudo' and 'gksudo' and got the same results. It works. Is there some special reason?

---

### Post by pretty_whistle on 2011-12-26
Thanks everyone.

As it turns out Lubuntu doesn't come with nautilus.  I'll have to install it first to use sudo nautilus.

That means this is resolved.

:)

P.S.
I'll just install nautilus because the file manager, pcmanfm, gave a access denied message.
Nautilus doesn't and works better because of it.

---

### Post by pretty_whistle on 2011-12-26
I added more to the post during edit just now, so if you already read the previous post please read it again.

---

### Post by WorMzy on 2011-12-26
> **RedRat said:**
> Why? I am curious. I have used both 'sudo' and 'gksudo' and got the same results. It works. Is there some special reason?

Indeed. It's all due to the way that the environment variables are handled. "sudo" doesn't unset all your user's environment variables, which means that your user's config files are used. If these config files are written to during the application's runtime, then the ownership of these files will be changed to root. In some cases this will just mean that your applications will function as normal, but any changes to their configuration won't be saved, meaning that you'll have to repeat the changes every time you run it. In other cases, it'll stop your applications running at all, with enigmatic messages like "Could not update xyz. Aborting.". And in other cases, it may even prevent your user from launching the graphical environment (X11), due to inconsistencies with the .Xauthority file. That can lead to inexperienced users either giving up with Linux entirely, or else reinstalling their entire operating system needlessly.

[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

---

### Post by RedRat on 2011-12-26
> **WorMzy said:**
> Indeed. It's all due to the way that the environment variables are handled. "sudo" doesn't unset all your user's environment variables, which means that your user's config files are used. If these config files are written to during the application's runtime, then the ownership of these files will be changed to root. In some cases this will just mean that your applications will function as normal, but any changes to their configuration won't be saved, meaning that you'll have to repeat the changes every time you run it. In other cases, it'll stop your applications running at all, with enigmatic messages like "Could not update xyz. Aborting.". And in other cases, it may even prevent your user from launching the graphical environment (X11), due to inconsistencies with the .Xauthority file. That can lead to inexperienced users either giving up with Linux entirely, or else reinstalling their entire operating system needlessly.

[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)


OK I see. Hey, thanks a lot. Next time I need to run as root I will use the '-i'. Good information.

---

### Post by WorMzy on 2011-12-26
Well, gksudo is still the preferred way of launching graphical apps as root, but "sudo -i", "sux", or "su -", are useful to fall back on, especially if you're trying to maintain a minimal installation, and don't want to install gksu with all it's dependencies.

---

### Post by Dennis N on 2011-12-26
Lubuntu's default file manager (pcmanfm) can be opened as root from it's Tools menu:

Tools > Open Current Folder as Root

---

### Post by pretty_whistle on 2011-12-26
> **Dennis N said:**
> Lubuntu's default file manager (pcmanfm) can be opened as root from it's Tools menu:

Tools > Open Current Folder as Root
Well I'll be darned!  There's that lil booger!  I thought he was hiding from me..lol.

Thanx for that. :D

---

