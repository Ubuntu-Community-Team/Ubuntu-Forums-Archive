---
title: "Emergency help!!!!UBUNTU DOSNT LOAD RIGHT"
date: 2006-05-12
forum: General Help
---

### Post by morbid_bean on 2006-05-12
Ok i had my computer shut down for about an hour...shut it down like i always do and never had this problem...now when i boot it up everyting goes normal then it will say ubuntu breezy 5.10 bla bla bla   and show login and ask for password....in what i belive is like a text based linux...and i type my name and password and basicly it looks like i have a full screen terminal...WTF???

---

### Post by aysiu on 2006-05-12
Have you tried logging in and then typing ```
sudo /etc/init.d/gdm restart
```?

---

### Post by morbid_bean on 2006-05-12
k ill give that a try...i wish it works

---

### Post by morbid_bean on 2006-05-12
oh no...didnt work...typed it in and pressed enter and it basicly did nothing and i restarted computer and still did same thing....anything else?? I hope im not screwed!](*,) ](*,) ](*,)

---

### Post by aysiu on 2006-05-13
When you say "did nothing," do you mean that this is what you see? ```
morbidbean@ubuntu:~$ sudo /etc/init.d/gdm restart
morbidbean@ubuntu:~$
```

---

### Post by morbid_bean on 2006-05-13
Yes exactly....dont have any idea what to do...WHAT DID I DO TO DISERVE THIS!!!!!!!!

---

### Post by kane_666 on 2006-05-13
try pressing Ctrl+F7   i think that will work (then again, im new to ubuntu) if F7 doesn't work, try F6, F5 etc...

---

### Post by morbid_bean on 2006-05-13
[QUOTE=kane_666]try pressing Ctrl+F7   i think that will work (then again, im new to ubuntu) if F7 doesn't work, try F6, F5 etc...[/QUOTE]


Do i do that during the start up or at the command thing??? And when i do what should happen so i know when i done it right...

---

### Post by kane_666 on 2006-05-13
do it at the command line. **IF** it works... it should load the gnome desktop (the GUI)

---

### Post by morbid_bean on 2006-05-13
will it fix my problem or will i have to do this for now on???

---

### Post by kane_666 on 2006-05-13
well first you should check to see if it works.. and if it does. then there should be a way to load it automaticly (without the ctrl+f7) but you will need someone thats a little more advanced then me for that lol

---

### Post by morbid_bean on 2006-05-13
Ok I tried that usinga all F keys (F1-F12) nothing happens...any other suggestions anyone???I so frustrated right now.](*,)

---

### Post by kane_666 on 2006-05-13
sorry i dont know.. :S try searching google for something like: ubuntu manually load gnome desktop. see if anything helps?

---

