---
title: "I'm very disappointed in Ubuntu"
date: 2011-07-27
forum: General Help
---

### Post by u0x on 2011-07-27
I'm newbie at Linux && English, I using command line "sudo -s" to be root

and using command "nautilus" to open my Nautilus Elementary with root

but while I manage my files, I pressed wrong button to "delete" my important folder

I thought that folder will going to Trash folder, but at the moment I click on Trash (in nautilus with root) my nautilus was broken, It was instant closed!!

I try to see at terminal, it show these message

> ** (nautilus:30221): CRITICAL **: nautilus_file_get_location: assertion `NAUTILUS_IS_FILE (file)' failed

(nautilus:30221): GLib-GIO-CRITICAL **: g_file_get_uri: assertion `G_IS_FILE (file)' failed
**
ERROR:nautilus-window-manage-views.c:819:begin_location_change: assertion failed: (location != NULL)
than, I try to search what is the path of trash folder..
and I found it is .Trash folder in each account

but in /root/ folder there are no .Trash folder for me..

where is my folder that I was deleted ? T_T

If I using Window$ I can go to recycle bin and restore it... how about my ubuntu?

With ubuntu I was deleted my important folder with one pressed, no confirm dialog, no restore, and no Trash folder at root?

---

### Post by flipper T on 2011-07-27
**_you_** deleted an important file & you are disappointed with ubuntu ???

stick with windows.

---

### Post by hakermania on 2011-07-27
Well, follow my advice please, you opened nautilus and deleted file as root and you searched your (simple) user's trash!
But the files are in root trash! Also, don't blame ubuntu for your own faults!
Before doing the following make sure you don't have any folder named 'files' on your desktop!
So, become root in a terminal and run these (DONT CHANGE ANYTHING):
```

cp -r /root/.local/share/Trash/files /home/$USERNAME/Desktop/
chown $USERNAME:$USERNAME /home/$USERNAME/Desktop/files

```After this, all your missing files (also probably files you had deleted in the past as root from nautilus) will be placed in a folder named 'files' on your Desktop.

---

### Post by u0x on 2011-07-27
> **hakermania said:**
> Well, follow my advice please, you opened nautilus and deleted file as root and you searched your (simple) user's trash!
But the files are in root trash! Also, don't blame ubuntu for your own faults!
Before doing the following make sure you don't have any folder named 'files' on your desktop!
So, become root in a terminal and run these (DONT CHANGE ANYTHING):
```

cp -r /root/.local/share/Trash/files /home/$USERNAME/Desktop/
chown $USERNAME:$USERNAME /home/$USERNAME/Desktop/files

```After this, all your missing files (also probably files you had deleted in the past as root from nautilus) will be placed in a folder named 'files' on your Desktop.

Ok, I'm sorry about my post.. but...

> root@homesmile:~# cp -r /root/.local/share/Trash/files /home/$USERNAME/Desktop/
cp: cannot stat `/root/.local/share/Trash/files': No such file or directory

T_T

---

### Post by CatKiller on 2011-07-27
> **u0x said:**
> I'm newbie at Linux && English, I using command line "sudo -s" to be root

Don't do this.

---

### Post by u0x on 2011-07-27
> **CatKiller said:**
> Don't do this.

Ok, but my mounted ext4 partition required root for handle files..

---

### Post by minerbog on 2011-07-27
> **u0x said:**
> 

If I using Window$ I can go to recycle bin and restore it... 

You cannot compare the two. Window$ by default assumes that every user is a kind of root user which is why it is full of security holes. Ubuntu on the other hand assumes all users as users unless otherwise stated so no-one can do major damage. Because of this (and a lesson I learn't the hard way :)) Ubuntu and any other Linux distro assumes that when you type "sudo" you know what you are doing!

So I suggest you learn a bit more about Ubuntu and Linux before 
A: You use sudo again
B: Criticise Ubuntu and Linux.

Happy learning.

Gavin.

---

### Post by hakermania on 2011-07-27
Weird, what kind of ubuntu do you use?
Also, remember the folder name and try the following as root (where folder_name place you actual deleted folder's/file's name):
```

cd /root
find . -name "folder_name"

```
Post back the output

---

### Post by nothingspecial on 2011-07-27
> **u0x said:**
> Ok, but my mounted ext4 partition required root for handle files..

Change the owner of the partition to your self.

It is possible that the deleted files are in the .Trash folder of the mounted partition. Maybe named .Trash-1000. Press Ctrl-H when in that partition.

---

### Post by u0x on 2011-07-27
> **hakermania said:**
> Weird, what kind of ubuntu do you use?
Also, remember the folder name and try the following as root (where folder_name place you actual deleted folder's/file's name):
```

