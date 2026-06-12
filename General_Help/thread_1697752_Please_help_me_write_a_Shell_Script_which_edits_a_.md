---
title: "Please help me write a Shell Script which edits a Config file!"
date: 2011-03-01
forum: General Help
---

### Post by dancapp on 2011-03-01
Can someone help me write some simple script? Here’s what I’m trying to do:

-	Qjackctl has a config file which is modified each time QjackCtl is shut down. This means that whatever preset is in use when QjackCtl closes is written into the QjackCtl config file as the DEFAULT PRESET, for the next time QjackCtl starts (or at least this is how I understand it).

-	I want to edit a specific line in the QjackCtl.config file, which specifies the DEFAULT PRESET. Obviously it’s easy to do manually, but I want to do it using a shell script which runs automatically on StartUp so that QjackCtl starts every time with the same DEFAULT PRESET, NOT the last one used.

-	Unfortunately I’m not at my Linux system right now (which is KXStudio/Kubuntu), but I believe the QjackCtl.config line looks something like this:
**DEF_PRESET=alsa** (where “alsa” is the name of the preset)
[B]PRESET1=alsa
PRESET2=firewire[/B]

I want a shell script which changes the line **“DEF_PRESET=alsa”** to **“DEF_PRESET=alsa”**, even when it may currently exist as **“DEF_PRESET=firewire”** due to occasions when “firewire” was the active preset when Qjackctl was last closed. I notice that the application in KDE that enables the user to set which applications open automatically on StartUp also allows the user to select shell scripts.

I’ve done some research, as a beginner, and I’m led to believe I might need to use AWK and/or CHMOD. I could have a go at writing a shell script but I’m always wary about experimenting with StartUp scripts/operations because obviously if I get it wrong and make my system unusable, then because it’s going to run first thing on each boot, I’d have great difficulty disabling it.

Any help or advice hugely appreciated! Remember – I’m a total beginner looking to gain an understanding. But if anyone feels like writing  the script for me I won’t object ;).

---

### Post by TeoBigusGeekus on 2011-03-01
```
sed -i 's/DEF_PRESET=firewire/DEF_PRESET=alsa/g' /path/QjackCtl.config
```

---

### Post by nothingspecial on 2011-03-01
```
sed 's/DEF_PRESET=firewire/DEF_PRESET=alsa/' /path/to/config
```

edit - beat to it

---

### Post by DaithiF on 2011-03-01
slightly more generically -- in case there are more possibilities than firewire:

```
sed -i '/DEF_PRESET=.*/s//DEF_PRESET=alsa' /path/to/file
```

or, for variety, using ed:

```
echo -e "/DEF_PRESET/s/=.*/=alsa/\nwq\n" | ed /path/to/file
```

---

### Post by SeijiSensei on 2011-03-01
Another option is to make the file read-only using chmod so the application can't overwrite it.

```
chmod a-w /path/to/QjackCtl.config
```

---

### Post by dancapp on 2011-03-01
> **DaithiF said:**
> slightly more generically -- in case there are more possibilities than firewire:

```
sed -i '/DEF_PRESET=.*/s//DEF_PRESET=alsa' /path/to/file
```
Ah yes, because the DEF_PRESET won't always have been saved as "firewire". There will be times when I'll shut QjackCtl down when the "alsa" preset is active. So the script needs to be able to alter the DEF_PRESET line to "DEF_PRESET=alsa" whether it already exists as "DEF_PRESET=alsa" or whether it's "DEF_PRESET=firewire".

This is what you're getting at right? I'll give it a go and report back.

Huge thanks everyone! :D

---

### Post by dancapp on 2011-03-01
Unfortunately it didn't work. I'm sure it's something I'm doing wrong. This is the script I wrote:

```
sed -i '/DefPreset=.*/s//DefPreset=alsa' /usr/config/rncbc.org/QjackCtl.conf
```I wrote it using kate and saved it as an "sh" file. Is this correct? The file icon is the same as the other startup shell script files.

This is the error message I got when restarting my computer:

> Error launching /usr/share/applications/kde4/kate.desktop. Either KLauncher is not running anymore, or it failed to start the application.


Any ideas?

---

### Post by TeoBigusGeekus on 2011-03-01
Have you made it executable?
```
chmod +x /path/scriptname
```

---

### Post by dancapp on 2011-03-01
> **TeoBigusGeekus said:**
> Have you made it executable?
```
chmod +x /path/scriptname
```
No. Please forgive my beginner-ness.

Do I just type the above as a one-off in terminal?

Also, it just occured to me - when you're specifying paths in a script, do you include the "." before hidden folders? e.g. 

/usr/.config/rncbc.org/QjackCtl.conf

---

### Post by TeoBigusGeekus on 2011-03-01
> **dancapp said:**
> 
Also, it just occured to me - when you're specifying paths in a script, do you include the "." before hidden folders? e.g. 

/usr/.config/rncbc.org/QjackCtl.conf

