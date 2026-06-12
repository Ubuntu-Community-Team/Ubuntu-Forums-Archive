---
title: "cron question"
date: 2011-09-17
forum: General Help
---

### Post by shantiq on 2011-09-17
[FONT="Arial"]starting to use cron

using this guide **[here]("http://www.scrounge.org/linux/cron.html")**[/FONT]

so i have my file called mousepad.cron


which contains this line

```
0,3,6,9,12,15 **** /usr/bin/mousepad
```


**just for testing** :KS


then i run 

```
crontab mousepad.cron
```



and get this


```
new crontab file is missing newline before EOF, can't install.

```





what does this mean?

---

### Post by Lisiano on 2011-09-17
EOF - End Of File. Seems it just wants you to make a newline right after /usr/bin/mousepad.
Btw. You can always just edit your own crontab instead of making a new one. Just type crontab -e. Before that you need to export a editor you wish to use to edit cron. For example nano.```
export EDITOR=nano
crontab -e
```

EDIT: To make it permanent you can always add it to the end of your ~/.bashrc
```
echo "export EDITOR=nano" >> ~/.bashrc
```
Don't accidentally type a single > . Or else you will overwrite your .bashrc to contain only that line. You can get a copy of the old one from /etc/skel/.bashrc if you do overwrite it.

---

### Post by papibe on 2011-09-17
Not related to your error, but I think [this]("https://help.ubuntu.com/community/CronHowto") community guide is very good.

Regards.

---

### Post by shantiq on 2011-09-17
thanx for replies Lisiano it may seem a dumb question   but how to do that

> EOF - End Of File. Seems it just wants you to make a newline right after /usr/bin/mousepad.
      what have i got to change to


```
0,3,6,9,12,15 **** /usr/bin/mousepad

```


to do that         sorry i do not understand :KS



ok got it 

just hit return before saving

---

### Post by shantiq on 2011-09-17
ok next question :KS


if i enter

```
1 20  * * *    /usr/bin/gnome-text-editor
```

gnome-text-editor should open at 20:01 right


but it does not


what am i not seeing? what could possibly be wrong?

---

### Post by papibe on 2011-09-17
Cron runs in a very limited environment. In order to open graphical applications you need to set the 'display' variable. Check the section 'GUI Applications' on the guide that I linked in my previous post.

Regards.

---

### Post by shantiq on 2011-09-17
thank you papibe for pointers will investigate


ok and with all your help guys finally got there


This will record a World Music Program on Radio 3 in 320kbps every sunday at 22:00 for an hour every week every month; which is what i wanted to do in the first place.   so thank you.

> 0 22 * * 0   get_iplayer --get --force --type=liveradio --stop 3600 "http://www.bbc.co.uk/mediaselector/4/gtis/?server=cp60703.live.edgefcs.net&identifier=Special_Event1_UK@s6485&kind=akamai&application=live"  && sudo shutdown -h +15

with shutdown set so it does not require a password

```
sudo gedit /etc/sudoers
```

and add

```
#includedir /etc/sudoers.d
username ALL=NOPASSWD: /sbin/shutdown
```

at bottom of file then save

---

### Post by Lisiano on 2011-09-18
I recommend you use ```
shutdown -h now
``` instead. You can use ```
sudo crontab -e
``` to add a entry as root and point to do ```
0 23 * * 0 shutdown -h now
``` or ```
0 22 * * 0 shutdown -h 23:00
```
Also you shouldn't edit /etc/sudoers manually. Use this instead ```
sudo visudo
```
(The EDITOR variable also makes you use nano here instead of vi)

---

### Post by shantiq on 2011-09-18
hi again Lisiano    2    questions

=======================
I have heard this before



> Also you shouldn't edit /etc/sudoers manually. Use this instead
Code:
sudo visudo



could you please explain why not    and why it is better to use visudo    i found its layout confusing why i chose gedit instead or even mousepad     what is the difference?

==================

**also**


is ```
shutdown -h now
```   different from ```
sudo halt
```    and how exactly?


Thanx for all info

---

### Post by Lisiano on 2011-09-20
visudo does a syntax check so your edits don't break sudo, since it obeys the EDITOR varibale you can export nano, gedit or mousepad and make edits with them but I don't know if using graphical applications work well as EDITOR variables.
As for shutdown against halt. As you noticed you can specify when to turn off the PC, while halt was modified to call shutdown instead (I think), it's better to call shutdown directly for the added functionality of being less brutal and letting users know that the system will turn off in N minutes. Also to scare users with the -k switch ('Fake' shutdown). You can actually cancel a shutdown if for example you are doing something and remember that you still need to do stuff, you can issue a ```
shutdown -c
``` and continue working without interruptions.
Also adding either one of those in the root crontab let's you use both of them without sudo. While under normal circumstances you need to call sudo either way. Also having them in the root crontab instead of being "sudo usable without a pass by anyone" makes sure that the system can be turned off only by using sudo AND a password or waiting (in your case) until it's 23:00.

---

### Post by shantiq on 2011-09-20
thank you Lisiano for very helpful clarifications  ):P

---

