---
title: "startup programs and ssh related questions"
date: 2009-08-26
forum: General Help
---

### Post by headrock29 on 2009-08-26
i have been using ubuntu for a while, and finally managed to get up my ssh server =D i was just wondering though perhaps to decrease ram i can find a list of all the programs that startup with ubuntu, and than uninstall them, or prevent them from starting up, how would i go about doing this through cli?

also after i created my ssh server i used the command 
sudo useradd -m username
sudo passwd username
but 1) when i use terminal its all weird, like tab doesnt complete like regular rather inserts a large space
2) i tried using the same private rsa key i use for my main acount, and it doesnt work either =/ how would i go about making a rsa private key that works? again through cli
thank you so much,
struggling with ubuntu but really worth it!!
rock

---

### Post by bchurchill on 2009-08-27
The easiest list of startup programs is what gnome does, and that's in the menus:
System->Preferences->Startup Applications

If you're into the sort of thing, there are also daemons which run in the background.  The scripts that start and stop them are located in /etc/init.d.  **You almost definitely do not want to modify or delete these scripts.**  There are symbolic links in the /etc/rc0.d, /etc/rc1.d,... directories starting with an "S" or a "K", and then a number.  S means start, K means kill.  Each directory corresponds to a different "runlevel".  I highly recommend reading about those before continuing.  

For example, if you do ls /etc/rc2.d you'll see a symbolic link called "S16ssh" (or similar) pointing to the script /etc/init.d/ssh.  This means that whenever you enter runlevel 2 the secure shell daemon will startup.  If you wanted to disable this, **you wouldn't delete the symbolic link**, rather you would rename the symbolic link to "K16ssh".  And would do the same for other applicable run levels.

Hope that helps.

---

### Post by slakkie on 2009-08-27
1) user issue with tab completion:

chsh and select a propper shell, eg /bin/bash or /bin/zsh, you can find out which shells you can use by running cat /etc/shells

2) disabling services

You can either remove the init.d scripts, or make them not executable. The latter is prefered:

sudo chmod -x /etc/init.d/service_you_dont_want_to_start

In addition to bchurchill, you can remove the scripts from rc?.d, you just need to make sure you really don't need them. Most of the scripts are provided by the package, so removing them can be undone by reinstalling the package... However, I would prefer to remove the executable flag. Undoing that is much easier then undeleting files ;)

---

### Post by headrock29 on 2009-08-27
thank you very much for bcchurchill!
so i will definitely check into these scripts, and will not delete them =D
if gnome is the only way to prevent startup programs than gnome i shall boot into, though i figured there must be some way to do it via cli, like a file that lists all the startup programs ^_^ 

now if anyone can tell me about the terminal and the private key, I would greatly appreciate it =D

thnx again!

---

### Post by slakkie on 2009-08-27
for your private key:

```

# Generate ssh keys
for protocol in rsa dsa
do
    file=$HOME/.ssh/id_${protocol}
    ssh-keygen -t $protocol -N "" -f $file
done

# Copy key file to the other box
ssh-copy-id server

# test your passwordless login
ssh server

```

done.

---

