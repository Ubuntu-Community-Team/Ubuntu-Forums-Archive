---
title: "Autostarting conky not working in 12.04"
date: 2012-06-06
forum: General Help
---

### Post by timgood on 2012-06-06
Autostarting conky from a script that worked flawlessly in 11.10 no longer works in 12.04 but will work when run from the command line, or when logging out and back in without restarting the machine.

 I have tried entering the following into Startup Applications: ```
conky -p 10 -c /home/username/.Conky/htc_home/conkyrc &
``` and this fails as well. However, it works when I log out and log in again, and works when run from the command line. 

I have tried altering the timeout to as much as 25 seconds but no joy. A similar script to run Skype after a timeout works flawlessly. Any explanations or ideas?

---

### Post by Habitual on 2012-06-06
Don't believe the script needs to go into the bg with " &".
Try it w\out it and let us know...

---

### Post by timgood on 2012-06-06
No, still doesn't work. I'm stumped.

---

### Post by Frogs Hair on 2012-06-06
This is what I use and the sleep delay time can be changed.  I use 10 to allow Compiz to start  . Just make it executable and add to start-up programs .

 ```
 #!/bin/bash
 sleep 10 && 
conky -c ~/.conkyrc;
```

---

### Post by Frogs Hair on 2012-06-06
If you have more than one it will look as follows.```
#!/bin/bash
 sleep 10 && 
conky -c ~/.conky1;
conky -c ~/.conky2;
conky -c ~/.conky3;
```

---

### Post by philinux on 2012-06-06
> **timgood said:**
> Autostarting conky from a script that worked flawlessly in 11.10 no longer works in 12.04 but will work when run from the command line, or when logging out and back in without restarting the machine.

 I have tried entering the following into Startup Applications: ```
conky -p 10 -c /home/username/.Conky/htc_home/conkyrc &
``` and this fails as well. However, it works when I log out and log in again, and works when run from the command line. 

I have tried altering the timeout to as much as 25 seconds but no joy. A similar script to run Skype after a timeout works flawlessly. Any explanations or ideas?

All I have is this in startup in 12.04. Seems to work fine.

---

### Post by chambemanela on 2012-06-09
Type this in Startup Applications => Command,

conky -p 5 -c /home/usr/bin/conky &


work for me,,,,,,,:popcorn:

---

### Post by frogotronic on 2012-06-29
> **timgood said:**
> Autostarting conky from a script that worked flawlessly in 11.10 no longer works in 12.04 but will work when run from the command line, or when logging out and back in without restarting the machine.

 I have tried entering the following into Startup Applications: ```
conky -p 10 -c /home/username/.Conky/htc_home/conkyrc &
``` and this fails as well. However, it works when I log out and log in again, and works when run from the command line. 

I have tried altering the timeout to as much as 25 seconds but no joy. A similar script to run Skype after a timeout works flawlessly. Any explanations or ideas?

I read in a post that conky won't start until after five minutes.. (300)

But re-rolled from git works on autostart.

- CH

---

### Post by frogotronic on 2012-06-30
So...I tried everything and no go...


from a terminal 

$conky & works everytime after about three minutes...

- CH

---

### Post by Gillingham on 2012-06-30
It works after 3 minutes?  

Are you using an execi or execpi command with the time set to ~180s.  If so you may be being affected by a known bug in conky 1.8 the version in the main repositories.  The fix is to enable the backports repository and upgrade conky to 1.9, or to delay to greater than 3 minutes.

David

---

### Post by stinkeye on 2012-06-30
The conky in 12.04 has a couple of bugs.
Try updating conky using this ppa.
```
sudo add-apt-repository ppa:vincent-c/conky
sudo apt-get update
```

Update manager should now open where you can update
or just run...
```
sudo apt-get install [COLOR="Magenta"]conky-all[/COLOR]
```

or use just [COLOR="magenta"]**conky**[/COLOR] depending on what package 
you have installed originally.

---

