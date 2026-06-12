---
title: "Startup conky as root"
date: 2011-10-30
forum: General Help
---

### Post by dimmuboy on 2011-10-30
Hello there,
i need to run conky after start system with root permissions because of wireless variables.
I've tried this method, but still ask for password.
[...799286&postcount=2]("http://ubuntuforums.org/showpost.php?p=799286&postcount=2")
btw here is my script:
```
#!/bin/sh

sleep 25
conky -c /home/dimmuboy/.conkyrc0 &
conky -c /home/dimmuboy/.conkyrc1 &
conky -c /home/dimmuboy/.conkyrc2 &
perl /home/dimmuboy/.conky/moc/mocstat.pl -f
```

and short print from visudo:
```
dimmuboy ALL=NOPASSWD: /home/dimmuboy/.conky.sh
```

---

### Post by robkendrick on 2011-11-10
I was able to get mine to work by first checking to see where conky was with 'which':
```
rob@meep:~$ which conky
/usr/bin/conky
```

From there, I added this line with visudo:

```
rob     ALL=NOPASSWD:/usr/bin/conky
```

This gets me the AP and ESSID info I need from iwconfig.

I'm not sure this will assist you since you're sudo-ing a separate script, though.  Does NOPASSWD normally only work with binary scripts?  Does it work if you add the conky lines to rc.local?

Hopefully someone more knowledgeable can jump in and help us.
Take care!
Rob

---

### Post by blueridgedog on 2011-11-10
In addition to the path to your script, you may want to try putting conky in the allow without a password.  There are significant security risks to this, but worth a try for testing.

---

