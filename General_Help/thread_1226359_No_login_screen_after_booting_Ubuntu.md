---
title: "No login screen after booting Ubuntu"
date: 2009-07-29
forum: General Help
---

### Post by orrie on 2009-07-29
After I've booted up my Ubuntu (mediacenter), the logon screen is not showing.
The only thing that is showing is an orange color (the default color).
It's connected up to my TV that supports 1920x1080p and it's set to 16:9.

How to resolve this?

The xorg.conf is attached.





edit:
When I'm running 'sudo /etc/init.d/gdm stop' and 'startx' in tty2, I can see the desktop and do whatever I want to.
The error lays in the login.
But I couldn't figure out what it is.

I have changed a GDM-theme for a while ago, but this haven't been any troubles with before now.
I'm running the 2.6.28-14-generic kernel, Ubuntu 9.04.
When I'm logged in and are looking at the nvidia-settings, the resolution is 1920x1080.


[COLOR="Red"]**Actually, I just realized that it was automatic logged in to the user `media` and there was no background and no possiblity to right click on the desktop.**[/COLOR]

---

### Post by orrie on 2009-07-30
I've solved it.

*The case was this:*
I have enabled automatic login with the user `media` that had no password (had done something with /etc/shadow/ so that the user got an "blank" password).
When the system logged in to the user, the background that was orange was just showing without something else.
That was the problem.

To solve this problem, I did this:
1. Logged in to an another tty, by pressing CTRL+ALT+1.
```
orrie@mediacenter:~$ sudo -i
Password:
root@medaicenter:~# /etc/init.d/gdm stop
root@mediacenter:~# startx

```
In this X-session I removed the user `media` that obvious was making trouble for GDM.
System > Administration > Users and groups
After I've done that, I booted it up in recovery mode and logged in to my user and running the command:
```

orrie@mediacenter:~$ sudo deluser media && sudo rm -rf /home/media/

```

Then when I'm booted the computer up, the GDM-theme was loading and I could login like an regular user.
Bug-problem solved!


[COLOR="Red"]**Be aware that you are loosing all media-data if you are deleting the home directory to the user `media`.**[/COLOR]

---

### Post by manlypain on 2009-07-30
i don't have mine auto login but i don't want to delete the account.  do you think there is a file to remove that would accomplish the same result?

---

### Post by orrie on 2009-07-30
> **manlypain said:**
> i don't have mine auto login but i don't want to delete the account.  do you think there is a file to remove that would accomplish the same result?

Not sure really, you could try to remove all folders that starts with a dot since some of them are configs.
You do have the exact same problem that I had except the auto login?



You could try to delete the user and add it again though, if that makes the same result for you.


To take backup to your home-directory:
```
$ mkdir $HOME/backup/ && sudo cp -R /home/<username> $HOME/backup/ && sudo chown -hR $USER:$USER  $HOME/backup/

```
This commands copies the files into the folder "backup" in your home-folder with the ownership of your user.

To delete the user (this couldn't be done when the user is logged in, you have to go to recovery mode if you don't get access to the user):
```
$ sudo rm -rf /home/<username> && sudo deluser <username> && sudo adduser <username> && passwd <username> temp123

```

Then, to copy the same data (without the directories with an dot before):
```
$ sudo cp $HOME/backup/* /home/<username>/
```

If you have done this, then you should have an "new" user with the same files in the home-directory, and password is temp123.
[COLOR="Red"]Note: This is an unsecure password.[/COLOR]


Or do you want it done another way?

---

### Post by manlypain on 2009-07-30
i figured out my issues

I fixed mine by loading up normally ( but not working) then going over to tty2 ( ctrl-alt-F2) then running

sudo service gdm stop
startx

x started up fine so i knew it was gdm
so i reconfigured gdm automatically after i logged out of gnome ( like normal, it took me back to the prompt)

sudo dpkg-reconfigure gdm


then i rebooted
it worked after that
thanks for the ideas but i think we had different issues

---

