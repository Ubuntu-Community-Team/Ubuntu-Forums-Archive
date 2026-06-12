---
title: "Help writing a bash script that will start Dropbox once a volume is mounted"
date: 2011-11-02
forum: General Help
---

### Post by echo59 on 2011-11-02
Hi,

I need help to write a bash script that will start Dropbox once the volume with my dropbox folder is mounted.  Basically, I've the dropbox folder inside a Truecrypt volume.  I've it set up for Truecrypt to run on boot and I've switched off "Start Dropbox on system start-up"

Essentially, I've a Truecrypt volume at:
/dev/sdb1

This mounts to a location at:
/mount/truecrypt1

The location of my Dropbox folder is at:
/mount/truecrypt1/Dropbox

I've a bash script set up which runs after login that says
```
#!/bin/sh
truecrypt --mount /dev/sdb1 /media/truecrypt1
```

What I want is to add to the script such that it will check every second or 2 until device/drive is mounted and then start Dropbox.

There is a batch file in Windows which does exactly this.  It works fine, I just want suggestions as to how it might be translated to bash for Ubuntu.

```
@echo off
rem Every second, check to see if volume is mounted
echo Waiting for volume...
:keepwaiting
ping -n 1 -w 1000 127.0.0.1 > nul
if not exist D:\ goto keepwaiting
start "Dropbox" "C:\Documents and Settings\YourUserName\Application Data\Dropbox\bin\Dropbox.exe"
```

Any help would be really appreciated!

---

### Post by Vaphell on 2011-11-02
try this

```
#!/bin/bash

dbox_dir=/media/truecrypt1/Dropbox
while true
do
  if [ -d "$dbox_dir" ]
  then
    echo Dropbox folder is ready
    break
  else
    echo Dropbox folder not available
  fi
  sleep 2
done

echo DO DROPBOX STUFF HERE
dropbox

```

i know nothing about dropbox (what is the exact name of the executable, are there any params required) so you need to figure out the last part. Echo commands and else part of if block are not required - they are for testing purposes

---

### Post by pr3zident on 2011-11-03
> **echo59 said:**
> Hi,

I need help to write a bash script that will start Dropbox once the volume with my dropbox folder is mounted.  Basically, I've the dropbox folder inside a Truecrypt volume.  I've it set up for Truecrypt to run on boot and I've switched off "Start Dropbox on system start-up"

Essentially, I've a Truecrypt volume at:
/dev/sdb1

This mounts to a location at:
/mount/truecrypt1

The location of my Dropbox folder is at:
/mount/truecrypt1/Dropbox

I've a bash script set up which runs after login that says
```
#!/bin/sh
truecrypt --mount /dev/sdb1 /media/truecrypt1
```

What I want is to add to the script such that it will check every second or 2 until device/drive is mounted and then start Dropbox.

There is a batch file in Windows which does exactly this.  It works fine, I just want suggestions as to how it might be translated to bash for Ubuntu.

```
@echo off
rem Every second, check to see if volume is mounted
echo Waiting for volume...
:keepwaiting
ping -n 1 -w 1000 127.0.0.1 > nul
if not exist D:\ goto keepwaiting
start "Dropbox" "C:\Documents and Settings\YourUserName\Application Data\Dropbox\bin\Dropbox.exe"
```

Any help would be really appreciated!

how are you running dropbox.(exe) ?

---

### Post by echo59 on 2011-11-03
> **pr3zident said:**
> how are you running dropbox.(exe) ?

The batch file is for when I am running Windows, it's a dual-boot system.  I'm just trying to set up the same thing for Maverick.

---

### Post by dave0109 on 2011-11-03
Reply #2 should do it.

But - it seems like the wrong way round to me.  Shouldn't the truecrypt file be on dropbox?  Then your files are encrypted on their disc as well as yours.

So in that case, you can start dropbox at boot time, pointing at a folder where you store your truecrypt file.  Truecrypt can also start at boot time and you've access to your secured files as usual.

Just an idea.  It may not be what you want. :)

---

### Post by echo59 on 2011-11-03
> **Vaphell said:**
> try this

i know nothing about dropbox (what is the exact name of the executable, are there any params required) so you need to figure out the last part. Echo commands and else part of if block are not required - they are for testing purposes

Thank's Vaphell!  That works a treat!

For anyone else who's using the script the code to start Dropbox is:```
dropbox start -i
```



> **dave0109 said:**
> Reply #2 should do it.

But - it seems like the wrong way round to me.  Shouldn't the truecrypt file be on dropbox?  Then your files are encrypted on their disc as well as yours.

So in that case, you can start dropbox at boot time, pointing at a folder where you store your truecrypt file.  Truecrypt can also start at boot time and you've access to your secured files as usual.

Just an idea.  It may not be what you want. :)

Dave, thanks for the comment.  Many people seem to do it that way, with truecrypt inside dropbox.  However I've a lot of stuff in truecrypt and only a minority is kept in my dropbox folder.  The dropbox server is "relatively" secure, and that is good enough for my needs.  However my big problem is if my laptop ever got stolen a lot of commercially sensitive information would go.

Thanks for your help, guys!

---

### Post by dave0109 on 2011-11-03
Fair enough. In that scenario, I'd create a second Truecrypt area.  It's not that I don't trust dropbox, or Ubuntu One or whatever, but any files that I need to encrypt locally don't go to the internet unencrypted either. IFSWIM. Anyway, glad you're sorted.

---

### Post by echo59 on 2011-11-03
> **dave0109 said:**
> IFSWIM. 
That's a new one on me...

---

### Post by dave0109 on 2011-11-04
Sorry - "If you see what I mean".

---

