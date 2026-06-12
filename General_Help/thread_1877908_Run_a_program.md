---
title: "Run a program"
date: 2011-11-08
forum: General Help
---

### Post by trans-am on 2011-11-08
Hi, may i know how to start Transmission automatically after i have log-in.

I was using Ubuntu 11.10 Destop

---

### Post by bluexrider on 2011-11-08
Go to: System> Preferences> Start-up Applications and add Transmission.

---

### Post by papibe on 2011-11-08
You can set an entry on 'Startup Applications'.

Note that some people have reported that "Startup Applications" is not available by default. If it doesn't come up in the search, use this [trick ]("http://ubuntuforums.org/showpost.php?p=11340819&postcount=5")to enable it.

Regards.

---

### Post by trans-am on 2011-11-15
Hi guy, i found the Start-Up Application BUT, does anyone know where this file "Transmission" is located at? 
I need to add it in the Start-Up Application.:)

---

### Post by papibe on 2011-11-15
In 10.4 is here:
```
/usr/bin/transmission
```
Nevertheless, you can always find out the path to a program using the command 'whereis' on the terminal:
```
whereis transmission
transmission: /usr/bin/transmission /usr/share/transmission /usr/share/man/man1/transmission.1.gz

```
Hope it helps.
Regards.

---

### Post by trans-am on 2011-11-15
@Papibe : Does your code apply to 11.10?

---

### Post by papibe on 2011-11-15
I'm not sure if the location is the same, but the command 'whereis' should be available for the terminal in 11.10:
```
whereis transmission
```
or
```
whereis transmission-gtk
```
Regards.

---

### Post by trans-am on 2011-11-15
> **papibe said:**
> 
```
whereis transmission-gtk
```Regards.

Can you explain what does this mean/do "** -gtk** "

---

### Post by papibe on 2011-11-15
I believe that in some Ubuntu distros (like Xubuntu or Lubuntu) the program itself it is called transmission-gtk instead of just transmission. I put the example just in case.

If you need a more help setting transmission as an startup application, run both commands on the terminal and post the results here. Then we can tell you exactly what to put the startup entry.

Regards.

---

### Post by 3rdalbum on 2011-11-15
> **trans-am said:**
> Can you explain what does this mean/do "** -gtk** "

The program's name is 'transmission-gtk' because it uses the GTK GUI toolkit. There are several different versions of Transmission that use different user interfaces, so putting '-gtk' at the end of the name helps to differentiate it from the others.

---

### Post by Cyclane on 2011-11-15
Papipe, wouldn't the command 'which' be better in this case. which only shows executables.

---

### Post by papibe on 2011-11-15
> **Cyclane said:**
> Papipe, wouldn't the command 'which' be better in this case. which only shows executables.
Very good point, thanks!
Regards.

---

### Post by trans-am on 2011-11-15
Is there a new command?

If so, the new command will be ...?

---

### Post by Cyclane on 2011-11-15
> **trans-am said:**
> Is there a new command?

If so, the new command will be ...?

To find out which command to put in run the following in a terminal:
```
which transmission transmission-gtk
```

Use the output as the Start-Up Application, which was explained earlier.

---

### Post by trans-am on 2011-11-15
```
 which transmission 
```Is this the one?

---

### Post by papibe on 2011-11-15
Yes. We need you to execute that on a terminal and post the results.

(That's not that actual command to set on startup applications, but we need its results to get the good one).

Regards.

---

### Post by trans-am on 2011-11-16
Case solve, thanks everyone for the help =D>

---

