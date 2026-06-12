---
title: "Conky on startup"
date: 2011-07-08
forum: General Help
---

### Post by whatthefunk on 2011-07-08
Hi all.  Im trying to get Conky to run at startup.  I created a file called conky_start.sh in etc/init.d that looks like this:

```
#!/bin/sh

### Starts up Conky ###

sleep 30 && conky

```

Then did this to get it into startup:

```
sudo update-rc.d conky_start.sh defaults
```

It made it into the /etc/rc?.d files the home/.config/autostart file.  The file in the /etc/rc?.d file is a symbolic link to my original script and the home/.config/autostart file looks like this:
```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=Conky
Name[en_US]=Conky
Exec=/usr/bin/conky
Comment[en_US]=
StartupNotify=true

```

Conky still refuses to run at startup.  How can I solve this?  Thanks.

---

### Post by dino99 on 2011-07-08
you will find a nice config here:

[http://ubuntuforums.org/showthread.php?t=1771033](http://ubuntuforums.org/showthread.php?t=1771033)

---

### Post by whatthefunk on 2011-07-08
> **dino99 said:**
> you will find a nice config here:

[http://ubuntuforums.org/showthread.php?t=1771033](http://ubuntuforums.org/showthread.php?t=1771033)

Thats an excellent link and Ill definitely be reading that later, but it doesnt tell me how to get Conky to run at startup...

---

### Post by dino99 on 2011-07-08
> **whatthefunk said:**
> Thats an excellent link and Ill definitely be reading that later, but it doesnt tell me how to get Conky to run at startup...

Vindsl conky start itself as i know, follow its howto.

---

### Post by timgood on 2011-07-08
Did you make your script executable? 

```
chmod +x yourscript.sh
```

Once you have done that, then go to System/Preferences/Start Up Applications and click the 'Add' button. Navigate to your script. Conky should now start when you reboot. 

In my case my script to start Conky is:

```
sleep 25
/usr/bin/conky &
```

And in start up applications I have an entry for Conky that reads:

```
/home/tim/Documents/conky_start.sh
```

Hope this helps.

---

### Post by foutes on 2011-07-08
> **timgood said:**
> Did you make your script executable? 

```
chmod +x yourscript.sh
```Once you have done that, then go to System/Preferences/Start Up Applications and click the 'Add' button. Navigate to your script. Conky should now start when you reboot. 

In my case my script to start Conky is:

```
sleep 25
/usr/bin/conky &
```And in start up applications I have an entry for Conky that reads:

```
/home/tim/Documents/conky_start.sh
```Hope this helps.

+1

Looks like you forgot to make it executable.

---

### Post by whatthefunk on 2011-07-08
> **timgood said:**
> Did you make your script executable? 

```
chmod +x yourscript.sh
```

Once you have done that, then go to System/Preferences/Start Up Applications and click the 'Add' button. Navigate to your script. Conky should now start when you reboot. 

In my case my script to start Conky is:

```
sleep 25
/usr/bin/conky &
```

And in start up applications I have an entry for Conky that reads:

```
/home/tim/Documents/conky_start.sh
```

Hope this helps.

My script is executable.  Ive set the sleep time as high as 80 seconds and it still wont start.  My desktop is calm within about 30 seconds after login so it should definitely be starting after 80.  I use Lubuntu...there is no Add button on my Startup Applications window, so I tried via this:

```
lxshortcut -o ~/.config/autostart/conky
```

From there I tried both directing it to Conky and then directing it to my script.  Still no dice.

---

### Post by timgood on 2011-07-09
Try using the GUI

```
lxsession-edit
```

and point the start up item to your script.

---

### Post by whatthefunk on 2011-07-10
> **timgood said:**
> Try using the GUI

```
lxsession-edit
```

and point the start up item to your script.

On the Desktop Session Settings window, there is no way to enter a script.  All I have is a list of programs available for startup, check boxes for those programs, an OK button, and a cancel button.

---

### Post by timgood on 2011-07-11
I'm guessing that this may be a permissions issue as /etc/init.d is probably owned by root. Can you successfully run the script from a terminal to start conky? Open a terminal and navigate to where your script is and then:

```
./yourscript.sh
```

If conky launches, you know your script is OK. So now it's just a matter of finding the right way to run it in your OS.

Recreate your startup.sh file and save it to a directory in which you have read/write access (somewhere in your home directory would be good). Remember to make it executable. Then create a .desktop entry file inside .config/autostart (do this in your home directory) that looks something like this:


```
[Desktop Entry] 

Type=Application

Exec=/pathtoyourscript/script.sh
```

Reboot and see what happens.

Hope this helps.

---

### Post by whatthefunk on 2011-07-12
> **timgood said:**
> I'm guessing that this may be a permissions issue as /etc/init.d is probably owned by root. Can you successfully run the script from a terminal to start conky? Open a terminal and navigate to where your script is and then:

```
./yourscript.sh
```

If conky launches, you know your script is OK. So now it's just a matter of finding the right way to run it in your OS.

Recreate your startup.sh file and save it to a directory in which you have read/write access (somewhere in your home directory would be good). Remember to make it executable. Then create a .desktop entry file inside .config/autostart (do this in your home directory) that looks something like this:


```
[Desktop Entry] 

Type=Application

Exec=/pathtoyourscript/script.sh
```

Reboot and see what happens.

Hope this helps.

Thanks for the help timgood, but it still isnt working.  I saved my script in the home directory and directed my .config/autostart file to go there, but it still isnt opening up.  I cant for the life of me figure out what is going on.  I have a couple other scripts that I run at startup up and they work fine.  Its driving me crazy!!!

---

### Post by timgood on 2011-07-12
Can you launch your script from a terminal? Does it work?

---

### Post by whatthefunk on 2011-07-12
Yes, the script works in the terminal.  My autostart config file looks like this:

```

[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=Conky
Exec=/home/zachleigh/Scripts/conkystart.sh
StartupNotify=true

```

The file is executable and the folder Scripts in my home file is set as a path for executable files in .bashrc.

---

### Post by Frogs Hair on 2011-07-12
Originally posted by ManualSparrow.

Re: Autostart
 You can autostart via script by creating a blank file and renaming it conky_start in your home directory. Right-click>Permissions>Allow Executing File as a Program>Check yes.

 Open the file, paste this inside:

Code:
#!/bin/bash
 sleep 10 && 
conky -c ~/.conkyrc;
Go to System>Startup Applications and click the + or Add button. Browse to the conky_start file (which should be in the home folder, path ~/conky_start) and click ok. Now this script should run on startup and after ten seconds start conky. This lets other things load first, such as compiz.
 If that doesn't work and you are only using a single config file .conkyrc in the home folder, try using 
Code:
#!/bin/bash
 sleep 10 && conky;
 in conky_start instead. If you do want to use more than one conky (ie, start more than one conky window) you can add start them all at the same time 
Code:
#!/bin/bash
 sleep 10 && 
conky -c ~/.conky1;
conky -c ~/.conky2;
conky -c ~/.conky3
etc. Just note that 
 a) you need to get the path to the files right (in this case they would all be in the home folder and hidden, as per the added '.') 
 b) it doesn't matter what you call the files if you use the longer versions - putting 
