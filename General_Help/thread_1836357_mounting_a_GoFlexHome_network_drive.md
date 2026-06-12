---
title: "mounting a GoFlexHome network drive"
date: 2011-08-31
forum: General Help
---

### Post by delvis on 2011-08-31
I have been searching the forum for awhile now and cant find an answer so I though I would make a new thread.
I have been using Ubuntu since 9.something but I am not good with the terminal or anything that doesn't work plug and play.
I just bought a GoFlex Home 2tb network drive and need some help mounting the network. I'm running windows xp on a dual boot and it works fine. I can go to places-->network and I see "SFPT file transfer on GoFlexHome" If I try to mount it I get "Unable to mount location""ssh program unexpectedly exited" I want to be able to mount the drive and transfer files to it.
Can anyone help
Im using 10.10
Thanks

---

### Post by sraghav on 2011-10-26
Had a similar problem, and found answers here...

[http://forums.seagate.com/t5/GoFlex-Net-GoFlex-Home/GoFlex-Home-and-Linux-mount-as-cifs/td-p/74127](http://forums.seagate.com/t5/GoFlex-Net-GoFlex-Home/GoFlex-Home-and-Linux-mount-as-cifs/td-p/74127)

Hope it helps...

---

### Post by arvin555 on 2012-08-10
This is an old post, but would like to share my experience.

I have Seagate GoflexHome network drive 2TB.
Running Ubuntu 10.04LTS

What I did was:

1. Check/learn what is the IP address of the Goflex drive, usually by going to your router and checking Goflexhome IP address. 

2. On Ubuntu I clicked Places/connect to server.

Service type: "Windows Share"
Server: xxx.xxx.xxx.xx (Type in the IP address of goflex)
Then click connect

3. The folders should then be mounted and be visible.

4. When you try to open the folder, a popup window will ask for user name and password, just use your username and password that you set up for Goflex. 

Hope this helps others.

TTFN
Arvin

---

### Post by s13_mills on 2012-10-07
Hi There,

Again, I note this is an old post, but I have recently been playing with the setup of my GoFlexHome on my Ubuntu install, and found the best solution to be the one posted by daithioc in the Seagate forum post linked above.

If you don't like putting your username and password for the drive in your fstab, there are good instructions on the [Ubuntu wiki]("https://wiki.ubuntu.com/MountWindowsSharesPermanently") about how to get around this!

One notable issue is that now if I run:
```
sudo mount -a
```

I get an error about the line in my fstab, but the drive seems to work fine - much more reliable than connecting with afp, which seems to be what Ubuntu wants to do if you browse for the drive through the 'Network' folder in the file manager.

---

### Post by jingaling on 2012-10-07
This is how I mount a path to my NAS in Ubuntu:

Run the following command in Terminal:

```
sudo apt-get install gvfs-bin
```

Open Gedit (Ubuntus version of Notepad) and enter the following text:

```
gvfs-mount smb://%Path_to_share%
```

NOTE: Where "%path_to_share%" is listed this will be replaced with the actual share path. So, if there is a share called 'share' on computer01 then the actual command would be:

```
gvfs-mount smb:computer01/share
```

Now save the file as .FILENAME.sh (e.g. .ShareMount.sh) in home and allow execution of the file (do this by right clicking, selecting properties and then permissions). 

Test the script by running it to see if it mounts the share.

Finally create a new startup item to run the script at startup. Re-boot your machine to test and the share should be mounted automatically.

Hope this helps :)

Jing

---

