---
title: "Bluetooth doesn't work after resume from sleep/standby"
date: 2010-01-21
forum: General Help
---

### Post by Ferux on 2010-01-21
Hello


I just bought a Logitech V470 bluetooth mouse. It's no problem to let it work under Koala 9.10 (gnome), but after shutdown/standby/sleep, it doesn't work anymore.

With my USB mouse, I have to click the bluetooth icon and select 'switch off bluetooth'. After that, I click 'switch on bluetooth' and bluetooth works again...

I thought switching on and off bluetooth with the applet is the same as 'sudo /etc/init.d/bluetooth start/stop', but it isn't! The previous command greyes out/in the bluetooth icon, but it doesn't resume my bluetooth.
If 'sudo /etc/init.d/bluetooth restart' would work, I would be able to add this line into /etc/pm/sleep.d, so it's automatically loaded on resume.



Does anyone know a solution?
Thanks!

---

### Post by Ferux on 2010-01-26
OK, after some days of searching, I found the solution myself. Appearantly the command is

$rfkill block bluetooth

to stop Bluetooth and

$rfkill unblock bluetooth

to resume Bluetooth.

So, my file in /etc/pm/sleep.d looks like this:

```

#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
    hibernate|suspend)
    rfkill block bluetooth
    ;;
    thaw|resume)
    rfkill unblock bluetooth
    ;;
    *)
    ;;
esac

exit
```

---

### Post by jeppebundsgaard on 2010-04-21
Thank you so much Ferux! =D> This problem with bluetooth going offline and restarting after an arbitrary timespan has been bothering me for so long! Now it seems to work thanks to your script.

It took me a while to understand what exactly to do, so here is a more elaborate explanation:

When the computer hibernate, suspends and resume linux looks in /etc/pm/sleep.d and run all files in there. Thus Ferux' script should be put in there in a file that is readable to all users:

```

cd /etc/pm/sleep.d
sudo touch 10_bluetooth
sudo chmod 0755 10_bluetooth
sudo kate 10_bluetooth

```Now copy and paste Ferux' script into the new file:

```

#!/bin/bash
#Code from http://ubuntuforums.org/showthread.php?t=1387211

. /usr/lib/pm-utils/functions

case "$1" in
    hibernate|suspend)
    rfkill block bluetooth
    ;;
    thaw|resume)
    rfkill unblock bluetooth
    ;;
    *)
    ;;
esac

exit

```Hit save and you are done! No more waiting for bluetooth!

---

### Post by AldenIsZen on 2011-01-23
> **jeppebundsgaard said:**
> 
```

cd /etc/pm/sleep.d
sudo touch 10_bluetooth
sudo chmod 0755 10_bluetooth
sudo kate 10_bluetooth

```Now copy and paste Ferux' script into the new file:



 Just wanted to mention that I try to look at all commands before I run a simple script. Those that have Gnome for example should run "gedit" instead of "kate":


```

cd /etc/pm/sleep.d
sudo touch 10_bluetooth
sudo chmod 0755 10_bluetooth
sudo gedit 10_bluetooth

```Now copy and paste Ferux' script into the new file as described above.


Oh, and yes thank you Ferux. I now can use my Blue Proximity program after suspend to lock/unlock my desktop without having to manually sign in with my cell phone now! Sweetness! Also, I learned about the case command. I thought the case was a letter case "switcher" (and therefore not sure why it was needed, lol), and I couldn't figure out "esac" lol. But I get it now after some [Google-fu]("http://ss64.com/bash/case.html").

---

### Post by lance2010 on 2011-02-13
Thanks Ferux et al.
Solution fixed the same frustrating issue I was having on an HP Mini 311 running 10.10

---

### Post by Protocol84 on 2011-02-22
thank you!! I an going to see if this works for the Rii Mini keyboard/mouse, will let you know if it works.

**edit**

Yes it did!!

---

### Post by Jezdec on 2011-03-02
Great work Ferux and jeppebundsgaard! This was forcing me to reboot constantly. I have 10.10, and from the start, my bluetooth got messed up following sleep. But lately, the first sleep froze bluetooth, and then the laptop wouldn't sleep anymore. I think the last kernel caused the change (2.6.35-27).

Actually, I now know that it wasn't the kernel, but KDE: [see here]("http://ubuntuforums.org/showthread.php?p=10728456")

---

### Post by frogotronic on 2012-03-16
This also works for tangerine media sharing...

See this post: [http://ubuntuforums.org/showpost.php?p=11770123&postcount=2](http://ubuntuforums.org/showpost.php?p=11770123&postcount=2)

---

### Post by rpress on 2013-01-20
I found this thread by looking at the file in /etc/pm/sleep.d/10_bluetooth.  Even with this file my bluetooth would not work after suspend.  Modifying the file as so has fixed this problem for me:
```
#!/bin/bash
#Code from http://ubuntuforums.org/showthread.php?t=1387211

. /usr/lib/pm-utils/functions

case "$1" in
    hibernate|suspend)
    rfkill block bluetooth
    ;;
    thaw|resume)
    rfkill unblock bluetooth
    rmmod btusb
    modprobe btusb
    ;;
    *)
    ;;
esac

exit

```

---

