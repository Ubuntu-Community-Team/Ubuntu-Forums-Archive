---
title: "Locked out of Root."
date: 2010-09-05
forum: General Help
---

### Post by Al_is_venting on 2010-09-05
Ok guys i am in desperate help, very frustrated.  Here is what i am trying to do.

I have a PDF file that opens withing a Morzilla browser.

Within is a link to a real player streaming audio .RM 

I have tried using default player to play it and it says there is a streaming issue. 


So

I install real player but it does not show up under open file with other program. 
I try saving .RM file and using real player to open it. wont work.


I try to go under ROOT to find real player but it wont let me go in Says Denied! WTF! 

If i am going about it the wrong way please tell me.

THanks

Please help.

---

### Post by WorMzy on 2010-09-05
What..?

As far as I know, Real Player hasn't been in the repos since Dapper Drake (6.06), so I'm guessing you installed it manually? How? Can you provide a link?

In any case, you shouldn't have any reason to go into /root, that's just where the root user's settings are stored.

I believe that mplayer and VLC should be able to play .rm files, so maybe you could try those out instead. Both are in the repos, so they should be installable from the Software Centre (Applications -> Ubuntu Software Centre) and Synaptic (System -> Administration -> Synaptic Package Manager), or through apt-get/aptitude:

```
sudo apt-get install vlc
``````
sudo apt-get install mplayer
```

After they're installed, they should appear under Applications -> Sound & Video.

---

### Post by Al_is_venting on 2010-09-07
SO is it normal for the root to be locked? I am new to Linux but i want to be able to do everything and i plan to experiment with lot of things.  Therefore i feel kinda buthurt that its tryingt  to control me telling me where to and not to go :D

here is the link to Real player

[http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb](http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb)

[http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.rpm](http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.rpm)

---

### Post by davidmohammed on 2010-09-07
root is a protected account in ubuntu.  You dont have to log into root to do stuff.

If you want to run something as root you prefix the command with "sudo"

this will ask you for your password - if you are an administrator you will be able to run the command.

---

### Post by Al_is_venting on 2010-09-07
thanks David, i actually googled it after asking :D and was just about to say i found it.
sudo -i is what worked for me, then my user password.

i am playing around wiht macchanger and other progs so needed root access.

---

### Post by Al_is_venting on 2010-09-07
Sorry me again, for the sake of not wasting another post for htis question;

What is the opposite command to  " ifconfig wlan0 down"?

I have tried On, Start, and UP. but nothing worked. i ended up having to restart the computer.

---

### Post by Smart Viking on 2010-09-07
> **Al_is_venting said:**
> Sorry me again, for the sake of not wasting another post for htis question;

What is the opposite command to  " ifconfig wlan0 down"?

I have tried On, Start, and UP. but nothing worked. i ended up having to restart the computer.

According to the man page, "up" is the way to go, so
```
ifconfig wlan0 up
```
should work(i think). :)

---