### Post by 216monster on 2012-07-04
> **Frogs Hair said:**
> This is what I use and the sleep delay time can be changed.  I use 10 to allow Compiz to start  . Just make it executable and add to start-up programs .

 ```
 #!/bin/bash
 sleep 10 && 
conky -c ~/.conkyrc;
```


I just wanted to reply and confirm that this method worked for me!

---

### Post by frogotronic on 2012-07-06
> **216monster said:**
> I just wanted to reply and confirm that this method worked for me!

Works for me as well.

Thanks!

---

### Post by BLTicklemonster on 2012-07-28
> **Frogs Hair said:**
> This is what I use and the sleep delay time can be changed.  I use 10 to allow Compiz to start  . Just make it executable and add to start-up programs .

 ```
 #!/bin/bash
 sleep 10 && 
conky -c ~/.conkyrc;
```

Worked for me, too.

---

### Post by Scott Goodgame on 2012-07-28
try this 
usr/bin/conky -d -c /home/user/.conkyrc

the important part is the -d is starts it as a daemon

---

### Post by Hreinsi on 2012-07-28
sudo apt-get install conky-all

2. Again via Linux terminal, make a config file named ".conkyrc" in your home directory

gedit ~/.conkyrc

3. Paste your preferred Conky config file and make sure that you set "own_window_type" to "override", and then save it.
gedit .conky_start.sh

Paste this code:

#!/bin/bash

sleep 15 && conky;

Make sure the script is executable:

chmod a+x .conky_start.sh
5. Now let's add conky_start script to your “Startup Applications”.
/home/your_user_name/.conky_start.sh

---

### Post by taras.kuzyo on 2012-08-22
> **stinkeye said:**
> The conky in 12.04 has a couple of bugs.
Try updating conky using this ppa.
```
sudo add-apt-repository ppa:vincent-c/conky
sudo apt-get update
```Update manager should now open where you can update
or just run...
```
sudo apt-get install [COLOR=Magenta]conky-all[/COLOR]
```or use just [COLOR=magenta]**conky**[/COLOR] depending on what package 
you have installed originally.

Worked for me.

---

### Post by 112123user on 2012-10-04
> **taras.kuzyo said:**
> Worked for me.

Not for me on sudio.  Annoying that this worked in other versions of ubuntu and is broken now.

Conky will not autostart on my system.  I followed the docs.  I added the repo above & reinstalled and it still will not autostart.  I refuse to do the shell script with the delay.

# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise

# echo $DESKTOP_SESSION 
ubuntustudio

---

### Post by stinkeye on 2012-10-04
> **112123user said:**
> Not for me on sudio.  Annoying that this worked in other versions of ubuntu and is broken now.

Conky will not autostart on my system.  I followed the docs.  I added the repo above & reinstalled and it still will not autostart.  I refuse to do the shell script with the delay.

# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise

# echo $DESKTOP_SESSION 
ubuntustudio
XFCE is the default desktop environment in ubuntustudio 12.04 and therefore a different window manager, xfwm.

In your conky config try different settings for **own_window_type**
```
own_window_type **desktop**
or
own_window_type **override** 
```

Delay the start of conky with the in built pausing(-p <secs>)
```
conky -p 20
```

---

### Post by patrickcage on 2013-03-17
> **Frogs Hair said:**
> This is what I use and the sleep delay time can be changed.  I use 10 to allow Compiz to start  . Just make it executable and add to start-up programs .

 ```
 #!/bin/bash
 sleep 10 && 
conky -c ~/.conkyrc;
```

Didn't work for me  :(

I'm running conky version 1.9.0

---

### Post by Frogs Hair on 2013-03-17
Once you create the text document in gedit name & save it to any folder you want . Open that location right click the document , go to Properties > Permissions and select the Execute check box and close. When  you add conky to startup applications   under command use browse to navigate the folder where the script is saved.  Select open and select save in the add to startup  application dialog box

---

