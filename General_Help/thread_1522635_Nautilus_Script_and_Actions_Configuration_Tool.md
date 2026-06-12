---
title: "Nautilus Script and Actions Configuration Tool"
date: 2010-07-02
forum: General Help
---

### Post by XenosD on 2010-07-02
Hello friends,
I've recently installed Nautilus Actions Configuration Tool (NACT), because I was interested in adding some more entries in my right click context menu. I've downloaded and installed successfully several nautilus actions. However, I'd like to add a script in the right-clicked menu. I know that the easiest way is to put the script in the " ~/.gnome2/nautilus-scripts" directory, but I'd like to add it  through NACT, because NACT can set script to appear only for certain type of file (for example only for folders). Also, through NACT I can add icon for the action, so that I can distinguish the action quickly.
The script is called "open file location" (download link: [http://pastebin.ubuntu-gr.org/pastebin.php?dl=f65463bb9](http://pastebin.ubuntu-gr.org/pastebin.php?dl=f65463bb9)) The main problem is that I don't know which parameters to add, so that the command functions correctly.
Can anybody make it function?
Thank you in advance.

I use Ubuntu 10.04 and NACT 2.30.2

---

### Post by gzarkadas on 2010-07-02
The script as is cannot work with nautilus-actions because nautilus-actions scripts do not use the NAUTILUS_... env. variables.

Since from what I see, the script opens the folder containing the first item of the selection (or the first item if it is a directory), this script should do the same job in nautilus-actions (at least for the standard filesystem).
```

#!/bin/bash
#Licence GPL v3 or (at your option) any later, as published by the FSF.
[ $# -ge 1 ] || exit 1
target="${1}"
if [ -h "${1}" ] ; then
    target="$(readlink \"${1}\")" 
fi
if [ -f "${target}" ] ; then
    target="$(dirname \"${target}\")"
fi
nautilus "${target}"

```Now, save it anywhere (I would suggest making a bin directory in your home folder, add it to your path in ~/.bashrc and put the script and all of your other scripts there) and make it executable, either by right-clicking, selecting `Properties' and checking the run checkbox in tab `Rights' or by typing `chmod u+x <filename>' inside a terminal window.

Then add the corresponding item in nautilus-actions. Put: 

[LIST]
[*]`<filename>' as `Path' and `%M' as `Parameters' (tab `Action');
[*]`*' in `Filenames', `*/*' in `Mime Types' and `Both' in `Apears if...' (tab `Conditions'.
[/LIST]
Oh, and don't forget to set the icon :).

---

### Post by XenosD on 2010-07-03
Thanks for the response, but the script you gave me does not function properly.
The script I use, is mainly used for links and search results in order to open the parent directory of the original file (or folder). 
Your script does not function at all. I followed your instructions and I added the action to the right-click menu (I named it "Open Containing Folder"). 
When I right click a link or a search result and I run the action, it always opens my home directory(~).
I also added the script in the "~/.gnome2/nautilus-scripts" directory and I launched script by right-clicking and choosing scripts>Open Containing Folder.
However, it gives error for search items and for links it opens the folder of the link, not the folder of the actual file.
I found this post which is closer to give the solution ([http://ubuntuforums.org/showpost.php?p=8490250&postcount=13](http://ubuntuforums.org/showpost.php?p=8490250&postcount=13))
This action works perfectly for search items, but there is problem with links. It opens like yours, the folder of the link, not the folder of the actual file.
I think that %d parameter which is used in this post, is not enough.
Anyway, thank you a lot for the interest.

---

### Post by gzarkadas on 2010-07-03
Yes, there are some surplus double quotes that escaped debugging :shock:. Anyway, this is easy to fix, so here is a version that works; I added one more check to address relative symlinks.
```

#!/bin/bash
#Licence GPL v3 or (at your option) any later, as published by the FSF.
[ $# -ge 1 ] || exit 1
target="${1}"
if [ -h "${1}" ] ; then
    target=$(readlink "${1}")
    if [ "${target:0:1}" != "/" ] ; then
        target=$(echo $(dirname "${1}")/"${target}" | sed 's_//_/_g')
    fi
fi
if [ -f "${target}" ] ; then
    target=$(dirname "${target}")
fi
nautilus "${target}"

```

---

### Post by XenosD on 2010-07-03
Wow, you seem to be an expert in nautilus actions! 
The nautilus action functions exactly the same as the script I was using so far.
Thank you a lot.
Maybe you could fix and a minor bug that I experience.  
This bug does not occur only in the nautilus script you created, but also occurred in the first script (open file location) I was running so far.
The bug is that if a link has a different name from the original file/folder, then it is not possible to distinguish which is the original file/folder in the parent directory.
In Windows Vista when the user runs the same command, the original file is automatically checked in the opened parent directory, so it is easy to find it.
If it is possible and not time-consuming for you, please fix it, so that the original file is automatically checked.
Anyway, thank you very much!

---

### Post by gzarkadas on 2010-07-04
I think that this is not actually a bug; it is a limitation of scripting extensions. The task of selection inside nautilus window needs a nautilus extension; a script is not enough. 

However, a similar and easy to implement approach is to show a zenity dialog with the name of the file for 3 seconds (to avoid having to manually close the popup; you may edit this value to your preferences). 

```

#!/bin/bash
#Licence GPL v3 or (at your option) any later, as published by the FSF.
[ $# -ge 1 ] || exit 1
target="${1}"
if [ -h "${1}" ] ; then
    target=$(readlink "${1}")
    if [ "${target:0:1}" != "/" ] ; then
        target=$(echo $(dirname "${1}")/"${target}" | sed 's_//_/_g')
    fi
fi
[COLOR=Navy]sel_target=""
[/COLOR]if [ -f "${target}" ] ; then
[COLOR=Navy]    sel_target="${target}"
[/COLOR]    target=$(dirname "${target}")
fi
nautilus "${target}"
[COLOR=Navy]sleep 1
if [ -n "${sel_target}" ] ; then
    zenity --info --title "Linked File" --text $(basename "${sel_target}") --timeout 3
fi
[/COLOR]
```

The changes are highlighted in blue; you need of course to have zenity installed.

The `sleep 1' is for allowing time to nautilus to start, so that the zenity dialog appears on top of the new nautilus window. You may need to tweak it if you have a slower or faster system.

---

### Post by XenosD on 2010-07-05
Thank you for the trick. Now all work perfect with this script.
Another script I implemented in the right-click menu through NACT is the Empty Bin script, which is this:
```
#!/bin/bash

# Empty Bin script for Gnome 2.22 by Romain Desaleux (Fivizzz) translated by Fivizzz

NBITEMS="$(ls -A ~/.local/share/Trash/files/ | wc -l)"

while true
do
    if [ "$NBITEMS" = 0 ]
    then
        notify-send -u critical "Error" "Bin is already empty"
        exit
    else
        
        if [ "$NBITEMS" = 1 ]
        then
            ITEM="$(ls ~/.local/share/Trash/files/)"
            zenity --question --title "Empty Bin" --text "Are you sure you want to permanently remove '$ITEM'?"
            if [ $? = 0 ]
            then
                rm -r .local/share/Trash/files/
                notify-send "Bin Empty" "'$ITEM' was deleted."
                exit
            else
                notify-send "Cancelling" "No file was removed from the bin."
                exit
            fi
        else
            zenity --question --title "Empty Bin" --text "Are you sure you want to permanently remove all $NBITEMS from your bin?"
            
            if [ $? = 0 ]
            then
                rm -r .local/share/Trash/files/
                notify-send "Bin Empty" "All files were deleted."
                exit
            else
                notify-send "Cancelling" "No file was removed from the bin."
                exit
            fi
        fi
    fi
done
```
The problem with this script is that it does not recognize and empty the recycle-bin (.Trash-1000) in NTFS Drives.(I can only empty the bin in these drives only by through the trash icon).

I've modified the script to recognise my two ntfs drives. It successfully empties the bin in all drives, but it cannot count correctly the total number of the  items in the bin. Could you find my mistake and fix it?
```
# Empty Bin script for Gnome 2.22 by Romain Desaleux (Fivizzz) translated by Fivizzz

NBITEMS="$(ls -A ~/.local/share/Trash/files/ [COLOR=Blue]/media/sda2/.Trash-1000/files/ /media/sda5/.Trash-1000/files/[/COLOR] | wc -l)"

while true
do
    if [ "$NBITEMS" = 0 ]
    then
        notify-send -u critical "Error" "Bin is already empty"
        exit
    else
        
        if [ "$NBITEMS" = 1 ]
        then
            ITEM="$(ls ~/.local/share/Trash/files/ [COLOR=Blue]/media/sda2/.Trash-1000/files/ /media/sda5/.Trash-1000/files/[/COLOR])"
            zenity --question --title "Empty Bin" --text "Are you sure you want to permanently remove '$ITEM'?"
            if [ $? = 0 ]
            then
                rm -r .local/share/Trash/files/  
               [COLOR=Blue] rm -r /media/sda2/.Trash-1000/files/
                rm -r /media/sda5/.Trash-1000/files/[/COLOR]
                notify-send "Bin Empty" "'$ITEM' was deleted."
                exit
            else
                notify-send "Cancelling" "No file was removed from the bin."
                exit
            fi
        else
            zenity --question --title "Empty Bin" --text "Are you sure you want to permanently remove all $NBITEMS from your bin?"
            
            if [ $? = 0 ]
            then
                rm -r .local/share/Trash/files/  
               [COLOR=Blue] rm -r /media/sda2/.Trash-1000/files/
                rm -r /media/sda5/.Trash-1000/files/[/COLOR]
                notify-send "Bin Empty" "All files were deleted."
                exit
            else
                notify-send "Cancelling" "No file was removed from the bin."
                exit
            fi
        fi
    fi
done
```

---

### Post by gzarkadas on 2010-07-07
When ls-ing multiple directories, headers are added in the output to show the directory from which the listing comes. So, you 'll have to ls the directories one by one and add the results, like this:

```
NBITEMS=$(( $(ls -A ~/.local/share/Trash/files/ | wc -l) + $(ls -A /media/sda2/.Trash-1000/files/ | wc -l) + $(ls -A /media/sda5/.Trash-1000/files/ | wc -l) ))
```

---

### Post by XenosD on 2010-07-07
Thanks a lot. I followed your instructions and the empty_bin script works fine now. 
If I don't disturb you, I have another script, which I cannot run at all. It is supposed to copy the full path of a right-clicked file or folder. Of course if I manage to run the script, I will make nautilus action for it.
```
#!/bin/bash
#
echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"|xargs echo -n | /usr/bin/xclip -selection "primary"
```Also I'd like to create a nautilus action for refreshing the desktop (just like pressing ctrl+r or f5). I cannot find which command is executed when pressing ctrl+r or f5.

Finally, I've tried to assign shortcuts for my scripts, but they do not function. What do you think might be the problem?

Thank you in advance.

---

### Post by gzarkadas on 2010-07-07
The intermediate xargs is not necessary; so does the -selection option (primary is the default); try simply:

```

#!/bin/bash
echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | /usr/bin/xclip

```The above puts the entire selection to clipboard. If you want to limit the selection to only the first item, them enter a `| head -n 1' just before the pipe symbol.

For nautilus-actions this script has to be changed to:

```

#!/bin/bash
 echo "$@" | /usr/bin/xclip

```Now about the others:

The command you look is probably `xrefresh'. However, I think it is better to create a launcher somewhere in your app bar for this than to make a nautilus script.

Both nautilus scripts and nautilus-actions scripts operate from inside of nautilus to have their input (either as environmental variables or as positional parameters) supplied. When you create a desktop shortcut you subtract the input from the overall picture: no input = no function.

PS: Due to this thread I have discovered some nice little apps; you thus earned the right to unlimited questions :D.

---

### Post by XenosD on 2010-07-07
Neither the nautilus script, nor the nautilus action you gave me, function. They give no output (nothing to paste)
I didn't mean desktop shortcuts. I meant keyboard shortcuts.
Thank you.

---

### Post by gzarkadas on 2010-07-07
Yes, but it is xclip that does not function as documented; there is nothing wrong with the scripts per se. I am investigating it.

How did you assigned shortcuts? I don't see any option in the nautilus menus.

---

### Post by gzarkadas on 2010-07-07
It seems that the 0.08 version of xclip shipped by ubuntu does not update the clipboard. The solution:

1. download the version 0.12 tarball from [http://sourceforge.net/projects/xclip](http://sourceforge.net/projects/xclip)
2. unpack it to a directory of your choice
3. Open a terminal and change to this directory, bootstrap, configure, make and install. The exact sequence of code I used is:
```

cd ~/source/xclip-0.12
./bootstrap
export CFLAGS='-O3 -Wall -march=native -mtune=native'
./configure
make
sudo make install

```4. Update the scripts to use `/usr/local/bin/xclip' and add the option: -selection 'clipboard' to the xclip command line

---

### Post by XenosD on 2010-07-08
I looked for xclip in synaptic  and my system (Ubuntu 10.04) has already installed the latest version (0.12-1). I was wondering wether it is a compatibility issue between ubuntu 10.04 and xclip.
I've tried assigning keyboard shortcuts for my scripts through CompizConfig Settings Manager (Section: Commands).
Xrefresh seems not to be the same with ctrl+r.
Thank you.

---

### Post by gzarkadas on 2010-07-08
I can't answer to this because I do not have a 10.04 system, nor plans to upgrade in the near future. You may try though to build locally your xclip and test whether it works; it is a small executable and the build time is minimal in a reasonably fast system. 

According to [this guide]("http://linuxfud.wordpress.com/2007/02/15/add-a-refreshreload-gui-button-to-your-gnome-panel/"), linked by [a thread in linuxquestions.org]("http://www.linuxquestions.org/questions/linux-software-2/f5-or-ctrl-r-refresh-desktop-what-is-the-command-it-invokes-619398/"), ctrl+r can be simulated by killing gnome-panel and nautilus (see the guide for details). It is a bit drastic though in my opinion, thus I first suggested xrefresh. You can try it and see whether it has the desired effect.

The compiz commands are for general shortcuts, where input is known beforehand (the command lines are fixed). So, they cannot function for the reason I mentioned. Thus, since nautilus does not expose a shortcuts interface, the only way to make such a thing work is to create a nautilus extension that logs the last user selection in any nautilus window and then use as shortcut command a wrapper script that creates the input from the log and then calls your original nautilus script.

---

### Post by XenosD on 2010-07-09
What do you mean by telling me to build localy xclip? I have downloaded the executable, but the only thing I can do is to install it; actually reinstall xclip.
I have tried kill all nautilus command, but as you mentioned is a bit drastic, as it closes all active nautilus windows. This is equal to restarting explorer in Microsoft Windows. The command for refreshing the desktop in Linux is a real mystery. Maybe the developers of Linux want this to be secret.
Anyway thank you.

---

### Post by gzarkadas on 2010-07-09
I was saying to download the source tarball from sourseforge.net/projects/xclip and compile it. But don't do that; I have just checked the debian xclip package sources and are the same. It is better to submit a bug report upstream to the xclip project and have them resolve the issue.

Regarding F5/ctrl+r I have found another related thread; you may want to give it a try: [http://ubuntuforums.org/showthread.php?t=1063300](http://ubuntuforums.org/showthread.php?t=1063300).

---

### Post by XenosD on 2010-07-09
The last thread you gave me guided me to find the solution. Now I have a Windows equal refresh option in my right-click menu. 
Thanks a lot!
I cannot find the site to report the bug for xclip. Please send me a link!

---

### Post by gzarkadas on 2010-07-09
It was a bit zig-zag way, but eventually it came to an end :).

The links for xclip project are:

home page : [http://sourceforge.net/projects/xclip/](http://sourceforge.net/projects/xclip/)
bug tracker (submit there) : [http://sourceforge.net/tracker/?group_id=198423&atid=965419](http://sourceforge.net/tracker/?group_id=198423&atid=965419)

There is an open bug report with that issue, on the top of the bugs table. I have added a comment; you may add one yourself too. Before doing so, please ensure that you have run xclip with option -selection "clipboard"; if you didn't it may be the case that it actually functions in your ubuntu version.

---

### Post by XenosD on 2010-07-10
Where do you want to add the option -selection "clipboard"? In the script or in the parameters in the nautilus action we are trying to make?

---

### Post by gzarkadas on 2010-07-11
In the script, after xclip (they are xclip's params):
```

... | xclip -selection "clipboard"

```

---

### Post by XenosD on 2010-07-11
I was lucky to end in a nautilus script which functions.
The original script I gave you was ```
#!/bin/bash
#
echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"|xargs echo -n | /usr/bin/xclip -selection "primary"
```I just replaced "primary" with "clipboard" and it works perfect.
```
#!/bin/bash
#
echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"|xargs echo -n | /usr/bin/xclip -selection [COLOR=Navy]"clipboard"[/COLOR]
```Now I need your help to modify the script so that it works with nautilus actions.

---

### Post by gzarkadas on 2010-07-11
As I said in the 10# post of this thread, I believe the intermediate |xarg  echo -n is not necessary, so the nautilus-actions script should simply be:

```

#!/bin/bash
 echo "$@" | /usr/bin/xclip -selection "clipboard"

```

If however, the above does not function as you like, you can add back the `|xarg  echo -n ' just before the pipe symbol.

NB: I'll update the comment in xclip project's tracker to let them know it is working on lucid also.

---

### Post by XenosD on 2010-07-11
I've tried with and without `|xarg  echo -n ' but no result. Are you sure that no parameter is needed for the nautilus action?

---

### Post by gzarkadas on 2010-07-11
You should put %M as parameter of the script in the nautilus-actions dialog. This is the most common one (press the button to the right to see other options). I considered it so obvious, I forgot to mention it; assume it is there unless I say something different :smile:.

---

### Post by XenosD on 2010-07-11
It is almost OK. However something strange occurs. When I paste the path in a text file for example, the cursor goes to the  the next line (like pressing ENTER). How can I fix this? Note that this does not happen when I run the nautilus script (the one I created by luck).

---

### Post by gzarkadas on 2010-07-11
You may have to put the |xargs echo -n in between to eat the final newline; I 'll try to also test it in the next couple of days.

---

### Post by XenosD on 2010-07-11
I added '|xargs echo -n', but the nautilus action does not function at all.

---

### Post by gzarkadas on 2010-07-12
Tested, it: the last newline is by echo itself; to suppres it you must use `echo -n', like this:

```

#!/bin/bash
echo -n "$@" | xclip -selection "clipboard"

```

---

### Post by XenosD on 2010-07-12
Just Perfect! Thanks a lot.:D

---

### Post by XenosD on 2010-07-17
I was looking for a script to toggle between disabling and enabling touchpad. 
I found several solutions but this is the only that functions for me. 
The following commands disable and enable the touchpad.
DISABLE:
```
sudo rmmod psmouse
```ENABLE:
```
sudo modprobe psmouse
```Is it possible to make a script using these commands, which would toggle between disabling and enabling touchpad?

PS: I found this script ([COLOR=Blue][https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey](https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey)[/COLOR]) but it doesn't work:
```
# toggle synaptic touchpad on/off

# get current state
SYNSTATE=$(synclient -l | grep TouchpadOff | awk '{ print $3 }')

# change to other state
if [ $SYNSTATE = 0 ]; then
    synclient touchpadoff=1
elif [ $SYNSTATE = 1 ]; then
    synclient touchpadoff=0
else
    echo "Couldn't get touchpad status from synclient"
    exit 1
fi
exit 0
```

---

### Post by gzarkadas on 2010-07-17
You need a file to record the state of the toggle: we 'll use /var/run to host it. And gksudo, to get a nice gui box for the password. Since the script is a toggle, we don't need any options. Now lets put them all together:

```

#!/bin/bash
if [ -f /var/run/touchpad-toggle ] ; then
    # the toggle is on, ie touchpad is disabled; enable it
    gksudo modprobe psmouse
    gksudo rm -f /var/run/touchpad-toggle
else
    # the toggle is off, ie touchpad is enabled; disable it
    gksudo touch /var/run/touchpad-toggle
    gksudo rmmod psmouse
fi

```

Now save this script (either in your home or, if you want to make it a system script, in /usr/local/bin - in the later case make it owned by root and you can omit the gksudo within the script; just put a `gksudo <script-path>' as the command line of the launcher), make a launcher in your deskbar and you are done.

---

### Post by XenosD on 2010-07-17
No result. The box for the password does not appear.

---

### Post by gzarkadas on 2010-07-17
Maybe the script is not run; did you make it executable (chmod u+x)?

---

### Post by XenosD on 2010-07-17
I had made it executable.

---

### Post by XenosD on 2010-07-17
After rebooting the script almost worked. When the system starts the touchpad is enabled. After running the script the touchpad is disabled (OK). After rerunning the script the touchpad is re-enabled(OK). However, after running the script again the touchpad is not again disabled. :confused:

---

### Post by gzarkadas on 2010-07-17
This looks subtle; and that kind of things are usually hard to debug. Anyway, these are the steps to track the issue:

[LIST]
[*]Try to use `modprobe -r' instead of `rmmod' in the script.
[*]Also, while debugging add in all modprobe invocations the `-v' switch to make modprobe be more verbose.
[*]Use the terminal to invoke the script, to catch possible error messages that go to console instead of the logs.
[*]Execute a `modprobe -l' to list the modules, after each script invocation. Also make an `ls /var/run/' to verify that the control file the script uses is properly created/deleted.
[*]Open the `Log Viewer' application (menu `System|Administration') and go to the `dmesg' log; see if there are errors printed there.
[/LIST]
Report your findings back, to review the situation. I am leaving on vacation (very) soon, so I will be available only for a few hours more; I hope it is something small that can be fixed quickly.

---

### Post by XenosD on 2010-07-17
I reply from work. Have a nice vacation. You may reply when  you arrive home from vacation.

---

### Post by XenosD on 2010-07-17
When I use sudo instead of gksudo, all works ok.
```
#!/bin/bash
if [ -f /var/run/touchpad-toggle ] ; then
    # the toggle is on, ie touchpad is disabled; enable it
    [COLOR=Blue]sudo[/COLOR] modprobe psmouse
    [COLOR=Blue]sudo[/COLOR] rm -f /var/run/touchpad-toggle
else
    # the toggle is off, ie touchpad is enabled; disable it
    [COLOR=Blue]sudo[/COLOR] touch /var/run/touchpad-toggle
   [COLOR=Blue] sudo[/COLOR] rmmod psmouse
fi
```The problem was that the /var/run/touchpad-toggle could not be deleted. The command ```
gksudo rm -f /var/run/touchpad-toggle
``` cannot execute; something needs to be changed.

The command ```
sudo rm -f /var/run/touchpad-toggle
``` works OK.

---

### Post by gzarkadas on 2010-07-17
Then keep sudo. If you don't get a dialog box to enter the password, then use the other way I suggested: omit all "sudo/gksudo" inside the script and use `gksudo <script-path>' as the command of the launcher.

---

### Post by rickcjmac on 2010-12-16
I am new to writing scripts and the context menu. I want to add a script to the context menu also. My script is simple:

#!/bin/sh
pdflatex *.tex
gnome-open *.pdf

It finds a file that ends in .tex and compiles it. Then the script opens the .pdf. I haven't gotten as far as to specify which .tex file I want to compile and open. This is one of the main reasons I want to add the option to the context menu.

My overall goal is to be able to right click on a .tex file and select an option right from the menu to compile and open the pdf file. 

Thank you for any help in advance :)

Richard

---

