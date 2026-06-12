---
title: "The folder that won't go away"
date: 2010-06-30
forum: General Help
---

### Post by Total Noob on 2010-06-30
Help!

I copied my backup disk (3.2 GB) onto my hard drive using 10.4 in order to reorganize my storage, but then I could not trash it.

In "file browser" a lock icon appears next to the folder name, and I always get the error message that it can not be put into trash in one step, would I like to delete it? I click on "delete" and no help.

Further trial led to an error message that I don't have "permission." I'm the only user.

I don't know anything about terminal and not one command, and usually when I ask for help, people provide "code" but no instructions on how to enter it or where.

I'm the rawest beginner at terminal, but I am asking to be walked thru instructions to delete 30% of my hard drive's capacity with plain English and no jargon whatever. I'm filling up rapidly.

Thanks.

---

### Post by varunendra on 2010-06-30
To open a terminal, click on "Applications" on the left side of the upper panel. Then, in the opened menu, click on "Accessories > Terminal". This will open a terminal where all the commands are entered.

To delete a locked folder/file or to change its permission so that you can do whatever you want to do with it, you need to access it as root. The easier way to do so with gui (graphical user interface) is to open a "file browser" as root. The command (that you'd have to enter in the terminal) for this is:
```
sudo nautilus
```
It will ask you to enter your password. Enter the same password that you use to log in (password won't show up as you type it, just type it correctly & press 'Enter').
This will open nautilus - the default "file browser" for ubuntu - as root.

But before you can access a drive's contents, you need to mount it first. Remember when you go into 'computer' from 'Places' menu, you see there all the different drives of your computer including those attached from outside. These may or may not be mounted depending upon various facts.
The best way to ensure they are mounted is to just double-click them to get into.

Now, once they are mounted, open nautilus as root as told above & browse to the file/folder you want to delete or change permissions of. (you can find the drives in **File System > media > (desired drive)**).
[COLOR=Red]
[/COLOR]**[COLOR=Red]Be cautious: [/COLOR]System keeps critical file/folders locked to prevent accidental deletion/modification of them. But opening nautilus as root gives you full permission to everything and gives no warning before applying the changes. So you should be extra cautious while making changes as root!**

Remember: All this long story can be actually summarized to a couple of lines of commands in the terminal like 'mount', 'chmod', 'chown', etc. But I thought doing it through GUI would appear more friendly to you as a beginner & would be more understandable to you.
Once you get used to the linux file system, you should try doing things from commandline as much as possible, because it is easier, faster & sure-shot method of doing them.

---

### Post by Total Noob on 2010-07-01
Thanks, but this worked only partially.

I was able to find my huge folder in my "home" folder, and I put all of the unwanted stuff into trash.

But I was unable to empty the trash, the error message was "Operation not supported," I was unable to even see what was in the trash even though I was "root."

Which means I still have the big folder taking up space but unable to actually purge it.

Anything else to try?

---

### Post by varunendra on 2010-07-01
To delete it permanently, try "shift+Delete" instead.

For emptying root's trash, look here: [http://www.ubuntugeek.com/how-to-empty-root-trash.html](http://www.ubuntugeek.com/how-to-empty-root-trash.html)
(Also read the comments on this page in case of problems)

Again, BE CAREFUL while 'Shift+Deleting' !!

---

### Post by Total Noob on 2010-07-02
> **varunendra said:**
> To delete it permanently, try "shift+Delete" instead.

For emptying root's trash, look here: [http://www.ubuntugeek.com/how-to-empty-root-trash.html](http://www.ubuntugeek.com/how-to-empty-root-trash.html)
(Also read the comments on this page in case of problems)

Again, BE CAREFUL while 'Shift+Deleting' !!

This didn't work either. After sudo nautilus, I found "trash" listed amongst the folders, but was still unable to get past "operation not supported." 

Then I went to the link, where the advice was to use terminal to access the trash more directly, ```
gksudo nautilus ‘/root/.Trash/’
```

I cut and pasted the code into terminal, but I got > Could not find "/home/(my name)/‘/root/.Trash/’". Please check the spelling and try again.

Further down in the thread, there was more advice that root trash doesn't exist until you put something in trash as root. I tried that, trashing three files directly as root. 

But when I tried to open trash as root after that, it was still "Operation Not supported."

Have I reached the end of the line?

Thanks.

---

### Post by Monotoko on 2010-07-02
/root/.Trash

No quotation marks...or it will screw up :)

---

### Post by varunendra on 2010-07-02
> **Total Noob said:**
> I went to the link, where the advice was to use terminal to access the trash more directly, ```
gksudo nautilus ‘/root/.Trash/’
```I cut and pasted the code into terminal, but I got > Could not find "**/home/(my name)/[COLOR=Red]‘/[/COLOR]root/.Trash/**[COLOR=Red]’[/COLOR]". Please check the  spelling and try again.                      

Sorry, I didn't try it myself (folder structure has been changed a bit in newer versions as also commented in the linked page). Besides, there is some syntax error in your command. Let me try to explain in detail:

If you deleted the files as 'root', they would be in 'root's' trash. Open nautilus with sudo or gksudo (gksudo is supposed to be more suitable for GUI applications, I don't know why. To me, there's no difference)
```
sudo nautilus
```When in nautilus as root, tick **View>Show Hidden Files**. This will enable you to see hidden folders (whose names are followed by '**.**'). Now if you can't find **.Trash** folder, then browse to > /root/.local/share/Trash/files/Your deleted files should be there (if you deleted them as root). Select them and press Shift+Delete. Job's done!! :D

In the similar fashion you can also access the trash of any user when you are root (/root would then be replaced by /home/(user) where (user) would be the name of the user whose trash you want to access).

Try & tell us if still having problems. ;)

