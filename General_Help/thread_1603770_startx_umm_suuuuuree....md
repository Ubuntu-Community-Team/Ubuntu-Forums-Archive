---
title: "startx? umm suuuuuree..."
date: 2010-10-23
forum: General Help
---

### Post by Joker Pawn on 2010-10-23
[DANGER] ubuntu noob ahead [/DANGER]


as you can see in the title, im am looking for an answer. the startx command. oh, i do not remember how many times i have restarted my computer. i thought its just an error. but now, i think its a little bit more:

it all happened last night, where i finally got my VPN internet connection working. i had to login as root and mess around with the /etc/ppp folder. then i got some updates installed. on the next boot, it asked me to download an Nvidia driver( my card is geforce 7600 gs). alright, i downloaded it, it installed by itself, and then, it asked me to reboot. i said "ok, theres no harm here", but i was wrong. when it "booted up", it said some error which i cannot remember right now, and then, after a few seconds, it showed a FULLSCREEN 8-bit-like looking terminal, which said: welcome to ubuntu! i think that was not a warm welcome.

it displayed a login. now, what to do? i logged in as root. now what?

i grabbed my iPhone, and started broswing for a solution. it ended up that google was not my friend after all. But, some people said: "type in the "startx" command and you will be fine".

"oh, great, that simple, huh?" i said to myself. typed in the startx command, but i ended up getting something like this:

(EE)(<i think it was EE here) NVIDIA - blablabla... turn off the computer, check the connections of the graphics card... blablabla... and in the end, it said:

(ee) screen(s) found, but none of them are suitable(something).
i think that was the error.

and right under it, it said:

fatal error(something like that): no screens found


i was like "umm suuuureee, why tell me, ubuntu, have you asked yourself how i *see* the error, if no screens(i guess it stands for monitors) are found?"

i was a little bit confused.

i typed the startx command again, and again, and again. i was a little bit angry at me, but most on my computer, which cannot do a simple task like booting up an OS.

i ended up choosing windows xp this time(i installed ubuntu(version 10.10) through wubi) and started playing minecraft. i was fed up with the errors.

now, here come the questions:

1. how to fix the startx command in the ugly fullscreen terminal?
2. if there is a solution, do I need to login as root and type the command every time i turn on my computer?
3.(see question2) can i create a script of some sort in the system, so it auto-types the command(in the ugly fullscreen terminal), so i dont have to do it every time?


Thanks alot for helping. God bless you. seriously.

i will check this thread in a few hours, so dont expect an instant reply from me.

:)

---

### Post by WorMzy on 2010-10-23
Try running ```
sudo nvidia-xconfig
``` then startx.

Why are you logging in as root?

---

### Post by 3rdalbum on 2010-10-23
> **WorMzy said:**
> Try running ```
sudo nvidia-xconfig
``` then startx.

Why are you logging in as root?

Just typing "startx" does not work. You'd need to run it as root - and then it will go straight into your default session as root (REALLY bad idea).

Instead of "startx", use this:

```
sudo service gdm start
```

It sounds like you might need to put the X server back to its default configuration. You can do it by typing this into the command-line:

```
sudo rm /etc/X11/xorg.conf
```

(it basically removes the existing xorg configuration file).

What I believe might have happened is this: You installed the Nvidia driver from the "Additional Drivers" program, then installed the Nvidia driver manually from [www.nvidia.com](www.nvidia.com). The latter will overwrite the former, but the former will never overwrite the latter properly, not even if it comes through the Update Manager.

---

### Post by Joker Pawn on 2010-10-23
thanks guys, both of you :)

I will try these steps, and i will inform you if it worked.
3rdablum :yes, i needed to install Nvidia driver for windows, AND it asked me to install a driver for ubuntu. I DID install ubuntu through wubi, so i have dualbooting on my computer. its quite logical that two drivers from other OS's are not really best friends :s

WorMzy :yes, I will try that. Why did I need to login as root? I dont know. Root, by my experience, is the head of ubuntu, the CEO, the... "root". so it gives me a little bit more freedom than my standard login account, am I right?

thanks again guys :)

---

### Post by Dans564 on 2010-10-23
what they are saying is that loging in as root can be extremely dangerous.  its better to login as you and use "sudo" before a command. for example,
```
sudo service gdm start
```
"sudo" stands for Super User DO and allows a user to have a temporary root access without logging in as root.

---

### Post by Joker Pawn on 2010-10-23
Dans: thank you for the warning. I know what sudo stands for, but only some things in ubuntu can be done in terminal. I mean, everything can be done in that 8bit lookalike box, but its just difficult, for me atleast.

As of these little commands. None worked. Wormzy's command backed up the all-magical xorg.conf file. After that I typed in startx, same thing. An nvidia error, next to a fatal one. 3rdalbum's advice was to delete that file, resetting everything back to normal. I ended up with the message that the beautiful xorg.conf file does not exist(!?).

What i did:
1. Reset the computer, so i can get the dual-boot screen
2. Chose ubuntu, brought me back to that ugly 8bit look-alike fullscreen terminal, which asked me to login.
3. I logged in as root. I mean, in situations like this, my standard account is pretty much worthless, cuz it has everything locked up in the file system :s
4. Followed WormZy's advice. Did not work.
5. Followed 3rdalbum's advice. Did not work. The "gdm" command did not let me finish, because the gdm was already started
6. Just for curiousity, i removed the nvdidia driver from windows xp, so i dont have two drivers installed on the same graphics card. Did not work.
7. Grabbed my iphone to read some responses, if any happened while i was trying to fix this. I ended up reading what sudo means.

