---
title: "how can i change the time on xubuntu"
date: 2011-10-12
forum: General Help
---

### Post by tobythedog on 2011-10-12
hi my pc time is wrong , i go to sttings and click on time and date to put it wright but nothing happens , how can i put the time back to its correct setting please

---

### Post by linuxwin2 on 2011-10-12
You can use 
```
$ sudo date -s "11 OCT 2011 18:00:00"

```

---

### Post by deathadder on 2011-10-12
If the machine is always connected to the internet, I would suggest using NTP.

Go to System->Time and Date and then in the window that pops up click on the padlock so you are able to modify the settings. This will ask you for your password. There's a drop down menu called "Configuration" from that choose "Keep synchronised with Internet servers". You will probably be prompted to install NTP, just enter your password and let apt do it's thing. You'll then need to select the time servers you want, I would choose all of them just to be safe.

---

### Post by tobythedog on 2011-10-12
no good as when i go to time and date in settings , when i click on time and date nothing happens nothing opens nothing else to fill in click on etc

---

### Post by tobythedog on 2011-10-12
tried the comand line one as well , this also does not work command not found

---

### Post by cryptotheslow on 2011-10-12
Restart the PC and just as it initially starts look for the option to enter the BIOS settings. Depending on the motherboard BIOS supplier it will require pressing a particular key... common ones are Esc, Del, F2, F11, F12 - but there are many others.

Once in the BIOS settings, set the correct time then find the "Exit and Save" option (again the menu location or particular key sequence is dependent on the BIOS supplier). Generally the acceptable key inputs are shown on the screen when in BIOS settings - so read and use common-sense :D

---

### Post by deathadder on 2011-10-13
> tried the comand line one as well , this also does not work command not found
Hmm, that's rather strange. The date command is in /bin so shouldn't be a problem. Can you try the absolute path?
```
sudo /bin/date -s "13 Oct 2011 08:00:00"
```
If that works then your $PATH has been changed some how. You can fix that by typing:
```
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```
Then try setting the date via the GUI again. If this works you'll need to make the PATH changes persistent by adding it to either ~/.bashrc or /etc/base.bashrc

---

### Post by tobythedog on 2011-10-13
no still no luck tried the sudo /bin/date -s "13 Oct 2011 when i do this with the time it asks for my password and when this is given i hit the return key and the pc flashes the screen saver for a couple of seconds and then returns to what was there before time is still incorrect

---

### Post by tobythedog on 2011-10-13
tried it again and it haqs updated the time to the correct setting , however when i go to settings and click on time and date , still nothing happening , have tried your repar command and still nothing

---

### Post by deathadder on 2011-10-14
Sorry I got myself the wrong way round there, I meant to say:
> 
If that works then your $PATH has been changed some how. You can fix that by typing:

export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

You'll need to make the PATH changes persistent by adding it to either ~/.bashrc or /etc/bash.bashrc then try setting the date via the GUI again. 

From a fresh shell, presuming you haven't already changed your PATH in ~/.bashrc or /etc/bash.bashrc can you post what your PATH currently is? You can see it by typing:
```
echo $PATH
```
The XFCE app I've used to set my date and time is called 'time-admin', can you run the following commands and let me know the output?
```
$ time-admin
```
```
$ /usr/bin/time-admin
```

---