Code:
conky -c PATH/TO/FILENAME
 will start it up.

---

### Post by whatthefunk on 2011-07-13
> **Frogs Hair said:**
> Originally posted by ManualSparrow.

Re: Autostart
 You can autostart via script by creating a blank file and renaming it conky_start in your home directory. Right-click>Permissions>Allow Executing File as a Program>Check yes.

 Open the file, paste this inside:

Code:
#!/bin/bash
 sleep 10 && 
conky -c ~/.conkyrc;
Go to System>Startup Applications and click the + or Add button. Browse to the conky_start file (which should be in the home folder, path ~/conky_start) and click ok. Now this script should run on startup and after ten seconds start conky. This lets other things load first, such as compiz.
 If that doesn't work and you are only using a single config file .conkyrc in the home folder, try using 
Code:
#!/bin/bash
 sleep 10 && conky;
 in conky_start instead. If you do want to use more than one conky (ie, start more than one conky window) you can add start them all at the same time 
Code:
#!/bin/bash
 sleep 10 && 
conky -c ~/.conky1;
conky -c ~/.conky2;
conky -c ~/.conky3
etc. Just note that 
 a) you need to get the path to the files right (in this case they would all be in the home folder and hidden, as per the added '.') 
 b) it doesn't matter what you call the files if you use the longer versions - putting 
Code:
conky -c PATH/TO/FILENAME
 will start it up.

I use Lubuntu...my Desktop Session Settings window does not have an Add button.

---

### Post by Quackers on 2011-07-13
I don't use lubuntu but I wouldn't have thought there would be any difference.
What is Desktop Sessions Settings?
This is my .conky_start.sh ```
#!/bin/bash
sleep 20 && conky;
``` which is a hidden file in my home folder.
Then go to Startup Applications and select ADD then put a name in the first field (mine is conky) then from the second field browse to your home folder, hit ctrl+h to show hidden files and double-click on your .conky_start.sh file.
That starts conky for me every time :-)

---

### Post by whatthefunk on 2011-07-13
> **Quackers said:**
> I don't use lubuntu but I wouldn't have thought there would be any difference.
What is Desktop Sessions Settings?
This is my .conky_start.sh ```
#!/bin/bash
sleep 20 && conky;
``` which is a hidden file in my home folder.
Then go to Startup Applications and select ADD then put a name in the first field (mine is conky) then from the second field browse to your home folder, hit ctrl+h to show hidden files and double-click on your .conky_start.sh file.
That starts conky for me every time :-)

Guys.  Please understand that there is no Startup Applications window in Lubuntu.  There is a Desktop Session Settings window with a list of startup applications to choose from but no way to add a new startup application.  There is no ADD button.  There is no plus sign.  There is an OK button and a Cancel button.  That is all.

I need either a LDXE specific solution or a command line solution.

---

### Post by timgood on 2011-07-13
I must confess that I am a little nonplussed as all the lubuntu stuff on google suggests that your solution should work. As I don't use lubuntu, I can't experiment myself. Sorry.

Where and in what folder is your .desktop entry?

You could try this:

```
gksu gedit /etc/rc.local
``` (or in your case use a more lubuntu specific editor)

Add the line

```
/home/zachleigh/Scripts/conkystart.sh
```

before the exit 0

Save and reboot. What happens?

---

### Post by whatthefunk on 2011-07-13
Got it.  With LXDE, you first have to make a .desktop file in /usr/share/applications then copy that file into home/username/.config/autostart  The system seems to be picky about these two files so it takes a lot of messing around to get it right.  Thanks for the help timgood.

---

### Post by breezypt on 2013-05-02
[**[COLOR=#000000]timgood[/COLOR]**]("http://ubuntuforums.org/member.php?u=186361") ~ That script works perfect for me.....Thanks much! Needs a little tinkering but its almost there for what I need it for:
[IMG]http://img703.imageshack.us/img703/9059/mayascriptconky.png[/IMG]

---

