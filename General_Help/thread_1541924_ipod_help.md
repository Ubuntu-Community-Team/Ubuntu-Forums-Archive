---
title: "ipod help"
date: 2010-07-29
forum: General Help
---

### Post by tal32123 on 2010-07-29
I know how to copy music to my ipod touch through rythmbox, but how do I copy videos? I've been looking on google and youtube for help so pls no evil comments

---

### Post by dacman48 on 2010-07-29
is the 'pod jailbroken? if so, use sftp to go into the device and find the videos that way

---

### Post by tal32123 on 2010-07-29
> **dacman48 said:**
> is the 'pod jailbroken? if so, use sftp to go into the device and find the videos that way

sftp for the ipod or ubuntu?

---

### Post by dacman48 on 2010-07-30
apologies, shoulda been more specific. if the idevice is jailbroken, make sure u have the ftp server package installed(i forgot wat its called). after that is done, simply use an ftp client to access the idevices filesystem, remembering that the port for sftp is 22, not 21. as for ftp clients, i recommend filezilla

---

### Post by tal32123 on 2010-07-30
> **dacman48 said:**
> apologies, shoulda been more specific. if the idevice is jailbroken, make sure u have the ftp server package installed(i forgot wat its called). after that is done, simply use an ftp client to access the idevices filesystem, remembering that the port for sftp is 22, not 21. as for ftp clients, i recommend filezilla

i dont want to access it through the internet, isn't there some sort of application that i can run on ubuntu and it can send it through the itouch's usb?

---

### Post by dacman48 on 2010-07-30
honestly, i dont know offhand of any that run in ubuntu, but i think that a program called iphone browser should run just fine in wine. the program download link should show up as the first result in a google search

---

### Post by tal32123 on 2010-07-30
> **dacman48 said:**
> honestly, i dont know offhand of any that run in ubuntu, but i think that a program called iphone browser should run just fine in wine. the program download link should show up as the first result in a google search

honestly i've had nothing but trouble from wine/playonlinux/crossover :(

---

### Post by dacman48 on 2010-07-30
hrmm... that complicates things slightly. ill do a couple google searches, see if i cant find a solution. u sure that a wifi connection is an impossibility?

---

### Post by jerenept on 2010-07-30
GTKPod.

---

### Post by tal32123 on 2010-07-30
> **dacman48 said:**
> hrmm... that complicates things slightly. ill do a couple google searches, see if i cant find a solution. u sure that a wifi connection is an impossibility?

yes, since i like watching tv series so i put a bunch of them on my ipod, my internet speed is decent, yet not good enough for that. gtkpod doesnt find my itouch

---

### Post by dacman48 on 2010-07-30
connecting how im describing, the connection doesnt depend on your internet connection speed, but your wlan speed. assuming u have a wireless g network, theres 54mb/s of connection. so long as your not doing any heavy torrenting or downloading, this should move your files with a decent degree of speed. admittedly not as fast as usb, but still zippy

---

### Post by tal32123 on 2010-07-30
> **dacman48 said:**
> connecting how im describing, the connection doesnt depend on your internet connection speed, but your wlan speed. assuming u have a wireless g network, theres 54mb/s of connection. so long as your not doing any heavy torrenting or downloading, this should move your files with a decent degree of speed. admittedly not as fast as usb, but still zippy

:( fine since its the only way i know of, can you please give me some detailed instructions since im a total noob to this. by the way is the video folder in the ipod as cluttered as the music one? since the music one changes the names of all the songs to random ones thrown across random folders. thanks for all the help so far :)

---

### Post by dacman48 on 2010-07-31
sorry to break it to you, but absolutly EVERTHING about idevices' filesystems is a cluttered mess. are you absolutly sure that u cant get wine working? that way would be the easiest

---

### Post by tal32123 on 2010-07-31
> **dacman48 said:**
> sorry to break it to you, but absolutly EVERTHING about idevices' filesystems is a cluttered mess. are you absolutly sure that u cant get wine working? that way would be the easiest

I tried using ifunbox in wine but that doesn't work unless you have iTunes installed, which didn't work for me (I tried iTunes 9 I that helps)

---

### Post by dacman48 on 2010-08-01
well, the jailbreaking route it is. ill need u to post ur device details, eg the device model, firmware. after that i can direct u to the correct jb too

---

### Post by tal32123 on 2010-08-01
I have an iPod touch 3g firmware 3.1.3,  jailbroken of course,(I might update the firmware when the jb comes out but for now 3.1.3)

---

### Post by dacman48 on 2010-08-02
so ur already jailbroken? thats good. do u have the ssh package installed?

---

### Post by tal32123 on 2010-08-02
What is the package called?

---

### Post by dacman48 on 2010-08-02
uhhhhhh...... i kinda forgot >.<

---

### Post by tal32123 on 2010-08-02
> **dacman48 said:**
> uhhhhhh...... i kinda forgot >.<

Do u know any other ways?

---

### Post by dacman48 on 2010-08-02
the package is called openssh. install from cydia

---

### Post by tal32123 on 2010-08-02
> **dacman48 said:**
> the package is called openssh. install from cydia
Okay I'm done now what?

---

### Post by dacman48 on 2010-08-02
do u already have an ftp client installed?

---

### Post by Cpierce on 2010-08-02
see if this will help

[http://dlb-network.com/2010/05/ubuntus-libmobiledevice/](http://dlb-network.com/2010/05/ubuntus-libmobiledevice/)

and this

[http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

---

### Post by tal32123 on 2010-08-03
I only have it if it's in the default ubuntu programs

---

### Post by dacman48 on 2010-08-03
well, since im not sure ubuntu comes with an ftp client by default, i recommend going into the application adder(?) thingy, and seearching for filezilla

---

### Post by tal32123 on 2010-08-16
> **dacman48 said:**
> well, since im not sure ubuntu comes with an ftp client by default, i recommend going into the application adder(?) thingy, and seearching for filezilla
ok i know how to ssh now, but is there a way where i can get it in to the regular videos app? that way it is much faster and it bookmarks where i was last on the video.

---

