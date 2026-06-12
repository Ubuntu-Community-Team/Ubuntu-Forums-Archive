---
title: "unable to switch user !!"
date: 2012-08-05
forum: General Help
---

### Post by mohanp06 on 2012-08-05
I am using Ubuntu 10.04 LTS.    There was some problem with my old user account, so I created a new one. I was copying files via 

sudo cp -r -d --preserve=mode,timestamps -T ~old ~new   (newbie: got this from google on how to copy old user to new in ubuntu)  from old to new account, when suddenly disk got full. 

There is a third 'user' account from which I freed 1.4G space. Now disk has 1.4G free space. I am logged into new account. I want to switch to old so that I can free some more disk space to complete the copy operation. When I click 'switch from new' login screen appears, but after I log in to other account, it does not log in but comes back to login screen showing list of users. 

I am new to all this and need to get out of this ASAP.

 Thanking in anticipation.. mohanp06 ubuntu 10.04 LTS Genome

---

### Post by unevenflow on 2012-08-05
A quick way is from terminal to use
**sudo nautilus**
A new nautilus will pop up and you can navigate to /home where all users are.From there you can cut/paste or copy/paste to wherever you want.After that again from terminal you can change the permissions of a folder and all the files in that folder from root to owner using
**chown -R user:user dir**
where _user_ your current user and _dir_ the path to folder
Hope that helps!

---

