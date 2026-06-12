---
title: "Ubuntu Lite woes"
date: 2006-03-19
forum: General Help
---

### Post by Dafydd on 2006-03-19
Is anyone using ubuntulite? I've been looking for several months for a lite system for my laptop. I'm keeping Ubuntu 6.04 but need sth that boots really fast and is lite (as a second boot). I want to switch on the computer and get going 30 secs later etc.

I installed Ubuntu Lite - it does not boot any faster (I've also tuned the services that should start at boot). Also, it's really annoying that it does not autologin. I've tried a few things learnt on forums to make autologin but to no avail. Also the wdm manager does not allow me to turn off the computer! I've had to just use the power off button!

It would be great if Ubuntu had a real Lite in the Ubuntu spirit - ie. for also for silly newbies like myself.

I'm going to reinstall Puppy Linux (that's fast, has autologin and auto shutdown). The only problem is that Puppy Linux 1.08 still does not recognize my Centrino Intel Pro 2200BG wireless card. But now Puppy has Alsa, I can configure the sound (on my Sony Vaio, I need to turn off the external amplifier).

Has anyone had any success on a Lite system with Wireless?

Dafydd

---

### Post by Ramses de Norre on 2006-03-19
Try Xubuntu, sudo apt-get install xubuntu-desktop.
I have never heard of ubuntu lite before, where do you find it?

---

### Post by Sef on 2006-03-19
> Also, it's really annoying that it does not autologin.

To autologin: System > Administration > Login Screen Setup > check Login a user automatically on the first boot up > Highlight the name under "Automatic login user name" > click close.

---

### Post by bunced on 2006-03-19
@SEF

That'll only work if he is using GDM as a login

---

### Post by PhoenixP3K on 2006-03-20
[QUOTE=Ramses de Norre]Try Xubuntu, sudo apt-get install xubuntu-desktop.
I have never heard of ubuntu lite before, where do you find it?[/QUOTE]
There was a time where you could download a torrent or the iso directly from the [Ubuntu Lite website]("http://www.ubuntulite.org/"). But since they updated the site to a new version, it's no where to be found.

---

### Post by Dafydd on 2006-03-23
Cheers for the info but I finally got Puppy Linux (1.08) to work with the ipw2200 driver. It's great, fast and simple. I think it's faster than Ubuntu Lite and I don't have the hassle of trying to figure out how to logout or login.

Dafydd

---

### Post by rayburn on 2006-03-23
In case anyone is interested in Ubuntulite, here is a link to the installation instructions:

[https://wiki.ubuntu.com/InstallingUbuntuLite](https://wiki.ubuntu.com/InstallingUbuntuLite)

I have recently experimented with it on an old computer and found it excellent. Using apt-get I have installed other software to personalise it to my requirements.

---

### Post by Dafydd on 2006-03-24
[QUOTE=rayburn]I have recently experimented with it on an old computer and found it excellent. Using apt-get I have installed other software to personalise it to my requirements.[/QUOTE]

How lite is Ubuntu Lite? I had the feeling that it was still some 400MB. Also, it is fast but I get the feeling Puppy Linux is slightly faster, and importantly, boots and goes down v. fast. But it would be great to get on top of Ubuntu Lite with all the software that goes with it. I've just found that it takes a bit more effort to configure etc than Puppy (login/out).

Dafydd

---

### Post by Dafydd on 2006-03-24
[QUOTE=bunced]@SEF

That'll only work if he is using GDM as a login[/QUOTE]

Maybe I'll reinstall with GDM (I did WDM). But GDM is slower, isn't it?

Dafydd

---

### Post by rayburn on 2006-03-25
[QUOTE=Dafydd]How lite is Ubuntu Lite? I had the feeling that it was still some 400MB. Also, it is fast but I get the feeling Puppy Linux is slightly faster, and importantly, boots and goes down v. fast. But it would be great to get on top of Ubuntu Lite with all the software that goes with it. I've just found that it takes a bit more effort to configure etc than Puppy (login/out).

Dafydd[/QUOTE]


It is about 486MB I believe, but quite usable on a 400Mhz/64Mb computer.

Here is another link to the original thread that sparked my interest in this project:

[http://ubuntuforums.org/showthread.php?t=98233&highlight=ubuntulite](http://ubuntuforums.org/showthread.php?t=98233&highlight=ubuntulite)

Lots of useful info there.

---

### Post by rayburn on 2006-03-25
[QUOTE=Dafydd]How lite is Ubuntu Lite? I had the feeling that it was still some 400MB. Also, it is fast but I get the feeling Puppy Linux is slightly faster, and importantly, boots and goes down v. fast. But it would be great to get on top of Ubuntu Lite with all the software that goes with it. I've just found that it takes a bit more effort to configure etc than Puppy (login/out).

Dafydd[/QUOTE]


It is about 486MB I believe, but quite usable on a 400Mhz/64Mb computer.

Here is another link to the original thread that sparked my interest in this project:

[http://ubuntuforums.org/showthread.php?t=98233&highlight=ubuntulite](http://ubuntuforums.org/showthread.php?t=98233&highlight=ubuntulite)

Lots of useful info there.

---

### Post by rayburn on 2006-03-25
[QUOTE=Dafydd]How lite is Ubuntu Lite? I had the feeling that it was still some 400MB. Also, it is fast but I get the feeling Puppy Linux is slightly faster, and importantly, boots and goes down v. fast. But it would be great to get on top of Ubuntu Lite with all the software that goes with it. I've just found that it takes a bit more effort to configure etc than Puppy (login/out).

Dafydd[/QUOTE]


It is about 486MB I believe, but quite usable on a 400Mhz/64Mb computer.

Here is another link to the original thread that sparked my interest in this project:

[http://ubuntuforums.org/showthread.php?t=98233&highlight=ubuntulite](http://ubuntuforums.org/showthread.php?t=98233&highlight=ubuntulite)

Lots of useful info there.

---

### Post by rayburn on 2006-03-25
Apologies for the double post, I was having problems with this site.

---

### Post by isTHEr3mOr3 on 2006-04-09
Forget Ubuntu Lite! If you want a fast, easy to install and a very complete distro there is no better choice than Puppy Linux (It's already stated by someone else in this thread) 
There are many people working on it and there's a nice community. If you want to get rid of the fat and slow distro's try Puppy Linux. 
Also very usable on modern PC's (lightning fast). 

[http://www.puppylinux.com/]("http://www.puppylinux.com/")

---

### Post by derjames on 2006-04-14
Yes, if you really want to resusita an old computer or make a new computer run at lightspeed (seriously!!!) install puppyLINUX, its amazing and fully functional, ready for MP3 and MPEG, etc... you won't belive when you read that the default size is just 65MB, and basically all the distribution is loaded to RAM (RAMdisk) so if you have a pretty nice computer you will feel like running an F1 car or even better a F14 aircraft... PuppyLINUX is the right complement for Ubuntu...  Another one is Damn Small LINUX (DSL) however I haven't play aroud with it...

Cheers

---

