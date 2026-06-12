---
title: "Trying to get Transmission to start via script"
date: 2011-04-11
forum: General Help
---

### Post by polardude1983 on 2011-04-11
Ideally I would love to have a script that watches my Home/Dropbox/Attachments folder for any torrent files. When there is a torrent file in the Attachments folder it will launch Transmission if it is not up already.

But if not I can do it this way too

Basically what I somewhat have now is I'm trying to use Dropbox to start Transmission when I want it to.

I have this script running every 3 minutes in Ubuntu Tweak to watch for any scripts I want to run from my Dropbox/remote/commands folder. Whenever a script gets placed in the commands folder it runs it. Which is this

```
#!/bin/bash

REMOTEFOLD="${HOME}/Dropbox/remote"
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

[Original webpage]("http://wiki.dropbox.com/TipsAndTricks/RemoteControl2")

and here is the script that I have to launch Transmission

```
#!/bin/bash
transmission-gtk %F
exit
```

Now if i right click on this file and tell it to run, it starts transmission.

But when I place this is my commands folder in dropbox, The script in Ubuntu Tweak picks up my starttransmission.sh script and seems to run it but transmission never starts up.

Any help would be appreciated.

---

### Post by r-senior on 2011-04-11
First thought would be to try the full path to transmission-gtk in the script, or define a PATH variable.

---

### Post by polardude1983 on 2011-04-11
I did try changing the script to this with the full path

```
#!/bin/bash
/usr/bin/transmission-gtk
exit
```

As same thing happens if I just normally right click the file it opens transmission. But it doesn't seem to open it when I place it in the commands folder in my dropbox.

---

### Post by polardude1983 on 2011-04-11
Its obviously something wrong with the first script that I run in Ubuntu Tweak.

---

### Post by polardude1983 on 2011-04-11
Anybody have any suggestions why I can't get any script to run?

---

