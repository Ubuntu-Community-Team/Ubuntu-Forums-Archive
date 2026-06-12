---
title: "Help! Openssh, ssh-askpass-gnome?"
date: 2011-04-25
forum: General Help
---

### Post by Sirkyuubi on 2011-04-25
I have ubuntu 10.10 Desktop.

When I tried to run apt-get isntall openssh-server I was told I had a dependency issue with openssh-client here is the exact message.

The following packages have unmet dependencies:
 openssh-server : Depends: openssh-client (= 1:5.5p1-4ubuntu4) but 1:5.5p1-4ubuntu5 is to be installed

I noticed that the openssh-client installed is version 1:5.5p1-4ubuntu5 but the only server version available was 1:5.5p1-4ubuntu4 so I tried to remove openssh-client to install the ubuntu5 one which also gave me dependency errors. So I ran sudo aptitude remove openssh-client hit yes to everything and it ended up removing ubuntu-desktoip ssh-askpass-gnome and openssh-client. After that I installed the ubuntu4 version of both ssh client and server.

My question is what is this ssh-askpass-gnome for? 
I have not run a restart yet. If it is something important what do I do fix any future issues?

---

### Post by antony.s on 2011-04-25
```
apt-cache show ssh-askpass-gnome

...

Description: interactive X program to prompt users for a passphrase for ssh-add
 This has been split out of the main openssh-client package so that
 openssh-client does not need to depend on GTK+.
 .
 You probably want the ssh-askpass package instead, but this is
 provided to add to your choice and/or confusion.
```Basically, it provides a GUI for asking for your password when the ssh-add command is invoked (so it probably should be installed). Normally you would want this installed :)

---

### Post by Sirkyuubi on 2011-04-25
I still don't understand what it is for. Give me some examples. I've never used ssh-add before. I read the man file for ssh-add, but that didn't help me understand.

---

### Post by earthpigg on 2011-04-25
I do not understand what "eog" or "bc" is for, but it must be installed for the Ubuntu Desktop package (ubuntu-desktop) to be installed.

At some point, we just have to trust the distribution maintainers. Else, we ought to do the Linux From Scratch route.

I realize that is not a specific answer to your question, but that is my conclusion having never seen ssh-askpass-gnome in action either. 

My gut instinct is "Why would gnome and ssh interact with eachother anyways? If I am using a terminal, I don't need gnome mucking things up..."

---

### Post by Sirkyuubi on 2011-04-25
I dont understand what it is either, but it is a problem for me because I cant have openssh-client and server installed if ssh-askpass-gnome is installed.

So what my main concern is...
If I reboot my box will I have any problems getting the system up and running?
How crucial is this?

---

### Post by Sirkyuubi on 2011-04-25
I hope its ok to bump.

---

### Post by Sirkyuubi on 2011-04-25
bumpage

---

### Post by collisionystm on 2011-04-25
> **Sirkyuubi said:**
> I have ubuntu 10.10 Desktop.

When I tried to run apt-get isntall openssh-server I was told I had a dependency issue with openssh-client here is the exact message.

The following packages have unmet dependencies:
 openssh-server : Depends: openssh-client (= 1:5.5p1-4ubuntu4) but 1:5.5p1-4ubuntu5 is to be installed

I noticed that the openssh-client installed is version 1:5.5p1-4ubuntu5 but the only server version available was 1:5.5p1-4ubuntu4 so I tried to remove openssh-client to install the ubuntu5 one which also gave me dependency errors. So I ran sudo aptitude remove openssh-client hit yes to everything and it ended up removing ubuntu-desktoip ssh-askpass-gnome and openssh-client. After that I installed the ubuntu4 version of both ssh client and server.

My question is what is this ssh-askpass-gnome for? 
I have not run a restart yet. If it is something important what do I do fix any future issues?

Next time use

```

sudo apt-get install ssh

```

Ask pass gnome is probably the part of the ssh that checks rsa key validation.

---

### Post by Sirkyuubi on 2011-04-25
Ask pass gnome is probably the part of the ssh that checks rsa key validation.

meaning?

As far as apt-get install ssh goes that command wouldn't work. It said to use either openssh-client or server

---

### Post by collisionystm on 2011-04-25
Ubuntu uses ssh to install both in one shot.
install ssh is what I have always used.

Google about ssh rsa keys. Im on a phone and not typing that much.

---

