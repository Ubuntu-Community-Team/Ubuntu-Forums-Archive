---
title: "Login as root"
date: 2011-10-22
forum: General Help
---

### Post by lwalper on 2011-10-22
Is there any way to set permissions so that I can automatically log in as root when the system starts up? I get tired of trying to do something (like move a file from one folder to another) without getting "Error moving file: Permission denied".

---

### Post by masgeeks on 2011-10-22
Sudo doesn't work for you?  gksudo nautilus ?  If you do that from command line you can move files around all you like.

Auto login is an evil thing.  Have you done sudo passwd root and set a root password?  If so, you can just log in as root from the login screen, but its never recommended to run as root...

---

### Post by lisati on 2011-10-22
The ability to login as "root" has been disabled in Ubuntu. Please take a look at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by masgeeks on 2011-10-22
Interesting - guess I should tell Canonical that I was able to log in as root, huh...???

lol

---

### Post by CharlesA on 2011-10-22
> **masgeeks said:**
> Interesting - guess I should tell Canonical that I was able to log in as root, huh...???

lol
If you want to tell them I suppose you could..

Find more info [here]("http://ubuntuforums.org/showthread.php?t=1486138").

That being said - we don't support logging in as root, or showing people how to login as root here.

It's easy enough to google to find out how.

---

### Post by lisati on 2011-10-22
> **masgeeks said:**
> Interesting - guess I should tell Canonical that I was able to log in as root, huh...???

lol

It can be done, but we normally point people who ask in the general direction of sudo.

---

### Post by egalvan on 2011-10-22
The OP doesnt only want to log in as root ...

**automatically log in as root when the system starts up**

He wants to do it AUTOMATICALLY ON LOGIN.

Talk about a security nightmare...
and a cracker's delight!:KS

---

### Post by MG&amp;TL on 2011-10-22
If you just want a shell as root(permamently, until you close the shell), then:

```
sudo -i
```

```
sudo bash
```

```
sudo gnome-terminal
```

All work. (although I understand sudo -i is preferred.)

I really wouldn't reccomend automatic login <fullstop>, let alone as root.

---

### Post by MG&amp;TL on 2011-10-22
Or you could try Debian, which is where ubuntu comes from. Which does have root login.

[http://www.debian.org/]("http://www.debian.org/")

..considerably less user-friendly though.

---

### Post by CharlesA on 2011-10-22
> **egalvan said:**
> The OP doesnt only want to log in as root ...

**automatically log in as root when the system starts up**

He wants to do it AUTOMATICALLY ON LOGIN.

Talk about a security nightmare...
and a cracker's delight!:KS

Thought there was a policy in place that prevented logging into the GUI as root?

I haven't tried it, but I seem to recall something like that.

---

### Post by T.J. on 2011-10-22
Before I say how, I want you to keep in mind that logging is as root is considered VERY "bad".  I cannot underemphasize the risk you'd be taking to log in as root automatically.  You can delete protected files and "hose" your entire installation with little or no warning.  

That does not even take into account that many programs will refuse to run as root for security reasons or the holes in security you might unknowingly create.   


Please consider what you are about to do very carefully.  Be sure that it is what you want, and make lots and lots of backups!




Since there is not real difference between Debian and Ubuntu, you can enable root logins on Ubuntu simply by resetting the root password with sudo.

sudo passwd root

You can disable it again

sudo usermod -L root


You should be able to set automatic GUI logins from that point.

---

### Post by coffeecat on 2011-10-22
@OP, what you are asking is not good practice which is why there is a forum policy about root logins. The two important links have been posted, but here they are again: 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[Forum policy on log-in-as-root tutorials](http://ubuntuforums.org/showthread.php?t=1486138)

Thread closed.

---

