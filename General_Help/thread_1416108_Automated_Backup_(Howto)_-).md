---
title: "Automated Backup (Howto) :-)"
date: 2010-02-25
forum: General Help
---

### Post by d3v1150m471c on 2010-02-25
This is for kubuntu but the same can be done with ubuntu. I will tell you how.

You'll need 2 tools for this. 1 is for security, and the other you will already have onboard.

Tools:
1. shc-3.8.6  [B][Click Here To Download SHC]("http://softwaredownloadmirror.com/shareware/shc-3.8.6/9519460")
[/B]2 Any text editor (kate, gedit, vi, nano)

Open up your text editor and input the following text below. Adjust the fields in red to your liking. where it says "yourpasswordhere" you're going to put your user password.
The first red path is the path you will copy from and the second is where you will copy to. The red input following "sleep" is how often it will backup your files.
```

#!/bin/bash
sleep 30
echo '[COLOR=Red]yourpasswordhere[/COLOR]' | sudo -S rsync -a -v /[COLOR=Red]home[/COLOR] /[COLOR=Red]media/disk/[/COLOR] > ~/backup.log
sleep [COLOR=Red]30[/COLOR]m
~/.kde/Autostart/.backup.x
exit 0

```Now save the file as [COLOR=Red]backup[/COLOR]
Now go and extract shc-3.8.6 from it's tar ball. Open up a terminal and navigate to it.
```

cd ~/Downloads/shc-3.8.6

```Now that you're inside the shc folder you're going to do the following:
```

shc -f /path/to/[COLOR=Red]backup[COLOR=Black]
[/COLOR][/COLOR]
```[COLOR=Red][COLOR=Black]
shc will compile the script you just saved and encrypt it. It will also make it so that it only works on your machine. This is very important because it contains your password. However, it is compiled to binary so the file will no longer be legible. shc will spit out the new binary executable as [COLOR=Red]backup.x[COLOR=Black] in the same directory as [COLOR=Red]backup[/COLOR] (remember this)[/COLOR][/COLOR] :-)

Next we're going to delete the old [COLOR=Red]backup [COLOR=Black]script you created. Make sure you empty your trash can afterwards. Now open up dolphin and press alt+. (alt plus the period symbol)
This will allow you to see hidden files. Navigate to .kde/Autostart/ and move [COLOR=Red]backup.x [COLOR=Black]
inside this folder. Now we are going to rename [COLOR=Red]backup.x [COLOR=Black]to .backup.x so that it is hidden. (all i did was add a period to the beginning of the name). Now all you have to do is logout and log back in for the script to run. The new backup service will update the specified path with the files inside the source path you made on the script and leave a log that you can read in your home folder every so often for the increments you specified.

Now...For ubuntu directions first read the kubuntu directions so you have a clear understanding to what I'm doing. Next you're going to make the script as:
```

#!/bin/bash
sleep 30
echo '[COLOR=Red]yourpasswordhere[/COLOR]' | sudo -S rsync -a -v /[COLOR=Red]home[/COLOR] /[COLOR=Red]media/disk/[/COLOR] > ~/backup.log
sleep [COLOR=Red]30[/COLOR]m
/[COLOR=Red]path/to/[/COLOR].backup.x
exit 0

```Follow all the above directions for converting the script over to an encrypted binary.
Now, navigate to system>preferences>startup applications and create a new startup process. For the command you're simply going to put the path you saved [COLOR=Red].backup.x[COLOR=Black] to.[/COLOR][/COLOR]


[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]

---

