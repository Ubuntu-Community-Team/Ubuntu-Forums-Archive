---
title: "GDM configuration Error"
date: 2009-07-22
forum: General Help
---

### Post by kxhitiz on 2009-07-22
Hello I got problem starting my ubuntu 9.05.
When starting Ubuntu it stops in following line

> 
#starting system log daemon ---[ok]
#starting kernal log daemon ---


Later it gave error this:
> Server authorization directory (daemon/ServAuthDir) is set to /var/lib/gdm but this does not exist. Please correct GDM configuration & restart GDM

I think i need to correct GDM configuration, so please can you suggest me how to do this.

---

### Post by kxhitiz on 2009-07-22
ain't here anyone to solve my problem?

---

### Post by Enneagon on 2009-07-23
I get a very similar error after installing updates and restarting my computer. I don't have a solution and if someone cannot help me fix this I'm gonna bail!

---

### Post by stoneage on 2009-07-23
I have no idea what the problem is, but you could as a last resort try reinstalling gdm:-

```
sudo apt-get --reinstall install gdm
sudo shutdown -rn now
```

---

### Post by Zorael on 2009-07-23
Maybe the directory it complains about really doesn't exist?
```
$ file /var/lib/gdm
**/var/lib/gdm: ERROR: cannot open `/var/lib/gdm' (No such file or directory)**

$ sudo mkdir /var/lib/gdm
$ sudo service gdm restart
```

---

### Post by Enneagon on 2009-07-25
Stoneage and Zorael (dawn god?) could you explain what the codes you recommend are doing? Also when I try to do anything in sudo I am told that I am not in the sudoer file. I am pretty unacustomed to working in code and I don't know what the commands mean.

---

### Post by Zorael on 2009-07-26
> **Enneagon said:**
> Stoneage and Zorael (dawn god?)
Hmm, dawn god? Is that a reference?

> could you explain what the codes you recommend are doing?
Certainly. The first command just accesses /var/lib/gdm and divines what that location *is*. It's supposed to be a directory, but your error message suggests that it doesn't exist at all. If it doesn't return the text highlighted in bold, don't bother with the other commands.

The second command creates /var/lib/gdm as a directory (mkdir = "make directory"), hopefully satisfying what spawned the error in the first place.

The third command restarts GNOME, but you could just reboot the system instead.

> Also when I try to do anything in sudo I am told that I am not in the sudoer file.
Hmm, I think that suggests your user account lacks the privileges to use sudo. That's great for security, but can be in the way when you need to fix stuff. Did someone else set up your installation for you?

---

### Post by Enneagon on 2009-07-26
Zorael thank you for your help, first the (dawn god?) was curiosity about your name. I am somewhat interested in etymology and the meaning of names. Maybe it would not please you to know but zora is I believe Slavic for dawn and el is Hebrew for god. It would be a bit of a linguistic mash-up but it is what I saw in your name.

I just retried the commands you suggested and after the first one I do get the the text you predict. Then I enter the second command and I am prompted with ```
[sudo] pasword for michael:
``` I then enter my pass word that I use for all administrative tasks and then I get ```
michael is not in the sudoer file. this incident will be reported.
``` I was the one who set up my installation and I cannnot recall doing anything out of the ordinary. I am ignorant enough that I usually just click on standard installation whenever I install anything. I may have somehow removed administrative priveleges from my user account (when I was running windows I didn't use the computer as an aministrator at the recommendation of a friend) but it is the only user account on the computer, and I cannot imagine what else I could have used as a password when I installed the OS.

I wonder if my hard drive could be damaged and be unable to access the critical parts.

---

### Post by Zorael on 2009-07-27
> **Enneagon said:**
> It would be a bit of a linguistic mash-up but it is what I saw in your name.
Ah, I see. Well, that's news to me; I just made up the name as a game character long ago, and it's stuck ever since. ;3

As for you not being in the sudoers group, you should be able to remedy this, but we'd have to figure out what's actually wrong first.

When trying out these commands, have you been in recovery mode? Seeing as gdm has been complaining (and gdm starting is practically a prerequisite to get the graphical interface going), I thought for sure your system was in an unusable state.

If you're in recovery mode, you're automatically logged in as root, and root is the very embodiment of the superuser. So in that case, you needn't prepend sudo to those commands; just run the second, then exit recovery mode and pick **resume**.
```
# mkdir /var/lib/gdm
# exit
*(pick resume)*
```

As for fixing your user to be allowed to use sudo, what is the output of the following command (when logged in as your user and not root)?
```
$ groups
sunspire adm dialout cdrom plugdev lpadmin **admin** sambashare
```
Your output will differ from mine a bit, but if yours doesn't contain **admin**, then you don't seem to belong to the group that's set up by default to be able to use sudo. To fix this, you need to be root again, in a recovery session.
```
# adduser *michael* **admin**
```
(Replace *michael* if that's not your username.) If that doesn't help either, then there really could be something wrong with your sudoers file. That can be fixed in a recovery session, as well, if need be.

---

### Post by Enneagon on 2009-07-27
Zorael, thanks for all your help. So, the way things stand is I went into recovery mode by hitting Esc during startup and once there this is what I did and got: ```
root@michael-laptop:~# file var/lib/gdm
**var/lib/gdm: ERROR: cannot open `var/lib/gdm' (No such file or directory)**
root@michael-laptop:~# mkdir var/lib/gdm
**var/lib/gdm: ERROR: cannot create directory `var/lib/gdm' No such file or directory**
```

---

### Post by Enneagon on 2009-07-27
Stoneage, how much of a last resort is your recommendation? I have been hesitant to use it because you put it that way. my ultimate goal is to keep all the data on my hard drive.

---

### Post by Zorael on 2009-07-27
> **Enneagon said:**
> ```

root@michael-laptop:~# mkdir var/lib/gdm
**var/lib/gdm: ERROR: cannot create directory `var/lib/gdm' No such file or directory**
```
You forgot a slash;
```
# mkdir **[COLOR="Red"]/[/COLOR]**var/lib/gdm
```

---

### Post by Enneagon on 2009-07-27
so I did. now I get: ```
/var/lib/gdm: sticky directory
```

---

### Post by Zorael on 2009-07-28
Do you still get the error now, then?

---

### Post by Enneagon on 2009-07-28
I first tried to do ```
~#mkdir /var/lib/gdm
**mkdir: cannnot create directory `/var/lib/gdm': File exists**
```Then I entered ```
~#file /var/lib/gdm
**/var/lib/gdm: sticky directory**
```Which seems strange to me because if I do not press Esc during start up then I see the Ubuntu logo and it looks like it is loading but then a blue screen with a gray window with the message

 "The GDM user 'gdm' does not exist. Please correct GDM configuration and restart GDM." 

Then I have to hit spacebar or enter to get to a command prompt login. And that is where I can do nothing because I am not in the sudoer file.

---

### Post by Zorael on 2009-07-28
I don't know enough about gdm to take it from here. Try reinstalling the package (you won't lose any settings). From a recovery session, do the following.
```
# aptitude reinstall gdm
```

---

