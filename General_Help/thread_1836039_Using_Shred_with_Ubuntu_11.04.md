---
title: "Using Shred with Ubuntu 11.04"
date: 2011-08-30
forum: General Help
---

### Post by Panawe on 2011-08-30
I've been trying to get Shred to work with Ubuntu 11.04. Googled and installed Nautilus 3.1.2 but I can't seem to get Shred working on my right-click. 
Can anyone help?

---

### Post by Enigmapond on 2011-08-30
Have you installed 'Nautilus-Actions"? It used to be "Nautilus-actions-configuration" in every distro prior to Natty...You need this to set the parameters.

---

### Post by seawolf167 on 2011-08-30
[Here is how ]("https://help.ubuntu.com/community/NautilusScriptsHowto")you can add scripts to your right-click 'scripts' context menu.

---

### Post by Panawe on 2011-08-31
> **Enigmapond said:**
> Have you installed 'Nautilus-Actions"? It used to be "Nautilus-actions-configuration" in every distro prior to Natty...You need this to set the parameters.

Yes, I believe so. I tried working with Nautilus Actions but I kept getting an error message when I tried to save it.

---

### Post by Panawe on 2011-08-31
> **seawolf167 said:**
> [Here is how ]("https://help.ubuntu.com/community/NautilusScriptsHowto")you can add scripts to your right-click 'scripts' context menu.
  Don't know much about scripting language and there doesn't seem to be one ready made :(

---

### Post by seawolf167 on 2011-08-31
Your script can be super simple, something like

```
#!/bin/bash
shred *-add you options here*
```

---

### Post by Panawe on 2011-08-31
> **seawolf167 said:**
> Your script can be super simple, something like

```
#!/bin/bash
shred *-add you options here*
```

Okay, I create this as a text document and save it in the nautilus directory? What's the file extension?

---

### Post by seawolf167 on 2011-08-31
Create and open your script for editing

```
touch name-of-script
gedit name-of-script
```

Write your script (see previous post - make sure to add your options you want), save and close the file

Mark the script as executable

```
sudo chmod +x name-of-script
```

Move the script to the required directory as per the previous link

```
mv name-of-script ~/.gnome2/nautilus-scripts
```

Read the note on the link provided:

"***Note:*** *Once you place a script in your  scripts directory, it's name will not necessarily appear in the scripts  menu immediately. You might have to visit the scripts directory with  Nautilus - which can be done using the last option in the scripts menu.  Once the directory is visited, Nautilus will know about which scripts  you have, and you will be able to use them."*

---

### Post by Panawe on 2011-08-31
> **seawolf167 said:**
> Create and open your script for editing

```
touch name-of-script
gedit name-of-script
```Write your script (see previous post - make sure to add your options you want), save and close the file

Mark the script as executable

```
sudo chmod +x name-of-script
```Move the script to the required directory as per the previous link

```
mv name-of-script ~/.gnome2/nautilus-scripts
```Read the note on the link provided:

"***Note:*** *Once you place a script in your  scripts directory, it's name will not necessarily appear in the scripts  menu immediately. You might have to visit the scripts directory with  Nautilus - which can be done using the last option in the scripts menu.  Once the directory is visited, Nautilus will know about which scripts  you have, and you will be able to use them."*

Hi, done that. Now, when I select a file and right click I have a scripts entry in the drop-down menu which holds "Shred" - but when I left-click on it nothing happens.

---

### Post by seawolf167 on 2011-08-31
In your shred script you need to define the file with your options.

So go back and edit your script, then after all your options that you defined from

```
man shred
```you need to define the file name, i.e.

*shred [OPTION]... **FILE**...*

to do this with a right-click script as per the previous link, your file is defined as

$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS

add that and you should be good to go

---

### Post by Panawe on 2011-08-31
> **seawolf167 said:**
> In your shred script you need to define the file with your options.

So go back and edit your script, then after all your options that you defined from

```
man shred
```you need to define the file name, i.e.

*shred [OPTION]... **FILE**...*

to do this with a right-click script as per the previous link, your file is defined as

$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS

add that and you should be good to go

I defined the options in the Shred script but not the file! I want to be able to use it on files and folders by right-clicking. Forgive my ignorance, there's something I'm not getting here.

---

### Post by seawolf167 on 2011-08-31
You can't explicitly define the file, since as you mention, you will not be using it on only one hard-coded file/folder. Instead, you have to use the nautilus path (since nautilus is handling the script functions of right-clicking and defining the path for the selected item). This path is the variable previous posted which is defined once you select (highlight) items in the window.

---

### Post by cipherboy_loc on 2011-08-31
Script that works:

```

#!/bin/bash

OPTIONS='-n 5 -z'

if [ -e $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ]; then
    if [ ! -d $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ]; then 
    shred $OPTIONS $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
    fi
fi

```

Change OPTIONS (at the top of the script) to suit your needs.



Cipherboy

---

### Post by seawolf167 on 2011-08-31
Could you clean that up to:

```
#!/bin/bash
OPTIONS='your-options-here'
if [ -e && ! -d $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ]; then
shred $OPTIONS $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
fi
```

?

---

### Post by cipherboy_loc on 2011-08-31
Yep. Sorry about that. You could also add symbolic link checking. 


Cipherboy

---

### Post by Enigmapond on 2011-08-31
Nautilus actions is the easiest way...OMHO. the parameters are as follows:

Path = /user/bin/find

Parameters =  %M -type f -exec shred -f -u -z '{}' \;

Then make sure that you choose both files and folders, save, logout/in...done.

The only drawback here is it, for some reason, won't delete the actual folder it will delete only the content..even if multiple folders exist inside one folder. It will delete only the content of them all and leave the folders then just delete the folders.

---

### Post by Panawe on 2011-08-31
> **seawolf167 said:**
> Could you clean that up to:

```
#!/bin/bash
OPTIONS='your-options-here'
if [ -e && ! -d $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ]; then
shred $OPTIONS $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
fi
```?

Done that, went through touch/gedit/chmod/mv process outlined earlier, still not working.

---

