---
title: "Modifying a crontab"
date: 2012-03-23
forum: General Help
---

### Post by rmcellig on 2012-03-23
This is the crontab I use to record my radio shows. For months I have been figuring out how to add a date and tiime stamp to the code.

arecord -t wav -f cd -d 8800 /root/radioshows/intransition.wav


 I found a web site that has different date and time formats ([http://www.foragoodstrftime.com/](http://www.foragoodstrftime.com/)). Is there a way to take the code from this web site and incorportate it into my cronjob code? That would REALLY help me out!!

---

### Post by Habitual on 2012-03-23
[http://forums.linuxmint.com/viewtopic.php?f=18&t=97906#p558532](http://forums.linuxmint.com/viewtopic.php?f=18&t=97906#p558532)

---

### Post by ajgreeny on 2012-03-23
I am not sure that I understand what it is you want.

That is not a crontab, it's just a command which you could run with cron easily enough.

If you are just wanting the .wav file to have a datestamp on it, that is very easy with a date variable in the filename, so for example, call the file **$(date +%F %H-%M)-intransition.wav** instead of just **intransition.wav**.  The file will then ber named as **2012-03-23 23-03-intransition.wav**

In choosing the time/date variable value, make sure you don't use one that has a / in the output, such as %x, as / is not allowed in filenames.

---

### Post by rmcellig on 2012-03-23
Thanks! I will try that out. I guess I used the wrong term saying it was a crontab. I'm still learning the proper terminology for all this stuff.

---

### Post by rmcellig on 2012-03-24
Would this code work:

IT %frmt_B %frmt_d %frmt_Y

This is what I use in a Mac application called Audio Hijack Plus. I don't think this code is specific to Audio Hijack Plus. It does exactly what I want. I am hoping that this code will work in my arecord code that mentioned in my initial post.

---

### Post by Habitual on 2012-03-24
updated answer at [http://forums.linuxmint.com/viewtopic.php?f=18&t=97906#p558856]("http://forums.linuxmint.com/viewtopic.php?f=18&t=97906#p558532")

---

