---
title: "Cannot Access my Home Partition: Lack Permissions"
date: 2010-10-11
forum: General Help
---

### Post by Sef on 2010-10-11
How can I set my permissions so I can access my home partition? (I am the sole user.)

---

### Post by oldfred on 2010-10-12
See this on some info:

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by Sef on 2010-10-13
Tried first command ('sudo chown username /home/username/.dmrc'), and I lost all of my permissions. Now I can do nothing, and other than the terminal coming up, nothing works.

Any ideas or should I just reinstall.

Note: Dual boot with Windows 7 from which I am writing this from.

---

### Post by dino99 on 2010-10-13
just checked mine:

owned by user: read & write
group: user read only
others: read only

[http://ubuntuforums.org/showthread.php?t=847406](http://ubuntuforums.org/showthread.php?t=847406)

---

### Post by garvinrick4 on 2010-10-13
What happens when you open nautilus in root?
Properties in home and change permissions and save their.
Should work.
 *Just noticed you were down hope you get her running quickly.

---

### Post by Rocket2DMn on 2010-10-13
Can you show us what the permissions are? You can try from a root console or a LiveCD.
```
ls -l /home/*yourusername*
ls -l /home/*yourusername*/.dmrc
```

Normally you need to chown with the default group, too (from a root console):
```
chown *yourusername*:*yourusername* /home/*yourusername*/.dmrc
```
You can also recursively chown your home directory if stuff is really messed up:
```
chown -R *yourusername*:*yourusername* /home/*yourusername*
```

---

### Post by nothingspecial on 2010-10-13
Is it a multi user system.

I ask because this got me a few days ago. I created the accounts in the wrong order. As a result all the gids were wrong.

First user was me so that was fine gid 1001

But I did the wife and kids in the wrong order and had to remove them then readd the account with the correct gids to solve it.;

---

### Post by Sef on 2010-10-15
When I went into Ubuntu to try to get my permissions back, I got these 3 error messages (in order):

1) Could not update ICEauthority file /home/sef/.ICEauthority

2) There is a problem with configuration server (/usr/lib/libconf 2-4/gconf-sanity-2 exited with status 256.

3) Nautilus could not create the  following required folders. /home/sef/Desktop, /home/sef/.nautilus

What can I do?

---

### Post by nothingspecial on 2010-10-16
Boot into recovery mode, root shell, whatever they call it these days. (Hold down shift during boot)

```
chown -R sef:sef /home/sef/
chmod 644 /home/sef/.ICEauthority
chmod 644 /home/sef/.dmrc
exit
```

---

### Post by Sef on 2010-10-17
> Boot into recovery mode, root shell, whatever they call it these days. (Hold down shift during boot)

Code:
chown -R sef:sef /home/sef/
chmod 644 /home/sef/.ICEauthority
chmod 644 /home/sef/.dmrc
exit

After unsuccessful doing the above permissions, I reinstalled 10.10 and found the problem, which I posted in a [new thread]("http://ubuntuforums.org/showthread.php?p=9984639#post9984639"). Basically the files on my external hard drive which I want to copy over, do not have any permissions.

---

