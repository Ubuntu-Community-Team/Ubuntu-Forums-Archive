---
title: "How to share files between two ubuntu?"
date: 2006-02-21
forum: General Help
---

### Post by jasonli on 2006-02-21
Hi there.

I am a beginner and don't know how to share my files between two ubuntu computers, one is a Dell Laptop and the other is an iMac G3, both of them are installed with ubuntu 5.10.

I tried Samba but failed, and i guess there must be some way other than the windows Samba sharing.

Thanks for any of your advice or hints. Bow.

---

### Post by not_yet on 2006-02-21
how did samba fail?

---

### Post by professor_chaos on 2006-02-22
Applications/MainMenu->Places->ConnectToServer
SSH should work for you, provided you install SSH server and client on both machines. You can do that through synaptic.

There are other ways, but this should work for you.

Samba is for windows <-> linux/other sharing

---

### Post by matthinckley on 2006-02-22
yes ssh works great but make sure on the computer that has the folder you want to share to do a 'sudo apt-get install ssh' to install the ssh server

---

### Post by jasonli on 2006-02-22
[QUOTE=not_yet]how did samba fail?[/QUOTE]
I created a samba user on my iMac (with ubuntu) with the same user name of both of my two computers, and set the pwd for it. Then I can connect to it using a windows xp, and it works terrificly. Then  I removed xp and installed ubuntu, it either asks for pwd(although i gave the right one, it asks again and again, apparently, it thinks my pwd is wrong, and very strangely, it does not ask for my username, but for the domain name, I don't know what that is but the computer told me the domain name is something like MS Home), or it simply sais couldn't display all contents of the destination folder. Anyway, I tried to install samba and restart samba daemon and with no success.

I will try SSH and hopefully there can be some good and easy-to-use way to share files. I think Mac OS X did a great job, it provides nearly all kinds of web services out of the box, ftp, samba, http, atp, and a firewall, and the configuration is just fabulous. If ubuntu can make it more easier and user friendly, i mean more friendly to common people trying to use a linux and don't know much about this new world, it can be more popular and successful.

---

### Post by jasonli on 2006-02-22
[QUOTE=matthinckley]yes ssh works great but make sure on the computer that has the folder you want to share to do a 'sudo apt-get install ssh' to install the ssh server[/QUOTE]
Hey thank you guys, SSH is good!
Here I found a wiki page describing the usage of SSH, check it out, if anyone need:
[https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)

---

### Post by pato101 on 2006-02-22
[quote=jasonli] SSH is good!
[/quote] In fact, SSH is almost god! :-P

Note that once you have ssh working, you may run other machine's apps at current display as well, by doing like this at gnome-terminal:
```

machine_display$ ssh -X machine_remote
password:
machine_remote$ xeyes &

```

---

### Post by jasonli on 2006-02-22
I got a very very strange and severe problem!!!

In windows, usually for transfering big files between my two computers, I use a network line just as the normal ones that would fit into a ethernet plug and connect you to the internet , not the reversed kind. Then I set my two computers like this: I don't know why this works and why should I do this, simply remembered this tricky way and all goings well in xp:

computer 1:
ip: 10.10.10.10
subnet mask: 255.255.255.0
gateway: 10.10.10.10

computer 2:
ip: 10.10.10.11
subnet mask: 255.255.255.0
gateway: 10.10.10.10

the point is to make one computer the gateway of itself and the other, and give the two computers their respective ip, and with a single network line, they are connected, at least in windows xp, os x. Then I 

I found out that if I do this with two ubuntu, you can not use ssh. If you try to connect to a server in the Place menu, you can not open the icon on the desktop, neither can you make it in the nautilus window manager. This is something like what I get with the samba. However, if you go to the terminal and type:

ssh <user name>@<ip address>

after typing password, you can log into the computer, strange huh? you can also ping each other and the response is very very quick.

I just turned my two computers both onto the internet using dhcp cable network, so now they can just transfer files, on the INTERNET, which is very very slow...

I don't know where the settings got wrong but this is what happened to me. I really need some help since I got several gigabytes of data to copy and i don't want spend 70 hours 20 minutes and 33 seconds, which is exactly the remaining time showed on the screen, on this.

Thanks a lot!

---

### Post by yota on 2006-02-22
Hi,

strangely nobody mentioned NFS. It's the mainstream way to share files via network (moreover to have a real Network File System) between unix machines.
It's hi-perf, on my network is 25% quicker than smb, and not too difficult to set-up; you can find two wikis (many other on the net) on:

[https://wiki.ubuntu.com/NFSServerHowTo](https://wiki.ubuntu.com/NFSServerHowTo)

[https://wiki.ubuntu.com/NFSClientHowTo](https://wiki.ubuntu.com/NFSClientHowTo)

Autofs is not necessary, but will handle very nicely dynamic mount and unmount of the shares.
If you "can't live without gui" you can define network shares under (translated from italian) system/administration/network shares and select nfs as the type.

Hope you'll find this handy!

---

