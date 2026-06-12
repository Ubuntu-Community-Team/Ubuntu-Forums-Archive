---
title: "Should I have chosen Server edition for my Server when I don't know the CLI?"
date: 2010-08-29
forum: General Help
---

### Post by misterdna on 2010-08-29
I'm somewhat familiar with Linux, just not with pretty much all of the command line stuff. I built a server that will function both as a master node for my render farm and a general place to store family data. I installed Ubuntu LTS 10.04 64-bit Server on it and immediately became uncomfortable when I was greeted by the CLI.
 
I feel like I'm in over my head here--in a bad way. It's like the first time my immediate family had a computer. It was a DOS/Win 3.1 system and while I learned my point-click way around Windows and played around in DOS enough to use qBASIC within the first month, it took a couple of years before I was flying around in DOS and editing the startup files with complete confidence. I was dropped into DOS at the C:\ prompt once way too early on in the learning process and you can imagine how I reacted at age 12.
 
What I'm wondering is whether I maybe should have installed the Desktop version of the OS just to be able to get around more easily as I get my feet wet. I would hope the Desktop version won't prevent me from such things as hosting Etherboot images for the farm nodes. I want to get in real deep with Linux, just not all at once.

---

### Post by lsmobrian on 2010-08-30
You can always install a GUI on top of a server install, something lightweight like xfce or lxde so you dont have a lot of the extra desktop stuff, fluxbox if you want something really light.

I really like [webmin]("http://www.webmin.com/index.html") for server installs if I have to do a lot of services, its not in the repos that i know of but fairly easy to install

---

### Post by lukeiamyourfather on 2010-08-30
Installing the server edition and a GUI or installing the desktop version is okay for your uses. Both the desktop and server edition can do things like serve files with Samba. Though if you want to get into the real "server" side of Linux you'll need to learn to use the command line.

Using ssh can make it a lot easier to learn because you can copy and paste from tutorials into the terminal from another machine. Good luck with it and feel free to ask question about it here either way you go.

---

### Post by dtoronto on 2010-08-30
I agree that if you're looking to setup a server install you really need to learn CLI, but you could also install the ubuntu server and put webmin on it.  Webmin has some mixed reviews by linux experts and you'll probably end up dropping it when you get to know CLI better, but for getting started it's pretty good.

---

### Post by misterdna on 2010-08-30
> **lukeiamyourfather said:**
> Installing the server edition and a GUI or installing the desktop version is okay for your uses. Both the desktop and server edition can do things like serve files with Samba. Though if you want to get into the real "server" side of Linux you'll need to learn to use the command line.

Using ssh can make it a lot easier to learn because you can copy and paste from tutorials into the terminal from another machine. Good luck with it and feel free to ask question about it here either way you go.

Thank you.  This is what I needed to know.

I have no problem with the idea of using the CLI, it's just going to take a while.  I do know I'll be faster with the CLI than with the mouse once I'm used to it.  It's just nice to have things running first before I goof around and make them go "boom", intentionally or otherwise.

If there's any interest in the nuts and bolts side of my project, I have a thread at HardOCP's forum: [http://hardforum.com/showthread.php?t=1522253](http://hardforum.com/showthread.php?t=1522253)

---

### Post by lukeiamyourfather on 2010-08-30
> **misterdna said:**
> 
If there's any interest in the nuts and bolts side of my project, I have a thread at HardOCP's forum: [http://hardforum.com/showthread.php?t=1522253](http://hardforum.com/showthread.php?t=1522253)

Cool project! What do you plan to render with it? I've done some computer graphics work as well. :popcorn:

[http://www.whenpicsfly.com/tool/reel/lukeOlson2010.mp4](http://www.whenpicsfly.com/tool/reel/lukeOlson2010.mp4)

---

### Post by wojox on 2010-08-30
> **misterdna said:**
> 
If there's any interest in the nuts and bolts side of my project, I have a thread at HardOCP's forum: [http://hardforum.com/showthread.php?t=1522253](http://hardforum.com/showthread.php?t=1522253)

I'm jealous of those pics. :D  

How do you get any work done with all that beautiful mountain scenery?

---

### Post by bdentremont on 2010-08-30
> **lukeiamyourfather said:**
> Using ssh can make it a lot easier to learn because you can copy and paste from tutorials into the terminal from another machine.

I agree -- ssh is your friend. :-)

---

### Post by Iowan on 2010-08-30
Unless I missed it (entirely possible), [this]("https://help.ubuntu.com/community/ServerGUI") help page hasn't been mentioned...

---

### Post by v1ad on 2010-08-30
also something to keep in mind. if you are managing your server from another computer, you will be using ssh. another helpful command is sshfs.
ssh will launch you in to a console in the server.
how you use is is:
```

ssh username@ipaddress

```
it will ask you for a password and then it will log you in.

also what sshfs does is creates a virtual folder that links to your server.
first you will create a folder (in console):
```

mkdir folder_name

```
then you will log in using the sshfs command. (you might need to install it on both)
to install:
```

sudo apt-get install sshfs

```
then login (. means current directory forward slash is option just my habit): 
```

sshfs username@ipaddress:./ folder_name

```
so you can than add files to that folder or delete and everything that occurs in that folder actually occurs on the server, its very helpful since on servers usually we have no screen, or keyboards, or mice.

---

