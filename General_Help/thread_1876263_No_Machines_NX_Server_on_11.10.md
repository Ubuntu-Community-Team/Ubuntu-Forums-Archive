---
title: "No Machines NX Server on 11.10"
date: 2011-11-05
forum: General Help
---

### Post by DapperMe17 on 2011-11-05
Has anyone had success installing the client, node and server from No Machines on 11.10?

Upon installing the server with Gdebi, is showed as a successful install, but also showed a "conflict error with installed nxserver" warning. 

Any comments would be appreciated.

Thanks!

---

### Post by DapperMe17 on 2011-11-09
bump

---

### Post by DapperMe17 on 2011-11-15
bump

---

### Post by DapperMe17 on 2011-11-18
Anyone with NoMachines NX Server and Node running on 11.10?

Have not been able to install NoMachines NX Server on multiple 11.10 systems...Ubuntu Software Center closes without installation, and Gdebi installs, but with red conflict errors on the multiple PC's.

Never a problem installing NoMachines NX Server on Ubuntu versions through 11.04!

Conflicts beginning with 11.10.   

?

---

### Post by azmyth on 2011-11-21
I found you have to install nxclient and nxnode before you install nxserver. I would remove all three and then install the client then node then server.

---

### Post by DapperMe17 on 2011-11-22
Thanks, that is the order I've used.

---

### Post by collisionystm on 2011-11-22
I had never even heard of it! :p

---

### Post by azmyth on 2011-11-22
I was surprised too. I just downloaded the packages from nomachines and I got a dependency issue when I installed nxserver first. I used NxClient successfully on 11.10 but I recently switched to NX 4 due to pulseaudio forwarding.

---

### Post by DapperMe17 on 2011-11-22
Yes, NX4 installed fine, but NX3 Server will not without conflict...beginning in 11.10.

However, NX4 final appears that it will be fee-for-service. 

X2Go has very recently released it's new version, which includes "desktop sharing/shadow". 

It installed effortlessly! However, I haven't installed it on a "remote" server yet, to test the "shadow" session. 

If you try it, please report back on any shadow session experience.

---

### Post by azmyth on 2011-11-23
Now that I think of it, I never used NX 3 in 11.10 as I just went ahead and upgraded to NX 4. NX 4 is more of a screen grab whereas NX 3 was more of a login based system where you could change the remote desktop to something different like fluxbox. With NX 4, I can't get the SSH key based auth to work so I'm using an nx user I created.

Will X2go forward the audio? If you know. I couldn't find anything on their site.

---

### Post by DapperMe17 on 2011-11-24
Yes, X2Go does it all! Here's the PPA....[https://launchpad.net/~x2go/+archive/ppa](https://launchpad.net/~x2go/+archive/ppa)

I've tested it on my system as a loopback...using x2go server, x2go desktop sharing and x2go client.

Installed perfectly, with no configuration of config files whatsoever...as compared to NX3.

I had a loopback desktop in 2 minutes. 

However, I've not had the chance yet to try out desktop sharing(shadow) on a remote server. 

If you try it, let us know your results. I will do the same.

:guitar:

---

### Post by azmyth on 2011-11-24
Thanks for turning me onto x2go. This works great and was super simple to setup even with ssh key based auth. I couldn't get vlc audio to work though through forwarding but mplayer did and so did the system. It even recognized my mic on the windows side.

I tried the shadow connection but it doesn't appear to work from Windows 7 to Ubuntu. I did try it on the localhost (server and client on same PC) and it worked all beit I got stuck in an infinite loop but I thought this would happen. I have a 10.04 mythtv install. I may try from there later.

---

### Post by DapperMe17 on 2011-11-24
Hear ya on the infinite loop! That's the same behavior that I encountered. I haven't yet had a chance to test it between two seperate PC's.

[-o<

---

### Post by DapperMe17 on 2011-11-24
azmyth,

How did you connect via RSA Key Auth?


[I][B]Here's what worked for me...albeit, the key sharing seems backwards compared to NX. 
[/I][/B]

I generated the RSA key pair on the "client" machine. 


I pointed the X2Go Client RSA/DSA location....to the client "id_rsa" *(private key) in the client's .ssh folder.


Then, I distributed the client's "id_rsa.pub" (public key) to the server, and placed it in the server's "authorized_keys2" file, located in the server's .ssh folder.


After accepting the initial SSH fingerprint (that's automatically placed in the client's "known-hosts" file in the client's .ssh folder), I was able to connect to the session with the RSA key auth handshake, rather than using the name & password login method. 


Does this sound right?


Thanks!

---

### Post by azmyth on 2011-11-25
I agree key auth in NX 3 seemed backwards.

I did like you said you did for x2go and key auth worked without issue. I have my ssh key based auth so both x2go and ssh work as desired.

NX 4 didn't work like this. I ran ssh in debug mode and it showed the key auth working but then nx 4 would timeout thus the key auth wouldn't work and I'd get an nx error. I just turned on NXs user db and created a user and I was able to login. I don't really like not being able to use key auth though.

---

### Post by DapperMe17 on 2011-11-25
Great, thanks much for your confirmation.

Best of luck with NX4 and X2Go!

:popcorn:

---

### Post by DapperMe17 on 2011-11-26
After a X2Go server reboot, I connect just fine to a regular Gnome/KDE/etc session. 

However, now when I try to desktop share (shadow), I receive an error in the X2Go client...."access denied from user". 

Ironic, as I was able to shadow fine after X2go install, but prior to the first server restart. 

Obviously, after the first server restart it's probably a simple permission issue...I presume on the server. 

Would you have an idea on this? 

Thanks

---

### Post by azmyth on 2011-11-26
Did you start x2godesktopsharing on the server side? You need to do this then enable desktop sharing which should change the icon in the tray from an x to a green check.

---

### Post by DapperMe17 on 2011-11-27
Thanks.

It's working today, after a restart of the server. 

On the server end, I don't seem to have to "activate" desktop sharing through the panel icon, in order to shadow. It will shadow even with the icon showing "inactive" (icon/red x).  

:P

---

