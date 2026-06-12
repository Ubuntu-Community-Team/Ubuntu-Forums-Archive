---
title: "Server"
date: 2011-12-31
forum: General Help
---

### Post by dRounse on 2011-12-31
I am about to make my server and I am going to put it on my computer with Lubuntu, for some reason i cant get my Ubuntu Server disk to work so I installed Lubuntu and I am going to remove all the excess baggage but I need to know the programs to install, or maybe a command to install a server over it, because I could uninstall the desktop all together. Any help would be great. 

I would like to have it be a file server, so I think thats SFTP or SSH, Ive seen the LAMP thing but I dont need a mail server or webhosting and that jazz, just something to store my files and be able to access them from anywhere not just in my house.

---

### Post by d3v1150m471c on 2011-12-31
10.04 server + virtualbox + sshd. you might even throw in port knocking for good measure. you can make a tor hidden service and host a media directory with python SimpleHTTPServer. whatever.

---

### Post by Lars Noodén on 2011-12-31
If you need to access the files from anywhere, not just your house make sure that your router (if you have one) is forwarding SSH to your server.  Then you can use [SSHFS](https://help.ubuntu.com/community/SSHFS) to mount the remote file system and get at your files.  It's easy and very secure.

---

### Post by dRounse on 2012-01-01
I know those things I need to know the back end programs for the server.

---

### Post by Lars Noodén on 2012-01-01
> **dRounse said:**
> I know those things I need to know the back end programs for the server.

For SSH and SSHFS all you need on the back end is the package OpenSSH-Server.

What other activities did you want to make possible?

---

### Post by dRounse on 2012-01-01
> **Lars Noodén said:**
> For SSH and SSHFS all you need on the back end is the package OpenSSH-Server.

What other activities did you want to make possible?
  Thank you and I would like to be able to stream video and music and that stuff, so if im out I could stream a movie to my Android Tablet or maybe stream music to my ipod if I want to set up my ipod on a player and stream, like christmas music, so I dont need to save it to my ipod (if thats possible) and make it accessible for my family to also use, so any user friendly front ends would be nice.

---

### Post by Lars Noodén on 2012-01-02
Icecast ([http://icecast.org/](http://icecast.org/)), VLC ([http://wiki.videolan.org/](http://wiki.videolan.org/)), or FFmpeg ([http://ffmpeg.org/](http://ffmpeg.org/)) can stream music.

---

### Post by dRounse on 2012-01-02
Do those have guis or are they comandline?

---

### Post by Lars Noodén on 2012-01-02
Icecast has an easy to use configuration file.

VLC has a [GUI-based wizard](http://www.videolan.org/doc/streaming-howto/en/ch02.html).

---

### Post by dRounse on 2012-01-02
I have ben having trouble partitioning my new Caviar Green HD it keeps saying that something isnt aligned, by like 512MB or even up to 3000MB and I have formatted it and it wont boot after I have installed an OS, it says theres isnt anything to boot. any help there would help, and would using RAID be worthwhile?

---

