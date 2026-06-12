---
title: "building a home network using ubuntu and windows"
date: 2006-02-18
forum: General Help
---

### Post by yotama9 on 2006-02-18
hello.

I having lodas of truble creating home network betwin the two computers. (using both linux and windows) I think that the rauter is the source of the problems, here is my "infrastrcature"

Desktop copmuter running Windows XP PRO (soon to be downgraded to home eddition) this computer is conneted via ethernet to the Router (EDIMAX).

Laptop computer running Ubuntu Breazy, connected via wireless connection to the same router (LAN Wireless network)

the Router - EDIMAX is conneceted via the WAN port to the MODEM (and to the internet ofcourse).

Both the machine have no problem connecting to the internet but I didn't manage to connect betwin them (there are some shared folders on the windows but I can't see them)
what do I have to do? open some port on the router or something alse?

I should mention that while on other wireless networks I could have seen other computers, only on my wireless network I have this problems
thanks

---

### Post by nalmeth on 2006-02-18
hmm, what are you using to try to connect to the windows share? I think samba comes installed on breezy, but try in terminal:
sudo apt-get install samba

then, hit alt-F2, and type in the command:
nautilus smb:/
I wouldn't recommend using nautilus for browsing in the future, but just for testing right now. 

EDIT: also make sure all firewalls disabled. If you really think router is the problem, you can use a web-browser to connect to your router by entering its IP address, and change its settings there.

---

### Post by yotama9 on 2006-02-18
well I'm not sure if it's OK or not

I did as you told me to and a window poped up asking me for a password. I'm not sure weather it was a password for the windows machin or the ubuntu one. 

I tried logging in without a username and managed to but I only got to see the ubuntu machin

---

### Post by nalmeth on 2006-02-18
Hmm what was the network called? Did you only see the ubuntu computer? can you access its shared folders? At my home, the shared network is controlled by a Windows computer, and the network is called MSHOME.

---

### Post by knalle on 2006-02-18
[QUOTE=nalmeth]hmm, what are you using to try to connect to the windows share? I think samba comes installed on breezy, but try in terminal:
sudo apt-get install samba
[/QUOTE]

samba is for sharing files to a windows machine, not connect to a windows machines shared files.

you need to get **smbfs** for **mount**.

then you can do

**mount -t smbfs -o username =winuser //winbox/share /mount/point**

---

### Post by nalmeth on 2006-02-18
hey knalle :mad: 

good call! :grin:

---

### Post by yotama9 on 2006-02-18
nothing
I just can't see the windows machine

the network is named MSHOME indeed  and I try logging in the windows user but just can't do it
I used the windows wizard to configur the network. 

could it be that the router just can't connect the two computer?

thanks

---

### Post by knalle on 2006-02-18
easy to get it mixed up

---

### Post by knalle on 2006-02-18
first, can you ping the box?

in windows go to startmenu->run and write "cmd" then write "ipconfig" to get the windows box ip, ping it from ubuntu.

if you can ping it;

mount -t smbfs -o username =winuser //win.ip.add.ess/share /mount/point

---

### Post by yotama9 on 2006-02-18
well I got it one way

I can see the window machine and brows the shared foldres, but I browes the ubuntu machine. I can see it but it keep asking me for a password and my user password isn't anough.

any Idea?

---

### Post by knalle on 2006-02-18
man smbpasswd

and

man samba

---

### Post by yotama9 on 2006-02-19
well I've read the manuals but it didn't help me

I don't know what user should I try and log in.

any help?

---

### Post by knalle on 2006-02-19
the user is your ubuntu user account and our password is your ubuntu password,

**man smbpasswd**!!!!!!!!!!!!

---

### Post by yotama9 on 2006-02-19
no need to get obset. 
I did tried the ubuntu defoult username and passward without luck.

I've read the manual but I hadn't find any referance for user management. 

thanks

---

### Post by hamil on 2006-02-21
Well, you could try this command in a terminal:
smbpasswd –a username

where you replace username, with the desired username.
It will set the user and password for Samba.

Good luck! :)

---

### Post by nuno on 2006-02-21
You may also go to /etc/samba/samba.conf  and in the sector
 ####### Authentication ####### make the change
security = share

Now you dont need password :(

---