### Post by Sector11 on 2013-03-17
It's interesting to see all the different problems with starting conky.  It's pretty straight forward really.

In a terminal
```
conky
```
... will start one of the following ***in this order:***
**[COLOR="#A52A2A"]1.[/COLOR]**  *${sysconfdir}/conky/conky.conf*  On most systems, sysconfdir is /etc, and you can find the sample config file there (**/etc/conky/conky.conf**).
**[COLOR="#A52A2A"]2.[/COLOR]**  User defined default file *$HOME/.conkyrc* or *~/.conkyrc* or */home/username/.conkyrc*

**$HOME/.conkyrc** being a user created custom "default" conky.

However a conky file can be anywhere and called just about anything:
[LIST=1]
[*]~/.conkyrc (user defaultt as seen above)
[*]~/myconky
[*]~/myconky-2
[*]/media/5/Conky/top-conky
[*]/media/5/Conky/bottom-conky
[*]/media/5/Conky/email-conky
[/LIST]

#2 through #6 can be started with: **conky -c /path/to/the conky** - ie:
[LIST]
[*]conky -c ~/myconky
[*]conky -c ~/myconky-2
[*]conky -c /media/5/Conky/top-conky
[*]conky -c /media/5/Conky/bottom-conky
[*]conky -c /media/5/Conky/email-conky
[/LIST]

Example bash scripts to start a conky come in various forms as seen in this thread.

There is also a script that can start a conky if it's not running - or stop it if it is running: [Start/Stop Conky]("http://conky.pitstop.free.fr/wiki/index.php5?title=Start/Stop_Conky_%28en%29") - and as you see in that sample - it can be used for "multiple conkys as well.

It can also be used for your "autostart"

Mine for OpenBox is: **S11_T2_SSC.sh** and it is the last command in my ~/.config/openbox/autostart.sh file
```
## Start Conky after a slight delay
(sleep 2s && /media/5/Conky/OBMenuS/S11_T2_SSC.sh) &
exit
```

**S11_T2_SSC.sh**
```
   #!/bin/bash
   # click to start, click to stop
if pidof conky | grep [0-9] > /dev/null
  then
	exec killall conky
  else

# on all desktops
	conky -c /media/5/Conky/S11_Email_1.conky &

# Start with low sleep and build up per desktop.
# on desktop 4 only
	(sleep 1s && wmctrl -s 3 && conky -c /media/5/Conky/mrp/conky3/conky3.conky) &

# on desktop 3 only
	(sleep 6s && wmctrl -s 2 && conky) &
	(sleep 6s && wmctrl -s 2 && conky -c /media/5/conky/Conky/conkymain) &
	(sleep 6s && wmctrl -s 2 && conky -c /media/5/Conky/S11_HUD3.conky) &

# on desktop 2 only
	(sleep 8s && wmctrl -s 1 && conky -c /media/5/Conky/S11_Dates.conky) &
	(sleep 8s && wmctrl -s 1 && conky -c /media/5/Conky/S11_VNS.conky) &
	(sleep 8s && wmctrl -s 1 && conky -c /media/5/Conky/S11_Rem_Cal.conky) &
	(sleep 8s && wmctrl -s 1 && conky -c /media/5/Conky/S11_Disk_Activity.conky) &

# on desktop 1 only
        (sleep 10s && wmctrl -s 0 && conky -c /media/5/Conky/S11_VSIDO_v9.conkyrc) &
        (sleep 10s && wmctrl -s 0 && conky -c /media/5/Conky/S11_Cal_br.conky) &
  exit
fi
```

---

### Post by patrickcage on 2013-03-18
I changed the delay in the script from 10 to 15 then to 20 - Conky now starts up as expected.

---

### Post by Sector11 on 2013-03-18
*[facepalm]***[COLOR="#FF0000"]Oops![/COLOR]***[/facepalm]*

Should have seen that coming.  Depending on the DE/WM there is a delay required for some in order to get the desktop drawn before conky starts.

---

