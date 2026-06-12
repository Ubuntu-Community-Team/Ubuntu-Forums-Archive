---
title: "Sound system problem (not responding to commands)"
date: 2010-05-28
forum: General Help
---

### Post by pr0t3g3 on 2010-05-28
Hi, I'm using  a(n) old Dell Inspiron 8600 with Ubuntu v. 10.04 (lucid)

I seem to be having volume adjusting problems, (it's stuck on a low  volume setting) and, I can't seem to get into the control panel for  'system sound'; when I try I get this error:
Waiting for Sound system to reply.

I just recently had this problem, and can't seem to figure out how to  fix it.

Check out my other thread to see what I tried and failed to do:


[http://ubuntuforums.org/showthread.php?t=1491810&page=2](http://ubuntuforums.org/showthread.php?t=1491810&page=2)


What are my options; Should I get the sound driver checked out, or  should I keep trying to troubleshoot?  I'd rather not have to spend  money on new hardware for two reasons:

1.  I'm a bit broke at the moment

2. since this is an old laptop it would be a bit pointless to add new  hardware to it.

I'd rather not have to buy a new laptop either... help?

---

### Post by cariboo on 2010-05-29
Have you tried alsamixer, to set the volume levels? If that works, once you have set the volume levels to where you want, in the same terminal type:

```
sudo alsactl store
```

---

### Post by pr0t3g3 on 2010-05-29
That's uh gonna be a problem >.<

---

### Post by cariboo on 2010-05-29
Alsamixer is a command line program that should have been installed by default, you don't need to install any additional software. From the error you are getting, you need to fix the broken installation before continuing. Open a terminal and type:

```
sudo apt-get -f install
```

IF that doesn't work, go to System->Administration->Synaptic Package Manager->Edit->Fix Broken Packages. You may have to completely remove Gnome Alsa Mixer in order to repair it.

---

### Post by pr0t3g3 on 2010-05-29
> **cariboo907 said:**
> Alsamixer is a command line program that should have been installed by default, you don't need to install any additional software. From the error you are getting, you need to fix the broken installation before continuing. Open a terminal and type:

```
sudo apt-get -f install
```IF that doesn't work, go to System->Administration->Synaptic Package Manager->Edit->Fix Broken Packages. You may have to completely remove Gnome Alsa Mixer in order to repair it.
how?

---

### Post by cariboo on 2010-05-29
What part of the instructions are you having a problem with?

---

### Post by pr0t3g3 on 2010-05-29
> **cariboo907 said:**
> What part of the instructions are you having a problem with?
where do I go to remove the sound device you specify .. I have the icon on my top menu but I can seem to find the program to remove it ....

---

### Post by ubudog on 2010-05-29
You have to open a terminal (Applications>Accessories>Terminal) and then type ```
sudo apt-get -f install
```  Let me know if that works.

---

### Post by Yellow Pasque on 2010-05-29
This fix often solves the issue:
```
pulseaudio --kill
rm -rf ~/.pulse*
```
At this point, log out and in to restart your sound system.

---

### Post by pr0t3g3 on 2010-05-29
> **Temüjin said:**
> This fix often solves the issue:
```
pulseaudio --kill
rm -rf ~/.pulse*
```At this point, log out and in to restart your sound system.
Yeah thanks.. someone already asked me in the link to my other post in the op... .^_^ thanks though!



Edit: This is what happens when I copy and paste all that into my terminal!


E: main.c: Failed to kill daemon: No such process

---

### Post by pr0t3g3 on 2010-05-29
> **ubudog said:**
> You have to open a terminal (Applications>Accessories>Terminal) and then type ```
sudo apt-get -f install
```  Let me know if that works.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-docky librsvg2-2.18-cil gnome-games-common libclutter-1.0-0
  libclutter-gtk-0.10-0 libwnck2.20-cil libphysfs1 libnotify0.4-cil
  libgnomedesktop2.20-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


uhm... not sure if it worked...

---

### Post by cariboo on 2010-05-29
Did you check synaptic for broken packages? Can you install any packages?

It would be nice if you could list all the changes you have made to get sound working.

---

### Post by pr0t3g3 on 2010-05-29
> **cariboo907 said:**
> Did you check synaptic for broken packages? Can you install any packages?

It would be nice if you could list all the changes you have made to get sound working.It should all be here ^_^ not to seem like a big bother but if you read my first post and check the link... read all thats there and then read my new thread here... all the way to the end you should see....

---

### Post by pr0t3g3 on 2010-05-29
I'M LOSING IT HERE..... how the flip do I simply remove the default sound tool.. and then reinstall it... I need a name to match it.. is it called:

ALSA-utilities?  Or is that for more than just sound.. or sound at all??

---

### Post by ubudog on 2010-05-29
I'll see what I can find, but it is getting late here.

---

### Post by pr0t3g3 on 2010-05-29
.......right... I'm just going to fool with it till I get it to work.. If ubuntu stop's working then I'm uninstalling it... windows is even more disgusting.. but those 10 years of exp on it arent for nothing... if all fails I'll just buy a test pc and fiddle with ubuntu on there... I'm stuck with this foreign os for now... >.< either I'm out of my depth or I haven't explored ubuntu enough >.<

---

### Post by pr0t3g3 on 2010-05-31
solution here in pages 2 and 3:  [http://ubuntuforums.org/showthread.php?t=1491810](http://ubuntuforums.org/showthread.php?t=1491810)

---

### Post by ubudog on 2010-05-31
Glad you finally got it fixed.

---

### Post by pr0t3g3 on 2010-05-31
> **ubudog said:**
> Glad you finally got it fixed.
Lol... yeah It was but I didn't do it properly and so it got glitched... I'm waiting to get it fixed...

---

