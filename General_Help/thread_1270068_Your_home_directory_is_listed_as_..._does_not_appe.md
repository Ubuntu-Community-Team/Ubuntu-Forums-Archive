---
title: "Your home directory is listed as ... does not appear to exist"
date: 2009-09-19
forum: General Help
---

### Post by mjh007 on 2009-09-19
Hi All

I had a bit of a scare yesterday when I was just busy on my laptop, when all of a sudden the screen went all funny and black... So I shut down the computer and tried to restart it, only to find the following error message pop up after entering my username and password:

> Your home directory is listed as '/home/username' but it does not appear to exist. Do you want to log in with the/root directory as your home directory? it is unlikely anything will work unless you use a failsafe session

Clicking on "No" did nothing, while clicking on "Yes" got me through to a desktop wallpaper and some other errors and that was it.

So after much searching on many forums, I found a solution and thought I might share it with you. I'm not sure that it will solve all similar problems, but it worked for me.

[LIST=1]
[*]At the Login Screen press Ctrl-Alt-F1 to bring up the terminal
[*]Login normally using your username and password
[*]Then type in ```
sudo touch /forcefsck
``` to force a file system check on startup
[*]Type in ```
exit
``` to exit the terminal and then click on the options and then restart 
[/LIST]

fsck started checking my partitions on my drive for errors and found an error on the root partition (or was it the boot? - I can't quite remember). It said something about > needing to run fsck manually and then put me into a maintenance terminal where I ran ```
fsck
``` again and it found an > unallocated inode pointing to ```
/home/lost+found
``` and would I like to fix it. I just said yes to all the options and typed in ```
Ctrl-D
``` to restart and then all was well again.

Anyway I hope that helps someone else who might have a similar problem.

---

### Post by blueridgedog on 2009-09-19
Excellent advice.  One other option is to bood off of a LiveCD and run fsck on the partition manually.

---

