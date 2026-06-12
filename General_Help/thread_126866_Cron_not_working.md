---
title: "Cron not working"
date: 2006-02-07
forum: General Help
---

### Post by Im_Just_GrayT on 2006-02-07
ok well I am trying to create an alarm clock with cron, but its not doing anything.
here is my crontab entry:
```
07 22 * * 1-5 /home/shane/alarm/alarm

```

and i dont know if this helps but here is the bash script its supposed to run:
```

#!/bin/bash

# "alarm" wakes me up with the selected mp3/ogg file.

amarok /media/hybrid/Music/Blink-182/Blink-182/Blink-182\ -\ Go.mp3

```

any clue what im doing wrong?:confused: 
any help would be greatly appreciated

---

### Post by hfdragon on 2006-02-07
what do you have in your syslog a the time this batch script is supposed to be started ?

---

### Post by z_diver on 2006-02-07
The 'at' deamon and 'cron' don't have the permissions necessary to run any X windows programs.  I had a similar issue and made the alarm run with mpg321.  Works great.

---

### Post by Im_Just_GrayT on 2006-02-07
thanks for the help. but im kinda new to linux in general so i dont know exactly what i need to do. could someone tell me what i need to do to make this work? (i cant stand booting into :twisted: windows:twisted:  every night, it gives me chills)

Thanks!:-D

---

### Post by z_diver on 2006-02-07
Just install mpg321 from synaptic and replace the word amarok with it in your alarm file.  It will look something like this.

mpg321 /media/hybrid/Music/Blink-182/Blink-182/Blink-182\ -\ Go.mp3

That should do it.

---

### Post by Im_Just_GrayT on 2006-02-07
Hey thanks!! its working now.
but one more question. how do i stop it? can i like stop or pause the music before the song is done? becuase I would really rather just shut it off when i wake up instead of listening to the whole song.

Thanks alot!:D

---

### Post by z_diver on 2006-02-09
That's a good idea.  So I made a script and ran chmod 755 on the file to make it exectable.  Now I can click it to turn off the alarm as it's too early for typing. ;-)
!#/bin/bash
pkill mgp321

---

