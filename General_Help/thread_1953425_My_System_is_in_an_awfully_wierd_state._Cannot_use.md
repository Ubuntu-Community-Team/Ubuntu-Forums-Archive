---
title: "My System is in an awfully wierd state. Cannot use sudo or login."
date: 2012-04-06
forum: General Help
---

### Post by Flaminghedgehog on 2012-04-06
For what it's worth, this is an urgent matter at hand. I hope to solve this problem in a timely fashion so I may get back to work.

In an elaborated sense, I cannot seem to login to my user ($HOME) directory, however I can login through root. Sudo doesn't work under root either which leaves me concerned for what else I may have done wrong to my system.

Scenario: Home one night, I see a firmware update for my ASUS Android Tablet. Tried to install and it errored out. Thought it may have been a root problem. Tried to unroot my device via[PrimeTime](" http://forum.xda-developers.com/showthread.php?t=1427125") which worked for rooting. Although when I tried to unroot my device, I slowly became victim to seeing a purple background, and all of my icons on my desktop looked like blank files. I cannot click on anything either, I've lost access to them in my session. I also cannot shut down or log off my system while in my session.

Hard reset time!

So this is where I am right now. I cannot login to my usual user, flame, but I can login through root. Sudo doesn't work and I'm afraid to find out what else might be broken. I've also looked through /etc/passwd to see that my user account is gone from the file. However the termainal doesn't throw back incorrect username/password. BUT, when I try to login through my account (flame), I get an error saying cd: cannot cd to directory '/home/flame'

For Reference: I am using Ubuntu 11.04 system. 
I can do a uname -a if desired

Additional screenshots for reference:
[http://i.imgur.com/T3wDn.jpg](http://i.imgur.com/T3wDn.jpg)
[http://i.imgur.com/0kA8k.jpg](http://i.imgur.com/0kA8k.jpg)

PrimeTime.sh, the main file I used to unroot my Android Device.
[http://www.sendspace.com/file/41a3u9](http://www.sendspace.com/file/41a3u9)

Any  help would be greatly appreciated! :)

(By the way, I'm unsure if this is in the right forum or not. Can someone confirm for me if it is?)
(Sent from my ASUS Transformer Prime)

---

### Post by dino99 on 2012-04-06
dont know what driver you have installed, but on Linux, drivers come with the kernel; everything else will break your system (but you still know that now)

The fastest solution: google around "ubuntu+adduser" to log with a new user as yours is borked

The real solution: redo a fresh install

---

### Post by winh8r on 2012-04-06
Try this for starters:

[http://www.psychocats.net/ubuntu/fixsudo#repaircommands]("http://www.psychocats.net/ubuntu/fixsudo#repaircommands")

Although I do not know what you have done when "rooting" the Android device, I don't have one and don't know what the process involves.

It does sound as though you may have altered all the permissions on your home directory which is a bit of a problem.

---

### Post by Zill on 2012-04-06
> **Flaminghedgehog said:**
> ...In an elaborated sense, I cannot seem to login to my user ($HOME) directory, however I can login through root. Sudo doesn't work under root either which leaves me concerned for what else I may have done wrong to my system...
If you *can* "login through root" then this may well be why you are having problems now.  Logging in as root is unnecessary and is positively discouraged with Ubuntu systems precisely because it allows you to break your system so easily.

I suggest you reinstall, *without* enabling the root account!

See the [RootSudo]("https://help.ubuntu.com/community/RootSudo") community documentation.

---

### Post by Flaminghedgehog on 2012-04-06
> **winh8r said:**
> Try this for starters:

[http://www.psychocats.net/ubuntu/fixsudo#repaircommands]("http://www.psychocats.net/ubuntu/fixsudo#repaircommands")

Although I do not know what you have done when "rooting" the Android device, I don't have one and don't know what the process involves.

It does sound as though you may have altered all the permissions on your home directory which is a bit of a problem.

Ironically, this is one of the first few pages I stumbled on. Unfortunately, when I tried to execute one of the cases, this happened.
[http://i.imgur.com/GEysd.jpg](http://i.imgur.com/GEysd.jpg)

'flame' (me) seems to still exist on the system although strangely not in /etc/passwd

@dino99:
A fresh install would seem to fix the problem easily, wouldn't it? Although I have a lot of information on here that I'd hate to lose and I have no way of presently backing it up right now. I do not have an external hard drive, nor the money to purchase one. I have about 30 GBs of data on here and I'd hate to lose it all.

I do appreciate your input though!

---

### Post by winh8r on 2012-04-06
Maybe try doing this:

at the root prompt

```
adduser newflame
```

see if it will create a new account with a new password and let you login normally to the new account.

Then maybe you can get things sorted out from a new admin enabled account.

---

### Post by Flaminghedgehog on 2012-04-06
newflame user added. Everything seemed to go swimmingly well until I tried logging in.

It reads being unable to cd to '/home/newflame', strangely.

Screenshot output:
[http://i.imgur.com/5jMUz.jpg](http://i.imgur.com/5jMUz.jpg)

---

### Post by Flaminghedgehog on 2012-04-06
So I've been looking into this deeper and deeper, and I'm not sure if i'm on the right track with this. I read some neighboring forums about file permissions on some file directories. More specifically /etc/sudoers, /usr/bin/sudo as well as the absolute root directory (/)

[http://i.imgur.com/3vCOz.jpg](http://i.imgur.com/3vCOz.jpg)
Do these permissions look correct? I'm wondering why /usr/bin/sudo is highlighted in red.
> -r--r----- 1 root root    574 2011-05-30 2:06 /etc/sudoers
-rws-r-xr-x 2 root root  168800 2011-05-30 02:06 [COLOR="Red"]/usr/bin/sudo[/COLOR]

I read somewhere I may need to chmod the root directory (/) to 755, but this may be unnessasary. I want to get input from you guys first.

---

### Post by Flaminghedgehog on 2012-04-06
Anybody?

What about a default directory listing? Surely there's one of these I can look off of.

---

### Post by Flaminghedgehog on 2012-04-06
.. Oh hey, so I managed to fix this on my own.

All I had to do was chmod the root directory (/) to 755 (rwxr-xr-x). Surprisingly odd. Although I don't know if any other files had a change mode (chmod) applied to them. Isn't there a command/file that will allow me to see background executions that weren't explicitly executed in the terminal by myself?

So yeah.. I guess [solved] for the most part.

---

### Post by sudodus on 2012-04-06
> **Flaminghedgehog said:**
> So I've been looking into this deeper and deeper, and I'm not sure if i'm on the right track with this. I read some neighboring forums about file permissions on some file directories. More specifically /etc/sudoers, /usr/bin/sudo as well as the absolute root directory (/)

[http://i.imgur.com/3vCOz.jpg](http://i.imgur.com/3vCOz.jpg)
Do these permissions look correct? I'm wondering why /usr/bin/sudo is highlighted in red.


I read somewhere I may need to chmod the root directory (/) to 755, but this may be unnessasary. I want to get input from you guys first.
The first one looks the same, but the second one differs from mine (in Ubuntu 10.04 LTS).

```
-rwsr-xr-x 2 root root 127668 2011-01-19 19:01 /usr/bin/sudo
```
They are almost similar, the difference might be because of different versions, but it might also cause your problem. I have not tampered with these things, so the only thing I can do, is to show the difference.

---

