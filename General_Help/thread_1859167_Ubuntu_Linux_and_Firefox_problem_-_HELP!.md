---
title: "Ubuntu Linux and Firefox problem - HELP!"
date: 2011-10-13
forum: General Help
---

### Post by Big Dog Dad on 2011-10-13
Since I'm on disability with a lot of time on my hands, I decided to install Ubuntu Linux on an old PC and start the learning process. All I can say is WOW!. Very impressive and a lot to learn. The problem I'm having is I get the following error when I try to access the web a second time using Firefox. 

A program is still running.
Firefox-bin
not responding
Waiting for program to finish.
Interrupting program may cause you to loose work.

(Choice of these buttons)
Lock Screen - Cancel - reboot anyway

I always reboot the PC and am able to gain access to Firefox again. Like I said, I am a complete newbie, but this is making me feel like I'm on Microsoft PC, which is a feeling I'm trying to get away from. Any help would be greatly appreciated. Thanks in advance.

Mike

---

### Post by Big Dog Dad on 2011-10-13
Please - anybody!!
 
Mike

---

### Post by retchid on 2011-10-13
install chrome (cromium) from the software centre 

you will then have option to use chrome when firefox locks up
 and then 
upgrade firefox  that may get rid of the problem

or uninstall firefox in software centre and then reinstall firefox 

but put cromium on first

---

### Post by Dangertux on 2011-10-13
Alternatively you can open a terminal and type

```

sudo killall -9 firefox

```

Then restart Firefox normally.

Hope that helps.

---

### Post by Big Dog Dad on 2011-10-26
Thanks for the replies, but the "sudo" string did not work. My next question is where do I uninstall firefox and then how do I reinstall. Please be specific. Like I said, you have a total beginner on your hands. Thanks in advance!
 
-=BDD=-

---

### Post by usr1one on 2011-10-26
try to upgrade / update firefox. hope it helps

[COLOR=#000000][FONT=Times New Roman][FONT=Tahoma]sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get upgrade
[/FONT][/FONT][/COLOR]

---

### Post by jonobr on 2011-10-26
I use windows too much in work and had a problem with firefox freezing..... not too often that would make me crazy, but often enough, that it mildly agitated me.

It would lock for around 30 seconds, unfreeze and then work ok for around 2~3 hours 
I tried everything, going through add-ons removing reinstalling the whole 9 yards
it went on for around 3 months, I eventually found a post in an obscure place that recommended something that fixed my firefox.

Man it peed me off so much but I was so glad when I found it.

Where am I going with this?

I just read another post where someone was really annoyed about something similar on ubuntu , but was throwing the baby out with the bathwater, and was really annoyed with the whole ubuntu thing....

It was nice reading your post.

Your going to start wanting to do more and more, and Im sure your going to be here more and more as a result.

Your going to pull your hair out and I reckon, also be impressed.

Your going to wonder how you can do something on linux that you used to do on windows, and then be amazed that you could do it and not have to pay a huge license fee for doing it.

Either that, or your going to be scared off by someone telling you to recompile or chroot or chmod or ifconfig or ps -ef | grep and you will think life was soooo much easier in windows.

Well, get well soon and [enjoy your flight!!!!!!!]("http://www.urbandictionary.com/define.php?term=linux&defid=406702")

---

