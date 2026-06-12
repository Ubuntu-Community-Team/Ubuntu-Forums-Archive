---
title: "Can't log in on Ubuntu 8.04.1!"
date: 2010-04-27
forum: General Help
---

### Post by jojoguy10 on 2010-04-27
Hello, I'm new to these forums, so I don't know if this is already out there, but here it goes.  When I try to log on to my account (Ubuntu v8.04.1), it shows an error stating 

"Your  home directory is listed as: '/home/*username*' but it does not appear to exist.  Do you want to login with the /(root) directory as your home directory?  It is unlikely anything will work unless you use a failsafe session"  

There are "yes" and "no" options.  So, if I press "no", it takes me back to the log in screen, if I click "yes" it takes me to another error 

"User's $HOME/.dmre file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users."  

There's only an "OK" button.  So, I click "OK", then it takes me to ANOTHER error 

"Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space.  try logging in with one of the failsafe sessions to see if you can fix this problem."

There's an "OK" button and a "Details" checkbox.  When I click "OK" it takes me back to the log in screen.  Now, I'm VERY new to Ubuntu, so I don't know what to do.  Can anyone help please?

---

### Post by mhgsys on 2010-04-27
8.04 you say? You are running a little behind ., (running 10.04 beta and the final stable version of 10.04 will be released on April 29, 2010)

Anyway; 

To solve the .drmc error switch to tty by pressing
```
 ctrl+alt+f1
``` (f2,f3,f4,etc..f7 should be X again)

log in on the tty with your username and password.
then typ
```
 sudo /etc/init.d/gdm stop
```

```
sudo chmod 644 /home/username/.dmrc
```

```
sudo chown username /home/username/.dmrc
```

```
sudo chmod 755 /home/username
```

```
sudo /etc/init.d/gdm start
```

edit ps ; replace the "username" with your own username of course

---

### Post by jojoguy10 on 2010-04-27
I tried the first code, and it worked fine, but then I tried the second code, and an error cam up saying

"the directory /home/username does not exist" (or something along those lines)

That error cam up for the rest of the codes that had "/home/username" in them.

---

### Post by mhgsys on 2010-04-27
I guess you overlooked the ps edit on the bottom of the commands I gave you.

Anyway;
[B]
Replace the "username" with _your_ username
[/B]

f.e
Let's say on my computer I'm the user mhgsys.
It would be like;

sudo chmod 644 /home/mhgsys/.dmrc
sudo chown mhgsys /home/mhgsys/.dmrc
sudo chmod 755 /home/mhgsys

---

### Post by jojoguy10 on 2010-04-27
lol, yes I DID do my username.  It still brought up that error.  I understand all of that.  But, the error still cam up.

---

### Post by mhgsys on 2010-04-27
Ok then , sorry for underestimating you lol. 

Try in this order; 

```
sudo chown username:username /home/username/.dmrc
```
```
chmod 644 /home/username/.dmrc
```
```
sudo chown username:username /home/username
```     
```
chmod 755 /home/username
```

---

### Post by jojoguy10 on 2010-04-27
Now there's an error stating "chown: cannot access home/username/.dmrc :no such  file or directory"

P.S. Yes, I put in my UN :-)

---

### Post by Iowan on 2010-04-27
Does */home/yourusername* exist?

---

### Post by jojoguy10 on 2010-04-27
I don't know.  Like I said, I'm COMPLETELY new to Ubuntu.  Can you tell me HOW I can check if /home/username exists?

---

### Post by Iowan on 2010-04-27
If you can't get logged in, it's gonna be tough.
Otherwise...
```
cd /home
ls -al
```

---

### Post by jojoguy10 on 2010-04-27
Sadly, I get another error saying that there is no "/home" directory or file :-(  Should I just reinstall Ubuntu?

---

### Post by mhgsys on 2010-04-28
Since you don't have a /home dir, I have a question .

Did this install of 8.04 ever work?

If no; then reinstalling should be the best option.

If yes; You could also create a /home with
```
mkdir /home
```

But to be honest, that's not really the way it should be.

Since you are gonna reinstall anyway; I strongly advise you to install a newer ubuntu version, since 8.04 will not be supported anymore.. meaning no updates whatsoever.

---

### Post by jojoguy10 on 2010-04-28
I think i AM just going to reinstall the OS.  Maybe add Windows instead.  Thanks everyone for your help!  It was greatly appreciated!

---

### Post by mhgsys on 2010-04-28
Just one more day and 10.04 LTS will be released.

 In case you want a dual boot, I recommend to install windows first...So you won't have to bother reinstalling grub.

When installing ubuntu first, and then windows , windows will remove the grub.
meaning you have to reinstall grub via live cd.

Good luck with it;

---

