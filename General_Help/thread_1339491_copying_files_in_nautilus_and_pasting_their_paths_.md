---
title: "copying files in nautilus and pasting their paths into a terminal"
date: 2009-11-27
forum: General Help
---

### Post by paulgault on 2009-11-27
Hi all, 
when i first started using ubuntu (the first disto i used was fiesty fawn) i could copy a file in the file browser nautilus and when i used the paste function in a terminal it would pastes the location of the file in question. e.g. it would paste "/etc/fstab", which i thought was rather handy. 
i'm currently on ubuntu 9.04. a few distros ago this changed and now when i try and paste a file in the terminal it adds "file://" to the front of the path so i end up with "file:///etc/fstab" instead. this is a bit of an irritation as i have to keep going back and deleting the extra bit at the front as it's not needed and just stops the command from working. i've never managed to figure out how to stop it doing this. it's only a little thing but i'd appreciate it if anyone out there knows how to sort this out as it's annoying me.
BTW, when i paste a file into the text editor gedit it doesn't include this prefix, and it never has (back to 7.04 anyway)
thanks
Paul

---

### Post by sisco311 on 2009-11-27
I don't know how to fix this, but dragging the file in the terminal works for me.

---

### Post by paulgault on 2009-11-27
Nice. never thought to do that. works on mine as well. thanks.

have got used to CTRL+SHIFT+V to paste in a terminal though and would appreciate it if anyone could help me do it this way?!?!?!

---

### Post by Rebelli0us on 2009-11-27
That would be the equivalent of "Send To", "Clipboard as Name", I do miss the Send To menu. Also linux doesn't know how to open the file, asks every time if you want to "execute" a text file or display it, ... how do you execute a text file, and why?

---

### Post by t0p on 2009-11-27
> **Rebelli0us said:**
> That would be the equivalent of "Send To", "Clipboard as Name", I do miss the Send To menu. Also linux doesn't know how to open the file, asks every time if you want to "execute" a text file or display it, ... how do you execute a text file, and why?

If Nautilus asks you if you want to open a file or executed, this means the file has been made executable.  You can check this (and change it), right click on the file and go to Properties.  Click on the Permissions tab.  Now you can see if the 'Allow executing file as program' box has been ticked.  Untick it and close the Properties window.  Now when you double-click on the text file, Nautilus will open it with gedit (or whatever text editor you use).

---

### Post by NFblaze on 2009-11-27
> **Rebelli0us said:**
> That would be the equivalent of "Send To", "Clipboard as Name", I do miss the Send To menu. Also linux doesn't know how to open the file, asks every time if you want to "execute" a text file or display it, ... **how do you execute a text file, and why?**

Well, it's possible to execute a txt file if it has scripting code in it. Like you could straight paste a couple of linux commands into the textfile, and it can then be executed. I think people do this if they have a repetitive task that they dont want to consistently type in over and over.

---

### Post by raktarok on 2009-11-27
You can disable the executing by going to Edit > Preferences > Behavior in a nautilus window and selecting 'view execuatable text files when they are opened' One of the first things I do after a fresh install. and I can always run scripts and other executable text files via terminal.

I don't know how to solve the pasting problem though, but if you are using it to change directories in terminal, you can install 'nautilus-open-terminal'. Then you can right click on the folder and open a terminal in that directory.

---

