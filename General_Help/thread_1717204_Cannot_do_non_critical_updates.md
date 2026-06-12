---
title: "Cannot do non critical updates"
date: 2011-03-29
forum: General Help
---

### Post by uaebuntu on 2011-03-29
I'm running 32 bit 10.10 on a Lenovo N200 laptop, I have 3 other Ubuntu computers on my home network and they don't suffer from this problem, 1 is 10.10 32 bit, 1 is 10.10 64 bit and one is 10.04 32 bit. they are on the same network and I cannot see a difference.  

However when update manager says there are some updates available, I can install the critical ones but not the "other updates", it tells me that they would require installation from non authenticated sources then after agreeing will not install and goes back to the start of the update process.

The error message lists ALL the "other updates" if I deselect them then the critical upgrades down load and install OK.

I've taken screen shots of the relevant pages, can anyone help?

---

### Post by linuxuser12345 on 2011-03-29
How new is your installation? You can try reinstalling new.
Or, you can take the updates you can get, and then try again afterwards

---

### Post by uaebuntu on 2011-03-30
I probably upgraded to 10.10 about 3 months ago, I run a new release on one of the other boxes for a while before moving over to the ones everyone in the house uses.

As the updates are non critical I guess I'll live without them... but its strange and I'd like to find out why.

---

### Post by uaebuntu on 2011-04-11
So as part of this continuing saga I get a red warning triangle in the panel at the top of my screen. It tells my that repositories could be out of date and that I should run update manager and check this. I did and it appears that the two medibuntu repositories were the offending parties so I deselected them. Update manager ran again itself to update the software and I got the attached error message, however 4 critical and 1 non critical updates appeared like magic, when earlier it had not shown any, and they all installed.

I've thought of one difference between this and my other computers, being a laptop it is often connected by wireless, like now, though only on my home network

---

### Post by Krytarik on 2011-04-12
Like the error messages states, the GPG key is invalid, try updating it with this command:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```
Greetings.

---

### Post by uaebuntu on 2011-04-12
Thanks for the reply. I did as you suggested (see screenshot) and then ran Update manager again and got the attached error message, which looks the same. 

The medibuntu repositories do not load either when I reselected them.

As I say it may be something to do with the wireless connection, so I'll connect to the wired Lan when I get a chance later today.

---

### Post by Krytarik on 2011-04-12
It seems like the key on the server is invalid as well. Can you reproduce this error by doing the same, incl. the key update, at one of your other machines?

---

### Post by uaebuntu on 2011-04-13
I put the laptop on the wired LAN and Update Manager worked OK, all the backlog of non critical updates installed and no error messages. 

I ran the key update on the other 32 bit 10.10 machine (on the same LAN) and got the same results as before in the terminal and no error message in Update Manager, the tree built OK.

I'm wondering if it is someting to do with delays on the wireless. However I'll mark this thread solved as the solution seems to be "plug it into the LAN".

Thanks for all your help.

---

