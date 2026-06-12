---
title: "ssh gui"
date: 2010-04-26
forum: General Help
---

### Post by Ready2DropWin on 2010-04-26
Hello,
Is there any good gui ssh for Ubuntu x64???
Thanks

---

### Post by Bachstelze on 2010-04-26
Please elaborate, what do you mean by "a GUI for SSH"?

---

### Post by Ready2DropWin on 2010-04-26
I would like a graphical ssh client program for Ubuntu

---

### Post by Bachstelze on 2010-04-26
> **Ready2DropWin said:**
> I would like a graphical ssh client program for Ubuntu

To do what? Run graphical applications? Then you can use either X forwarding with the regular OpenSSH client, or use a remote desktop protocol like VNC.

---

### Post by carl4926 on 2010-04-26
Eg:

ssh -X xxxx@192.168.0.2
then you start applications Eg: firefox
will start firefox on the device at 192.168.0.2
But will display at your machine

Does filezilla do ssh? Not sure.

---

### Post by Ready2DropWin on 2010-04-26
I have a server and I want to transfer files from my desktop to the server graphically I am new to Ubuntu, so will openSSH do that?

---

### Post by Bachstelze on 2010-04-26
> **Ready2DropWin said:**
> I have a server and I want to transfer files from my desktop to the server graphically I am new to Ubuntu, so will openSSH do that?

OK, then there are a lot of graphical apps you can use for that. FileZilla supports the SSH file transfer protocol, and you can also use WinSCP on Windows, or your favourite file management app (Nautilus, Konqueror, Dolphin...) in Linux.

---

### Post by Ready2DropWin on 2010-04-26
Yeah I used WinSCP on windows, but I can use that now and I have never used one in Linux so I was wondering what the best one was.

---

### Post by Bachstelze on 2010-04-26
> **Ready2DropWin said:**
> Yeah I used WinSCP on windows, but I can use that now and I have never used one in Linux so I was wondering what the best one was.

FileZilla is good, or you can use the default file manager (Nautilus). I can't exactly tell you how, though, I don't use it.

---

### Post by Ready2DropWin on 2010-04-26
Right on filezilla will work. Now I feel like a noob wipe, but why is it when I download a linux file off the net I can't find the file that runs it, like how windows has a exe file?

---

### Post by carl4926 on 2010-04-26
You should install via apt or aptitude
Or look in Software Centre.

I would just use nautilus it's easy
Open your home folder, go to File - Connect to Server.....

Complete as necessary
Bob's your Uncle:)

---

### Post by Bachstelze on 2010-04-26
> **Ready2DropWin said:**
> Right on filezilla will work. Now I feel like a noob wipe, but why is it when I download a linux file off the net I can't find the file that runs it, like how windows has a exe file?

[This]("http://psychocats.net/ubuntu/installingsoftware") might be of interest to you.

---

### Post by Ready2DropWin on 2010-04-26
Alright thanks for the help!!!

---

### Post by perseo22 on 2010-04-28
> **Ready2DropWin said:**
> I would like a graphical ssh client program for Ubuntu

Try "PAC Manager" at 

[http://sourceforge.net/projects/pacmanager/]("http://sourceforge.net/projects/pacmanager/")

---

### Post by The Cog on 2010-04-28
I think nautilus is easiest. Just type Ctrl-L to get to type into the location bar, then enter something like:
> sftp://steve@192.168.1.103/home/steve
Alternatively from the nautilus menu, use **File / Connect to Server...**

You can drag/drop to/from your desktop or other nautilus windows. You can even open remote files in gedit etc. - neat!

---

### Post by jerome1232 on 2010-04-28
> **The Cog said:**
> I think nautilus is easiest. Just type Ctrl-L to get to type into the location bar, then enter something like:

Alternatively from the nautilus menu, use **File / Connect to Server...**

You can drag/drop to/from your desktop or other nautilus windows. You can even open remote files in gedit etc. - neat!

That's what I was about to recommend, nautilus handles it nicely.

+1 for nautilus becoming my favorite file manager.

---

### Post by flamacue on 2010-04-28
I'm not sure what the OP wants to do, but he may find [_[COLOR="Blue"]PuTTY[/COLOR]_]("http://www.putty.org/") of interest.  It's listed in Add/Remove Programs...at least it is on my 9.04 Jaunty.

---

### Post by itnet7 on 2010-08-26
You could also try Pyconnmgr.. Check out[ Lupine's Pyconnmgr](http://thelupine.com/pyconnmgr) I think that you will like it! 

Thanks for your time,

Chris Crisafulli
itnet7

---

