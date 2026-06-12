---
title: "Can't Login after fresh install of karmic"
date: 2010-02-17
forum: General Help
---

### Post by cforput on 2010-02-17
I did a fresh install of karmic and everything (wifi, graphics, sound, etc) actually worked UNTIL........

I rebooted and I received 3 errors in the following order before getting to a login screen:

1) +could not update ICEauthority file /home/username/.ICEauthority". My only option was to close the error message so I did.

2) There is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256. Again only option was to close the error message

3) Nautilus could not creae the following required folders; /home/username/desktop, /home/username/.nautilus. Only option this time was an OK button

I then get a wallpaper type screen (mustard yellow) but there are absolutely no icons or options available. If I press ctrl-alt-del I can shutdown, reboot, etc.

I booted with my Live CD and finally found my way to my home folder /home/username. I did an ls -l and it shows this:
dr-x------ 2. The ubuntu user off of the Live CD shows this: drwxr-xr-x 25.

There were 2 things I did on 9.10 that I have not done before. First I encrypted my home folder. Second, I went into users and groups and selected the option to automatically log me in. I did this because I didn't want the other users on the system all listed.

ANY help would be greatly appreciated!!! I'm stuck. Thank goodness for an old Window$$$ computer so I can search the forums but I couldn't find anything.

---

### Post by tom4everitt on 2010-02-17
Boot normally. When you reach that screen you press ctrl+alt+f2. You login with your normal user (which should hopefully work), or, better, if you have another admin user use that. 

As root remove the encrypted home folder and replace it with a normal one:
sudo chmod -R 777 /home/username
sudo rm -rf /home/username
sudo mkdir /home/username
sudo chown user:user /home/username

This will remove your encrypted home folder and replace it with a normal one. This should enable you to login as normal. 

I suspect it was the combination of auto-login and encryption that caused the error. To unlock the encryption it will need your password. But you never gave your password because of auto-login. Terrible bug. I guess you just have to choose one of the features for now (and file a bug report if you're ambitious :))

---

### Post by cforput on 2010-02-17
Thanks for the directions. Before proceeding, I have one question. It looks like I am going to remove my home directory and recreate it. I have already copies a bunch of files into it. Can you verify that I am going to delete my home folder. I will backup everything first.

Thanks again.

---

### Post by tom4everitt on 2010-02-17
sorry, yes. it sounded like you had a fresh install. you will erase it, so backing it up will be a good idea.

another option would be to turn off the auto-login somehow. i don't know how to that from a terminal though.

---

### Post by darolu on 2010-02-17
Before deleting your /home directory, try this. When you are the terminal (ctrl+alt+F1) log in with your regular user and then do:
```
sudo su
```
With this you'll be root; now try:
```
chown -R <yourusername> /home/<yourusername>
```
Then verify that you own the .ICEauthority file with:
```
ls -l /home/<yourusername>/.ICEAuthority
```
Give the appropriate permissions to it:
```
chmod 600 /home/<yourusername>/.ICEAuthority
```
And then reboot with:
```
init 6
```

---

### Post by cforput on 2010-02-17
tom4everitt & darolu,
thanks to both of you, I think I am back up again! It took a combo of both your information and some tweaking but I can now login again.

---

### Post by bingobingo on 2010-02-19
It is NOT .ICEAuthority it is .ICEauthority

---

### Post by bingobingo on 2010-02-19
I was able to get into 'safe default gnome' at start up and follow this too.....

[http://ubuntuforums.org/showthread.php?t=1402525&highlight=ICEauthority](http://ubuntuforums.org/showthread.php?t=1402525&highlight=ICEauthority)

---

### Post by julio prada on 2010-02-21
I SOLVED my problem!!!!!!
I noticed that there was a problem when I changed my password, so what I did is:
1. Log into another user I had created.
2. Open a terminal window (menu accesories terminal).
3. Change to the damaged user using the "su myname" command.
(now I had my prompt looking like: myname@mylaptop:$~)
4. Change my password again, because the proccess was not done correctly I dont know why.
"passwd myname"
Current Password:
New Password:
Confirm New Password:
5. Exit terminal
6. Restart pc
7. Log in as new user and...

EVERYTHING IS BACK TO NORMAL!!!!!

---

### Post by tom4everitt on 2010-02-22
Aah, very interesting. Thanks for sharing! (and mark the thread as solved, and it will be even more useful to others. its under thread tools in the top of thread.)

---

### Post by hanitra.rabari on 2010-03-12
thanks for the post [tom4everitt]("http://ubuntuforums.org/member.php?u=749614")!
I had the exact same problem and following your advice fixed it!

---

### Post by hanitra.rabari on 2010-03-12
My mistake! I could login in the failsafe session but not into the gnome session:frown:
I'm really lost:confused:

---

### Post by tom4everitt on 2010-03-12
If you describe your problem in a little more detail (either here on in a new thread that you link to from here) I can probably help you.

---

### Post by Flos Headford on 2010-04-08
This worked for me:
Use a Ubuntu Live CD to boot up, and choose a command-line (shell) option.
With this, set your $HOME directory (/home/username) permissions to something appropriate (I used 755) and make sure all directories can be listed with the "ls" command. Then remove nautilus with ```
sudo apt-get remove nautilus
``` and delete the .ICEauthority entry in $HOME, and possibly in /var/lib/gdm. Then reboot with ```
sudo shutdown -r now
``` When you choose the same option on boot-up, from the command line you can use ```
sudo apt-get install nautilus
sudo shutdown -r now
``` and retrieve the CD a bit smartish. I do hope you get a clean straight boot and login, as I did!
With thanks to all who helped me,
Phil

---

