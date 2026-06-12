---
title: "changed name and ubuntu wont load...help!!!!!"
date: 2011-05-05
forum: General Help
---

### Post by weva111 on 2011-05-05
(first and formost let me start by saying that im currently using ubuntu 10.10)

ok so im not claiming to be a genius or anything but in my infinite wisdom i wanted to change the names that came up in the terminal because it wasnt cool enough :P. you know 

xxx@xxxx: /$

i went onto google to see if this was possible and saw that all i had to do was input the following commands.... 

gksu gedit /etc/hosts 
         and
gksu gedit /etc/hostname

and change it to the new names.  well it worked...sorta.  from what i could tell the group name was changed but not the username.  so i then went to system---> preferences----->username groupnames (***this order might be typed in wrong since im NOT in ubuntu!!!)  and proceeded to change the info there.  I went ahead and selected the name and then clicked on the advance setting.    From what I remember, I went into the last tab and saw the old username.  I went ahead again and changed it to the new name that I wanted.  Not sure if this matter but I chose a first and a last name with a space (xxxx xxxx). Any who, it then asked me if I wanted to copy something from one folder to the other....and agian i said sure why not.  

After everything copied over, i decided to restart my comp to make sure everything worked accordingly.  well that's when all the fun started.  as it rebooted i started to get wonderful little  messages. they are 

1.   hostname main process xxx terminated with status 1

2.  Could not update iceauthority file /home/xxxx/.ICEauthority

3.  there is a problem with the configuration server. (usr/lib/libgconf2-4)gconf-sanity-check2-exited with status 256)

4.  nautilus could not create the following required folders: /home/xxxx/desktop,/home/xxxx/.nautilus

it then takes me to a bare original desktop background that ubuntu 10.10 came with wih.  i then started to research what could be the problem and found nothing.  what i did stumble upon was this...

i hit ALT + F2 and typed "gksu nautilus"

it brought up a folder.  I started clicking away randomly and managed to find all of my files sitting nicely just waiting for my return.  Additionally, I somehow randomly saved a blank file on the desktop.  I then right clicked it and chose to open it with Mozilla. It opened it up!!!.   i then managed to surf as usual like nothing ever happened.

so, im not sure where to go from here.  ALL my files are still there and im still able to surf the web albeit in a odd manner.  so this being my case........

CAN SOMEONE PLEASE HELP ME GET BACK TO WHERE I USE TO BE?!?!?!?!?!?!?!?!?

Im knew to Ubuntu (clearly) and have spent days on end getting everything to work just right.  I would hate to start everything from scratch.  please help

thank you all for your help in advance!!!!!

---

### Post by falko on 2011-05-05
Can you post the contents of /etc/hosts  and /etc/hostname?

Changing hostnamescan be done as follows:
```
echo server1.example.com > /etc/hostname
/etc/init.d/hostname restart
```

---

### Post by weva111 on 2011-05-05
by typing in cat /etc/hosts   i get

192.168.1.96    xxxx #added by networkmanager
127.0.0.1         localhost.localdomain    localhost
::1 xxxx  localhost6.localdomain6 localhost6
127.0.1.1

# the following lines are desirable for IPv6 capable hosts 
::1 localhost ip6-localhost ip6-loopback
fee00::0 ip6-localnet
ff00::0   ip6-mcastprefix
ff002::1 ip6-allnodes
ff02::2   ip6-allraouters
ff02::3   ip6-allhosts




by typing  cat  /etc/hostname   i get
xxxx

---

### Post by weva111 on 2011-05-05
I also would like to point out that I left the PC alone and it went into hibernation.  Doing so it took me to the Log In Screen where I could see my theme in the background.  Everything is there I just have to get back to it somehow.  Please halp!!!

---

### Post by weva111 on 2011-05-06
OK going on day #5398309534 without any help. :(:(:(:(

That said, I managed to do something I think.  For some reason the screen kept going into away mode forcing me to log in.  After a few times, I noticed that it allowed me to switch user.  Doing so I could see my theme in all its glory just waiting for me to come back.  Anywho, I somehow thought, what would happen if entered root as the SN......and viola, I have a desktop.  Albeit, not my desktop or theme but a desktop nonetheless....yay im getting somewhere....but im still trying to get back to how everything was.   I then went to where the problem started. 

System--->Administration----->Users and Groups

After i went in there all i see is the little cursor going and going just waiting for something to pop back up.....


i know ive said this before and im not sure any one understood me so Ill say it this way......... help!!!!

thank you

---

### Post by nothingspecial on 2011-05-06
Log in to a root recovery console (reboot and hold down shift (or escape))

Change your user name back like this

```
usermod -l name-it-is-now name-it-was-before
```

edit /etc/hosts and /etc/hostnames back to the way they were before using nano

eg  ```
nano /etc/hosts
```

Ctrl-O to save
Ctrl-X to exit

Use your new old user name next, as in the one it started off as and you have changed it back to, every time you see username.

```
chmod 644 /home/*username*/.ICEauthority
```

```
chown *username*:*username* .ICEauthority
```

Absolutely no clue if that will work,
But it may be possible??????

---

### Post by weva111 on 2011-05-06
yea that didnt work.

when i typed in 

chmod 644 /home/*username*/.ICEauthority
what showed up was

chmod: cannot access /home/xxxx/.ICEauthority : no such file  or directory

ugh....all i want to do is get back to my system with my new cool name :mad:

---

### Post by nothingspecial on 2011-05-06
> **weva111 said:**
> 

when i typed in 

chmod 644 /home/*username*/.ICEauthority
what showed up was

chmod: cannot access /home/xxxx/.ICEauthority : no such file  or directory



You are supposed to change the username back to the original one and use that instead of xxxx

You would have been better creating a new user "xxxx" and switching when you want a new cool name.

---

### Post by weva111 on 2011-05-06
yea i still got nothing

---

