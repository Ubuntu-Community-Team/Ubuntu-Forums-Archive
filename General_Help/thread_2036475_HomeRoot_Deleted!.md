---
title: "Home/Root Deleted!?"
date: 2012-08-02
forum: General Help
---

### Post by JosephBeck on 2012-08-02
I was trying to remove the desktop icon from my sidebar, and switched to tree mode. Deleted it not knowing that tree mode deletes everything and moves everything around. I accidently copied home folder to my file system directory and deleted it out right away....only to learn that I had deleted my home folder, everything in it, ability to view trash, and ability to open file system folders etc. Is there any way to get the files back. I don't care that I'll have to reinstall Ubuntu to fix the rest of it but i really, REALLY, need the files that were in the home folder back. I cant access the Root .trash folder as I have revoke my permission to enter it by deleting my home folder. From what I've read the minute I logout of my computer I wont be able to log back in so im keeping it on. I looked at the Disk Usage Analyzer and it shows me as sstill having 50gigs used space so I dont think it fully deleted my data...how on earth do I get it back :(. Its years and years worth of photos and videos that I desperately need.

I need a real response that won't take days to get support like all my other help requests. This is urgent.

---

### Post by itagomo on 2012-08-02
yeah I think they are still on the .trash folder .. open Terminal (CTRL + ATL + T) and log in as root .. go to .trash

---

### Post by itagomo on 2012-08-02
can you still go to this path ~/.local/share/Trash/files/ ?

here are some possible locations..

**~/.local/share/Trash/files/ **
**~/.Trash**
**~/.Trash-XXXX**

**XXXX  **is your username

---

### Post by JosephBeck on 2012-08-02
> **itagomo said:**
> can you still go to this path ~/.local/share/Trash/files/ ?

