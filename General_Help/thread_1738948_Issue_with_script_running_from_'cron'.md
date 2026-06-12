---
title: "Issue with script running from 'cron'"
date: 2011-04-25
forum: General Help
---

### Post by Gaba_p on 2011-04-25
Hi,

I'm having a weird issue.

I have a script that runs perfectly when the system boots up and when I run it manually, but fails when it's started by '*cron*'.

This is the script (the real script is actually much bigger, but this are the things I'm having problems with):

```
#!/bin/bash

MOUNT_DIR="/home/user/Dropbox/crypt"
VAULT_FILE="/home/user/Dropbox/truecrypt-file"
KEY_FILE="/home/user/Escritorio/truecrypt-keyfile"

truecrypt -d "${VAULT_FILE}"
zenity --warning --text="Volume un-mounted.\n Starting Dropbox.";

# Piece of code where Dropbox is executed and after is finished, stopped. This works fine.

truecrypt --keyfiles="$KEY_FILE" "${VAULT_FILE}" "${MOUNT_DIR}"


```

Now, neither the '***zenity***' nor the '***truecrypt***' command will work when the script is launched from '*cron*'. I know '*cron*' **is** launching the script correctly because I have a log output (not shown in this excerpt of the script) that records whenever the script is started.

This is the '*cron*' command I use by the way:

```
0 */10 * * * /home/gabriel/check-dropbox.sh
```

I use this because I see no reason why Dropbox should run more than twice a day (once when the system starts, and once more 10 hours later)

Any ideas?

Regards,
Gabriel

---

### Post by matt_symes on 2011-04-25
Hi

Cron does not have your environmental settings. Try using the full path to truecrypt and zenity.

Kind regards

---

### Post by collisionystm on 2011-04-25
edit using 
```

sudo crontab -e

```

---

### Post by DaithiF on 2011-04-25
Hi, cron is not running in a graphical session as you are, so zenity has no way of knowing what X display you want your warning notifications displayed on.

add the line:
```
export DISPLAY=:0.0
```
to your script before the call to zenity.

---

### Post by Gaba_p on 2011-04-25
Hi,

thanks for the replies.

@collisionystm: editing crontab with sudo didn't help

@ matt_symes: writing the full path to 'truecrypt' made it work

@DaithiF: added that line and 'zenity' in now capable of displaying windows

Thanks to all!

One more question if it's not too much trouble :)

I'm trying to make the script realize if a file within a given folder is opened (this is so 'Dropbox' won't sync un-encrypted files inside the un-encrypted folder)

I've tried both this codes:

```

for f in /path/to/folder/*
do
    lsof "$f" | grep -q COMMAND &>/dev/null
    if [ $? -eq 0 ]
    then
        echo "Warning: Open file $f"
    fi
done
```

and

```

if mount | grep "${MOUNT_DIR}" >/dev/null; then
     dir="/path/to/folder/"
     lsof +D $dir | grep -q COMMAND &>/dev/null
     if [ $? -eq 0 ]
     then
       export DISPLAY=:0.0
       zenity --warning --text="Warning: Open files found in $dir \n Please close ALL open files BEFORE moving on.";
     fi
fi

```

The first method can identify *single* files, the second only tells you that there's *some* file is opened in that dir.

The problem with both this methods is that they both fail to see files opened with 'gedit', basically any image file or *zip files (opened with 'Ark'); this are all I've tried. They do warn me about opened *.mp3's or *.doc files.

'TrueCrypt' has an internal option to detect opened files, but that won't halt the script. I want to check for ANY opened file, display a warning through 'zenity' if one is found, and then give the user the option to exit the script by clicking one of 'zenity's' buttons (either 'Ok' or 'Cancel'; I think they are both displayed with 'zenity --info')

Can this be done?

Thanks!

---

### Post by Gaba_p on 2011-04-26
Well I guess I'll just open another post with the questions about 'lsof'

To close this one, I'll add that I got it working adding 'export DISPLAY=:0.0' before the 'truecrypt' call. It looks lie this:

```

export DISPLAY=:0.0
/usr/bin/truecrypt -d "${VAULT_FILE}"  "${MOUNT_DIR}"

```

Truecrypt could work with less parameters (perhaps just 'truecrypt -d'), I didn't try

---

### Post by Geilviech on 2012-08-10
I know this is a old thread.. but I just wanted to add that it should also work if you add the -t switch to Truecrypt like this:

```
/usr/bin/truecrypt -t -d "${VAULT_FILE}"  "${MOUNT_DIR}"
```

See the Truecrypt --help reference for more information:

-t, --text
Use text user interface. Graphical user interface is used by default if available. This option must be specified as the first argument.

---

