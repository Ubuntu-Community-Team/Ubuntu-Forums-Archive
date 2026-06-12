---
title: "kde download; can't log on."
date: 2011-03-15
forum: General Help
---

### Post by GBGamer117 on 2011-03-15
I need help. I have ubuntu 10.04, and I downloaded the kde package, because  I wanted to see if I liked it. It then changed the login screen to something completely different, and since I never bothered to learn my username, I can't login. Is there something I can do?

---

### Post by dabl on 2011-03-15
You "downloaded" it?  Or did you ```
sudo apt-get install kubuntu-desktop

```
?

---

### Post by ankspo71 on 2011-03-16
Hi,
Your username should be the same name that was used to name your personal home folder in Ubuntu, eg: /home/username. If you don't remember the name of it, boot into your live cd and use it to browse your hard drive to find the name of that /home/username folder. Once you have the live cd running, you can browse the hard drive by looking in the places menu for an entry similar to "** GB Filesystem" See image here: [https://wiki.edubuntu.org/Artwork/Incoming/Karmic/Humanity_Icons?action=AttachFile&do=get&target=places_menu.png](https://wiki.edubuntu.org/Artwork/Incoming/Karmic/Humanity_Icons?action=AttachFile&do=get&target=places_menu.png)

Hope this helps.

---

### Post by Sina_RJ on 2011-03-16
restart your pc,try to boot in safe mode
you get into a command-line linux,enter your username and password
you will log in and allow just to write command-line
and then as every other app,do the
sudo apt-get remove ...

---

### Post by Krytarik on 2011-03-16
> **Sina_RJ said:**
> restart your pc,try to boot in safe mode
you get into a command-line linux,enter your **username** and password
you will log in and allow just to write command-line
and then as every other app,do the
sudo apt-get remove ...
Ok, this is somewhat senseless, since it is the username what this is all about. ;-) But *Sina_RJ* is right about booting into "recovery mode", but then choose "root shell prompt". This way neither username nor password will be asked for. Then simply enter those command:
```
ls /home
```

---

### Post by Sina_RJ on 2011-03-16
> **Krytarik said:**
> booting into "recovery mode", but then choose "root shell prompt". This way neither username nor password will be asked for. Then simply enter those command:
```
ls /home
```

thanks for that,i didn't know this one :)
but once i had the problem with log in ( i couldn't see log in screen ) i did this and all I got was the problem fixed!
I think i didn't get the problem correctly!

---

### Post by GBGamer117 on 2011-03-24
How do you boot into recovery mode? (I'm a newbie at linux)

---

### Post by Krytarik on 2011-03-24
> **GBGamer117 said:**
> How do you boot into recovery mode? (I'm a newbie at linux)
Please follow the first part of this guide:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

