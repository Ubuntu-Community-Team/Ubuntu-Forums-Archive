---
title: "Truecrypt Installing problems"
date: 2010-09-02
forum: General Help
---

### Post by mailc on 2010-09-02
I downloaded Truecrypt and unpacked with no problems. It was supposed to install by a simple double click but it did not . So I am trying in the terminal.

 sudo apt-get install ./truecrypt-7.0-setup-ubuntu-x86
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package .

What does that mean?

---

### Post by gandaran on 2010-09-02
> **mailc said:**
> I downloaded Truecrypt and unpacked with no problems. It was supposed to install by a simple double click but it did not . So I am trying in the terminal.

 sudo apt-get install ./truecrypt-7.0-setup-ubuntu-x86
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package .

What does that mean?
first click the file properties option, go to permission tab and mark the execute file box, now you can double click the file and execute/install.

to install from the terminal, cd to the directory where the file is and type the run command 
```
sudo sh truecrypt-7.0-setup-ubuntu-x86
```

---

### Post by mailc on 2010-09-02
Thanks gandaran,

Permissions are Read and Write for everybody. The execution box was marked all along

And I did cd to Downloads. But it does not open (neither by double clicking nor in terminal)


~/Downloads$ sudo sh truecrypt-7.0-setup-ubuntu-86
sh: Can't open truecrypt-7.0-setup-ubuntu-86

Hope there is a solution for this.

Thanks

---

### Post by gandaran on 2010-09-02
> **mailc said:**
> Thanks gandaran,

Permissions are Read and Write for everybody. The execution box was marked all along

And I did cd to Downloads. But it does not open (neither by double clicking nor in terminal)


~/Downloads$ sudo sh truecrypt-7.0-setup-ubuntu-86
sh: Can't open truecrypt-7.0-setup-ubuntu-86

Hope there is a solution for this.

Thanks
try this, move the extracted file to the your user folder (/home/user), open the terminal and type **sudo sh**, drag the file with mouse and drop it in terminal, (keep space between **sh** and file name) next hit enter, must work this time.

---

### Post by gandaran on 2010-09-02
> **mailc said:**
> Thanks gandaran,

Permissions are Read and Write for everybody. The execution box was marked all along

And I did cd to Downloads. But it does not open (neither by double clicking nor in terminal)


~/Downloads$ sudo sh truecrypt-7.0-setup-ubuntu-86
sh: Can't open truecrypt-7.0-setup-ubuntu-86

Hope there is a solution for this.

Thanks
is the file name really truecrypt-7.0-setup-ubuntu-86?
or truecrypt-7.0-setup-86?
theres no Ubuntu file in truecrpt website!

---

### Post by mailc on 2010-09-02
thanks - this is working indeed .

it tells me that it is installing it in usr/bin and  usr/share .

But how long does this take? 
The last entry is 'Press Enter to exit... '

Does it mean that it was already installed?

---

### Post by gandaran on 2010-09-02
> **mailc said:**
> thanks - this is working indeed .

it tells me that it is installing it in usr/bin and  usr/share .

But how long does this take? 
The last entry is 'Press Enter to exit... '

Does it mean that it was already installed?
look in applications » accessories, if installed it will be there.

---

### Post by mailc on 2010-09-02
TrueCrypt was in the Applications and was actually working.

But after restarting the laptop, Truecrypt is no longer there...

this has happened also before.

Hope that this tells you something and i can fix it.

Thanks

---

### Post by mailc on 2010-09-03
Just as a follow-up:

I changed the Desktop view from UNR to GNOME  and miraculously TrueCrypt reappeared in the Applications/Accessories  and is working fine. Guess that it was somewhere all along but just could not find it.

Thank you very much for the help

---

### Post by abexs on 2010-11-07
I'm new to Ubuntu and linux, I tried to install Truecrypt, but I can't get it fixed. I extracted truecrypt-7.0a-setup-x64 to Desktop.  Then in typed in terminal:  sudo sh truecrypt-7.0a-setup-x64  The terminal asks my password and I type in my password and hit enter. The terminal disappears and nothing is happening. Who can help me out?

---

