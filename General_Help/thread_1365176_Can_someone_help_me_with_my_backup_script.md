---
title: "Can someone help me with my backup script?"
date: 2009-12-26
forum: General Help
---

### Post by dillandriskell on 2009-12-26
Hi, I've been working on a backup script that I'd run every night before I went to sleep.  What the script should do is backup my files, clean out some unnecessary stuff, and then shut itself down.  I *think* I've got it right but it would be so much appreciated if you guys could look over it for me, suggestions are awesome too!  I'm messing with "rm -r" so I'm being ultra-paranoid I've got it right! 
:lolflag:

```


#!/bin/bash

# Backs up files, cleans out the junk, then turns off the computer

##### Backup #####
rm -r /home/dillan/bak/* &&
cp -r /media/files/* /home/dillan/bak/ &&

##### Clean #####
apt-get autoclean &&
apt-get clean &&

##### Shutdown #####
shutdown -h now


```NOTE: I keep all my files on an external hard drive, and I'm using the computer's hard drive as backup.  And of course this script would be run with "sudo".

---

### Post by angry_johnnie on 2009-12-26
maybe

```
#!/bin/bash

##### Backup #####
rm -r /home/dillan/bak &
cp -r /media/files/ /home/dillan/bak/ &

##### Clean #####
sudo apt-get autoclean &
sudo apt-get clean &

##### Shutdown #####
sudo shutdown -h now
```


shutdown cannot be run by you, unless you mingle with /etc/sudoers


jbrown96 covered what you could to about /etc/sudoers [here]("http://www.uluga.ubuntuforums.org/showthread.php?p=8501254").

just make sure, if you are going to edit the sudoers file, to do it with visudo.

---

### Post by x33a on 2009-12-26
instead of removing and copying all the files daily, you should synchronize the 2 folder.

you could give rsync a try.

try
```
rsync -ruv --delete [FONT=monospace]/media/files /home/dillan/bak [/FONT]
```[FONT=monospace]
note: try rsync with the --dry-run switch first, to confirm that everything works as expected.

this will copy newer files to the destination, and delete any files not found on the source folder. rest seems fine.

also, you could make a cronjob for the script, instead of manually doing it. though, then the shutdown line should be removed from the script.
[/FONT]

---

### Post by dillandriskell on 2009-12-26
Thanks for the reply! 
I can see I did in fact mess up a few things :P

So it's only one "&" instead of "&&"?
And "shutdown -h now" needs to be behind sudo?
Hmm...would it work the same if I ran the script in sudo?
The name of the script is "backup", so if I did

```
sudo backup
```

Then typed in my password would it still shutdown at the end?

I'm trying to make the whole thing automated, 
So when I'm ready to retire for the night I just type "sudo backup"
Then I can just walk away and let it finish

---

### Post by angry_johnnie on 2009-12-26
> **dillandriskell said:**
> Thanks for the reply! 
would it work the same if I ran the script in sudo?
The name of the script is "backup", so if I did

```
sudo backup
```

Then typed in my password would it still shutdown at the end?



Yes, it would.  :-)

---

### Post by dillandriskell on 2009-12-26
> **x33a said:**
> instead of removing and copying all the files daily, you should synchronize the 2 folder.

you could give rsync a try.[FONT=monospace][/FONT][FONT=monospace]
[/FONT]

rsync sounds like a much better alternative!
In fact the constant removing/copying was my workaround to synchronizing.
Now so far my script now looks like this;

```


#!/bin/bash

# Backs up files, cleans out the junk, then turns off the computer

##### Backup #####
rsync -ruv --delete /media/files /home/dillan/bak &

##### Clean #####
apt-get autoclean &
apt-get clean &

##### Shutdown #####
shutdown -h now


```

And I've considered doing it through Cron, but I'm too bad at keeping a strict schedule to do that. :P I'm always staying up late to finish some things up or something like that.

---

### Post by stinkeye on 2009-12-26
For an easy to follow Gui based on rsync and allows to schedule have a look at
[_[COLOR="DarkRed"]luckyBackup[/COLOR]_]("http://luckybackup.sourceforge.net/")

---

### Post by dillandriskell on 2009-12-27
Alright, I finally got everything in order and decided to test the script!
But ahk! I was met with failure.

I first tested rsync which x33a gave me, first by itself, both a --dry-run and a full run, absolute success!

So then I tried running the script itself, and my computer proceeded to shutdown?  What I'm guessing is happening is it's trying to run all the commands at once.  I remember reading about this when I was studying BASH a while ago, I'm thinking I need to replace "&" with something else.  I think the proper command is either ";" or ";;".  

What's happening, if I remember correctly, is "&" tells the computer to run the command before *and* after the symbol.  Where the ";" or ";;" counterpart tells the computer to run the command following the symbol *after* the first command is run.  Which is exactly what I want.

Unfortunately my Google searches have been inconclusive on the subject at best.  Does anyone by chance have any light to shed on the situation?  I'll continue to try Googling it, but this is one of those things with very difficult search terms on a subject already lacking online documentation.

---

### Post by CharlesA on 2009-12-27
I must have done something differently when I wrote my script. I basically strung a bunch of commands together using "&&"

Like this:

```
sleep 5
#Create array directory and change owner and permissions
echo "Creating /array and setting owner and permissions..." && sleep 2
mkdir /array && chown charles:raid /array &&chown charles:raid /array/ && chmod 770 /array && echo "Completed." && sleep 5
#Create DVD backup directory and change owner and permissions
echo "Creating /dvdback and setting owner and permissions..." && sleep 2
mkdir /dvdback && chown charles:charles /dvdback && chown charles:charles /dvdback && chmod 770 /dvdback && echo "Completed." && sleep 5
#Create Doc backup directory and change owner and permissions
echo "Creating /docback and setting owner and permissions..." && sleep 2
mkdir /docback && chown charles:charles /docback && chown charles:charles /docback && chmod 770 /docback && echo "Completed." && sleep 5

```

