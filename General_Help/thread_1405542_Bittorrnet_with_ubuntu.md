---
title: "Bittorrnet with ubuntu"
date: 2010-02-12
forum: General Help
---

### Post by emunrradtvamg on 2010-02-12
Hi everyone, 

I'm probably the Linux's fan number 1 right now. So please help me with my first goal:

To download a torrent file by using the command line. I have installed a python-called program but I cannot find where it was installed well, I don't even know anything about it (no information is displayed with man command either).

Please if you have any suggestion or related information (manual, web links, etc), I will appreciate that. 

I'm just a hobbyist, I can read long or short articles, that doesn't matter.

Luis

---

### Post by Satoru-san on 2010-02-12
Hey, Welcome to the forums :)

I am glad you decided to use ubuntu.

Luckily there is server torrents for ubuntu, I use ktorrent, it is my favorite, however there are several others.

My guess is that you want to know how to find their names and install them.

You are going to be happy to know you DONT have to use the terminal to install software. There should be a button that say add software in your system menu, if you cant find that search that third tab in administration for synaptic package manager.

Then you are able to search "torrent" for example and just choose to install.


If you want to use the terminal its also easy.
```
apt-cache search torrent
sudo apt-get install <program name>
```

cheers!

---

### Post by emunrradtvamg on 2010-03-03
> **Satoru-san said:**
> Hey, Welcome to the forums :)

I am glad you decided to use ubuntu.

Luckily there is server torrents for ubuntu, I use ktorrent, it is my favorite, however there are several others.

My guess is that you want to know how to find their names and install them.

You are going to be happy to know you DONT have to use the terminal to install software. There should be a button that say add software in your system menu, if you cant find that search that third tab in administration for synaptic package manager.

Then you are able to search "torrent" for example and just choose to install.


If you want to use the terminal its also easy.
```
apt-cache search torrent
sudo apt-get install <program name>
```cheers!



Hi, and thanks for helping me :)

I was using  a software known as "Client de bittorrent transmission". It is very straightforward when using in a graphic mode but it is a little troblesome when using it through commands.

Well Ktorrent is my new bittorrent version but I cannnot make it work property either. I found this command to start the download :

**ktorrent [Qt-options] [KDE-options] [Options] [URL]**

and my questions are about this:

is [URL] like a "web link" or is it the name of the torrent file I download from the internte?? I made a first try assuming [URL] meant the file name and the download started in a graphic mode.  But I would like it starts in a command mode. How can I do that???

I do this because I need to enter into a host miles away from the cyber where I type the commands. Thus, the download starts and I can go home and come back next day and get my files without staying at the cyber al the night long.


I'm a spanish speaker and I hope you can understand my really bad English.


Thanks again,
Luis

---

### Post by deadlockedgamer on 2010-03-03
Please clarify, are you trying to download torrents via cli? If so please explain why!

---

