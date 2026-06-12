---
title: "Ubuntu Server"
date: 2011-10-20
forum: General Help
---

### Post by Grenad on 2011-10-20
First of all, sorry I put this in a general category; I didnit have time to find the correct category for ubuntu server edition.
 
So heres my problem. I have an old laptop from 2003 that I want to turn into a server. I know its probably not powerful enough and not have enough memory blah blah blah but I want to anyway. It will access the internet through wifi and be plugged in 24/7. I want to use linux because of the excellent price and because of my previous experience. I want a gui however. SHould I use USE or regular Ubuntu and just download server stuff? And then what, should I use LAMP or what? I am not new to linux, but I am new to servers so please pardon me if I ask some obvious question. THanks.

---

### Post by papibe on 2011-10-20
Hi Grenad,

Could you tell us a little bit about the laptop's hardware? CPU, RAM, HD size?

It would be easier to make suggestions that way.
Regards.

---

### Post by Grenad on 2011-10-20
Im sorry but I do not have access to this computer at the moment. WHen I get home tonight I will get the specs and post them. If it helps, this is a 2003 (bought in 2003) HP Pavillion laptop that is very well used and probably not very fit to be a server; however, I want the experience, and it will probably be sufficient for a simple file server if anything.

---

### Post by papibe on 2011-10-20
Sure thing.

The question is regarding the GUI. The server edition actually has lower requirements than a desktop edition. And for a file server, you don't really need fast/modern hardware.

As a rule of thumb (IMHO):
```

pentium 3 (>= 128 Mb RAM) -> Lubuntu
pentium 4 (<    1 Gb RAM) -> Xubuntu
penitum 4 (>=   1 Gb RAM) -> Ubuntu 10.04 LTS
```
Now, if you have less 128Mb RAM, we'll have to think beyond the Ubuntu family (for a GUI).

I hope it helps.
Regards.

---

### Post by Grenad on 2011-10-20
THank you so much for replying. Alright I actually ended up lending it to my friend for a bit (xp crashed so its already loaded it with lubuntu, which has become unbeleivably slow for an unknown reason:() so no certain info on the specs. However, I am certain that it has over 128Mb RAM -that was a pretty nice computer back in 03- so that shouldnt be a problem. I might end up with xubuntu server edition anyway because it is supposedly lighter. As for the GUI, does the server edition come with a GUI? When I researched, i got the notion that it didnt.

---

### Post by papibe on 2011-10-20
In case there's some confusion with the names:
[LIST]
[*]There's only one version of the server edition: Ubuntu Server.
[*]Ubuntu Server does not have a GUI, it is all text based.
[*]Although there are differences underneath the Server and Desktop editions, they are very subtle, and both can offer the same services.
[*]Xubuntu and Lubuntu are exclusively desktop versions.
[/LIST]
In short you can install Xubuntu, and provide the same services of a server. For example, remote connection (OpenSSH), access to your files (sftp, scp, rsync), shares over the network (Samba), etc.

I hope that clarify things a bit.

):P Have fun!
Regards.

---

### Post by Meelad on 2011-10-20
As a beginner who isn't asking a lot from his server, and still needs a GUI, I'd recommend that you install the Desktop edition (whichever you like). In Ubuntu, unlike Windows, there is no separate systems for Desktops and Servers. It's essentially the same system with different packages/features installed by default.. For a simple server where you need a GUI, installing the extra packages that you need would be easier if you start with a Desktop edition than if you start with a Server edition.. Besides, for beginners, installing the Desktop edition is much easier and quicker than the Server edition.

---

### Post by Grenad on 2011-10-20
Thank you papibe for clarifying. I didnt know that xubuntu was strictly desktop. I guess i could just download xubuntu and just install server features if i really wanted to. I undersand that ubuntu server edition doesnt have a gui but couldnt I install a gui package if I wanted to?
 
Meelad, thanks for the recommendation. I just thought that the server edition would better facilitate creating a server. I dont think the installation process would be a problem (it cant be any worse than installing arch). I may end up going with the desktop edition if there really are no major differences between it and the server edition.

---

### Post by Grenad on 2011-10-21
So final question. Will the GUI help in administering my own server or would I have to do everything from the terminal anyway? What exactly is the software I would need to create a server from the desktop edition anyway?

---

### Post by as2000 on 2011-10-21
It really depends on what you want to do. For example if you wanted it to serve web pages then you would install Apache. You can install Ubuntu server and then install a gui of your choice or you can install a web based gui such as Webmin (my favorite).

---

### Post by Grenad on 2011-10-22
Alright thank you. I want my server to work with windows (my laptop) so is there any special software I would need for that?

---

### Post by cryptotheslow on 2011-10-22
If you mean sharing files over your network then either the desktop or server can do that using samba to create folder or file shares that appear to the windows machines just like any other windows share.

The server installation is really quite simple and at one point asks you what services you want to install (FTP / Apache / Samba / SSH etc.) and will set them up with a basic running configuration.

Take a look at Webmin also (some screenshots here: [http://www.webmin.com/demo.html](http://www.webmin.com/demo.html)) - it basically allows you to configure and maintain your server using a web browser e.g. from your own laptop.

I don't use it myself these days as I prefer to just use SSH and the CLI, but when I did use it briefly it was quite slick and painless.

---

### Post by Grenad on 2011-10-26
Thank you everyone for your help. I know exactly I want to do now.

---

### Post by collisionystm on 2011-10-26
> **Grenad said:**
> First of all, sorry I put this in a general category; I didnit have time to find the correct category for ubuntu server edition.
 
So heres my problem. I have an old laptop from 2003 that I want to turn into a server. I know its probably not powerful enough and not have enough memory blah blah blah but I want to anyway. It will access the internet through wifi and be plugged in 24/7. I want to use linux because of the excellent price and because of my previous experience. I want a gui however. SHould I use USE or regular Ubuntu and just download server stuff? And then what, should I use LAMP or what? I am not new to linux, but I am new to servers so please pardon me if I ask some obvious question. THanks.

Heres what I would do.

Install 10.04 LTS

Plug your computer into the internet with a wire

sudo apt-get install lxde

downloads 50mb of files

reboot

you now have a GUI that is extremely lightweight and easy to use. Now move on to configuring your wireless

---

### Post by Grenad on 2011-10-26
Thanks, I was going to do something along those lines except with the newest stable release. I am still considering not using a gui and learning to operate solely from the command line, but that is for me to figure out. Thank you everyone for your help. Consider this thread closed.

---