---

### Post by philinux on 2010-07-02
verunendra, > Open nautilus with sudo or gksudo (gksudo is supposed to be more suitable for GUI applications, I don't know why. To me, there's no difference)

Yes theres is. Stick to gksudo for gui apps.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by varunendra on 2010-07-02
> **philinux said:**
> verunendra, 

Yes theres is. Stick to gksudo for gui apps.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Thanx philinux (or Travolta?)!
I saw that page once but overlooked it. But now I got it! The good thing is to know that it (gksudo) is either good or not bad for gui apps, so I'd stick to it from now on.

-Varun

---

### Post by Total Noob on 2010-07-02
> **varunendra said:**
> /root/.local/share/Trash/files/

That procedure worked like a charm, except I evidently did not use the above browsing code correctly, receiving an error message.

I simply typed that in at a prompt, and was told there was no such folder.

Fortunately, I was able to browse to the trash folder within Nautilus and shift-delete from there.

Thanks a million.

I don't know anything about the changes in the folder structures, and I don't know why some earlier advice had quotation marks around code that you are supposed to cut and paste, which made it confusing for a newbie. All I know is that the 10.4 upgrade put it past the specs of a different (old) computer I was using 9.10 on, with, unfortunately, no advance warning. Maybe these things are related.

Any chance that more of the housekeeping functions or root functions will be more intuitive and GUI'd? I knew going in that Linux uses lots of memorized and obscure code words and abbreviations to do housekeeping, but having used it now, it seems old fashioned and from the 1970's when I was doing BASIC in college and when I owned DOS-based and C/PM based computers in the 1980's.

Last, do you know of a government wipe in any Ubuntu repository, more particularly, one usable in root? I could not for the life of me get a "tarball" to install, and I can't remember the detailed procedures to get it to install even if it would work.

Thanks.

---

### Post by varunendra on 2010-07-02
You were in college in 70s!!

After reading this & all your questions, I can think of only one thing: "Who actually should be named 'Total Noob'?"

I don't find myself eligible enough to give you an opinion or to provide you with a precise answer. Perhaps this may explain why: [http://ubuntuforums.org/showpost.php?p=9408238&postcount=92](http://ubuntuforums.org/showpost.php?p=9408238&postcount=92)

Tonight I'm packing my stuff to leave for home & may not come online for next 10-12 days. But I hope you solved your original problem anyhow.

See you later!

-Varun

---

### Post by Total Noob on 2010-07-27
> **varunendra said:**
> You were in college in 70s!!

After reading this & all your questions, I can think of only one thing: "Who actually should be named 'Total Noob'?"



Total Noob is someone who doesn't do computers for a living, just lives with computers as a necessary evil and for information access, and wants as much of computing as possible to be as easy as possible, and mostly GUIded because his brain cells are filled with other kinds of tasks unrelated to computing that actually pay, and with sports, literature and music, who may dabble in Linux if it could mean not having to buy a new computer and more software.

---

