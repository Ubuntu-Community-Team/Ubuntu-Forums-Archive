---
title: "Skype video"
date: 2012-04-24
forum: General Help
---

### Post by Ycanti on 2012-04-24
Hi

installed ubuntu 12.05 yesterday and since noticed i can't get video of myself when calling - i can see them they can't see me. I have Cheese installed and that works OK.

Can you help please?

Roy

---

### Post by techsupport on 2012-04-24
> **Ycanti said:**
> Hi

installed ubuntu 12.05 yesterday and since noticed i can't get video of myself when calling - i can see them they can't see me. I have Cheese installed and that works OK.

Can you help please?

Roy

Did you go down the checklist to make sure you have all your proper video codecs installed right?  Like this:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

:)

---

### Post by Ycanti on 2012-04-24
> **techsupport said:**
> Did you go down the checklist to make sure you have all your proper video codecs installed right?  Like this:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

:)

No was that when skype was installing? How do i find the codecs?

---

### Post by techsupport on 2012-04-24
> **Ycanti said:**
> No was that when skype was installing? How do i find the codecs?

You just go down the list and double check that you have everything installed correctly. Only you would be able to find that out.

---

### Post by Ycanti on 2012-04-24
sorry for being thick.

I clicked link and scrooled down page. Nothing about skype or codec but a link on 12.04. 
i click that and see lots of obscure writing about metalinks and images. again nothing relating to what should be useful? nothing makes any sense to me.

i suppose ubuntu is for tehnical people with software engineering expertise. Sorry

---

### Post by techsupport on 2012-04-24
> **Ycanti said:**
> sorry for being thick.

I clicked link and scrooled down page. Nothing about skype or codec but a link on 12.04. 
i click that and see lots of obscure writing about metalinks and images. again nothing relating to what should be useful? nothing makes any sense to me.

i suppose ubuntu is for tehnical people with software engineering expertise. Sorry

Well sounds like you know more about your problem then I do. You seem to know what you have installed correctly or not. Sounds like you took the time to read through the list I gave you and double check to make sure you have all the codecs and packages you need installed. Here is my suggestion since you seem to know what the problem isn't:

[http://www.ubuntu.com/business/services/overview](http://www.ubuntu.com/business/services/overview)

Or you can go back over the list I gave you and double check to make sure you have everything installed properly.  It is totally on you.

The link I provided you with is more than metalinks, and pictures; That much I do know about your problem..  Maybe you need to open that link with a different browser perhaps? Or maybe you need to sign up for paid tech support through ubuntu business support services? I don't know. That's up to you. They are standing by.

---

### Post by Ycanti on 2012-04-24
Think i found the code i am meant to paste into terminal. makes a bit more sense now

Should mention that when i installed ubuntu 12 i did so without internet as it was not working then
> **techsupport said:**
> You just go down the list and double check that you have everything installed correctly. Only you would be able to find that out.

---

### Post by techsupport on 2012-04-24
> **Ycanti said:**
> Think i found the code i am meant to paste into terminal. makes a bit more sense now

Should mention that when i installed ubuntu 12 i did so without internet as it was not working then

There you go. Keep going down that list and make sure you have EVERYTHING installed right this time.  Goodluck!

:lolflag:

---

### Post by Ycanti on 2012-04-24
Thanks.
Cheese is working now. Was not before. Installed codecs so should be ok. Can't test vid on skype until

> **techsupport said:**
> There you go. Keep going down that list and make sure you have EVERYTHING installed right this time.  Goodluck!

:lolflag:

---

### Post by gradinaruvasile on 2012-04-24
You DONT need any codecs and installing them wont help. Skype has his own built in codecs and stuff and does not need anything else.

The thing is that certain webcams are not recognized correctly by Skype. They work with Cheese and whatnot but not with Skype. The workaround is to launch them with preloading a compatibility library that fakes the cam as a v4l1 device:

```

LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype

```

The above line works in Debian and the path might differ in Ubuntu, but the idea is the same - you need to locate the v4l1compat.so file and put its full path there.
The line can be launched from a terminal. If it works, you can edit Skype's launcher in the menu and put that command there.
If you dont have a graphical menu editor, you can edit the 

/usr/share/applications/skype.desktop

file and adjust the "Exec" line by replacing "skype" with the whole stuff from above (or a corrected version of it, that work on your computer).

---

### Post by techsupport on 2012-04-24
They just confirmed that Skype works for them now. What's the problem? Otherwise mark the thread solved and close it.

---

### Post by gradinaruvasile on 2012-04-25
> **Ycanti said:**
> Thanks.
Cheese is working now. Was not before. Installed codecs so should be ok. Can't test vid on skype until

Who said Skype is working...?

---

### Post by techsupport on 2012-04-25
> **gradinaruvasile said:**
> Who said Skype is working...?

They did. They said they found the "bit of code" they needed to get it running now. 

Make sure to close this thread by marking it as solved when you are done here. 

Cheers! :)

---