cd /root
find . -name "folder_name"

```Post back the output

Nothing output.. I using Ubuntu 11.04

> **nothingspecial said:**
> Change the owner of the partition to your self.

It is possible that the deleted files are in the .Trash folder of the  mounted partition. Maybe named .Trash-1000. Press Ctrl-H when in that  partition.

Thanks everyone.. I don't know how to change the owner of the partition..

my deleted folder located /home/MyUSER/ << with nautilus as root

... I suppose my problem is my root didn't have trash !

when I open nautilus (by type sudo nautilus) as root and go to Trash (on left side)
nautilus is closed and on terminal show

> ** (nautilus:4429): CRITICAL **: nautilus_file_get_location: assertion `NAUTILUS_IS_FILE (file)' failed

(nautilus:4429): GLib-GIO-CRITICAL **: g_file_get_uri: assertion `G_IS_FILE (file)' failed

(nautilus:4429): GLib-GIO-CRITICAL **: g_file_equal: assertion `G_IS_FILE (file2)' failed
**
ERROR:nautilus-window-manage-views.c:819:begin_location_change: assertion failed: (location != NULL)

---

### Post by nothingspecial on 2011-07-27
> **u0x said:**
> Nothing output.. I using Ubuntu 11.04



Thanks everyone.. I don't know how to change the owner of the partition..

my deleted folder located /home/MyUSER/ << with nautilus as root

Change the ownership of the partition like this if ext4.

```
sudo chown -R $USER:USER /partitions/mountpoint
```

Get the mountpoint right and whatever you do, [COLOR="Red"]dont leave a space after the first /[/COLOR]

If you don't fully understand that, post back with the mountpoint before you try it.

---

### Post by nothingspecial on 2011-07-27
With nautilus go to filesystem, then root

Press Ctrl-H,

you should see a folder called .local

go in there and click share, then you should see Trash

---

### Post by u0x on 2011-07-27
> **nothingspecial said:**
> Change the owner of the partition to your self.

It is possible that the deleted files are in the .Trash folder of the mounted partition. Maybe named .Trash-1000. Press Ctrl-H when in that partition.

Ah, Thanks you! and every posts..

I give up hopes to recovery my folder, but I still need to know why my root didn't have Trash.. can any solution what I can check my root really have Trash?

---

### Post by CatKiller on 2011-07-27
> **u0x said:**
> Ok, but my mounted ext4 partition required root for handle files..

Then you've mounted it incorrectly for what you're trying to do.

Blundering around as root is not a solution to anything. Ever. Use of root should be surgical.

If you need to run a command as root, you precede that command with sudo. This is the best use case; you run one and only one command as root. You can still do significant damage.

