---
title: "Need Lots os help"
date: 2010-08-31
forum: General Help
---

### Post by jmel on 2010-08-31
Hello Folks
i have a laptop which i cant install windows. i got a new WD 320gb Hard drive and i would like to install Linux on it. the only problem is that it refuses to finish installing windows and i would like to bypass that and just install this OS. i burned the ubuntu disk on my other computer but cant get the lap top to just run/load or what ever i need to to..please help me load this so i can begin to experience this laptop and not be wasted equipment.. thanks please respond quick i dont think i want to sleep early tonight ha ha..please help

---

### Post by luisito on 2010-08-31
Can you turn off you laptop, remove the Windows installation CD, insert the Ubuntu CD, and turn it back on?

---

### Post by QIII on 2010-08-31
Did you just copy the downloaded file to disk, or did you burn it as an .iso?

---

### Post by jmel on 2010-08-31
Luisito = yes i can restart the computer but the CD wont install
 
Q = i just downloaded the software and burned to the CD as normal. i didnt kow there was a special way to do it..
 
Please keep advising
Lets get this installed tonight

---

### Post by jmel on 2010-08-31
Luisito = yes i can restart the computer but the CD wont install

---

### Post by jmel on 2010-08-31
Q = i just downloaded the software and burned to the CD as normal. i didnt kow there was a special way to do it..

---

### Post by 3rdalbum on 2010-08-31
> **jmel said:**
> Q = i just downloaded the software and burned to the CD as normal. i didnt kow there was a special way to do it..

You need to use the Burn Image function of your burning software.

---

### Post by jmel on 2010-08-31
ok i dont know exactly what or how to do this but im determined to do this tonight. im going to do the download again and use what? and how ..please explain... after tonight i should be an expert..thanks and please keep it going

---

### Post by psavva on 2010-08-31
> **jmel said:**
> Luisito = yes i can restart the computer but the CD wont install
 
Q = i just downloaded the software and burned to the CD as normal. i didnt kow there was a special way to do it..
 
Please keep advising
Lets get this installed tonight

Here's a Howto:
[https://help.ubuntu.com/community/BurningIsoHowto#Windows](https://help.ubuntu.com/community/BurningIsoHowto#Windows)

When you open the Cd after burning it, it should not contain only 1 file with the .iso extension

It should look something like this 
[IMG]https://help.ubuntu.com/community/BootFromCD?action=AttachFile&do=get&target=correctcd.png[/IMG]

And here's a howto on Booting off the CD
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

Good Luck :D

---

### Post by jmel on 2010-08-31
ok doing the imagi file worked and the file was loading but now is frozen at the welcome screen. dont know if i should re boot.. please advice..i wish these answers would go much faster...if you or anyone is willing to help please IM me on yahoo jmel_316..i hope that wasnt an illegal thing to do but i need the help

---

### Post by QIII on 2010-08-31
jmel --

The answers come as fast as we can get them.  Remember that we are all  here voluntarily as we have time.  Many of us are trying to help several  people at once.  Also remember that the community is world-wide.  The  guy with the perfect answer for you may live half way around the world  and be asleep, at work or playing with his children at the time you make  your post.

Generally, most of us don't like to provide help via IM or PM because doing so makes the solution invisible to the community and others with similar problems will not benefit.

OK.  Moving forward.

On the "Welcome Screen", are you able to run a Live session by selecting the option to run Ubuntu without changes to your machine?

The next question is about your hardware.

Could you give us as much detailed information as you can about your machine?

---

### Post by jmel on 2010-08-31
First i would like to say thanks for those who were willing to help and did not get offended by my comment or sense of urgency as i do know the help is voluntary and that folks have families and priorities in life. 
Moving along........
Well it loaded fine when i did the image and i have been using it since last night. but now it seems that the authentication password is all messed up (or i messed it up). it works fine when i use it to authorize the wireless connection but it doesn't allow me to authorize anything else. it said authorization failed. don't understand what is really happening but otherwise i like the system so far.

---

### Post by QIII on 2010-09-01
Could you give me an example of exactly what you are trying to do when you are told that authorization failed and the exact steps you take leading up to that?

(No offense taken, by the way.  It is just important for everyone to realize that immediate answers my not be forthcoming because of the nature of the forum, not because nobody wants to help.  We certainly do want to help!)

---

### Post by jmel on 2010-09-01
[QUOTE=QIII;9793257]Could you give me an example of exactly what you are trying to do when you are told that authorization failed and the exact steps you take leading up to that?

first time this happened was when the computer locked and i couldnt unlock it with that password
then it happened when i tried to authorize some change or upgrade on the system.  the password works for allowing the internet connection, automatic update manager and thats about it. 

Just remember, i tried to downloading the Flash player driver and the password didnt work.  thats when i noticed. and everything else i try to update.

---

### Post by QIII on 2010-09-01
And you are using the password you created when you installed?

Are you using the CLI/terminal and failing to use 

```
sudo
```

By the way, install Flash from the repo via Synaptic.  It will pull in the 32 bit wrapper if you are using a 64 bit OS.

---

### Post by jmel on 2010-09-01
yes i an using the password from initial installation
No i am not using the terminal
 
while i was surfing the net on my other laptop i noticed (idled for too long) it locked. now is on the password screen and i typed my magic password (not so magical at all) and it sais" Incorrect Password" 
 
Help me out Q.  take your time (ha ha j/k)
 
i appreciate the help

---

### Post by QIII on 2010-09-01
Have you installed or uninstalled any programs lately?

In particular, have you uninstalled anything like Evolution?  Some default programs like Evolution have dependencies that are removed, like gnome-session, that might cause a problem like this.

Don't know if that is the problem specifically, but let me know.

---

### Post by psavva on 2010-09-24
> **jmel said:**
> yes i an using the password from initial installation
No i am not using the terminal
 
while i was surfing the net on my other laptop i noticed (idled for too long) it locked. now is on the password screen and i typed my magic password (not so magical at all) and it sais" Incorrect Password" 
 
Help me out Q.  take your time (ha ha j/k)
 
i appreciate the help

I truly believe your Magic password is probably not so magic... I'm guessing you either forgot it, or you had CAPS lock on when you typed it...

try resetting your password...
[http://www.watchingthenet.com/ubuntu-guide-for-windows-users-reset-your-password-when-you-have-forgotten-it.html](http://www.watchingthenet.com/ubuntu-guide-for-windows-users-reset-your-password-when-you-have-forgotten-it.html)

---

