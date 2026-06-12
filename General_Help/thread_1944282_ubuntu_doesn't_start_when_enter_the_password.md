---
title: "ubuntu doesn't start when enter the password"
date: 2012-03-21
forum: General Help
---

### Post by active3 on 2012-03-21
Hi

i have a problem with ubuntu 11.10
it happen when ubuntu ask me about the password of my username
i type the password correctly, and a black screen apear for seconds and gone
and return me to the password and username ask :mad:

i can'y even enter the "guest session" because of the same problem
i tried to reset and change the pass in Recovery mode, but it didn't work too
please help me, i really don't want to install ubuntu and all applications again :(

thanks

---

### Post by Bucky Ball on 2012-03-21
Have you done any updates, added new drivers or apps recently?

---

### Post by active3 on 2012-03-21
> **Bucky Ball said:**
> Have you done any updates, added new drivers or apps recently?
thank you for you response
yes, i installed an updated ClamAV and scanned ubuntu with it
and i did a stupid thing in terminal wich removed "Restart" & "Shutdown" icons before this problem happened
but i don't remember what i did in terminal :(
anyway, i restarted the system with "sudo reboot" and then get this problem :mad:

Note: im using ubuntu and windows 7 on the same computer

---

### Post by Bucky Ball on 2012-03-21
Yea, ClamAV seems to be causing a few problems not unlike this for some people I've noticed recently. You might want to dig there. That may be preventing the login or may have changed something. You might also want to try changing the password and trying that.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

The dual-boot with Windows would probably have nothing to do with your problem but thanks for adding that info. ;)

---

### Post by active3 on 2012-03-21
> **Bucky Ball said:**
> Yea, ClamAV seems to be causing a few problems not unlike this for some people I've noticed recently. You might want to dig there. That may be preventing the login or may have changed something. You might also want to try changing the password and trying that.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

The dual-boot with Windows would probably have nothing to do with your problem but thanks for adding that info. ;)

actually i did this more than one time, but it still not working

is there anyway to save my applicatins that installed in ubuntu so i can make them back when i install it again?
by the way i have another question has nothing to do with this problem

is the dualbooting a bad thing? and (if it is) why?

---

### Post by drakemata on 2012-03-21
> **active3 said:**
> actually i did this more than one time, but it still not working
 
is there anyway to save my applicatins that installed in ubuntu so i can make them back when i install it again?
by the way i have another question has nothing to do with this problem
 
is the dualbooting a bad thing? and (if it is) why?
 
@active3, first I would say you can probably fix this without having to reinstall your distro. But if you can't, all of the debs (at least on my kubuntu install) for any updates or other programs you have installed should be located in /var/cache/apt/archives/ (unless you have flushed your cache) and you can copy all of those to an external HDD to restore when you reinstall Ubuntu by navigating to the drive/directory in terminal and executing the command:
 
```
sudo dpkg -i *.deb
```
 
As for the dual booting, I wouldn't say it is a bad thing. There are some times that you need to run another OS for a specific program. The only issue that I have seen with dual booting is when a user unknowingly mounts the other partition and starts messing around with the file system. There are ways to prevent that, but if it just you using the computer, it shouldn't be an issue (just don't do it).

---

### Post by active3 on 2012-03-21
> **drakemata said:**
> @active3, first I would say you can probably fix this without having to reinstall your distro. But if you can't, all of the debs (at least on my kubuntu install) for any updates or other programs you have installed should be located in /var/cache/apt/archives/ (unless you have flushed your cache) and you can copy all of those to an external HDD to restore when you reinstall Ubuntu by navigating to the drive/directory in terminal and executing the command:
 
```
sudo dpkg -i *.deb
```As for the dual booting, I wouldn't say it is a bad thing. There are some times that you need to run another OS for a specific program. The only issue that I have seen with dual booting is when a user unknowingly mounts the other partition and starts messing around with the file system. There are ways to prevent that, but if it just you using the computer, it shouldn't be an issue (just don't do it).

i tried to copy the archives folder, by typing this:
```
cp -r /var/cache/apt/archives /media/6014DB2514DAFD4A
```"6014DB2514DAFD4A" is "D" Drive
and entered windows 7 to see if its working but it didn't :(
if i could remove the user and password asking (or someting like that :p) i think that the problem will be solved
but is there anyway to do this ?

thanks about the dualboot answer

---

### Post by Bucky Ball on 2012-03-21
Dual-boot not an issue. I have no ideas on the original problem but I don't doubt there is a fix somewhere. Perhaps keep digging for awhile; reinstall considered last resort. ;)

---

### Post by dave2001 on 2012-03-21
If you think ClamAV might be an causing some problems, just remove it for the time being. Start in recovery mode and go to root cli.

```
 apt-get purge *clamav*
```

you can also reset your password, just in case that helps.

```
ls /home
``` should return a list which verifies your username.

```
passwd *username*
``` where username is replaced with your  username

---

### Post by drakemata on 2012-03-22
> **active3 said:**
> i tried to copy the archives folder, by typing this:
```
cp -r /var/cache/apt/archives /media/6014DB2514DAFD4A
```

 
I am pretty sure the reason this didn't work is because when you specified 
```
/media/6014DB2514DAFD4A
```
you were basically trying to copy to the root of that partition. Try making a new directory first to backup your debs.
```
mkdir /media/6014DB2514DAFD4A/*path/to/new/folder/*
```
 
I also have to agree with dave2001, that you should just remove ClamAV because that seems to be the root of all of your problems and that reinstalling your distro should be considered your last resort. Good luck.

---