If there's a graphical program that you need to run as root, you need to use *gksudo* since otherwise the program is run as root but with your user settings. This leads to programs that will subsequently only run as root because the configuration files are now not owned by the user. For example, ```
gksudo nautilus
```It is a good idea to make the file browser window when run as root hideously ugly so that you won't use it unless you absolutely have to.

If you need to run a series of commands as root and won't use sudo, the correct way to get a root terminal is to use ```
sudo -i
``` This will correctly set up root's environment so that you don't, for example, delete things and not know where they've gone.

Since the directory was on another partition, the Trash will be on that partition too. Probably hidden, and because of the uncertainty about environment it may or may not be .Trash-root.

```
sudo updatedb
sudo locate Name\ of\ file\ you\ deleted
``` may or may not help you locate the file.

---

### Post by u0x on 2011-07-27
> **nothingspecial said:**
> With nautilus go to filesystem, then root

Press Ctrl-H,

you should see a folder called .local

go in there and click share, then you should see Trash


Thanks but there are no Trash !!

[IMG]http://s4.postimage.org/5ze8az6iz/Screenshot_49.png[/IMG]

---

### Post by westie457 on 2011-07-27
Hello, I have learned something new today.
In the past when informing people to use 'gksudo nautilus' I have warned them to be very careful in what they are deleting as there is no recovery option. This thread has proved me wrong on that assumption however the recovery steps seem complicated to me. I think I will keep going with the warning "no recovery option". This I believe makes people take more care.

---

### Post by nothingspecial on 2011-07-27
> **u0x said:**
> Ah, Thanks you! and every posts..

I give up hopes to recovery my folder, but I still need to know why my root didn't have Trash.. can any solution what I can check my root really have Trash?

You need to change the owner of the partition to your user so you can manage your files as a user and not root, then it doesn't matter weather root has a trash or not.

How do you mount the partition?

---

### Post by u0x on 2011-07-27
> **nothingspecial said:**
> You need to change the owner of the partition to your user so you can manage your files as a user and not root, then it doesn't matter weather root has a trash or not.

How do you mount the partition?

I using gui tool in Mint linux live to seperate (resize) my ext4 ubuntu partition to new one,  then I login to Ubuntu new partition auto-mount with read-only (I try to change /home to new partition)

---

### Post by flipper T on 2011-07-27
bite the bullet

re install the os

it will take you 30 minutes

---

### Post by u0x on 2011-07-27
> **flipper T said:**
> bite the bullet

re install the os

it will take you 30 minutes

Thanks I going to do it.. may be with mint

---

### Post by u0x on 2011-07-27
> **CatKiller said:**
> Then you've mounted it incorrectly for what you're trying to do.

Blundering around as root is not a solution to anything. Ever. Use of root should be surgical.

If you need to run a command as root, you precede that command with sudo. This is the best use case; you run one and only one command as root. You can still do significant damage.

If there's a graphical program that you need to run as root, you need to use *gksudo* since otherwise the program is run as root but with your user settings. This leads to programs that will subsequently only run as root because the configuration files are now not owned by the user. For example, ```
gksudo nautilus
```It is a good idea to make the file browser window when run as root hideously ugly so that you won't use it unless you absolutely have to.

If you need to run a series of commands as root and won't use sudo, the correct way to get a root terminal is to use ```
sudo -i
``` This will correctly set up root's environment so that you don't, for example, delete things and not know where they've gone.

Since the directory was on another partition, the Trash will be on that partition too. Probably hidden, and because of the uncertainty about environment it may or may not be .Trash-root.

```
sudo updatedb
sudo locate Name\ of\ file\ you\ deleted
``` may or may not help you locate the file.

Thanks, what is different of "sudo -s" and "sudo -i"

---

### Post by CatKiller on 2011-07-27
> **u0x said:**
> Thanks, what is different of "sudo -s" and "sudo -i"

-s just launches a shell. -i simulates logging in as root, so it sets all the environment variables.

---

### Post by u0x on 2011-07-27
> **CatKiller said:**
> -s just launches a shell. -i simulates logging in as root, so it sets all the environment variables.

Thanks :popcorn:

I just try "sudo locate myfolder", there are nothing output

I try to logging as root (sudo -i) and create text file then deleted with "Delete button"

and then it so lost, there are really no Trash folder in my root system -_-''

---

### Post by CatKiller on 2011-07-27
You can generally find out about a command by reading the manpage, with ```
 man* command*
```

---

### Post by cybergalvez on 2011-07-27
> **u0x said:**
> I'm newbie at Linux && English, I using command line "sudo -s" to be root

and using command "nautilus" to open my Nautilus Elementary with root

but while I manage my files, I pressed wrong button to "delete" my important folder

I thought that folder will going to Trash folder, but at the moment I click on Trash (in nautilus with root) my nautilus was broken, It was instant closed!!

I try to see at terminal, it show these message

than, I try to search what is the path of trash folder..
and I found it is .Trash folder in each account

but in /root/ folder there are no .Trash folder for me..

where is my folder that I was deleted ? T_T

If I using Window$ I can go to recycle bin and restore it... how about my ubuntu?

With ubuntu I was deleted my important folder with one pressed, no confirm dialog, no restore, and no Trash folder at root?

You are the one who logged in as root, and deleted the file, can't blame ubuntu for doing things in an unsafe way

---

### Post by bodhi.zazen on 2011-07-27
> **cybergalvez said:**
> You are the one who logged in as root, and deleted the file, can't blame ubuntu for doing things in an unsafe way

Those who play with root eventually kill tree - Ancient Chinese Proverb.

If you deleted a critical file you may need to re-install. Sort of depends on what you deleted.

---

### Post by nothingspecial on 2011-07-27
I worry for this thread because I don't think the OP worded his title or his post in the best possible way.

He's even tried to edit the threads title to

> **I'm very excited using Ubuntu**

> **u0x said:**
> I'm newbie at Linux && English

And been very courteous in replying to any help

> **u0x said:**
> Ok, I'm sorry about my post..

> **u0x said:**
> 

Thanks everyone.. 

> **u0x said:**
> Ah, Thanks you! and every posts..


And anyway, I don't think he cares anymore

> **u0x said:**
> 
I give up hopes to recovery my folder

But I can see a lot of people reading, the title, first post and flaming.........

Anyway..

---

### Post by CatKiller on 2011-07-27
> **u0x said:**
> I just try "sudo locate myfolder", there are nothing output

Did you do the updatedb first? That's critical; it creates an index of the files in the filesystem tree which is then searched by the locate command. If you did, then I'm afraid that folder might be lost.

---

