---
title: "run script at startup"
date: 2012-01-23
forum: General Help
---

### Post by D0Z on 2012-01-23
I made the following simple script to make xrandr configure my monitors correctly:

```

#!/bin/sh
####################################
#
# This script fixes resolution nightmare.
#
####################################

#create mode
cvt 1600 1200

#utilize mode
xrandr --newmode "1600x1200_60.00"  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync

#bind mode to monitor
xrandr --addmode VGA-1 1600x1200

#set monitor resolution
xrandr --output VGA-1 --mode 1600x1200

#set monitor postition
xrandr --output VGA-1 --left-of DVI-I-1

#set monitor position 2
xrandr --output DVI-I-1 --right-of VGA-1

#set primary monitor
xrandr --output DVI-I-1 --primary

#set primary monitor 2
xrandr --output VGA-1 --primary

```

It is called resofix.sh.

When I run ```
 sudo bash resofix.sh
``` it runs just fine.
I like to make it run at startup, so I added it to Xfce start up list.
Settings->settings manager->sessions and startups->application autostart.
But this doesn't work.

I also tried copying it to /etc/init.d/ and:

```
sudo update-rc.d resofix.sh defaults
sudo chmod +x /etc/init.d/resofix.sh
```


Found here [http://ubuntuforums.org/showpost.php?p=4945649&postcount=3](http://ubuntuforums.org/showpost.php?p=4945649&postcount=3)

That also doesn't work. How do I make the script autorun during startup?

---

### Post by Lars Noodén on 2012-01-23
Copying it to /etc/init.d is not enough, that's just a holding ground for scripts.  To get it to run at start up you need to use [update-rc.d](http://manpages.ubuntu.com/manpages/oneiric/en/man8/update-rc.d.8.html)

However, the simple way would be to run it from /etc/rc.local.  That script gets run after all the SystemV init scripts.

---

### Post by D0Z on 2012-01-23
> **Lars Noodén said:**
> Copying it to /etc/init.d is not enough, that's just a holding ground for scripts.  To get it to run at start up you need to use [update-rc.d](http://manpages.ubuntu.com/manpages/oneiric/en/man8/update-rc.d.8.html)

However, the simple way would be to run it from /etc/rc.local.  That script gets run after all the SystemV init scripts.

You mean altering /etc/rc.local:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

```

To:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#create mode
cvt 1600 1200

#utilize mode
xrandr --newmode "1600x1200_60.00"  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync

#bind mode to monitor
xrandr --addmode VGA-1 1600x1200

#set monitor resolution
xrandr --output VGA-1 --mode 1600x1200

#set monitor postition
xrandr --output VGA-1 --left-of DVI-I-1

#set monitor position 2
xrandr --output DVI-I-1 --right-of VGA-1

#set primary monitor
xrandr --output DVI-I-1 --primary

#set primary monitor 2
xrandr --output VGA-1 --primary

exit 0

```

Like that?

---

### Post by Lars Noodén on 2012-01-23
That's one way.  Another would be to put everything into a script and then call the script from /etc/rc.local

---

### Post by Jose Catre-Vandis on 2012-01-23
The other way, though not secure as you have to write you sudo password in plain text for the commands that require sudo e.g.:

```
 echo "xxxxxxxx" | sudo -S command 
```

where xxxxxxxx is your sudo password, and command is the command you want to run

Example:

```
echo "mypassword" | sudo -S shutdown -h now
```

---

### Post by Lars Noodén on 2012-01-23
> **Jose Catre-Vandis said:**
> The other way, though not secure [snip]

The way to get it done that way would be to customize [sudoers](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sudoers.5.html).  Take a look at [font=Courier New]Cmnd_Alias[/font] for some good examples.

---

### Post by D0Z on 2012-01-23
> **Lars Noodén said:**
> That's one way.  Another would be to put everything into a script and then call the script from /etc/rc.local

I tried adding to /etc/rc.local like I opted, but it doesn't work.

---

### Post by Lars Noodén on 2012-01-23
Maybe you mean when the user's X session starts up rather than when the machine starts up?  In that case, you'll want to create [font=Courier New].xsessionrc[/font] in the user's home directory and edit that.

---

### Post by matt_symes on 2012-01-23
Hi

@OP. I'm pretty sure your script does not need to be run with root privileges.

cvt and xrandr do not require the use of sudo to gain elevated privileges.

Kind regards

---

### Post by D0Z on 2012-01-24
> **Lars Noodén said:**
> Maybe you mean when the user's X session starts up rather than when the machine starts up?  In that case, you'll want to create [font=Courier New].xsessionrc[/font] in the user's home directory and edit that.

Thanks, this solved it!

---