No...it doesnt exist anymore :( I think im **** out of luck but the disk usage says its still on my hard drive and not gone. I know if I logout I wont be able to log back in. If it is still on my Hard Drive and Disk Usage isn't lying to me then I think what I'm about to do will help. Im making the ubuntu installer on my usb and ill go into the LIVE and access trash that way....I really hope everything is there. Some of these files are priceless to me, and to other people. I've had many problems with Ubuntu even if I like it over Windows, but after this I don't see myself using Ubuntu much longer. All I was trying to do was put the Home directory on my launcher (home on launcher doesnt show the home icon so was trying to fix that), identically moved it to file system, tried to delete it and erased everything.

---

### Post by itagomo on 2012-08-02
how about finding them?

sudo find / -name <filename> -print

it will look for files with the name <filename> starting from the / directory

---

### Post by itagomo on 2012-08-02
> **JosephBeck said:**
>  All I was trying to do was put the Home directory on my launcher (home on launcher doesnt show the home icon so was trying to fix that), identically moved it to file system, tried to delete it and erased everything. 

your using Unity, right? there's a different method of adding folders to launcher. you need to create a .desktop file or look for some examples in /usr/share/applications/ .. you need to open those files using gedit ..

try to read this page .. talks about a GUI app on adding files/folders to your launcher ..
[http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html](http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html)

---

### Post by JosephBeck on 2012-08-02
> **itagomo said:**
> how about finding them?

sudo find / -name <filename> -print

it will look for files with the name <filename> starting from the / directory

Can't find home, trash, .trash, anything.... I'm realling hoping the LiveUSB will let me access what I need to access....

---

### Post by itagomo on 2012-08-02
> **JosephBeck said:**
> Can't find home, trash, .trash, anything.... I'm realling hoping the LiveUSB will let me access what I need to access....

so there's really no folder with your username or there's no ```
/home/
``` folder?

and I'm not sure if LiveUSB will give you something different from what you're getting now .. just want to clarify, did you delete the /home folder by pressing DEL or right clicking then choosing move to trash, something like that?

---

### Post by JosephBeck on 2012-08-02
> **itagomo said:**
> so there's really no folder with your username or there's no ```
/home/
``` folder?

and I'm not sure if LiveUSB will give you something different from what you're getting now .. just want to clarify, did you delete the /home folder by pressing DEL or right clicking then choosing move to trash, something like that?

Delete. I used the LiveUSB to help fix my girlfriends computer when she had a windows error. For her, she couldnt get windows to run so I used the LiveUSB to access her files and save them to my usb so we could reinstall it without losing her files. If my files are still there i should be able to access them in the same way...I hope. Worth a shot. I really have no Home folder or anything, it was fully deleted and I cant access root to check the root .trash file to recover it. It erased me so stripped me of permission. Atm compiz is also crashed and i cant open a terminal. It messed up everything, so I have to wait till the download is done for the .iso then i can log off and deal with it and mount the iso with my other computer.

---

### Post by itagomo on 2012-08-02
> **JosephBeck said:**
> Delete. I used the LiveUSB to help fix my girlfriends computer when she had a windows error. For her, she couldnt get windows to run so I used the LiveUSB to access her files and save them to my usb so we could reinstall it without losing her files. If my files are still there i should be able to access them in the same way...I hope. Worth a shot. I really have no Home folder or anything, it was fully deleted and I cant access root to check the root .trash file to recover it. It erased me so stripped me of permission. Atm compiz is also crashed and i cant open a terminal. It messed up everything, so I have to wait till the download is done for the .iso then i can log off and deal with it and mount the iso with my other computer.

that's nice .. I was just thinking maybe the /home/<yourUsername> folder was moved to the Root's folder (**/root/**) .. you can still access the console by pressing CTRL + ATL + F1 .. it's called TTY .. i call it fullscreen terminal .. it will ask for you username & password ..

---

### Post by JosephBeck on 2012-08-02
> **itagomo said:**
> that's nice .. I was just thinking maybe the /home/<yourUsername> folder was moved to the Root's folder (**/root/**) .. you can still access the console by pressing CTRL + ATL + F1 .. it's called TTY .. i call it fullscreen terminal .. it will ask for you username & password ..

That is really cool and great to know how to do now. Sadly, I can't get into nautilus or start Compiz even when using it. Forgot to ask how to turn it off but I managed to find out by going through the Fx keys.

---

### Post by shamoon633206 on 2012-08-02
> **itagomo said:**
> can you still go to this path ~/.local/share/Trash/files/ ?

here are some possible locations..

**~/.local/share/Trash/files/ **
**~/.Trash**
**~/.Trash-XXXX**

**XXXX  **is your username


Thanks it works for me.......

---

### Post by itagomo on 2012-08-02
> **JosephBeck said:**
> That is really cool and great to know how to do now. Sadly, I can't get into nautilus or start Compiz even when using it. Forgot to ask how to turn it off but I managed to find out by going through the Fx keys.

Oh, sorry. **CTRL + ALT + F1** to **F6** will open **TTY** .. **CTRL + ALT + F7 ** will bring you back to Unity or normal session .. have you tried the commands I gave by going to TTY?

---

### Post by jocko on 2012-08-02
You should be able to make a new home folder for your user by booting into recovery mode.

Reboot your computer and hold down the shift button until you get the boot menu. Pick one of the lines ending with "(recovery mode)" and hit enter.
When you get the recovery mode menu, pick "drop to a root terminal" and hit enter.
Then type these commands:
```
mkdir -p /home
mkdir -p /home/[COLOR=Blue]username[/COLOR]
chown [COLOR=Blue]username[/COLOR]:[COLOR=Blue]username[/COLOR] /home/[COLOR=Blue]username[/COLOR]
reboot
```After that you should be able to log in and get a working session. All configuration files will be recreated from the default settings, so you will loose all your customized settings.

To see if you have any Trash folder anywhere on your system, run these commands:
```
sudo updatedb
locate Trash
```If you can't find your missing files in any Trash folder, there are some things you can do to recover deleted files. But before you have recovered the files, avoid writing to the hard disk. I would boot off a live cd to avoid overwriting deleted files on the hard drive. 

Photorec can recover many different file types (not only photos). To install and run it, run these commands (from a live cd, to avoid overwriting the files):
```
sudo apt-get install testdisk
sudo photorec
```If you have an extra hard drive or partition with enough space to contain the lost files, it is a good idea to let photorec place the recovered files on that one to avoid overwriting any recoverable files...

Good luck.

---

### Post by JosephBeck on 2012-08-02
> **jocko said:**
> You should be able to make a new home folder for your user by booting into recovery mode.

Reboot your computer and hold down the shift button until you get the boot menu. Pick one of the lines ending with "(recovery mode)" and hit enter.
When you get the recovery mode menu, pick "drop to a root terminal" and hit enter.
Then type these commands:
```
mkdir -p /home
mkdir -p /home/[COLOR=Blue]username[/COLOR]
chown [COLOR=Blue]username[/COLOR]:[COLOR=Blue]username[/COLOR] /home/[COLOR=Blue]username[/COLOR]
reboot
```After that you should be able to log in and get a working session. All configuration files will be recreated from the default settings, so you will loose all your customized settings.

To see if you have any Trash folder anywhere on your system, run these commands:
```
sudo updatedb
locate Trash
```If you can't find your missing files in any Trash folder, there are some things you can do to recover deleted files. But before you have recovered the files, avoid writing to the hard disk. I would boot off a live cd to avoid overwriting deleted files on the hard drive. 

Photorec can recover many different file types (not only photos). To install and run it, run these commands (from a live cd, to avoid overwriting the files):
```
sudo apt-get install testdisk
sudo photorec
```If you have an extra hard drive or partition with enough space to contain the lost files, it is a good idea to let photorec place the recovered files on that one to avoid overwriting any recoverable files...

Good luck.

Thank you for that information. Thankfully I have my files safe and sound and I did it in a non-installing stuff way and didnt use the LiveUSB. I was able to right click my desktop, click change wallpaper and it brought that up. I used that window to get to all settings, accounts, and made a second administrator account with password. I was able to hit my power button, select suspend, unsuspend and switch accounts. On the second account I was able to use terminal and the Gksudo nautilus command to open root and find my home folder. I can now move it from root trash to my desktop of my second user account and find a way to somehow replace it to my first account. Anyway to transfer files between user accounts without using a usb by chance >_> It is 27gb worth of files I need to transport. This experience has made me realize it is about time I buy a low sized external hard drive to back things up on monthly. Thank you both for the help again and showing me some new tricks.

---

### Post by itagomo on 2012-08-02
very nice you solved .. don't forget to mark thread as Solved ..

---

### Post by JosephBeck on 2012-08-02
> **itagomo said:**
> very nice you solved .. don't forget to mark thread as Solved ..


My mind is shot after figuring all that stuff out ( I was super stressed as it may be a small amount of files but their value is very high). How do I go about marking this as "Solved". This is my first time having to actually do so.

---

### Post by itagomo on 2012-08-02
go to your very first post ..  you'll see an an option **Thread Tools**, then select **Mark this thread as solved** ..

---

