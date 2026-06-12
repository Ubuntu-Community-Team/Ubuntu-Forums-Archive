---
title: "how to install Google World"
date: 2010-11-18
forum: General Help
---

### Post by s1baker on 2010-11-18
Hi, 
Newby here. I just downloaded the Google World install, now i don't know what to do.
Can't see a install or anything. Anybody know what I should do to install Google World maps? I have heard that Google and Linux are similar.

---

### Post by pizza-is-good on 2010-11-18
I think you mean Google Earth...

IF that is what you meant. Does the file you downloaded end with .exe? If so, you have the file for windows, which does not work in Ubuntu. No need to worry though, there is one for Ubuntu. Open your software center (Applications>>Ubuntu Software Center) and search for 'Google Earth'. If nothing shows, let us know, we'll have to put it there.

What version of Ubuntu are you running?

Google uses many linux-based products, and in fact, it has created some themselves. Examples are Android OS and Chrome OS.

~pizza

---

### Post by PaulReaver on 2010-11-18
if you downloaded the bin file you'll need to make it executable (chmod +x) then run it.

should be okay to let it install in the default directories

:D

---

### Post by s1baker on 2010-11-18
woo . Pizza & Paul. 
Never posted a reply on this forum.
Forgive me, still trying to figure it out.

Went to software centr, and hit 
( applications / Umbutu Software Center ) 
nothing shows

---

### Post by s1baker on 2010-11-18
Google Earth is what I meant. I meen, how to install it.

---

### Post by sandyd on 2010-11-18
```

wget -c http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
chmod 777 GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```

---

### Post by s1baker on 2010-11-18
didn't work

---

### Post by Verbeck on 2010-11-18
> **s1baker said:**
> didn't work
what error did you get?

---

### Post by s1baker on 2010-11-18
can anybody tell me how to install Google Earth?

I have Ubuntu 10.10 32 bit Maverick MeeKat
thanks

---

### Post by s1baker on 2010-11-18
I put the lines that you had posted into my terminal , and after it ran for about 3 or 4 minutes it gave me this reply:
 
"couldn't load 'setup.data/setup.xml'
Press return to close this window

zsheee

---

### Post by sandyd on 2010-11-18
> **s1baker said:**
> I put the lines that you had posted into my terminal , and after it ran for about 3 or 4 minutes it gave me this reply:
 
"couldn't load 'setup.data/setup.xml'
Press return to close this window

zsheee

try again, maybe it didn't like gksudo.....

if the fixed commands still don't work
```

wget -c http://dl.google.com/earth/client/advanced/previous/GoogleEarthLinux.bin
chmod 777 GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```

if still no luck
```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
```then you should be able to see google earth in software center

---

### Post by s1baker on 2010-11-18
Can anybody give me a clue as to how to install Google Earth on Ubuntu 10.10

Thanks

---

### Post by overdrank on 2010-11-18
Threads merged. :)

---

### Post by s1baker on 2010-11-18
maybe I new to reboot the computer?

---

### Post by Zzl1xndd on 2010-11-18
Maybe this will help.

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by s1baker on 2010-11-18
no sandy, no luck

run the list that you posted thru my terminal and I still see no Google Earth there.

---

### Post by s1baker on 2010-11-18
can anybody here tell me how to install Google Earth?

---

### Post by dcstar on 2010-11-19
> **s1baker said:**
> can anybody here tell me how to install Google Earth?

Do a web search for the community documentation and follow the instructions.

---

### Post by uRock on 2010-11-19
Merged yet another duplicate thread. Please stop making duplicate threads.

Your answer is here [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

