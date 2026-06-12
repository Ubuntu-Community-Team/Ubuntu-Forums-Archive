---
title: "Stupid to run as root?"
date: 2010-05-19
forum: General Help
---

### Post by unplugged23 on 2010-05-19
Hey guys,

Something that I've always heard is that it's stupid to log-in as the root user for all of your daily tasks. This is not something that I'm interested in doing, but I am interested in the reasoning behind this.

Why is it stupid to perform all of your daily tasks as root?

---

### Post by -humanaut- on 2010-05-19
If your logged in as Root you have full access to all the files and could accidentally delete important files essential to running your system also if there where a remote attack against you while running as root and someone gained access to there system they would have Root access. (thats one of the major vulnerabilities in Windows)

---

### Post by cloyd on 2010-05-19
If you are not logged in as root, any time you try to make a change to your system, you will be asked for your password. It gives you a little time to think, especially at the terminal. If you were by mistake to enter a destructive command, many of which are quite simple looking, without sudo, you will be told to retry and use sudo, and then asked for your password.  You know you are in areas where you need to be careful.

If you log in as root, you can do what you please. If you enter into dangerous territory, you will get no warning; whatever you tell the machine to do, it will do, even if you tell it to erase your file system.

So, don't log in as root unless there is no other way. If you must, do what you have to do, and get out.  

By the way, "sudo" will give you administrative privileges for a few minutes, but just a few minutes. Watch what you do right after you use sudo.

Humanaut said it better and more concisely and mentioned a few things I didn't.

---

### Post by Serpher on 2010-05-19
First of all after using sudo, it just allows you to not have to type in the password to use sudo again. You still have to run everything with sudo to carry out admin tasks.

The main reason logging in as root is bad isn't because you can accidentally mess things up, rather than it would be exactly like Windows. The reason Windows sucks so hard is because your system is slowly messed up because even your internet browser has the Windows equivalent of "root" privilege. Javascript is then ran on your computer when you go on any website which pretty much means a website can do anything it wants to on your computer. The reason Linux is so secure is you're not really on an account that can do anything, rather than just getting root to quickly get things started up for you.

---

### Post by pqwoerituytrueiwoq on 2010-05-19
why do you need to login as root?
in 10.04 you can login as root if you set the root password

---

### Post by pizza-is-good on 2010-05-19
And if you ever need to run a program using root privileges you can always gksudo it.

Anyway, I only had to log in as root once. I don't remember what for, but I think it was while setting up some of those 'cheap' linux distros... It was a long time ago, but I remember that I couldn't get whatever I needed to get fixed done, so I tried Ubuntu!

Moral of the story, don't log in as root.

---

### Post by unplugged23 on 2010-05-21
Hey guys,

Sorry for the late reply, I've been busy lately, but thanks for all of these answers!

To answer your questions, I have to reason to log in as root, and I didn't want to. I had just heard it was stupid and was curious as to why.

Thanks again!

  -plugged

---

### Post by todak on 2010-05-21
Deleted by todak. After reading the 2nd message from OP, I believe he meant to say "I have NO reason..." rather than "TO reason..."

---

### Post by jerome1232 on 2010-05-21
It's not so much you as it is your programs that your running.

You really want every flash, javascript and java program you run having full access to your system? You want your email client having root access? You want Open Office having root access? (opening a document that exploits Open Office could possibly lead to a system wide infection)

They could do **anything**. Without your knowledge. anything. Including rooting your computer and creating backdoors which allow further compromising in the future.

So essentially running as root to do everyday tasks is asking to be taken down by malware. Infact it's begging for it.

---