I didn't use "&" at all.

I'd probably rewrite your script like this:

```
#!/bin/bash

# Backs up files, cleans out the junk, then turns off the computer

##### Backup #####
rsync -ruv --delete /media/files /home/dillan/bak

##### Clean #####
apt-get autoclean && apt-get clean

##### Shutdown #####
shutdown -h now
```

---

### Post by dillandriskell on 2009-12-27
> **CharlesA said:**
> I must have done something differently when I wrote my script. I basically strung a bunch of commands together using "&&"

That did the trick, thanks! :) Looks like I was overcompensating
:lolflag:
I tested it, and everything worked...theoretically.

It transferred all the files fine, sure.  But since the script has to be run as root, when I attempt to access the files under my normal user account later, all the files were locked.  Only accessible by one with root privileges.  That makes sense, the files were created by the root user.

Easy enough, I thought.  I'll just add **sudo chown dillan /home/dillan/bak/*** after the file transfer.  So it would now looks like this;

```


#!/bin/bash

# Backs up files, cleans out the junk, then turns off the computer

##### Backup #####
rsync -ruv --delete /media/files /home/dillan/bak
chown dillan /home/dillan/bak/*

##### Clean #####
apt-get autoclean && apt-get clean

##### Shutdown #####
shutdown -h now


```

However, here's the problem; it only gives the *top directories* permissions back to me.  Everything beneath it is still root!  Certainly you can see how long it would take to change the permissions in every directory of over 25 GB of files.  So now I'm trying to find a way around that.

The way I see it there's two options to find a fix.  Either there's some way to make chown change the permissions of *every* directory when I use "*", or there's a way to make **rsync -ruv --delete /media/files /home/dillan/.bak** (the file transfer/backup command) run as *me* and not root.  Both of those would fix my problem.  Unfortunately I can't run the whole thing as me, since **shutdown -h now** needs to be sudo.  And if I specify in the script itself to run (**sudo shutdown -h now**) it would no longer be automated, as I'd have to manually put in the password after all the other steps were complete.

I'm trying to find the answers on Google as well, but if anyone knows the way to achieve either of those workarounds it'd be very appreciated it you helped me out!

---

### Post by dillandriskell on 2009-12-27
Viva la Google!  I've found the answer!  I'm surprised I missed this in the man pages :confused:

```
Sudo chown -R dillan /home/dillan/bak
```All I needed was the -R to include the contents of the directory.

So I just tested it, and everything worked!  Success after debugging for a while is so nice isn't it?  Thank you everyone for your assistance, you all rock.  I don't know where I'd be without ubuntuforums! :)

EDIT: Here's the completed script, just for reference:

```


#!/bin/bash

# Backs up files, cleans out the junk, then turns off the computer

##### Backup #####
rsync -ruv --delete /media/files /home/dillan/bak
chown -R dillan /home/dillan/bak/

##### Clean #####
apt-get autoclean && apt-get clean

##### Shutdown #####
shutdown -h now


```

---

### Post by dillandriskell on 2009-12-27
Ohh!  One more thing I forgot.  I would also need to "safely remove" my external drive *and *wait for it to finish before shutting down my computer.  Is "Safely remove hardware" the same as "unmount"?  I remember I used unmount in 9.04 without consequence.

If that's the case then I just need to add **umount <name of drive>** to the script right?  Or is there another BASH command for safely removing hardware?  And how would I go about finding the name of the drive? :confused: I think I need to use something other than the name I gave it (files) and I think I can access it with some command like "ffdisk -l" or something like that.  Does anybody know what I'm talking about?

---

### Post by dillandriskell on 2009-12-27
Bump.

I found out that the proper term I was thinking of was **fdisk -l**, and the drive's name was /dev/sdb1.  Though I'm still not sure if I should be using /dev/sdb1 or just files.

---

### Post by Mister.Vash on 2009-12-27
I think you should be able to get rsync to preserve your user and group information.  Try

```
rsync --recursive --update --verbose --delete --perms --owner --group /media/files /home/dillan/bak
```

Just a note on the way I do it, I find in scripts it is easier to see what you did using the long options.  2 months from now, when you want to change something, the above options are a lot easier to read than rsync -ruvpog --delete

---

### Post by dillandriskell on 2009-12-27
> **Mister.Vash said:**
> I think you should be able to get rsync to preserve your user and group information.  Try

```
rsync --recursive --update --verbose --delete --perms --owner --group /media/files /home/dillan/bak
```Just a note on the way I do it, I find in scripts it is easier to see what you did using the long options.  2 months from now, when you want to change something, the above options are a lot easier to read than rsync -ruvpog --delete

I tried that and success! So thank you for that, I think I prefer just doing it that way as oppose to changing all the permissions then changing them back lol.  And I added the long options, as your logic behind that is right.  I've done that soo many times, I've got to get in the habit.

As far as safely removing it goes, I figured out it was in fact the same thing as unmount.  I also found out how to do it.  Which all it was is;

```
sudo umount <name of drive>
```

And you use the name shown right on the desktop when you plug it in (for me it was "files").  But here's the worst bit, after an hour of research I finally figured out that the computer unmounts it for me upon shutdown automatically, so it was completely unnecessary to explicitly tell it to do so. /facepalm

I'm pretty sure I've got this figured out now, so thanks again everyone for your help and putting up with me doing wayy more than I needed to lol.

---

