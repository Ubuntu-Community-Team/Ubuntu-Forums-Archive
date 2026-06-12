---
title: "Root Permission- 9.10 remix"
date: 2009-11-03
forum: General Help
---

### Post by peter1128 on 2009-11-03
I have install 9.10 remix on my netbook no problem. That was until I came to loging in as root.

On 8.04 & 8.10 I would I set up a password of root in the Users and Group (user setting) the go to the system-administrator-login window and click the allow local system administrator login.. and bobs your fathers brother.

But 9.10 remix we have the users and groups but no login window so how do I get to login as root? :(

---

### Post by sisco311 on 2009-11-03
We can not help you, it's against the forum policy:
[thread=716201]Forum policy on log-in-as-root tutorials[/thread]

---

### Post by wildweathel on 2009-11-03
Yeah, sorry.  Forum rules.  But, you probably don't have to run as root.  Maybe 5% of what you need to do requires root access, and 80% of that will prompt your for your password.  For the last 2% of your Ubuntu life (random numbers, by the way), forum policy requires us to point you to sudo (text)/gksudo (gnome/XFCE)/kdesu (KDE).

Most of the time this is really easy.  Like typing ```
sudo apt-get install
``` instead of ```
apt-get install
```.  You can also type ```
sudo -i
``` for a root shell.  If you have more complex needs, please say what your trying to do "FooServer needs to run as root," not just "I need a root login."

---

### Post by peter1128 on 2009-11-03
Sorry, my error no reading the rules
Well that's me out the game.
I need root to access the www folder in my local PHP set up

Back to working on windows.

Thanks for trying to help. I guess this is where it better to run window that linux.

---

### Post by alphaniner on 2009-11-03
You've been using Ubuntu since 8.04, and you're going to give up because of this?  If it really means that much to you, you could probably get help on another forum.  Although you would be better off taking 5 minutes to learn how to use sudo.

---

### Post by sisco311 on 2009-11-03
You can run applications as root with sudo/gksu.

For exemple to run your file manager as root:
```
gksu nautilus
```

[uhelp]community/RootSudo[/uhelp]

Take a look at this howto:
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

It will show you how to set up a LAMP server.


You can change DocumentRoot to point to the new location(not /var/www). For example, ~/public_html/ in your home directory:
[https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual Hosts]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual Hosts")

or you can simply chown the /var/www directory:
[https://help.ubuntu.com/community/ApacheMySQLPHP#Using Apache]("https://help.ubuntu.com/community/ApacheMySQLPHP#Using Apache")

---

### Post by peter1128 on 2009-11-03
Something as straight forward as add php & mysql to you netbook should not come with all the problems of accessing the root.

This is were Linux falls down a great basic desktop but move away from the open offices of the world and you are hit with problems.

I have been trying for year to get other people to use Linux and hitting a brick wall.

Even I'm getting cheesed off I wish they would stick with one version for a few years but no a update (new version) every 6 months.. no wonder we have problems.

---

### Post by sisco311 on 2009-11-03
never mind

---

### Post by QLee on 2009-11-03
[QUOTE=peter1128]Something as straight forward as add php & mysql to you netbook should not come with all the problems of accessing the root.[/QUOTE]

Well, I for one want it to be difficult for someone to install software on a system until they understand how the system works. But your needs may be different.

[QUOTE=peter1128]This is were Linux falls down a great basic desktop but move away from the open offices of the world and you are hit with problems.[/QUOTE]

It's generally Windows sys admins who have this kind of trouble until they learn about GNU/Linux.

[QUOTE=peter1128]I have been trying for year to get other people to use Linux and hitting a brick wall.[/QUOTE]

No surprise there, you don't appear to like it yourself and I imagine they can tell.

[QUOTE=peter1128]Even I'm getting cheesed off I wish they would stick with one version for a few years but no a update (new version) every 6 months.. no wonder we have problems.[/QUOTE]

Well, something like you are talking about is a LTS version of Ubuntu or something like Debian "stable". The newest versions are "cutting edge", naturally, people want the "newest" with a few problems for their desktops but a server doesn't always need the newest version of apps. Nothing is forcing you to use the newest version on your laptop, if you hardware works and you have the apps you need.

I hear your frustration, I understand how hard it is to learn things when we are frustrated and probably working under a time limit. Good luck.

---

### Post by bodhi.zazen on 2009-11-03
> **peter1128 said:**
> Something as straight forward as add php & mysql to you netbook should not come with all the problems of accessing the root.

To be honest, you are making a mountain of a mole hill. Just as you did not learn windows in a day, it takes time to learn to sys admin an new OS.

This is a security feature and to edit system files you can use either the command line :

```
sudo -i
```

and then chown / chmod :

[FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions") 

Or you can do it from a GUI

```
gksu nautils
```

bottom line: Just as with Windows, take the time to learn to sys admin and you will see this s a simple matter.

> This is were Linux falls down a great basic desktop but move away from the open offices of the world and you are hit with problems.

I have been trying for year to get other people to use Linux and hitting a brick wall.

Even I'm getting cheesed off I wish they would stick with one version for a few years but no a update (new version) every 6 months.. no wonder we have problems.

Ubuntu is not for everyone and , as I suggested above, you need to be wiling to learn.

---

### Post by OfNoNation on 2009-11-08
> You've been using Ubuntu since 8.04, and you're going to give up because of this? If it really means that much to you, you could probably get help on another forum. Although you would be better off taking 5 minutes to learn how to use sudo.With the signature starting...>  "Guard with jealous attention the public liberty. Suspect everyone who approaches that jewel."Is that irony?

Why is this a taboo?
What happened to the open-sourceness if Linux?
Shouldn't we all have the freedom to choose what we do on our own computer?  Isn't that what open source is all about?
You could say...'this is how you do it, but don't come here looking for solutions when you screw it up'?
Unfortunately it's this kind of attitude that will send many back to Windows.

To the original poster... I suggest you reinstall the older version that gave you the access you require.

---