Yep.

---

### Post by wormyblackburny on 2011-03-01
If you wrote it as a shell script using a text editor did you remember that the first line needs to be:

#! /bin/bash

---

### Post by dancapp on 2011-03-01
> **wormyblackburny said:**
> If you wrote it as a shell script using a text editor did you remember that the first line needs to be:

#! /bin/bash
No, and thank you. I really am a beginner ;).

---

### Post by dancapp on 2011-03-01
> **TeoBigusGeekus said:**
> Have you made it executable?
```
chmod +x /path/scriptname
```
Terminal keeps telling me:

> chmod: cannot access `/usr/.kde/env/myscript.sh': No such file or directory


---

### Post by SeijiSensei on 2011-03-01
/usr/.kde is a very unusual directory because the dot before "kde" makes the directory "hidden."  I take it you haven't installed this software from the Ubuntu repositories.  The set of directories below /usr in the Linux [Filesystem Hierarchy Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure") is strictly defined.  /usr/.kde certainly does not conform to the standard.

I doubt the file is where you think it is.  Run "locate qjackctl" to find all the files with that string in their names.  I'm guessing it's in $HOME/.kde/env.

---

### Post by dancapp on 2011-03-01
> **SeijiSensei said:**
> You need to use sudo.  You can't edit any files without it except for ones you create yourself in your home directory, /tmp, or mounted devices to which you have permissions.

```
sudo /usr/.kde/env/qjackctl-alsa-preset.sh
```
So... 

```
chmod +x /usr/kde/env/myscript.sh
```
Thanks but I already tried that. "Sudo" is the one thing I have picked up so far ;)

---

### Post by wormyblackburny on 2011-03-01
Ok, lets just start over from the beginning since it will be easier. First, there is no need to put that script where the program files reside. Open a terminal and do this:

cd ~
mkdir myscripts
cd myscripts
gedit qjackfix.sh

that should open up a blank text document in which you will type:

#! /bin/bash
sed -i 's/DEF_PRESET=firewire/DEF_PRESET=alsa/g' /path/QjackCtl.config  [U][B]<<remember to replace that with the full path to the conf file!!

[/B] [/U] Now save and close it. In terminal type:

chmod +x qjackfix.sh

now go to system>>administration>>startup programs and add it. the new path will be /home/(your-username)/myscripts/qjackfix.sh

Is the myscripts folder really necessary? No, you could create the file on your desktop, but what if in the future you want to modify it and you cant remember where you put the script? Just use this folder to keep all of your personal scripts so they are easy to keep track of....

---

### Post by wormyblackburny on 2011-03-01
Just occurred to me that the conf file is probably owned by root, so you may want to sudo chmod 777 qjack.conf on the conf file just in case so that the script has permission to write to the conf file. I would assume that the startup programs would run the script as root, but I'm not 100% positive. Anyone know for sure? Seems like that would be a pretty big security liability to have root running the startup scripts, and since the startup programs is customizable for each user, it is probably run at a user level...

---

### Post by dancapp on 2011-03-01
> **wormyblackburny said:**
> Just occurred to me that the conf file is probably owned by root, so you may want to sudo chmod 777 qjack.conf on the conf file just in case so that the script has permission to write to the conf file. I would assume that the startup programs would run the script as root, but I'm not 100% positive. Anyone know for sure? Seems like that would be a pretty big security liability to have root running the startup scripts, and since the startup programs is customizable for each user, it is probably run at a user level...
I haven't given your previous advice a go yet, but thought I'd apply what you say here to the script I've set up based on previous replies. It didn't help I'm afraid.

---

### Post by dancapp on 2011-03-01
SOLVED! :D

After experimenting with everyone's suggestions I decided to take a different approach. Rather than trying to edit the QjackCtl config file so that the "DefPreset" (default preset) was reset back to "alsa" each time the system starts up, I remembered a command someone in the Linux-Audio-User mailing list suggested:

```
qjackctl -p alsa
```*"Start QjackCtl with the preset called 'alsa'"*

Surely it would be too simple to simply put just this in the shell script file, but I gave it a shot and it works!!!!

The QjackCtl config file does still show whatever the last used preset in QjackCtl was as being default, but it now doesn't necessarily load it. Instead it always starts QjackCtl with the preset "alsa". For anyone else wanting to use this method, make sure you do the following:

- Get rid of any previous settings which cause QjackCtl to startup automatically on system startup. 
- The above script is the only auto-start command needed and it should go in a shell script file which is specified in "Autostart", and set the "Run On" option to "Startup", **not** "Shutdown" or Pre-KDE startup".
- In QjackCtl settings, you can enable "start JACK audio server connection on application startup" to not only have QjackCtl load with a particular preset, but to start the audio server straight away, seamlessly with that preset too.
- My preset is called "alsa". Remember to change that to whatever you named your desired default preset as.

Hope this helps someone else and thanks to everyone in this thread for getting me to the solution.

---

