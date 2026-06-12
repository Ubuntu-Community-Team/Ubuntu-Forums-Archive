---
title: "SAMBA:  Linux to Win machine.... Win wants password"
date: 2006-04-09
forum: General Help
---

### Post by Old Jimma on 2006-04-09
Hi Ubunto:

I'm having trouble with SAMBA, in the last steps needed to gain access to Windows computers on my home network. Here are the details.

I have a home network of 1 Ubunto machine (Asus)  and 2 windows machines (Scotty and Gateway). The workgroup name on the windows network is "PHILHOME".

I have: 
(i) installed Samba, following the wiki careully, 
(ii) started samba, 
(iii) provided samba with a password, and 
(iv) shut off the firewall on Asus, the Ubunto machine.

When I do a  Places > Newtowrk Servers from Asus I see the windows network icon.

When I click on that icon, I see "philhome" (specificed in lowercase on the icon).

When I click on the "philhome" icon, I see a "Gateway" icon , but not a "Scotty" icon.

When I click on the "Gateway" icon, a pop-up comes up with 
(a) a username corresponding to my username in the username box,
(b) a "Domain" box, with "WORKGROUP" specified in that box, and
(c) a "Password" box, that is blank.

I checked the network identification of my windows network.... a "Domain" name is not listed, only a "Workgroup" name, which is "PHILHOME"

What should I do to satisfy (b) and (c) above? Changing "WORKGROUP" to "PHILHOME"  in the "Domain" box, and then adding either my password, or the password for the Gateway machine dows not allow entry to Gateway.

Thanks,
Phil Smith
Duluth, GA

---

### Post by ubernoob on 2006-04-09
Thats a windows problem. Somewhere in windows you can change the sharing of files and folder to "simple file sharing" or something similar. I don't have a windows machine in front of me, so i can't be of more help.

---

### Post by bbarrons on 2006-04-09
I finished installing 2 days ago and have been setting up since. I have tried several linux dists orver the past 2 years. This is the first time I ran into this problem also. From my windows machine it asks for a password to log into unbuntu. I tried all users to no avail. even root and su. I installed smb4k to see if that helped. I had been using xandros for a year now without this problem. UB starts faster and seems to run better. Any ideas where to look?

---

### Post by bbarrons on 2006-04-09
[QUOTE=bbarrons]I finished installing 2 days ago and have been setting up since. I have tried several linux dists orver the past 2 years. This is the first time I ran into this problem also. From my windows machine it asks for a password to log into unbuntu. I tried all users to no avail. even root and su. I installed smb4k to see if that helped. I had been using xandros for a year now without this problem. UB starts faster and seems to run better. Any ideas where to look?[/QUOTE]
I should add that both machines have shared folders with no restrictions...

---

### Post by ubernoob on 2006-04-09
> From my windows machine it asks for a password to log into unbuntu
That is normal. If you want to access shared folder you can do like this in /etc/samba/smb.conf:

```

# Shared mp3's
[mp3]
   comment = My mp3 collection
   writable = no
   path = /data/share/mp3
   public = yes
   security = share
   guest ok = yes

```

If you try to access the windows machine from your ubuntu, then the problems is like i wrote over.
remember to do
sudo /etc/init.d/samba reload

---

### Post by Ramses de Norre on 2006-04-09
In the instructions ramses is my username, replace by your own.
```
sudo gedit /etc/samba/smbusers
```
and insert the line ```
ramses = "network username"

```
```
smbpasswd -a ramses
```
and set passwd, this passwd is asked from the windows machine.
```
sudo /etc/init.d/samba restart
```

---

### Post by Old Jimma on 2006-04-09
Hi Ramese:

Thanks for your scholarly reply. Can you please inform us what your code does? I feel that it will be helful for the community.

Gratefully,
Phil Smith
Duluth, GA

---

### Post by Ramses de Norre on 2006-04-09
Make a user file, define a user, set a password for the user, restart samba ;)

---

### Post by bbarrons on 2006-04-09
Once I setup the user and password in the smb.conf and restarted samba everything worked fine. I had no problem seeing the windows box from ubuntu and now I can see the linux from the windows. It had been years since I had setup samba to get a unix box to talk to windows.  The linux distros I had been testing didnt need to be setup.
So far ubuntu has run better on my laptop and this tower.

---

