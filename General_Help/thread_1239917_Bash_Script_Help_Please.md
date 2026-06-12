---
title: "Bash Script Help Please"
date: 2009-08-14
forum: General Help
---

### Post by martynp on 2009-08-14
Hi,

I need a bash script to pause until a program is no longer running.

i.e. Mount Windows Share
     Start Music On Console
-->  Wait Till Music On Console Closes <--
     Unmount Windows Share

I have all the commands to make the above happen except make the script wait until MOC is no longer active. I have done many searches but have not been able to find an acceptable fix.

Can anyone kindly help please?

Many Thanks

---

### Post by aloshbennett on 2009-08-14
The crude way is to use sleep in an infinite loop,and then check if the program is running by using 'ps | grep program_name'.

A better way is, to write a wrapper script for your music console like this:
1. Mount windows share
2. Launch music player
3. unmount windows share

This will work as long as the music player blocks the code.

---

### Post by DaithiF on 2009-08-14
Hi,
this should be normal behaviour for a script, ie. each line executes and only when it returns does the next line execute.

so if my script was:
mocp
echo "all done"

i shouldn't see the 'all done' message until moc has exited.

what is your command to run music on console?

---

### Post by credobyte on 2009-08-14
> **DaithiF said:**
> Hi,
this should be normal behaviour for a script, ie. each line executes and only when it returns does the next line execute.

so if my script was:
mocp
echo "all done"

i shouldn't see the 'all done' message until moc has exited.

what is your command to run music on console?

Command/application isn't executed successfully until it gives you an exit code ( which can be obtained only by exiting it ). While you don't have this info, it will be on *pause*.

---

### Post by martynp on 2009-08-14
Thanks for the prompt replies.....

I have been trying this:

#!/bin/bash
sudo mount -t smbfs //<some server>/users/Martyn/ /media/Share -o username=Martyn,password= &
terminator -x mocp &
wait
sudo umount /media/Share &
exit

(don't worry about the sudo, I have it passwordless whilst trying to get this running)

The share mounts OK. Music On Console loads fine. Music plays. However, if I kill mocp I want the unmount to take place. It doesn't. I have done loads of searching for an answer but cannot find anything that helps.

Many Thanks!

---

### Post by DaithiF on 2009-08-14
Hi, just don't start terminator/mocp in the background, ie. remove the trailing &.  this will pause execution of the script until mocp & terminator exit.

---

### Post by martynp on 2009-08-14
Oh man! It was THAT simple....How embarrassing!

All working now!

Many, many thanks! :):):):):)

---

### Post by mixmaster on 2009-08-14
I'd take the & off all the commands.  As it stands, if you leave it on the mount it would be technically possible for the mocp to fail if the mount were slow for some reason.

---

