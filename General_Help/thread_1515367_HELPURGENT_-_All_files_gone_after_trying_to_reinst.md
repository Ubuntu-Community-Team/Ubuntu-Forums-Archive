---
title: "HELP/URGENT - All files gone after trying to reinstall gnome panel"
date: 2010-06-22
forum: General Help
---

### Post by score100 on 2010-06-22
Hi there,
yesterday I uninstalled evolution - thats where the horror started. Today I had my whole gnome panel on top missing, which makes it practically impossible to work on netbook remix. Then I tried to follow instructions in this post.
 [http://newyork.ubuntuforums.org/showpost.php?p=7394034&postcount=5](http://newyork.ubuntuforums.org/showpost.php?p=7394034&postcount=5)

While trying to run that stuff in the terminal that I went into with strg-alt-f1, I think I either created a new user (with the same name???) or something else happened, ANYWAY NOW AFTER RESTARTING ALL FILES IN MY HOME FOLDER ARE GONE, SO ARE ALL MY SETTINGS.

the programs are oddly still there, even the additional ones that I installed. but for the rest all settings, passwords and files are like after a fresh ubuntu installation to clean hard disk.

btw i run lucid lynx on an eeepc 1008ha.

---

### Post by justleen on 2010-06-22
can you see any other users in /home/ (when in a terminal, ls -la /home/)?
Was the home dir on a seperate partitions, which might not be mounted?

---

### Post by score100 on 2010-06-22
no, no seperate partition and no I can't see any other user. I remember now that I was getting into the terminal to run the commands and pressing alt+f2 there. Could I have switched between tty1 and tty2 or something? and if yes how do I go back?
bedankt for the quick reply btw.

---

### Post by justleen on 2010-06-22
tty1 or 2 doesn't matter, if you logon as your self, you still login to the same account.


Looking at the post youfollowed.. Are you sure you rm'ed the correct directory?? 
I mean, if you login now in a terminal and you do an "ls" you see nothing (or next to nothing..)?

---

### Post by score100 on 2010-06-22
pretty much nothing. only the folders left, but nothing inside. I didn't copy paste the command in the post but wrote it down on paper...so if I put one space too much somewhere means everything is gone?

---

### Post by score100 on 2010-06-22
also I rememeber there was some error msg when I did the rm command. at least I think so. In my home folder there are still all of the ".conf" etc folders. just the documents/pictures and so on are all empty, also an additional folder that i created in there is gone. So are my basic configs like saved passwords, configurations in the for the main menu. :mad:

---

### Post by justleen on 2010-06-22
Yea, adding a space on the wrong place there could result in a wipe..

rm -rf ~/ .config/whatever
vs.
rm -rf ~/.config/whatver

1st deletes everything in /home/user/ **plus** .config/whatever (but not any other hidden files)
2nd deletes  /home/user/.config/whatever 



[SIZE="1"]Tip of the day:  replace rm commands with mv (move) to test if results are as expected..[/SIZE]

---

### Post by philinux on 2010-06-22
> **score100 said:**
> also I rememeber there was some error msg when I did the rm command. at least I think so. In my home folder there are still all of the ".conf" etc folders. just the documents/pictures and so on are all empty, also an additional folder that i created in there is gone. So are my basic configs like saved passwords, configurations in the for the main menu. :mad:

Let's see exactly what you did.

```
tail  -30 ~/.bash_history 
```

Increase the number of lines if it does not show all that went wrong.

Then dont use the machine. You may be able to recover some files using the livecd with testdisc's photorec and a usb stick.

---

### Post by score100 on 2010-06-22
thanks, tip of the day is a bit too late for me though now i guess :((((
just trying to find any recovery tools. don't know if there's anything findable for ext4 filesystem.

---

### Post by score100 on 2010-06-22
> **philinux said:**
> Let's see exactly what you did.

```
tail  -30 ~/.bash_history 
```

Increase the number of lines if it does not show all that went wrong.

Then dont use the machine. You may be able to recover some files using the livecd with testdisc's photorec and a usb stick.

ok on the recovery now. I'm a bit confused by the different descriptions on the net - I just want to recover my documents folder, which'd be especially valuable. I know I could use photorec - but I got a segmentation fault already 2 times after trying to run it. 

So best thing would be to create a bootable usb (its a netbook we're talkin bout), and then run photorec while writing recovered stuff on the usb?

---

### Post by philinux on 2010-06-22
> **score100 said:**
> ok on the recovery now. I'm a bit confused by the different descriptions on the net - I just want to recover my documents folder, which'd be especially valuable. I know I could use photorec - but I got a segmentation fault already 2 times after trying to run it. 

So best thing would be to create a bootable usb (its a netbook we're talkin bout), and then run photorec while writing recovered stuff on the usb?

Use the livecd and install photorec then you could use the usb as the destination.

---

