---
title: "Sudo Account."
date: 2012-09-23
forum: General Help
---

### Post by zahkloxx on 2012-09-23
Allright so, hi!
I'm Bob.
also known as Zahkloxx.

Kinda new to the Ubuntu community.
I only changed from Windows to Ubuntu recently, and I'm already liking it!

Yet, as developer I have encountered but 1 problem.
and that's the permissions I have in ubuntu.

I have an administrator account, yet I can not do all that I wish to do.

I've been told I have to do stuff through the terminal with the prefix "sudo".
But that's not what I am aiming for.
I just want to be able to log into a ROOT acount as soon as I boot up my laptop.

Please help me and tell me what I should do to make the ROOT account enabled to log into from the log-in screen.
I wish to have full permissions INSIDE ubuntu.
and not to everything through the terminal.

That way I would be better off using Windows.

Please help me.

~ Bob, Zahkloxx.

---

### Post by Elfy on 2012-09-23
[http://ubuntuforums.org/showpost.php?p=9315838&postcount=1](http://ubuntuforums.org/showpost.php?p=9315838&postcount=1)

Please read that - in particular

> ** Our "line in the sand" is with tutorials or posts that show people how to LOG IN to a graphical desktop (gnome, KDE, etc) as root. This is completely inappropriate and unnecessary.**

---

### Post by zahkloxx on 2012-09-23
> **Elfy said:**
> [http://ubuntuforums.org/showpost.php?p=9315838&postcount=1](http://ubuntuforums.org/showpost.php?p=9315838&postcount=1)

Please read that - in particular

Please may I know why?
seeing as in my case I find this highly neccesary.

if this REALLY is inappropriate, may I know a simliar solution or maybe is there a simliar OS where Developers are able to freely develope without limitations?


EDIT: Or can I maybe modify my current account so I have the permissions to do what I need to do?

---

### Post by Elfy on 2012-09-23
There are plenty of solutions on the internet - you'll just not be able to get help with it here :)

Everyone finds it highly necessary in their case.

---

### Post by Lars Noodén on 2012-09-23
If you're needed root to develop, you're probably doing it wrong. It defeats the security models that have been in place for years and years.  Yes, it's needed to install packages, but unless you are working at the kernel level, it is largely unnecessary and even harmful.  

What is it that you are really trying to do?

---

### Post by zahkloxx on 2012-09-23
> **Elfy said:**
> There are plenty of solutions on the internet - you'll just not be able to get help with it here :)

Everyone finds it highly necessary in their case.

I see, well thanks anyways.
I'll see if I can find some un-official forum where they are able to help me with activating a graphical ROOT account.

~ Bob, Zahkloxx.

---

### Post by zahkloxx on 2012-09-23
> **Lars Noodén said:**
> If you're needed root to develop, you're probably doing it wrong. It defeats the security models that have been in place for years and years.  Yes, it's needed to install packages, but unless you are working at the kernel level, it is largely unnecessary and even harmful.  

What is it that you are really trying to do?

Well I want to be able to add, remove, modify and replace files, praciticly ANYWHERE on my system.

As for example, I have a LAMPP server, installed in /opt/lampp.
Yet I cant do anything with it.

It's like owning a car but you don't have the keys.
So it's just standing there, and you're like
"Yea I got a car! it's right there!, I just can't drive it." 

I just want to be able to work without those limitations.

---

### Post by thnewguy on 2012-09-23
Most tasks you do not need to use the terminal and sudo for. Usually if you are using a program and it requires root access it will prompt you for your password. That will temporarily give the program you are using the ability to act as root. There really isn't any reason for anyone to regularly use the root account It is a much safer way to work than enabling the root account and logging into it.

Really, Ubuntu's security model is similar to the Windows model you mentioned. In Windows you generally aren't really the admin user, you're a semi-privileged user who can use UAC to temporarily act as the administrator. Ubuntu uses the same approach, but asks for your password instead of having you respond to an Allow/Cancel dialog box.

---

### Post by zahkloxx on 2012-09-23
> **thnewguy said:**
> Most tasks you do not need to use the terminal and sudo for. Usually if you are using a program and it requires root access it will prompt you for your password. That will temporarily give the program you are using the ability to act as root. There really isn't any reason for anyone to regularly use the root account It is a much safer way to work than enabling the root account and logging into it.

Really, Ubuntu's security model is similar to the Windows model you mentioned. In Windows you generally aren't really the admin user, you're a semi-privileged user who can use UAC to temporarily act as the administrator. Ubuntu uses the same approach, but asks for your password instead of having you respond to an Allow/Cancel dialog box.

Precisely, and I turned off UAC.
Also in Windows I was capable of doing whatever I please to do.
While in Ubuntu I'm not allowed to change, modify, add or remove files where I need them to do so..

---

### Post by Lars Noodén on 2012-09-23
Something went south there.  The data for the [LAMP server](https://help.ubuntu.com/community/ApacheMySQLPHP) should have ended up in /var/www by default.  There, once you set the permissions, you no longer need root access to work in the document root.  If you are the only one on the machine then it is enough just to change ownership of the directory before you begin.

```

sudo chown -R zahkloxx /var/www

```

---

### Post by zahkloxx on 2012-09-23
> **Lars Noodén said:**
> Something went south there.  The data for the [LAMP server](https://help.ubuntu.com/community/ApacheMySQLPHP) should have ended up in /var/www by default.  There, once you set the permissions, you no longer need root access to work in the document root.  If you are the only one on the machine then it is enough just to change ownership of the directory before you begin.

```

sudo chown -R zahkloxx /var/www

```

Thanks Lars! finally something that worked.

But do I have to continue doing this for every single location?
Can't I just globally do this for everything?

---

### Post by Lars Noodén on 2012-09-23
> **zahkloxx said:**
> Thanks Lars! finally something that worked.

But do I have to continue doing this for every single location?
Can't I just globally do this for everything?

Not really, that would nuke you system into unusability.  But you can do it for all your data directories.  But you only need to do it once before you get going.  

Windows is the odd-man out in the computing world.  All the other systems are (except for CP/M and a few other dinosaurs) designed for a networked, multi-user environment.  There is also a separation between programs and data.  Both factors mean that although things may be simple and logical there are certain ways of doing things.  It's easy to learn even if you are new.

Just as a precaution, double-check the LAMP documentation linked above and make sure everything is set up properly in the right locations.  There is a [place for everything](http://manpages.ubuntu.com/manpages/precise/en/man7/hier.7.html) and nothing should have ended up in /opt during LAMP setup.

---

### Post by zahkloxx on 2012-09-23
> **Lars Noodén said:**
> Not really, that would nuke you system into unusability.  But you can do it for all your data directories.  But you only need to do it once before you get going.  

Windows is the odd-man out in the computing world.  All the other systems are (except for CP/M and a few other dinosaurs) designed for a networked, multi-user environment.  There is also a separation between programs and data.  Both factors mean that although things may be simple and logical there are certain ways of doing things.  It's easy to learn even if you are new.

Just as a precaution, double-check the LAMP documentation linked above and make sure everything is set up properly in the right locations.  There is a [place for everything](http://manpages.ubuntu.com/manpages/precise/en/man7/hier.7.html) and nothing should have ended up in /opt during LAMP setup.

Thanks Lars, this is actually very helpful, and Ubuntu forum admins could take you as an example.


You have both my thanks and respect.
~ Bob, Zahkloxx.

---

