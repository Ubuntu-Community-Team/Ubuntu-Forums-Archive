---
title: "New to Ubuntu"
date: 2012-05-19
forum: General Help
---

### Post by Cheeseter on 2012-05-19
Hello All!

I am thinking about using Ubuntu, and I wanted to get a feel for what this operating system is all about. I am currently a Windows Vista, and I will say I am not happy with my current setup. I have a powerful computer but feel like Vista is holding me back a bit with all the restrictions. My biggest worry is that all my important documents may not transfer.

I was also interested in the gaming aspect of Ubuntu. I am a pretty avid gamer, and I enjoy playing Starcraft 2 and now Diablo 3, so I was wondering what sort of viability Ubuntu has in terms of running games like these?

How user friendly would Ubuntu be to a first time user like me? Would someone recommend a different Linux software? 

Any input is appreciated and I look forward to hearing any advice than anyone has!

---

### Post by carl4926 on 2012-05-19
You should keep Windows for games IMO
Especially if you are that keen on gaming.
Linux can use Wine to run some windows games, you can find info here
[http://appdb.winehq.org/index.php](http://appdb.winehq.org/index.php)

There are also native Linux games.

You can install Ubuntu and keep windows. But I suggest you backup all your important data. Any installation of a OS is a big step and backup is important.

Ubuntu should fly compared to windows, especially Vista.

Keeping both OS's will let you feel your way around Ubuntu and learn the ropes. Most people started that way.

Can we assume you are testing the Live CD/USB?

---

### Post by Cheeseter on 2012-05-19
I've got all of my documents on an external hard drive, but to be honest my computer is running so slow at the moment and I wanted to wipe my hard drive, but the problem is I am having trouble locating my Vista product key at the moment.

Are the Linux programs that will be able to read Word, Excel, and Powerpoint documents should I eventually make the full transition to Ubuntu?

If I install Ubuntu, they aren't open at the same time are they?

> Can we assume you are testing the Live CD/USB?

I guess I'm a huge novice here, but I'm not really sure what you're asking :D

Thanks for the quick response! I find Ubuntu fascinating and have recently been exposed to the existence of open source operating systems so I am super excited to learn more! My brother recently made the switch and has raved about it, but unfortunately he is out of town so I can't really pick his brain.

---

### Post by carl4926 on 2012-05-19
Ubuntu uses Libre Office [http://www.libreoffice.org/](http://www.libreoffice.org/)
It can read your MS documents fine

> If I install Ubuntu, they aren't open at the same time are they?Not too sure what you mean here.

If you have a backup, then feel free to wipe the HD and install Ubuntu
But most people download the the CD image, burn the .iso to a CD and boot from the CD, just to try it. Unlike windows, with most Linux OS's you can actually use it without installing it, though it will have limitations this way.

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

Don't install it in windows with Wubi !

---

### Post by Cheeseter on 2012-05-19
Okay I have the .iso file download started. How easy is it to remove Vista completely after I have them both on my system, should I decide I prefer Ubuntu?

And is Wine a program within Ubuntu or is than another operating system itself?

---

### Post by carl4926 on 2012-05-19
> **Cheeseter said:**
> Okay I have the .iso file download started. How easy is it to remove Vista completely after I have them both on my system, should I decide I prefer Ubuntu?

And is Wine a program within Ubuntu or is than another operating system itself?

It's better to remove Vista rather than try and do it later. But why not try booting the cd and see how Ubuntu is first.
And you could always install ubuntu alongside Vista to start with, and if you really like it, then install again.

When you boot the CD (You have to make sure you have set the CD as the first boot device in your BIOS) and run the installer
You get to a point like this
[http://www.su2root.ukfsn.org/files/Ubuntu/ubuntu_11.10/4_install_custom.jpeg](http://www.su2root.ukfsn.org/files/Ubuntu/ubuntu_11.10/4_install_custom.jpeg)
The option 'erase disk and install ubuntu' will remove Vista and install ubuntu

Wine is a Linux program that simulates a windows file system and environment within your  Linux user system

---

### Post by garyzw on 2012-05-19
Burn the ISO to a DVD I think a CD is to small.

WINE is a windows comparability layer for Linux not another operating system.

To install WINE open a Terminal crtl-alt-t and enter one line at a time pressing enter after each line.

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.5

The Live CD will give you the option to remove Windows completely and install Ubuntu-- it will also create a swap drive. When yo have the live CD loaded click install Ubuntu and carefully read the options it gives you. The live CD is a little slower then if it were installed on a hard drive so give it a little time to do its thing.

> **Cheeseter said:**
> Okay I have the .iso file download started. How easy is it to remove Vista completely after I have them both on my system, should I decide I prefer Ubuntu?

And is Wine a program within Ubuntu or is than another operating system itself?

---

### Post by laliperro on 2012-05-19
I suggest you to keep windows too, especially if you are a gamer. With Ubuntu you can play, but different way as windows. If you are looking for the newest games, you are wrong. For instance, with Ubuntu you can play emulators too, and other kind of games like open source, indie and not very popular but commercial games.

I think its better to keep windows for a few months while you are learning Ubuntu because its a radical change and you will need patience. Meanwhile you can continue using windows less hours than before, but you will feel safe if something goes wrong or goes slower than you thought.

I suggest you ([http://www.lgdb.org/](http://www.lgdb.org/)) for games.

Regards from Spain.

---

### Post by Swagman on 2012-05-19
If you are going to burn the iso to cd/dvd medium, then ensure you burn it **AS AN IMAGE**.

Depending on your system you might not have to faff about in the bios altering boot order.

On my system (Asus) immediately after I press the "On" button if I hit F8 I get "temporary boot options". Yours could be F12.

If all your important data is on the removable drive you could simply unplug it before installing then plug it back in afterwards. Ubuntu *should* enable access to it.

---

### Post by samwillc on 2012-05-19
From another new user, I was on win7 and have only looked back a few times!

Ubuntu 12.04 is very fast in comparison to window, I don't know why, maybe not as many processes, or only needed ones run? All I know that it's a real joy to use, themes are excellent too, and the cairo dock makes it so worthwhile for me. I don't see it as a poor mans mac at all (as mentioned in another forum!). I see it as an independent system with less problems as windows or mac, and more good stuff than both!

Total convert here after using windows since win95.

Sam.

---

### Post by Cheeseter on 2012-05-19
Would you guys recommend 32 bit or 64 bit? My last download stalled about 3/4 of the way through, I think I lost an internet connection.

Let me know!

Thanks for all the responses! I look forward to familiarizing myself with Ubuntu.

---

### Post by Swagman on 2012-05-19
Other people will say this is Heresy but I recommend the 32  bit version (PAE).

Just to clarify... Just about everything works ok on 64 bit except certain Facebook games (Flash). Now if you have a Mrs/girlfriend then their FB games are the be all and end all and you'll never hear the last of it if they don't work correctly.

---