### Post by Ycanti on 2012-04-25
Thanks so much for your help. I could not get video with codecs as you said. But now it works. I use Skype for job interviews so very much appreciated, especially as i have one tomorrow.

Thanks

> **gradinaruvasile said:**
> You DONT need any codecs and installing them wont help. Skype has his own built in codecs and stuff and does not need anything else.

The thing is that certain webcams are not recognized correctly by Skype. They work with Cheese and whatnot but not with Skype. The workaround is to launch them with preloading a compatibility library that fakes the cam as a v4l1 device:

```

LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype

```The above line works in Debian and the path might differ in Ubuntu, but the idea is the same - you need to locate the v4l1compat.so file and put its full path there.
The line can be launched from a terminal. If it works, you can edit Skype's launcher in the menu and put that command there.
If you dont have a graphical menu editor, you can edit the 

/usr/share/applications/skype.desktop

file and adjust the "Exec" line by replacing "skype" with the whole stuff from above (or a corrected version of it, that work on your computer).

---

### Post by Ycanti on 2012-04-25
its not solved. the video worked on skype once then not second time!!

howcan i make this permanent?

I don't want to spend every waking moment firefighting with Linux!!!

Want things to work.

---

### Post by Ycanti on 2012-04-25
How doinfind the file?
How do i edit the skype  launcher

i am not a computer programmer/Software engineer.

> **gradinaruvasile said:**
> You DONT need any codecs and installing them wont help. Skype has his own built in codecs and stuff and does not need anything else.

The thing is that certain webcams are not recognized correctly by Skype. They work with Cheese and whatnot but not with Skype. The workaround is to launch them with preloading a compatibility library that fakes the cam as a v4l1 device:

```

LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype

```The above line works in Debian and the path might differ in Ubuntu, but the idea is the same - you need to locate the v4l1compat.so file and put its full path there.
The line can be launched from a terminal. If it works, you can edit Skype's launcher in the menu and put that command there.
If you dont have a graphical menu editor, you can edit the 

/usr/share/applications/skype.desktop

file and adjust the "Exec" line by replacing "skype" with the whole stuff from above (or a corrected version of it, that work on your computer).

---

### Post by gradinaruvasile on 2012-04-25
1. Open a terminal.
2. write (copy-paste) the following:

```

nano /usr/share/applications/skype.desktop

```

Then make it look like this (the red is to see where you need to look):

```

[Desktop Entry]
Name=Skype
Comment=Skype Internet Telephony
Exec=[COLOR="Red"]LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype[/COLOR]
Icon=skype.png
Terminal=0
Type=Application
Encoding=UTF-8
Categories=Network;Application;

```

PS: Ctrl-o saves the file, Ctrl-x exits the application...

---

### Post by techsupport on 2012-04-25
> **gradinaruvasile said:**
> 1. Open a terminal.
2. write (copy-paste) the following:

```

nano /usr/share/applications/skype.desktop

```Then make it look like this (the red is to see where you need to look):

```

[Desktop Entry]
Name=Skype
Comment=Skype Internet Telephony
Exec=[COLOR=Red]LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype[/COLOR]
Icon=skype.png
Terminal=0
Type=Application
Encoding=UTF-8
Categories=Network;Application;

```

Microsoft bought Skype and they haven't updated it since. Typical crappy MS development. No patches.

---

### Post by gradinaruvasile on 2012-04-25
This issue is present since ages in Skype. Its not a Microsoft "feature".

OTOH i too believe we can kiss Skype goodbye on Linux at least. Google Talk works just fine BTW.

---

### Post by GreatDanton on 2012-04-25
> **gradinaruvasile said:**
> 
OTOH i too believe we can kiss Skype goodbye on Linux at least. Google Talk works just fine BTW.


