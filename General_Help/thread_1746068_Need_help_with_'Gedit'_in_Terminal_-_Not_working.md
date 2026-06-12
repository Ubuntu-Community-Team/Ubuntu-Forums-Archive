---
title: "Need help with 'Gedit' in Terminal - Not working"
date: 2011-05-01
forum: General Help
---

### Post by xkaijinx on 2011-05-01
I am trying to use the gedit command to edit my smb.conf file.  It was originally working and all of a sudden it has stopped working.  I have typed.. 'gedit /etc/samba/smb.conf' but it is a no go.  I used the chmod command to set permissions as..  'chmod 744 smb.conf' However I am still unable to get the file to open. 

If I do the 'more smb.conf' command I am able to read the contents of the file, however I am unable to edit them.  

Please help, thanks

---

### Post by idoitprone on 2011-05-01
> **xkaijinx said:**
> I am trying to use the gedit command to edit my smb.conf file.  It was originally working and all of a sudden it has stopped working.  I have typed.. 'gedit /etc/samba/smb.conf' but it is a no go.  I used the chmod command to set permissions as..  'chmod 744 smb.conf' However I am still unable to get the file to open. 

If I do the 'more smb.conf' command I am able to read the contents of the file, however I am unable to edit them.  

Please help, thanks

try
```
gksudo gedit /etc/samba/smb.conf
```
Your editing system file that are not owned by own the user. They are owned by root, which means you need admin rights

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Vaphell on 2011-05-01
don't play with permissions of stuff you don't own, otherwise you will hose your system sooner or later (i bet on sooner)
```
gksu gedit /etc/samba/smb.conf
```

---

### Post by xkaijinx on 2011-05-01
This is not working.  I used both commands you have both provided to me and the cursor in the terminal line just hovers to the next line, and does nothing.  Now when I press the 'ctrl + z' key to reset the terminal so that I can enter commands this displays....

[1]+ Stopped              gksudo gedit /etc/samba/smb.conf

Now if I try to do the command a second time the same exact process happens but now it will show... 

[2]+ Stopped              gksudo gedit /etc/samba/smb.conf

I do not want to hose my system!  Any other idea how I can reset this?  Still learning, thanks for help though.

---

### Post by idoitprone on 2011-05-01
it should open this prompt [http://en.wikipedia.org/wiki/File:Gksudo.png](http://en.wikipedia.org/wiki/File:Gksudo.png)

---

### Post by xkaijinx on 2011-05-01
I understand that.  I am trying to say that it is not working.

---

### Post by Vaphell on 2011-05-01
what does
```
ls -l /etc/samba/smb.conf
``` say?

---

### Post by Blasphemist on 2011-05-01
Not that I had run into this, but seeing this I tried it. I got the password screen but then just got the prompt back. No gedit opens. I can open gedit fine but not this way.

Edit, sorry typo was why it didn't work. Is fine now.

---

### Post by bobwyajnr on 2011-05-01
> **xkaijinx said:**
> I understand that.  I am trying to say that it is not working.

The command:
```
$ sudo gedit /etc/samba/smb.conf
```
will work just as well. You will be asked to type your 'root' password (just below the above command - in the terminal you typed the command in). The editor program (**Gedit**) will then be launched with admin rights.

Bob

---

### Post by xkaijinx on 2011-05-01
Vaphell:  After typing that command in it reads..  
-rwxr--r-- l root root

Bob:  I was already in root when using the gedit command.  However even when using the sudo command nothing happens.

---

### Post by bab1 on 2011-05-01
> **xkaijinx said:**
> Vaphell:  After typing that command in it reads..  
-rwxr--r-- l root root

Bob:  I was already in root when using the gedit command.  However even when using the sudo command nothing happens.

The logical thought then would be to see what *is* in the /etc/samba directory.

Try this:```
ls -l /etc/samba
```

---

### Post by WorMzy on 2011-05-01
> **bobwyajnr said:**
> The command:
```
$ sudo gedit /etc/samba/smb.conf
```
will work just as well. You will be asked to type your 'root' password (just below the above command - in the terminal you typed the command in). The editor program (**Gedit**) will then be launched with admin rights.

Bob

No. Don't use sudo for graphical apps, doing so may cause the permissions on your home folder to mess up. Use gksu or gksudo instead.


As for the problem at hand, I would guess that there is a problem with the gedit executable. Try reinstalling it.

```
sudo apt-get install --reinstall gedit
```

---

### Post by bobwyajnr on 2011-05-02
> **WorMzy said:**
> No. Don't use sudo for graphical apps, doing so may cause the permissions on your home folder to mess up. Use gksu or gksudo instead.


Yeh my bad - was just getting a bit desperate there!  Don't try this at home kids... :popcorn:

@**xkaijinx**
Time for some commandline love!

How's about:
```
sudo nano /etc/samba/smb.conf
```
in a terminal to edit your Samba configuration file.

1) It's worth learning about **nano** (or **vim**, etc.) now!! Before you stuff up your X-Server and need to be familar with TTY console commands!! :P
2) Try not to be heavy handed with your use of root - both from a security standpoint and for system stability (i.e. not hosing everything). Linux has excellent privilege escalation commands (**sudo**, **gksu**/ **kdesudo**) - so use them!! We aren't talking about some tacked on solution ala *UAC* on Windows!! :P

Bob

---

