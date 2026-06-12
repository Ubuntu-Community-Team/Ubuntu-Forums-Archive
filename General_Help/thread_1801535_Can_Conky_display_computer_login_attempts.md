---
title: "Can Conky display computer login attempts?"
date: 2011-07-10
forum: General Help
---

### Post by In2Blues on 2011-07-10
I think someone has been in my apartment when I'm at work and attempted to login to my computer.

Rather than searching through all the logs, is there any way for Conky to display the last 2 or 3 login attempts?

I've searched high and low and can't find an answer.

Thanks in advance.

---

### Post by Habitual on 2011-07-10
Terminal > 
```
grep 'Failed password' /var/log/auth.log | tail -3
```

and yes, conky can do this via a shell script but so can zenity via a GUI'ish (gnome-ish) popup dialog box. Like this one -> [http://susepaste.org/54315218](http://susepaste.org/54315218)

```
var1=$(grep 'Failed password' /var/log/auth.log | tail -3)
zenity --info --text="$var1"
```

add a !shebang to a file and chmod 700 it and you have a dialog that you can stick on the desktop. 

zenity should already be installed on your box.
This same code can be use for a conky rc file, if you know how...

What is your conky experience level?

---

### Post by In2Blues on 2011-07-11
Thanks for the info, Habitual.

I'm very new to Conky (new to Linux, in fact).  I've gotten some rc files, mixed and matched, and played around with the settings until I have a nice layout, but don't have experience with shell scripts, etc.  I'm learning more each time I want to do something, though. :D

---

### Post by Habitual on 2011-07-12
in2blues:

Fire up gedit or another editor and add this content:
```
#!/bin/bash
var1=$(grep 'Failed password' /var/log/auth.log | tail -3)
zenity --info --text="$var1"
```

Save it as say ~/knockknock.sh 
(The ~ designation is a "alias" for your /home/x directory and means /home/$YourUserName)

Once saved, open Terminal and type ```
chmod 700 ~/knockknock.sh
``` and exit the terminal with ```
exit
```

Right mouse click on the desktop and create a new launcher and point it at /home/$YourUserName/knockknock.sh for the "Command" entry of the new launcher.

Tada! Icon launcher for the above code that runs in a nice and neat dialog box. (you could even make this autostart, so you'd see it every time you logged in to your machine) ;)

HTH.

When you're more comfortable with Linux/conky you can add this code to a conky rc:
```
${execi 60 //home/$YourUserName/knockknock.sh}
```

---

### Post by In2Blues on 2011-07-12
Thanks for your help.

I followed your instructions exactly and the script works.  Very nice.

I tested it, but all I get is a popup box with a lightbulb in it.  I thought maybe it was because there were no failed login attempts, so I logged out and tried to login again with the wrong password.  After logging in properly, I got the same lightbulb.

I also was able to put the code in my conkyrc file, but got the same box (I guess because all conky did was run the same script).  For my purposes, autorunning the script is better, unless I could get conky to display the date and time of failed logins.

So, what about the lightbulb in the box?  Is this normal?

---

### Post by Habitual on 2011-07-12
In2Blues:

Sorry about that, but I think you may need sudo privs to peek at /var/log/auth.log.
I work with sudo privs so I generally miss little details like that.

To test that brain-fart, you can try this from terminal >
```
gksudo /home/$YourUserName/knockknock.sh
```

tell me if that works.

Edit:

I changed/altered/shortened the previous instructions.

---

### Post by In2Blues on 2011-07-14
Hi Habitual.

I tried it and got the same lightbulb box as before.

---

### Post by Habitual on 2011-07-14
Bummer.

Terminal> 
```
sudo grep 'Failed password' /var/log/auth.log | tail -3
```
give you an output about failed logins?

The bottom line is that I don't think conky utilizing a script can access /var/log/auth.log without sudo privs. Are you the sole "user" on this system? We could add your userid to the sudoers file and then the script should work w\out issue.

Someone else here may have another idea. Sorry.

---

### Post by In2Blues on 2011-07-14
No need to apologize.  I appreciate your help.

When I entered your latest code, I got this output in the terminal:

> Jul 14 16:57:10 terry-desktop sudo:    terry : TTY=pts/0 ; PWD=/home/terry ; USER=root ; COMMAND=/bin/grep Failed password /var/log/auth.log 
Jul 14 16:58:17 terry-desktop sudo:    terry : TTY=pts/0 ; PWD=/home/terry ; USER=root ; COMMAND=/bin/grep Failed password /var/og/auth.log 
Jul 14 16:58:48 terry-desktop sudo:    terry : TTY=pts/0 ; PWD=/home/terry ; USER=root ; COMMAND=/bin/grep Failed password /var/log/auth.log
After I restarted my computer, the same thing appeared in the lightbulb box.

I'm the only regular user on my system.  My wife uses it for a particular program occasionally, but she doesn't touch anything she's unfamiliar with.

---

### Post by Habitual on 2011-07-14
Terry: Forget the lightbulb (or accept that it's not working as intended) *for now*, ok?

I need to stand back and think about this. Once I "get out of the forest, I shall be able to see the tree" if you get my drift.

I am uncertain because on my 10.10 LTS Ubuntu VM I am now removed from the sudoers file but I can still grep the /var/log/auth.log file here without a (sudo) password...

Run this command and give me the output:
```
lsb_release -dr
```

JJ

---

### Post by In2Blues on 2011-07-15
This is what I got.

> Description:    Ubuntu 10.10
Release:    10.10


---

### Post by Habitual on 2011-07-16
Installling Ubuntu 10.10 Desktop now in a VM for debugging purposes....

Please stand by for an update.. :)

---

### Post by Habitual on 2011-07-16
Terry:
Change the knockknock.sh script to this:
```

#var1=$(grep 'Failed password' /var/log/auth.log | tail -3)
#zenity --info --text="$var1"
zenity --info --title="Echo:" --text "`echo $(egrep -i "authentication failure|error retrieving information about user"  /var/log/auth.log|tail -3)`"

```

See if that produces output in the form of a dialog box on the screen. (Not conky)

JJ

---

### Post by In2Blues on 2011-07-17
OK, I changed knocknock.sh and attempted to login again.  Twice I entered wrong passwords, and the third time the correct one.  I figure it should display the fact that someone tried to log into my system.

Here's what I got:

> Jul 14 17:43:55 terry-desktop gdm-session-worker[1541]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= user=terry Jul 16 22:22:03 terry-desktop gdm-session-worker[1555]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= user=terry Jul 16 22:22:09 terry-desktop gdm-session-worker[1663]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= user=terryTo be honest, I'm not sure what this means. :oops:

It looks like it's showing failed login attempts, especially the two I just tried.  Am I right?

---

### Post by Habitual on 2011-07-17
Terry:

That is exactly what it is showing you. 3 failed login attempts for user Terry.
the "error retrieving information about user " would be someone trying to login with a different username (that doesn't exist).


Here is what is looks like on my VM (see attachment).
The first field is the date and that is the record separator for the data shown.

So from Jul 16 hh:mm:ss to the next entry of Jul 16 hh:mm:ss is one record.

JJ

---

### Post by In2Blues on 2011-07-18
Excellent.  Just what I need.  Now I'll be able to tell if someone has tried to access my system when I'm not home.

Thanks for all your help, JJ.

---

### Post by Habitual on 2011-07-18
Terry:

No problem!
Glad it worked out.

JJ

Edit:
If you want 'formatted' output just run 
```
egrep -i "authentication failure|error retrieving information about user"  /var/log/auth.log|tail -3
```

in a terminal.

---

