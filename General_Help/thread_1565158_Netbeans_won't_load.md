---
title: "Netbeans won't load"
date: 2010-08-31
forum: General Help
---

### Post by Ravenshade on 2010-08-31
Hi, 

I've tried a quick google search and found nothing. I've recently had to remove openJDK due to the sheer sluggishness of the entire outfit and instead installed SunJDK. 

Now, I've been trying to get Netbeans to work again (had to reinstall it) but it won't load. Here are the simple steps. 

1. Click on netbeans (run) 
2. Netbeans shows up the taskbar
3. Netbeans disappears from the taskbar
4. user left  :confused:

Anyone know why it is doing this? 

Regards,

---

### Post by ean5533 on 2010-08-31
I'm not a netbeans user, but let's start by running it from the terminal and see if any interesting messages get spit out. Open up a terminal and run the program -- I'm assuming the command is just

```
netbeans
```

If that doesn't work, try tab completion.

---

### Post by Ravenshade on 2010-08-31
```
Cannot find java. Please use the --jdkhome switch
```

Uh, I know this means I need to switch netbeans to the new Java, anyone know the syntax for the terminal? 


regards
n00b at home >_<

---

### Post by ean5533 on 2010-08-31
> **Ravenshade said:**
> ```
Cannot find java. Please use the --jdkhome switch
```

Uh, I know this means I need to switch netbeans to the new Java, anyone know the syntax for the terminal? 


regards
n00b at home >_<

If you're uninstalled openJDK then you shouldn't need to do this, but try it anyway (in a terminal):

```
sudo update-java-alternatives -s java-6-sun
```

If that fails for some reason, let know what what the output of this line is:

```
update-java-alternatives -l
```

---

### Post by Ravenshade on 2010-08-31
output

```
java-6-sun 63 /usr/lib/jvm/java-6-sun
```

While it worked (there was no fail) it didn't solve the problem, and when I type in netbeans I still get:

Cannot find Java. Please use the --jdkhome switch

---

### Post by ean5533 on 2010-08-31
> **Ravenshade said:**
> output

```
java-6-sun 63 /usr/lib/jvm/java-6-sun
```

While it worked (there was no fail) it didn't solve the problem, and when I type in netbeans I still get:

Cannot find Java. Please use the --jdkhome switch

Weird. Well, try running it with this command then:

```
netbeans --jdkhome /usr/lib/jvm/java-6-sun
```

If that works, then for some reason netbeans can't find Java on its own and I don't know why. You can stop yourself from having to open netbeans this way every time by editing your netbeans.conf file, which should be at

```
/home/***yourUsername***/netbeans/etc/netbeans.conf
```

Just add this line somewhere to that file:

```
netbeans_jdkhome=/usr/lib/jvm/java-6-sun
```

---

### Post by Ravenshade on 2010-08-31
Perfect, thank you very much. 

*Enjoys netbeans*:popcorn:

---

