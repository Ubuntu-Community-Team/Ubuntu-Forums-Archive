---
title: "Ubuntu date of installation"
date: 2010-02-25
forum: General Help
---

### Post by Jaraxle on 2010-02-25
I was wondering if anyone could tell me a way, perhaps using the terminal, to get the date my current Ubuntu version (9.04 Jaunty) was installed.

If possible, I would also like to be able to get some stats such as average uptime, longest uptime, etc. -- perhaps using grep? I'm not sure, but preferably something where I wouldn't have to write a script, ex. Perl. I really have no experience doing that.

Thanks, I'm about to format and install 9.10 Karmic but wanted this info first.

---

### Post by jmszr on 2010-02-25
Jaraxle,

This certainly isn't an elegant way, but you could go to Synaptic > File > History and scroll down until you find out when you started installing things. Should be close anyway.

---

### Post by n0dix on 2010-02-25
Related thread [http://ubuntuforums.org/showthread.php?t=295371](http://ubuntuforums.org/showthread.php?t=295371)

---

### Post by Johnny B on 2010-02-25
i used:
```
sudo grep ubiquity /var/log/installer/syslog | awk '{print $1" "$2" "$3}' | sort -n | uniq | sed -n '1 p'
Dec 30 20:26:01
```

---

### Post by Jaraxle on 2010-02-25
> **jmszr said:**
> Jaraxle,

This certainly isn't an elegant way, but you could go to Synaptic > File > History and scroll down until you find out when you started installing things. Should be close anyway.

I had no idea that was there. Thanks, that's pretty cool. It's interesting going back and seeing when I installed things.

Thanks guys, I'm going to try: ```
grep ubiquity /var/log/installer/syslog | less
```

That should tell me the exact date.

---

