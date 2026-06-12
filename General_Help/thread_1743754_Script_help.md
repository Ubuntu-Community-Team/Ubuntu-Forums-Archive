---
title: "Script help"
date: 2011-04-29
forum: General Help
---

### Post by polardude1983 on 2011-04-29
Ok I found a script that runs any commands from a dropbox folder. It seems to take the scripts i have from the remote folder to the output folder to the old folder. but it never seems to actually run the scripts. it just seems to move the scripts from folder to folder

Here is the page of what I'm talking about. 

[http://wiki.dropbox.com/TipsAndTricks/RemoteControl2]("http://wiki.dropbox.com/TipsAndTricks/RemoteControl2")


I am trying the first script on that page. any help would be appreciated.

In a nutshell it seems to go through the motions, but never runs the script.

---

### Post by polardude1983 on 2011-06-16
Still haven't had luck with this.

If I run the double click the dropbox.sh script and then hit run. It executes any scripts in the Dropbox/remote/commands folder without flaw

but if I leave the dropbox.sh script in the cron.hourly folder it runs through the motions but never runs the script in the commands folder it just moves it to the log and old folder.

any ideas?

here is the script for the dropbox.sh

```
#!/bin/bash

REMOTEFOLD="/home/christoph-fedora/Dropbox/remote"
COMFOLD="${REMOTEFOLD}/commands"
OUTFOLD="${REMOTEFOLD}/output"
OLDFOLD="${REMOTEFOLD}/old"

cd "$COMFOLD"
for i in *
do
    if [ -f "$i" ]
    then
        chmod +x "$i"
        echo "==== Start: `date` ====" >> "${OUTFOLD}/${i}.log"
        "./${i}" >> "${OUTFOLD}/${i}.log" 2>&1
        echo "===== End: `date` =====" >> "${OUTFOLD}/${i}.log"
        echo >> "${OUTFOLD}/${i}.log"
        mv -t "${OLDFOLD}" "$i"
    fi
done
```

---

### Post by Dave_L on 2011-06-16
Try renaming "dropbox.sh" to "dropbox", and ensure that it's executable.

Scripts in /etc/cron.* will not run if they contain certain characters, including ".", because they're run by "run-parts":

[http://manpages.ubuntu.com/manpages/lucid/en/man8/run-parts.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/run-parts.8.html)

> If neither the --lsbsysinit option nor the --regex option is given then
       the names must consist  entirely  of  upper  and  lower  case  letters,
       digits, underscores, and hyphens.

---

### Post by polardude1983 on 2011-06-17
Well I had 2 shell scripts in my commands folder in my dropbox

gedit.sh
start_transmission

Both went through the commands to the output to the old folder but none of the scripts actually ran.

---

### Post by Dave_L on 2011-06-17
I don't understand "went through the commands".  How does that differ from "running"?

---

### Post by polardude1983 on 2011-06-17
Let me try to use the correct words

If I click on the dropbox script and run it manually the dropbox script runs and any scripts in the commands folder also run as long as they are named *.sh

If I put the dropbox script in the cron.hourly the dropbox script runs but none of the scripts in the commands folder get executed.

Hope that is better wording

---

### Post by Dave_L on 2011-06-20
Scripts in cron.hourly run as root, and the environment is different.  That may or may not matter.

You could enable debug output and see if any useful information shows up in the log files:

```
/bin/sh "./${i}" -xv >> "${OUTFOLD}/${i}.log" 2>&1
```

Reference: [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_02_03.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_02_03.html)

---