### Post by GreatDanton on 2012-08-05
^^ just to correct you; use **gksudo** instead of sudo for graphical apps.
Clarification: [http://crunchbanglinux.org/forums/topic/8468/please-clarify-sudo-vs-gksugksudo/](http://crunchbanglinux.org/forums/topic/8468/please-clarify-sudo-vs-gksugksudo/)

Regards.

---

### Post by mohanp06 on 2012-08-05
> **GreatDanton said:**
> ^^ just to correct you; use **gksudo** instead of sudo for graphical apps.
Clarification: [http://crunchbanglinux.org/forums/topic/8468/please-clarify-sudo-vs-gksugksudo/](http://crunchbanglinux.org/forums/topic/8468/please-clarify-sudo-vs-gksugksudo/)

Regards.

   when I do this, (i.e. use gksudo) terminal window shows 'No space left on device'  and a dialog pops up showing:  Failed to run nautilus as user root.  Unable to copy the user's Xauthorization file.

---

### Post by mohanp06 on 2012-08-05
> **unevenflow said:**
> A quick way is from terminal to use
**sudo nautilus**
A new nautilus will pop up and you can navigate to /home where all users are.From there you can cut/paste or copy/paste to wherever you want.After that again from terminal you can change the permissions of a folder and all the files in that folder from root to owner using
**chown -R user:user dir**
where _user_ your current user and _dir_ the path to folder
Hope that helps!
[B]
 A quick way is from terminal to use sudo nautilus A new nautilus will pop up and you can navigate to /home where all users are.From there you can cut/paste or copy/paste to wherever you want.  [/B]

I have opened this window, and I am at /home but---  

1. can I cut/paste to other (windows) drive, my linux partition is only 1.4 G free (almost full), and do I have to worry abt permissions in that case?

 2. In the previous cp operation some files have been copied and others not. How do I know which files are copied to new account and which are not and how do I account for these files?  
[B]
After that again from terminal you can change the permissions of a folder and all the files in that folder from root to owner using chown -R user:user dir where user your current user and dir the path to folder [/B]

This has gone over me :( I am unable to understand this part of your reply. Please elaborate...  :(

---

### Post by unevenflow on 2012-08-05
> **mohanp06 said:**
> [B]
 A quick way is from terminal to use sudo nautilus A new nautilus will pop up and you can navigate to /home where all users are.From there you can cut/paste or copy/paste to wherever you want.  [/B]

I have opened this window, and I am at /home but---  

1. can I cut/paste to other (windows) drive, my linux partition is only 1.4 G free (almost full), and do I have to worry abt permissions in that case?

 2. In the previous cp operation some files have been copied and others not. How do I know which files are copied to new account and which are not and how do I account for these files?  
[B]
After that again from terminal you can change the permissions of a folder and all the files in that folder from root to owner using chown -R user:user dir where user your current user and dir the path to folder [/B]

This has gone over me :( I am unable to understand this part of your reply. Please elaborate...  :(


1. YES you can you should navigate e.g. to /home/mohanp06 cut the files or folders you want and paste them to /home/mohanp07 that way you preserve your space
2.one way is to do it manually by checking the /home/mohanp0x files another is to use rsync like this
**sudo rsync -r --preserve -av --progress --delete /home/mohanp06/file_you_want  /home/mohanp07/file_you_want**
this will syncronize the folders and will delete any duplicates

As for chown -R user:user dir: lets say your user name is mohanp06 and you want to own the file in the path /home/mohanp07/file_you_want you should issue in teminal:
 **chown -R mohanp06:mohanp06 /home/mohanp07/file_you_want**
and then all files and subdirectories is owened by you
After finishing go from menu to users and groups make your new user administrator and delete your old account then again use **sudo nautilus** and navigate to /home folder use Ctrl+H to unhide the .TRASH FOLDER and right click delete to completely remove files and free up space in your hd
sorry for the reedits 
cheers

---

### Post by mohanp06 on 2012-08-05
well, I have done all that, also deleted my old user, well there wasn't any .trash folder even after pressing Ctrl+H, but firefox was not showing properly and desktop icons were also not showing properly, so I closed everything and restarted my PC, and now I am not able to log in !

Login screen colour has changed to blue-white from usual brown-magenta, and there is some message on top right in screen which shows something like 'Power users config files not properly set..." or something like tht.. Old account name is still showing up, but I am not able to log into any accounts...

---

### Post by unevenflow on 2012-08-05
reboot and press shift button repeatedly until grub menu shows up then with arrow keys choose recovery mode and and then from the new tab choose root shell or sth like that then type  **chown -R user:user /home/user/.***
remember replace user=your_username
then reboot
let me know if everything ok

---

### Post by mohanp06 on 2012-08-05
initially by mistake i typed _**sudo**_ chown -R ....instead of  chown -R.... in the recovery console and completed the command.
i restarted but the problem was still there.... 

then i restarted and typed chown -R... correct command, but still the problem persists.. 

btw I got the correct message this time on top right corner it was:

Install Problem! Config defaults for GNOME power manager have not been installed correctly.Please contact your system administrator.

Regds..

---

### Post by unevenflow on 2012-08-05
Again reboot and press shift button repeatedly until grub menu shows up then with arrow keys choose recovery mode and and then from the new tab choose root shell or sth like that then type
**apt-get purge gnome-power-manager**
and
**apt-get install gnome-power-manager**
i think this should do it

---

### Post by mohanp06 on 2012-08-05
i tried but problem is still the same...same blue-white login screen with samemessage on top right corner is showing up..

(note: i had to go to "**root shell with networking**" for apt-get install gnome-power-manager)

Regds..

---

### Post by unevenflow on 2012-08-05
do you have any live usb(ubuntu into it) to boot from?

---

### Post by mohanp06 on 2012-08-05
i dont have a live _USB_ as such but i do have a live _CD_ from which i can boot...

Regds..

---

### Post by unevenflow on 2012-08-05
ok boot from it and after you've copied everything you need to your windows drive or external hd(dont worry about permisions but don't copy config files hidden or not) then delete those files from your ubuntu then reboot and see if everything ok

---

### Post by mohanp06 on 2012-08-05
will try that..

---

### Post by mohanp06 on 2012-08-06
yes!...i transferred @14G data to other drive and yo!
the blue-white screen is gone...

now I am able to log in as new user with exactly all settings of my old user!

so seems it was just a free space issue!

plz comment how much % free space I should keep in ubuntu partition for smooth operation.

Thanks a lot...
cheers!

---

### Post by unevenflow on 2012-08-06
Hey, i'm glad that it worked for you!
in terminal type
**df -h**
and post the results
cheers

---

### Post by mohanp06 on 2012-08-06
"Filesystem" "Size" "Used" "Avail" "Use%" "Mounted on"
"/dev/sda5" "49G" "25G" "21G" "55%" "/"
"none" "971M" "276K" "970M" "1%" "/dev"
"none" "975M" "3.2M" "972M" "1%" "/dev/shm"
"none" "975M" "196K" "975M" "1%" "/var/run"
"none" "975M" 0 "975M" "0%" "/var/lock"
"none" "975M" 0 "975M" "0%" "/lib/init/rw"
"none" "49G" "25G" "21G" "55%" "/var/lib/ureadahead/debugfs"
"/dev/sda1" "30G" "29G" "793M" "98%" "/media/sda1"
"/dev/sda7" "81G" "76G" "5.3G" "94%" "/media/sda7"
"/dev/sda2" "40G" "39G" "1.1G" "98%" "/media/OS"
"/dev/sda3" "30G" "22G" "7.8G" "74%" "/media/STUFF"

---

### Post by unevenflow on 2012-08-06
I see that /dev/sda5 49G 25G 21G 55% / is only 49G including your home so you should store your big files in another partition and always leave about 8G free.
In the meantime you could do a
**sudo apt-get clean**
which will clear your apt-cache and save you some space and you could check baobab to see what's eating your space.
Another good idea would be to have a separate home partition if you ever or whenever reinstall so that your data will always be safe in case sth happens to your system again and you could also save time by just reinstaling only your system
so you see my system look like this
/dev/sdb1        15G  5,9G  8,4G  42% /
/dev/sda1        100G 80G   20G   80% /home  
cheers!

---

### Post by mohanp06 on 2012-08-06
Thanks so much!

I will try all that...

in addition to solving my problem, I have learnt so many new things about ubuntu which I would never know otherwise, and how to use the system in a correct way to get the best out of it. Its now that I am _beginning_ to understand how the system works!

---