### Post by aysiu on 2006-05-13
[QUOTE=morbid_bean]Yes exactly....dont have any idea what to do...WHAT DID I DO TO DISERVE THIS!!!!!!!![/QUOTE] If what I put as an example is what actually happened (just skipped to the next line, didn't even ask for a password), then your installation is in a bad state.

Ordinarily, any time you type the *sudo* command, you should be prompted for a password, and if the command fails, there should be some kind of error that comes back to you.

I'm not sure on this, but it may be that you've somehow corrupted your /etc/sudoers or /etc/group file.

I have "fresh" copies of these [here](http://www.ubuntuforums.org/showpost.php?p=1004086&postcount=12). Obviously, instead of *firstuser*, you would have your actual username. If it's possible to print out that link I just linked to, print it out.

Then reboot into **recovery mode**. You should then be logged in as root. ```
nano /etc/sudoers
``` Check to see it looks the same as the printout. If not, fix it. ```
nano /etc/group
``` Again, check this file and fix, if appropriate. To save out, press Control-X, Y, Enter (if you've made changes) or just Control-X (if you haven't made changes).

If you had to make changes, reboot into normal mode and see if the *sudo* command I gave you earlier works.

---

### Post by morbid_bean on 2006-05-13
Well it did ask for a password i though that you would have know that (next time im going to give every detail)...and im going to still try to check the code and see if  it matches.

---

### Post by aysiu on 2006-05-13
[QUOTE=morbid_bean]Well it did ask for a password i though that you would have know that (next time im going to give every detail)[/QUOTE] Ordinarily, of course, it asks for a password. When something's gone wrong, I make no assumptions about what *should* or *shouldn't* be happening.

---

### Post by morbid_bean on 2006-05-13
oh ok...well lets just hope this works...


thanks-

---

### Post by morbid_bean on 2006-05-13
AHHHHH!!!!!!!! NOTHING happend....i did exactly what i was told to do (check and make sure the codes matched up) and i had to fix one line.....and i restarted in the regular mode typed in the code  

sudo /etc/init.d/gdm restart

it asked for my password and i put it in and it made a new blank line....i restarted computer and it still dose this to me!!!!


What did i do to diserve this linix!!!!!!!


P.S. If there is any way possible how can i take off my important files off the HD using that stupid full screen terminal (thats what i call it),,,,i have very important files on there that i cant live the same anymore with out.


Please!!!someone out there has to have the answer to my tourture anybody!!?

---

### Post by aysiu on 2006-05-13
[QUOTE=morbid_bean]
P.S. If there is any way possible how can i take off my important files off the HD using that stupid full screen terminal (thats what i call it),,,,i have very important files on there that i cant live the same anymore with out.[/QUOTE] Yes. You don't have a live CD? A live CD would make it easier.

Since your sudo is messed up, you will have to boot into recovery mode, because you may need root privileges.

What do you have to back up your stuff? An iPod, some kind of USB stick?

---

### Post by morbid_bean on 2006-05-13
Yes i have cd-rws and flash drives i have all the tools need and thx for reminding me about the live cd.... for got about it....so when i boot the live cd up i should be able to surf the hd??

-thanx

---

### Post by aysiu on 2006-05-13
If it's a live *Knoppix* CD, you'll be able to just browse the drive.

If it's a live *Ubuntu* CD, you will have to manually mount the drive. Do you know how to mount drives?

---

### Post by morbid_bean on 2006-05-13
sure why not...ill probably just use the knoppix cd but it dosnt hurt to learn something new :)

---

### Post by sinkxdie on 2006-05-13
Wait morbid...
you know its not ctrl+F-
its CTRL+ALT+F-

---

### Post by aysiu on 2006-05-13
If you're rescuing data, just use Knoppix.

Learn how to mount manually when you're not trying to save important files.

---

### Post by morbid_bean on 2006-05-13
[QUOTE=sinkxdie]Wait morbid...
you know its not ctrl+F-
its CTRL+ALT+F-[/QUOTE]


what you mean :::::::: when i try to see if it will load???

---

### Post by sinkxdie on 2006-05-13
When your on ur "full-screen terminal" press 
CTRL+ALT+F7 to try and get to ur GUI
did you try "startx" yet also?

---

### Post by morbid_bean on 2006-05-13
[QUOTE=aysiu]If you're rescuing data, just use Knoppix.

Learn how to mount manually when you're not trying to save important files.[/QUOTE]



Lol yea really...thx ill give it a try if the ctrl **ALT** 7 dont work

---

### Post by sinkxdie on 2006-05-13
dont forget to try 

startx

also thats what saved me when i had this problem: 
[http://www.ubuntuforums.org/showthread.php?t=164494](http://www.ubuntuforums.org/showthread.php?t=164494)

---

### Post by sinkxdie on 2006-05-13
if this stil doesn't work, try updating

sudo apt-get update
sudo apt-get dist upgrade

by thats what im going to do now :D

---

### Post by morbid_bean on 2006-05-13
Alright...STARTX worked!!!however i did get one error saying a missing file...if I do sudo apt-get update? will that fix the file or....what....and after i did that start x command did it fix it or will i have to do it maunualy for now on??

BTW im finnaly back on ubuntu after 1 day of pain and suffering in windows xp!!!


And what dose the sudo apt-get dist upgrade do???

---

### Post by sinkxdie on 2006-05-13
that will update you to dapper, i dont recommend doing it unless you just a ubuntu user for fun.
yeah just dont update, the stable version comes out in 2 weeks

and you didnt say thank you :D

---

### Post by morbid_bean on 2006-05-13
But will i have to manualy do the startx command everytime i log on for now?? if so any idea how to fix it...if not i might re install my whole ubuntu because i do think i have 2 copies of it on my grub.

also....how did this problem occur in the fist place???? (the full screen terminal?)

-Thanks---for evertything...thanks in advance!!!!

---

### Post by sinkxdie on 2006-05-13
Edit: how do you delete a message


:D

---

### Post by sinkxdie on 2006-05-13
no just restart to make sure...if you **do** have to do startx again...
then try and reconfigure your x server


sudo dpkg-reconfigure xserver-xorg

---

### Post by morbid_bean on 2006-05-13
[QUOTE=sinkxdie]no just restart to make sure...if you **do** have to do startx again...
then try and reconfigure your x server


sudo dpkg-reconfigure xserver-xorg[/QUOTE]



K ill do that right now

---

### Post by morbid_bean on 2006-05-13
well i tried reconfigureing X but it still dose same thing to me so now i decided to back up all my stuff and format my linux HD and re install a fresh copy of it....now i know how to do this with windows but how do i do this for linux???

---

### Post by sinkxdie on 2006-05-14
What I would do would be to switch to KDE for an hour, use "Keep" and backup your stuff

---

