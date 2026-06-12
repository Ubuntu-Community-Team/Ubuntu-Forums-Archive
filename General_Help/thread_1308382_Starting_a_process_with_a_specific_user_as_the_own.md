---
title: "Starting a process with a specific user as the owner - is this possible?"
date: 2009-10-31
forum: General Help
---

### Post by viking_maniac on 2009-10-31
Usually when I start an application, the process is owned by me as in the user that I've logged into during startup.

I would like to do something strange, and I want to know if this is even possible:

I want to start an application, but when the application is running, it is then owned by another user that I've made, even though when I'm logged in with my own account and started the app from there.

I've already seen this happen after I installed TOR; even though I start the TOR app as my own personal user, the app is actually owned by [COLOR=Red]debian-tor[/COLOR] when I see it on the system monitor.

Thanks in advance! :)

---

### Post by oraerk on 2009-10-31
if the program you gonna run is normal executable and not some script, than you can use "set uid" bit ([http://en.wikipedia.org/wiki/Setuid](http://en.wikipedia.org/wiki/Setuid)). That fore you should do the following:
1) chown <user> <file> (where <user> is the one who's authorizations are to be used, <file> - target executable)
2) chmod +xs <file>

---

### Post by slakkie on 2009-10-31
Make a script:

```

#!/usr/bin/env bash

su - supybot -c "/usr/bin/supybot -d /home/supybot/supybot.conf"

```

Call the script as root, eg sudo supybot.sh

---

### Post by viking_maniac on 2009-10-31
I don't mean to offend anyone, but this was like reading Chinese.

It looks like a dead end to me; but thanks anyways! :)

---

### Post by slakkie on 2009-11-01
> **viking_maniac said:**
> I don't mean to offend anyone, but this was like reading Chinese.

It looks like a dead end to me; but thanks anyways! :)


It is not complex, as root you need to run 

su <username> -c "<command to execute as username>

eg,
```

su - supybot -c "/usr/bin/supybot -d /home/supybot/supybot.conf"

```

Runs */usr/bin/supybot -d /home/supybot/supybot.conf* as the *supybot* user.

Only thing you need to do, it run this as root. You put this in a script, call the script as root.

---

### Post by viking_maniac on 2009-11-01
What I want to do, as one example, is to make a system account (not an ordinary account).
Then I'd like to start e.g. kate (KDE text editor) as that user, not the user that I've logged in with, or start whatever program I'd like with that new system account.

I did try your sample, slakkie, but I got a lot of error messages in the console.

---

### Post by slakkie on 2009-11-01
Would be helpfull if you posted the error messages :)

---

### Post by blueridgedog on 2009-11-01
> **viking_maniac said:**
> What I want to do, as one example, is to make a system account (not an ordinary account).
Then I'd like to start e.g. kate (KDE text editor) as that user, not the user that I've logged in with, or start whatever program I'd like with that new system account.

I did try your sample, slakkie, but I got a lot of error messages in the console.

Question:  Why?

Also, if you post the errors Slakkie and others can help find the source of them.

---

### Post by viking_maniac on 2009-11-01
> **slakkie said:**
> Would be helpfull if you posted the error messages :)

Sorry...

$ sudo su test -c kate
or
$ su test -c kate

[COLOR=Red]No protocol specified
kate: cannot connect to X server :0.0

[COLOR=Black]I made a standard user named *test*[/COLOR][/COLOR]

---

### Post by sisco311 on 2009-11-01
```
sudo -i -u username kate
```

---

### Post by viking_maniac on 2009-11-01
> **blueridgedog said:**
> Question:  Why?


I just want to learn how to run specific application with spesific user accounts. I think this could be a nice thing to learn for the future if I should need one spesific application to have specific permissions. :)

---

### Post by viking_maniac on 2009-11-01
$ sudo -i -user test kate

[COLOR=Red]sudo: unknown user: ser[/COLOR]

---

### Post by slakkie on 2009-11-01
> **viking_maniac said:**
> Sorry...

$ sudo su test -c kate
or
$ su test -c kate

[COLOR=Red]No protocol specified
kate: cannot connect to X server :0.0

[COLOR=Black]I made a standard user named *test*[/COLOR][/COLOR]


That is because of a graphical interface

su test -c "DISPLAY=$DISPLAY kate"

Try that.

---

### Post by sisco311 on 2009-11-01
to start a GUI app you have to allow the user to connect to the x server:
```
xhost +SI:localuser:**username**
```

oh, a typo in my first post;

it's:
```
sudo -i -u **username** kate
```

---

### Post by viking_maniac on 2009-11-02
> **sisco311 said:**
> to start a GUI app you have to allow the user to connect to the x server:
```
xhost +SI:localuser:**username**
```oh, a typo in my first post;

it's:
```
sudo -i -u **username** kate
```

Finally!! :D 

:KS:KS:KS:KS:KS

I can now run both terminal and window apps as test!

But when I use the sudo command to launch this, does that mean that TEST get sudo permissions?

Are there any security risks by doing this?

Thanks to all of you who have helped me out! :)

---

### Post by sisco311 on 2009-11-02
> **viking_maniac said:**
> Finally!! :D 

:KS:KS:KS:KS:KS

I can now run both terminal and window apps as test!


Cool! To run GUI applications use kdesudo:
```
kdesudo -u username application
```

> **viking_maniac said:**
> 
But when I use the sudo command to launch this, does that mean that TEST get sudo permissions?


No, sudo allows you to execute a command as the superuser(root) or another user. If no user is given, the default is root, the superuser.

> **viking_maniac said:**
> 
Are there any security risks by doing this?


Be careful with the environment variables, use kdesudo for GUI applications.

[http://psychocats.net/ubuntu/graphicalsudo]("http://psychocats.net/ubuntu/graphicalsudo")

> **viking_maniac said:**
> 
Thanks to all of you who have helped me out! :)

You're welcome!

---