The problem is if you want to say goodbye to Google. The reason why somebody wants to go away is because they are tracking you (in case you don't know this :))
That's the reason why i prefer using skype instead of Google's services.

Cheers

---

### Post by gradinaruvasile on 2012-04-25
> **GreatDanton said:**
> The problem is if you want to say goodbye to Google. The reason why somebody wants to go away is because they are tracking you (in case you don't know this :))
That's the reason why i prefer using skype instead of Google's services.

Cheers

EVERYONE is tracking you.

In case you dont know, Skype uses a closed (really) source protocol that works in misterious ways. To use less servers this vpn like network appoints computers with higher capacity (bandwidth and processing power) to nodes - meaning that sometimes your computer is used as a traffic node. The thing is that they use your bandwidth for their purposes.
Your voice and video data flows throught other third party computers (home computers) aswell. They hide behind the "security through obscurity" principle, but the client was already reverse engineered so you dont now if someone develops a sniffer.
The whole network aware  in real time of the number of computers, nodes, ip addresses, system versions and god knows what else. Mind you, in real time (well, almost, because the data needs to propagate through the nodes).
Plain and simple they know where you are logged in just like google does, even more. And they have you practically in a vpn (meaning direct access to your computer unlike google who is limited to browser-based stuff) - and you dont know what the program/network is "aware" or capable of because they keep it secret. Everything you write, say or show can be listened to on their servers - AFAIK they have in the EULA the fact that your text messages stay on their servers + they obey the law meaning they hand over anything that concerns you if asked by law enforcement.

Now if that cannot be used for tracking... Microsoft had for ages some dubious encryption keys inside Windows that reportedly come from NSA plus being the largest OS supplier im pretty sure they incorporate tracking routines (read backdoors) in their products "in compliance with the laws" of course.

Google uses an open standard for voice and video, meaning that anyone can use it with their application.
For example Jitsi has google talk support + a supplementary peer-to-peer encryption layer meaning that the voice/video/text is encrypted between the 2 endpoints so if anything flows through the Google servers it is encrypted even to them. Skype does not allow this because they force you to use only their client that has a mind of its own.

So... Choose the lesser evil if you know which is it. Or just choose the one that works for you. I use both.

PS If you dont want tracking, set up your own VPN server with your own encryption keys and use a SIP client through it with supplementary encryption. Its really isnt that complicated to set up, the software is freely available (openvpn+Jitsi should do it).

---

### Post by GreatDanton on 2012-04-26
> **gradinaruvasile said:**
> EVERYONE is tracking you.

In case you dont know, Skype uses a closed (really) source protocol that works in misterious ways. To use less servers this vpn like network appoints computers with higher capacity (bandwidth and processing power) to nodes - meaning that sometimes your computer is used as a traffic node. The thing is that they use your bandwidth for their purposes.
Your voice and video data flows throught other third party computers (home computers) aswell. They hide behind the "security through obscurity" principle, but the client was already reverse engineered so you dont now if someone develops a sniffer.
The whole network aware  in real time of the number of computers, nodes, ip addresses, system versions and god knows what else. Mind you, in real time (well, almost, because the data needs to propagate through the nodes).
Plain and simple they know where you are logged in just like google does, even more. And they have you practically in a vpn (meaning direct access to your computer unlike google who is limited to browser-based stuff) - and you dont know what the program/network is "aware" or capable of because they keep it secret. Everything you write, say or show can be listened to on their servers - AFAIK they have in the EULA the fact that your text messages stay on their servers + they obey the law meaning they hand over anything that concerns you if asked by law enforcement.

Now if that cannot be used for tracking... Microsoft had for ages some dubious encryption keys inside Windows that reportedly come from NSA plus being the largest OS supplier im pretty sure they incorporate tracking routines (read backdoors) in their products "in compliance with the laws" of course.

Google uses an open standard for voice and video, meaning that anyone can use it with their application.
For example Jitsi has google talk support + a supplementary peer-to-peer encryption layer meaning that the voice/video/text is encrypted between the 2 endpoints so if anything flows through the Google servers it is encrypted even to them. Skype does not allow this because they force you to use only their client that has a mind of its own.

So... Choose the lesser evil if you know which is it. Or just choose the one that works for you. I use both.

PS If you dont want tracking, set up your own VPN server with your own encryption keys and use a SIP client through it with supplementary encryption. Its really isnt that complicated to set up, the software is freely available (openvpn+Jitsi should do it).


Can you provide some link about this Vpn (i don't know anything about this, but iam really interested). I think Internet should be free and without any tracking devices.

Thanks for your reply!

---

### Post by gradinaruvasile on 2012-04-26
This is offtopic. You should start another thread if you want to get more info. 


Home page:

[http://openvpn.net/index.php/open-source.html](http://openvpn.net/index.php/open-source.html)

OpenVPN is included in virtually all Linux distributions. Just 

apt-get install openvpn

But you will have to learn how to use it (everything is done via command line), there are many resources out there.

The basic idea is:

1. set up a server - this means:
   -set up the server computer to be reachable over the internet - either has to have fixed real ip or resolvable domain name - there are many free dns service providers, i use dyndns. 
   -set up all necessary settings to ensure that the openvpn service port is forwarded to the real ip (if another router has the external ip).
   -setting up the server software - install + configure the server by generating encryption keys for both server and all clients + setting up the server config file  then start the service.
   -setting up the client software - you have to set up the client connection script + provide the client the encryption keys (previously generated on the server) then start the client service.
Then you can do whatever you want over this secure connection.

Now, thats in a nutshell. In practice may be more or less complicated depending on your level of knowledge. First you should do some research and learn for yourself. If not, dont count on anyone to do the work for you.

---

### Post by Ycanti on 2012-04-28
I'm afraid it still doesn't work. I did try out the edtiting that gradinaruvasile suggested.
Here is the output from the terminal:

```
roy@roy-GF8100-M2G:~$ skype
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(skype:9706): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(skype:9706): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(skype:9706): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(skype:9706): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
```



Here is the output of lsusb for the webcam:
```
Bus 001 Device 005: ID 046d:08da Logitech, Inc. QuickCam Messanger
```I hope that helps

---

### Post by gradinaruvasile on 2012-04-29
What OS do you have? 64 or 32 bit? There seems to be a related problem.

What is the output of:

```

uname -a
dpkg --search /usr/lib32/libv4l/v4l1compat.so

```

?

---

