---
title: "HOW TO: Change your cursor!"
date: 2011-12-05
forum: General Help
---

### Post by Spyderkid on 2011-12-05
[COLOR="Blue"][SIZE="3"]I've bet at some point since 11.04 you've thought, damn I wish I could install a different cursor... WELL NOW YOU CAN :D[/SIZE][/COLOR]

[COLOR="Red"]**Just follow these very simple steps**[/COLOR]

[COLOR="SeaGreen"]1)[/COLOR] Download the attachment, then right-click on it and click properties, then permissions, then check the box that says "allow executing this file as a program"

[COLOR="SeaGreen"]2)[/COLOR] double click on the file and choose run in terminal, follow the instructions, (in the program i've given you 2 new ones to choose from, I recommend ubuntuareo)

[COLOR="SeaGreen"]3) [/COLOR]Log-out and back in again (if you haven't already), and you have a new cursor, WOW!

[COLOR="SeaGreen"]4) [/COLOR]if you wish to use your original one run the script again and choose default

---

### Post by Spyderkid on 2011-12-05
don't be worried about giving sudo perms, It does nothing bad, read it through if you wish

---

### Post by Spyderkid on 2011-12-05
will be adding more cursors to choose from :D

---

### Post by stinkeye on 2011-12-06
> 4) if you wish to use your original one run the script again and choose default
You may want to make the script not automatically download themes everytime run.
```
Please give sudo permissions...
[sudo] password for glen: 
Authentication Success!
Downloading the cursor themes
extracting cursor themes
moveing cursor themes to /usr/share/icons
mv: inter-device move failed: `Ubuntaero_v1.0' to `/usr/share/icons/Ubuntaero_v1.0'; unable to remove target: Is a directory
mv: inter-device move failed: `Pulse-Glass' to `/usr/share/icons/Pulse-Glass'; unable to remove target: Is a directory
Please choose a theme from the folowing 
default 
ubuntuaero 
pulseglass
```

---

### Post by didinium on 2011-12-06
You can also just choose one of the 5 default cursors...

---

### Post by Spyderkid on 2011-12-06
yes stinkeye, I've realised that, not sure how to prevent it though :S if you've come up with anything, message me?

And also didinium thanks for that, I've added options for the defualt set of cursors

---

### Post by stinkeye on 2011-12-06
Remember I just look at examples and read the man pages, but you could
probably use something like
```
ls /usr/share/icons ~/.icons | grep -c "Ubuntaero_v1.0\|Pulse-Glass"
```
Which counts the grepped instances of Ubuntaero_v1.0 and Pulse-Glass.
```
glen@Oneiric:~$ ls /usr/share/icons ~/.icons | grep -c "Ubuntaero_v1.0\|Pulse-Glass"
2
```

Then only download when **ls /usr/share/icons ~/.icons | grep -c "Ubuntaero_v1.0\|Pulse-Glass"** = 0.
:-k :idea:

---

### Post by Spyderkid on 2011-12-06
would I have to | it into a read or if?

---

