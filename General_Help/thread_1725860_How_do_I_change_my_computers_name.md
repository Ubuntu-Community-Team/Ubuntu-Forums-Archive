---
title: "How do I change my computers name"
date: 2011-04-10
forum: General Help
---

### Post by KegHead on 2011-04-10
Hi!

Slightly off topic, but does anyone know how to change or delete the name on my computer?

jim@jim-Inspiron-910:~$ 

Thanks!

KegHead

---

### Post by cariboo on 2011-04-10
Moved to a thread of it's own, as it had nothing to do with the thread it was in.

To answer your question, you need to run:

```
sudo hostname <new_name>
```

then edit /etc/host to change the name to the new one.

---

### Post by TripleTea on 2011-09-13
any ideas why it doesn't work on my end ??

im running a usb live boot...

when i did ```
sudo hostname <new_name> 
```i couldn't edit /etc/host afterwards...and it seems like ihv just broken my sudoers file after doing the above

```
>>> /etc/sudoers: syntax error near line 0 <<<
>>> /etc/sudoers: syntax error near line 1 <<<
>>> /etc/sudoers: syntax error near line 4 <<<
>>> /etc/sudoers: syntax error near line 5 <<<
>>> /etc/sudoers: syntax error near line 6 <<<
>>> /etc/sudoers: syntax error near line 7 <<<
>>> /etc/sudoers: syntax error near line 8 <<<
>>> /etc/sudoers: syntax error near line 9 <<<
sudo: parse error in /etc/sudoers near line 0
sudo: no valid sudoers sources found, quitting

```

---

### Post by haqking on 2011-09-13
> **oldfred said:**
> I have never done it but my files say you have to change both & reboot immediately. Also Ubuntu tweak should work.

Computer Name
Must do both & reboot right away
sudo gedit /etc/hostname
sudo gedit /etc/hosts
or
Ubuntu Tweak
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

> **TripleTea said:**
> hmmmm.....interesting how everyone could change it easily.....I tried editting /etc/hostname and /etc/hosts just like oldfred suggested but it didn't seem to change my computer's name....

anyone have any idea as to why it didn't work in my case ?? im using a live usb boot on Ubuntu 11.04.


mmm well the **sudo gedit** oldfred recommends should actually be:

**gksudo** gedit /etc/hostname
**gksudo** gedit /etc/hosts

as gksudo should be used for graphical apps such as gedit.

However you can still use sudo from CLI if you stick with CLI editors such as vi or nano.

As for the fact you are using USB, are you using persistence ?

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

also this thread is a little old ;-)

Edit: This post is from the merged thread incase you are confused ;-)

---

### Post by haqking on 2011-09-13
> **TripleTea said:**
> any ideas why it doesn't work on my end ??

im running a usb live boot...

when i did ```
sudo hostname <new_name> 
```i couldn't edit /etc/host afterwards...and it seems like ihv just broken my sudoers file after doing the above

```
>>> /etc/sudoers: syntax error near line 0 <<<
>>> /etc/sudoers: syntax error near line 1 <<<
>>> /etc/sudoers: syntax error near line 4 <<<
>>> /etc/sudoers: syntax error near line 5 <<<
>>> /etc/sudoers: syntax error near line 6 <<<
>>> /etc/sudoers: syntax error near line 7 <<<
>>> /etc/sudoers: syntax error near line 8 <<<
>>> /etc/sudoers: syntax error near line 9 <<<
sudo: parse error in /etc/sudoers near line 0
sudo: no valid sudoers sources found, quitting

```


do you have your USb to use peristsince ?


[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

and see here to fix sudo [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

and [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by TripleTea on 2011-09-13
ahh....yes2 i forgot about using gksudo instead of sudo.......i cant believe i keep forgetting that.

yes im using usb persistence, installed mine from universal usb installer from windows.

as for fixing sudo....i think ill stick with re-installing my ubuntu as i think i have broken more than just my sudo by running the below command lol....

```
sudo chmod 755 /
```

thank you for your help haqking, i will keep those links for future references XD

and.....a little off-topic question....with usb persistence and the default setup, will logs clutter up and possibly make my casper-rw full in space ?? and how do you find which programs do log ?

---

### Post by haqking on 2011-09-13
> **TripleTea said:**
> ahh....yes2 i forgot about using gksudo instead of sudo.......i cant believe i keep forgetting that.

yes im using usb persistence, installed mine from universal usb installer from windows.

as for fixing sudo....i think ill stick with re-installing my ubuntu as i think i have broken more than just my sudo by running the below command lol....

```
sudo chmod 755 /
```thank you for your help haqking, i will keep those links for future references XD

and.....a little off-topic question....with usb persistence and the default setup, will logs clutter up and possibly make my casper-rw full in space ?? and how do you find which programs do log ?


no problem

I wouldnt disable logging but you could look at changing the default logging with :
```

man logrotate
```

and edit the .conf file.

and also

```
man syslog
```

you could also read here about moving log files to RAM [http://wiki.geteasypeasy.com/How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive](http://wiki.geteasypeasy.com/How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive)

---

### Post by TripleTea on 2011-09-13
ohh ohh...thank you so much for the infos :D...really appreciated it. you showed me more than what i needed O_O...

you wouldn't mind if i pester you with more nooby questions in the future would you haqking [-o<:biggrin:

---

### Post by haqking on 2011-09-13
> **TripleTea said:**
> ohh ohh...thank you so much for the infos :D...really appreciated it. you showed me more than what i needed O_O...

you wouldn't mind if i pester you with more nooby questions in the future would you haqking [-o<:biggrin:


feel free to post support questions in the forum in the right areas ;-)

you can PM me if you like but you might get your answers faster posting on the forum, i occasionally sleep...LOL

Start new threads in appropriate areas if problems do not relate to original posts in the a given thread.

glad i could help.

enjoy, remember to mark thread as solved using thread tools also.

peace

---

### Post by TripleTea on 2011-09-15
thank you haqking...

but back on the topic. i'll try the code below on a fresh Ubuntu install soon and see if i can change it, and ill get back here with either good news or bad news...
```
gksudo gedit /etc/hostname
gksudo gedit /etc/hosts
```

---

### Post by The Cog on 2011-09-15
I have a feeling tahat you need to open **both** editors **before** you save either change because gksudo won't work if the hostname from /etc/hostname is not resolved in /etc/hosts. So having edited one file, you can't use gksudo (or sudo) to edit the other file to match.

---