Tl;dr: all of this, did not work. Anything else to offer?

---

### Post by sandyd on 2010-10-23
> **Joker Pawn said:**
> Dans: thank you for the warning. I know what sudo stands for, but only some things in ubuntu can be done in terminal. I mean, everything can be done in that 8bit lookalike box, but its just difficult, for me atleast.

As of these little commands. None worked. Wormzy's command backed up the all-magical xorg.conf file. After that I typed in startx, same thing. An nvidia error, next to a fatal one. 3rdalbum's advice was to delete that file, resetting everything back to normal. I ended up with the message that the beautiful xorg.conf file does not exist(!?).

What i did:
1. Reset the computer, so i can get the dual-boot screen
2. Chose ubuntu, brought me back to that ugly 8bit look-alike fullscreen terminal, which asked me to login.
3. I logged in as root. I mean, in situations like this, my standard account is pretty much worthless, cuz it has everything locked up in the file system :s
4. Followed WormZy's advice. Did not work.
5. Followed 3rdalbum's advice. Did not work. The "gdm" command did not let me finish, because the gdm was already started
6. Just for curiousity, i removed the nvdidia driver from windows xp, so i dont have two drivers installed on the same graphics card. Did not work.
7. Grabbed my iphone to read some responses, if any happened while i was trying to fix this. I ended up reading what sudo means.

Tl;dr: all of this, did not work. Anything else to offer?

```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
#Flush Nvidia Drivers
sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
#Restore OpenGL and Mesa Libs
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx libgl1-mesa-dri
sudo dpkg-reconfigure xserver-xorg

```
restart.

---

### Post by Joker Pawn on 2010-10-23
sandyd, i love you. as a friend ofcourse. ill try that now. but what do you mean by restart? like, pushing the restart button on my computer? I mean, i tried to run the restart command in that ugly terminal, and i got to say this to you: its pretty messed up.

---

### Post by Yidaki on 2010-10-23
Just restart your PC as usual. A normal restart. :)

---

### Post by Joker Pawn on 2010-10-23
> **Yidaki said:**
> Just restart your PC as usual. A normal restart. :)

No, its a little bit more than that. I do not have a gui, just a big terminal, so i was forced to press that button on my pc.

As for the solution:

The first apt-get works, but on the second, it cannot find libgl1 packages(both of them).

Now, assuming that theres no other fix, there are two more options:

1. Delete Ubuntu. Start all over again with a new one.
2. (this is rather a question) is it possible for me to download those two libgl1 packets and put them somewhere that ubuntu will find them? Since i installed ubuntu with wubi, i have acces to windows xp, and the internet. And the windows explorer. I could easily put the files there, switch back to my messy ubuntu, and run all of the commands again. But the problem is, i do not know where to put them.


Personally, i think the option 1. Would work. Option 2. Might not be possible, but.... I can always try.

---

### Post by sandyd on 2010-10-23
> **Joker Pawn said:**
> No, its a little bit more than that. I do not have a gui, just a big terminal, so i was forced to press that button on my pc.

As for the solution:

The first apt-get works, but on the second, it cannot find libgl1 packages(both of them).

Now, assuming that theres no other fix, there are two more options:

1. Delete Ubuntu. Start all over again with a new one.
2. (this is rather a question) is it possible for me to download those two libgl1 packets and put them somewhere that ubuntu will find them? Since i installed ubuntu with wubi, i have acces to windows xp, and the internet. And the windows explorer. I could easily put the files there, switch back to my messy ubuntu, and run all of the commands again. But the problem is, i do not know where to put them.


Personally, i think the option 1. Would work. Option 2. Might not be possible, but.... I can always try.

are you sure you typed the 5th letter as an numeric "one" not a "L"?

---

### Post by oldos2er on 2010-10-23
> **3rdalbum said:**
> Just typing "startx" does not work. You'd need to run it as root

 startx works fine for me with a text login, and no, I do not run as root. FWIW.

---

### Post by Joker Pawn on 2010-10-24
Yes, sandyd. Even though, from my phone, it looks like an L. Thank god for zooming in!

Hmm, i see that there aro no options left... Im going to keep this thread... "alive" for a few hours, if there is any solution left. Im gonna start all over again if theres no other solution. Thank you all for helping! :)

---

### Post by katykat on 2010-10-24
IF you have an /etc/X11/xorg.conf :
See if you have an X11.xorg.failsafe and copy the  the file to xorg.conf

Keep things simple and 

sudo apt-get install mc
and call sudo mc - its Midnight Commander - the best little file manager around. 

You can edit, rename, move - and do jsurt about everything needed without laborious and tedious typing with it. 

If its not on the main repo its on one of the other standard ones, and you can use Gnome Commander in its place - a little more kludgy .
I thinks Its sudo aptitude install gnome-commander

Lacking that failsafe file, edit xorg.conf to make the line UNDER "Configured Video Device" read :
Driver        "vesa"

That should work, and allow you to use normal graphics, but forget about 3d. 
On Jaunty thats pretty much what I needed to do with my Nvidia card.

You may also need to reinstall gdm and gnome-desktop. 

Stay clear of video drivers as they are a source of much confusion to Ubunto 9.x with nvidia 

In fact its one of the reasons I am removing Jaunty. 

I have Meerkat running and it runs flawlessley with an ancient Nvidia card. On Meerkay I dont seem to ev have anb xorg.conf so cant offer advice on the newest system,,

---

