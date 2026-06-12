---
title: "Cron job to reboot machine every hour?"
date: 2009-12-14
forum: General Help
---

### Post by ssandbhor11 on 2009-12-14
Please send me a cron script & procedure to reboot my pc every one hours interval.

Thanks

---

### Post by Sin@Sin-Sacrifice on 2009-12-14
```
#!/bin/bash
reboot
``` Then in /etc/crontab put ```
01 * * * * root /path/to/script
```
That will reboot at one minute past every hour.

---

### Post by ssandbhor11 on 2009-12-14
Dear Sir,

Sorry to disturb you again...
I am new to ubuntu, please tell  me the procedure in detail.

Thanks

---

### Post by Logan513 on 2009-12-14
Hmm... couldn't you do this in C++?

[html]#include <iostream>    //needs these four lines
#include <stdlib.h>    //needs these four lines
#include <unistd.h>    //needs there four lines
using namespace std;    //needs these four lines

int main(int argc, char *argv[]){
    sleep(3600);        //Makes the program wait 1 hour
    // code to reboot.
    return 0;
}[/html]I don't know. Just an idea. Have this program execute every time the machine starts up... You will have to figure out the code for the reboot on your own. I don't know it.

Well good luck with your project! ;)

return 0;

edit: You know, We could do this in PERL....

[html]#!/usr/bin/perl

sleep(3600);
print"rebooting...\n";
`sudo init 6`[/html]

But I don't know.... I am going to leave now...

return 0;

---

### Post by ssandbhor11 on 2009-12-14
I wanted to know the procedure of Cronjob & not of C++.

by the way I do not know any programming language.

---

### Post by Logan513 on 2009-12-14
Cronjob? Never heard of it.:lolflag:

---

### Post by SecretCode on 2009-12-14
Why do you need to do this? It's an unusual thing for a complete Ubuntu beginner to want ...

Exam question? ;)

---

### Post by JoeSolo on 2009-12-14
If you're running one of the desktop editions, you could just install gnome-schedule.

```
$ sudo apt-get install gnome-schedule
```

---

### Post by benjaminsuman on 2009-12-14
To create a cron job that runs as root do the following:

```

$ sudo su -
$ crontab -e

```That will open the editor for the root crontab file.  Then you can enter the a job as suggested above.  There is also a howto for the crontab in the community documentation:

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by ssandbhor11 on 2009-12-15
Actually I have a BSNL CDMA usb modem cum phone for internet dial up connection. After connecting some time it disconnects. Then I have to disconnect the usb cable connect it again, otherwise it does not get connected. But if I restart the system it gets connected.
Please help???

---

### Post by ssandbhor11 on 2009-12-29
Is there any way to unload usb drivers & load it again automatically?

---

