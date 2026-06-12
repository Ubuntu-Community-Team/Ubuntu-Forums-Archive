---
title: "so much confusion"
date: 2012-01-14
forum: General Help
---

### Post by masterrob213 on 2012-01-14
ok im running 9.04 because of 10.04 giveing me the white screen of doom (basicly white strips down on the screen and i lose control of my keyboard) and 10.10 freezes on me at any random moment. 11.04 and 11.10 says there is a keyword missing in the config file. so im useing 9.04 right now and im trying to install wine on it but idk how to do it on a discontinued system. so can anyone answer any of that

---

### Post by bluexrider on 2012-01-14
According to the WINEHQ

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```
```

sudo apt-get  update
```

```
sudo apt-get  install wine1.3
```

---

### Post by masterrob213 on 2012-01-14
masterrob213@masterrob213-desktop:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa[sudo] password for masterrob213: 
sudo: add-apt-repository: command not found```

masterrob213@masterrob213-desktop:~$ sudo apt-get  update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
  404 Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
  404 Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
  404 Not Found [IP: 91.189.92.167 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
  404 Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
  404 Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
  404 Not Found [IP: 91.189.92.167 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
  404 Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
  404 Not Found [IP: 91.189.92.167 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
  404 Not Found [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
  404 Not Found [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
  404 Not Found [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
  404 Not Found [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
  404 Not Found [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
  404 Not Found [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
  404 Not Found [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
  404 Not Found [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
  404 Not Found [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
  404 Not Found [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
  404 Not Found [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
  404 Not Found [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
  404 Not Found [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
  404 Not Found [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
  404 Not Found [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
  404 Not Found [IP: 91.189.92.177 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  404 Not Found [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources)  404 Not Found [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources)  404 Not Found [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  404 Not Found [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources)  404 Not Found [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages)  404 Not Found [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages)  404 Not Found [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources)  404 Not Found [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources)  404 Not Found [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources)  404 Not Found [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  404 Not Found [IP: 91.189.92.177 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
masterrob213@masterrob213-desktop:~$ sudo apt-get  install wine1.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wine1.3
masterrob213@masterrob213-desktop:~$
```

---

### Post by bluexrider on 2012-01-14
thats what I was afraid of because those repositories are no longer supported. 

[I]To get the most recent Wine 1.3 beta,  [click this link to install the wine1.3 package]("apt://wine1.3").

Per WineHQ
[/I]

---

### Post by bluexrider on 2012-01-14
I would like to make another suggestion. 

Might want to look into a different distribution of Ubuntu, say Pinguy 11.04. Very stable and has Wine included. It also has some proprietary drivers and software included.

[http://pinguyos.com/](http://pinguyos.com/)

---

### Post by masterrob213 on 2012-01-14
could not find package 'wine1.3'. 

im trying the pinguy op right now. do i have to install it by disk or can i do it by usb flashdrive?

---

### Post by bluexrider on 2012-01-14
I suppose if you use Unetbootin you can create a bootable USB but you still have to download the .ISO 

I use the Live DVD myself to install from. Haven't tried a USB. 

I know when I have used strictly Ubuntu installations that something had to be tweaked. Using Pinguy it worked straight away.

---

### Post by masterrob213 on 2012-01-14
ok interesting. whats "live dvd" ?

---

### Post by bluexrider on 2012-01-14
Go to the web site [http://pinguyos.com/](http://pinguyos.com/)
and select which distribution you want 32 or 64bit, select how you want to download it either a .torrent or from sourceforge.

Download the file then using your disk burner and whatever tools you have you will burn a bootable disk.ISO this is a installation/boot disk.

Once the disk is completed you would insert that into the CD/DVD tray and reboot your computer. 

Most computers have a BIOS selection tool that allows the PC to boot from a CD/DVD medium. You would want to have that enabled as to make sure the DVD is found and is able to boot.

The live CD allows you to try the distribution before committing to install it. This allows the USER-YOURSELF to test drive the new operating system and experience the features before hand.  

Pretty simple really. From start to finish in about 45 minutes. The version currently posted is 11.04.1 which is the latest from Pinguy. 

Good luck

---

### Post by masterrob213 on 2012-01-16
ok i downloaded it and i made it into a bootable flashdrive and when i try to boot it off it i get, boot:   so i tried putting something in there like boot: yes and i get yes is not the kernal image.

---

