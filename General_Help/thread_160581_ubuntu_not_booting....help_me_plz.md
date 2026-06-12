---
title: "ubuntu not booting....help me plz"
date: 2006-04-15
forum: General Help
---

### Post by larafan on 2006-04-15
when i enter my username and password...a message pops up saying your session didnt last for 10 seconds and when i press details it says "private socket dir:no space on the device".what to do.i can get into terminal.any command to b written.help me please

---

### Post by PriceChild on 2006-04-15
I think that this means you've filled your hard drive so ubuntu can't copy permissions files around to let you  in.

I've done it before, but can't remember the exact error.

Anyway, you should be able to press ctrl+alt+F1 then log in in the terminal. delete a file taking up a reasonably amount of space and then press ctrl+alt+F7 and try logging into gnome again.

Pricey

---

### Post by codejunkie on 2006-04-15
[QUOTE=larafan]when i enter my username and password...a message pops up saying your session didnt last for 10 seconds and when i press details it says "private socket dir:no space on the device".what to do.i can get into terminal.any command to b written.help me please[/QUOTE]
some permissions have gotten changed on some files under your user account, try this first and see if this works and we can go from there.
press ctrl+alt+F1 login with your user account and enter
```
sudo rm /home/yourusername/.ICEauthority
```
then
```
sudo rm /home/yourusername/.Xauthority
```
and reboot by entering ```
sudo init 6
```
when it boots back up try logging in again and see if this fixes it.

---

### Post by larafan on 2006-04-15
finally did 

sudo apt-get clear

that solved my problem

---

### Post by PriceChild on 2006-04-15
you did codejunkie's solution and then cleared apt-get?

Or apt-get while in terminal? Just interested to see if i was right lol

---

### Post by severedspirit on 2006-04-15
I have had a problem which seems to be similar to this, I log in with my user account and it brings this message but i use another user and it works perfectly. I have tried removing files and the apt-get clean with no avail. 

btw this happened after a crash (the first ive ever had in linux)

---

### Post by Ramses de Norre on 2006-04-15
Did you try removing ~/.Xauthority and ~/.ICEauthority ?
```
rm .Xauthority .ICEauthority
```

---

### Post by severedspirit on 2006-04-15
Yer, I have already done that but it did not help

---

### Post by Ramses de Norre on 2006-04-15
What's the exact error message?

---

### Post by severedspirit on 2006-04-15
your session only lasted less than 30 seconds. if you have not logged out yourself this might mean that there is some installation problems 

I cant read the rest as i am viewing it through a tv which is less as sharp as a normal monitor

---

### Post by codejunkie on 2006-04-15
[QUOTE=severedspirit]your session only lasted less than 30 seconds. if you have not logged out yourself this might mean that there is some installation problems 

I cant read the rest as i am viewing it through a tv which is less as sharp as a normal monitor[/QUOTE]
Try removing all the files in the /tmp dir you can do that with this, but **make sure you run these commands in order, or you could loose all your data**
1:```
cd /tmp
```
2:```
sudo  rm -R *
```
3:```
sudo rm -R .*
```
after you've done this reboot and try that user account again.

---

### Post by larafan on 2006-04-16
[QUOTE=PriceChild]you did codejunkie's solution and then cleared apt-get?

Or apt-get while in terminal? Just interested to see if i was right lol[/QUOTE]

no,did just sudo apt-get clear

i dont know how my disk got filled,i have installed usual codecs,mediaplayers,some small softwares.and i have allocate 9.5Gb for ubuntu.just wanted to tell ubuntu users abt the solution.thanx.

---

### Post by severedspirit on 2006-04-16
[QUOTE=codejunkie]Try removing all the files in the /tmp dir you can do that with this, but **make sure you run these commands in order, or you could loose all your data**
1:```
cd /tmp
```
2:```
sudo  rm -R *
```
3:```
sudo rm -R .*
```
after you've done this reboot and try that user account again.[/QUOTE]

This didnt work I received these messages from it

```
 rm: cannot remove '*': No such file or directory
```

---

### Post by severedspirit on 2006-04-16
btw I am running a mythtv box, incase this is relevant

---

### Post by severedspirit on 2006-04-16
would running it on a tv rather than a monitor affect this at all.

---

