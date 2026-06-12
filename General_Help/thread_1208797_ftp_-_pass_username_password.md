---
title: "ftp - pass username password?"
date: 2009-07-09
forum: General Help
---

### Post by Hawk__0 on 2009-07-09
I'm trying to make a script that will upload a file to an FTP server.  Problem is, I haven't been able to find a way to pass it a username and password in the script.  I want this to be non-interactive.

Can a bash script do this in any way?

---

### Post by geenux on 2009-07-09
I found this :
```
wget ftp://USER:PASSWORD@SITE/URL
```
It works perfectly.
Example :
wget [ftp://geenux:password@ftpperso.free.fr/index.php](ftp://geenux:password@ftpperso.free.fr/index.php) will download index.php.

---

### Post by Hawk__0 on 2009-07-09
Wow thanks, that's brilliant!  Problem is, I need to upload :(

edit: I found the command wput in the repository :D

Problem though: I keep getting login incorrect...

---

### Post by prem1er on 2009-07-09
scp would also work for this.

---

### Post by Hawk__0 on 2009-07-09
It would?  I tried it and -P 21 didn't help, I think it's because it's "secure copy" instead of just ftp authentication..

---

### Post by Slim Odds on 2009-07-09
you might want to look into a program called expect.

It's really good for automating things like this.

---

### Post by iponeverything on 2009-07-09
> **Slim Odds said:**
> you might want to look into a program called expect.

It's really good for automating things like this.

+1

This is the kind of thing that expect does best.

```
apt-get install expect
```

Here is example script for an interactive ftp session:

```
http://en.wikipedia.org/wiki/Expect
```

---

### Post by Hawk__0 on 2009-07-10
Thanks a lot guys, I will definitely try that out.  For now I've found something that works but it's UGLY.  I am using ~/.netrc to define the username/password, and to define an FTP macro.  I then have to call another script which runs the macro (bash doesn't like it when I run it from within the existing script :S)

---

