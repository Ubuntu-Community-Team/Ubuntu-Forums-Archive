---
title: "why cant i bloody backup my home folder"
date: 2010-02-10
forum: General Help
---

### Post by qqqq1112 on 2010-02-10
went into my home folder, marked everything i wanted to backup (including the "." folders with the settings), did 'rightclick' 'compress' with .7z selected and an appropriate name as target.
--> Permission Denied

The frack??? its my bloody home folder?!

tried again with root. did 'sudo nautilus' and retried it.
--> No such File or Directory

What??? <snip> OS (ubuntu 9.10) cant even compress files no more?!

tried again with '.tar.gz' and different name
--> same result

what do?

---

### Post by Enigmapond on 2010-02-10
See this thread regarding permissions and just skip the .dmrc stuff and make sure all the folders in you home folder are all "yours". Just follow the chmod examples....this should fix it.

Cheers...

[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)

---

### Post by qqqq1112 on 2010-02-10
all the things in my folder are mine (looked at the permissions with ls -l -a, and if i leave out .dmrc it still errors out

---

### Post by 23dornot23d on 2010-02-10
Where are you doing the backup to .... does it exist ......

do you have write permissions to the place you are doing the backup to ?

Just this seems an odd message to get ...... seems like it would be related
to where you are trying to do the backup to ..........
_________________________________________________
tried again with root. did 'sudo nautilus' and retried it.
--> No such File or Directory
_________________________________________________

---

### Post by audiomick on 2010-02-10
I've got one called .dbus that belongs to root, and .nvidia-settings.rc and karmic.list and a folder called .ure

Don't know what any of them are good for....

If you go to edit> preferences and add the column "owner" to the viewing options on the fourth tab, you can see them really easily.
I've had the same problem, but gave it up "to be looked at another day" at the time.

Using "gksu nautilus" you have to make sure that you are pointing at your home folder and not the root home folder.

---

### Post by philinux on 2010-02-10
> **qqqq1112 said:**
> went into my home folder, marked everything i wanted to backup (including the "." folders with the settings), did 'rightclick' 'compress' with .7z selected and an appropriate name as target.
--> Permission Denied

The frack??? its my bloody home folder?!

tried again with root. did 'sudo nautilus' and retried it.
--> No such File or Directory

What??? <snip> OS (ubuntu 9.10) cant even compress files no more?!

tried again with '.tar.gz' and different name
--> same result

what do?

This has hacked me off too as it doesn't tell you which file is the problem.

all you get it this error after 2 or 3 seconds.

---

### Post by philinux on 2010-02-11
By a process of elimination I've narrowed the culprit to the .wine folder.

If you select all and then ctrl click the .wine folder to exclude it you can compress your home folder.

There's so many things in .wine that I haven't got the time to find the culprit or culprits. But some items do have weird permissions.

---

### Post by SecretCode on 2010-02-11
I was convinced there should be a better way than a "process of elimination". And this might help:

```
find ~ ! -readable
```
- subsitituting another directory for ~ if necessary.

---

### Post by aeiah on 2010-02-11
if you're wanting to back up everything, why dont you do an exact copy of the entire partition using dd?

---

### Post by ushills on 2010-02-11
Why not use rsync.

The command

```
rsync -a /folder to backup /location for backup
```

Will retain all your permissions allowing you to restore with the correct permissions.

---

### Post by audiomick on 2010-02-11
> **ushills said:**
> Why not use rsync.

The command

```
rsync -a /folder to backup /location for backup
```Will retain all your permissions allowing you to restore with the correct permissions.
given that there are folders/files belonging to root involved, would one have to run that with "sudo", or does rsync have a way of getting around that?

---

### Post by ushills on 2010-02-12
from memory rsync with the a switch preverves all permissions, however, if it flags an error by all means use sudo, however, you may then need to use sudo when restoring, a better alternative for backups is rdiff-backup, this keeps incremental copies and does not require sudo.  install is and man rdiff-backup it is very easy and versitile.

---

### Post by qqqq1112 on 2010-02-12
- there is no .wine folder because i dont use wine
- i dont know much about rsync, but i dont think that it will put all my app settings into one file
- if have full read/write access to my target location when i try to do the compression
- all the folders in my ~ belong to my user and my group (i dont know if all the subfolders are the same and some of those '.' folders have a bloated recursion of subfolders, but they are in MY home folder and SHOULD all belong to me

what would happen if i do 'sudo chown <my_user>:<my_user> -R ~/'
would this break <snip>? would everything belong to me? would i finally be able to do a fracking backup without getting a **Masters Degree in Computer Engineering** on this operation system????

---

### Post by philinux on 2010-02-12
> **qqqq1112 said:**
> - there is no .wine folder because i dont use wine
- i dont know much about rsync, but i dont think that it will put all my app settings into one file
- if have full read/write access to my target location when i try to do the compression
- all the folders in my ~ belong to my user and my group (i dont know if all the subfolders are the same and some of those '.' folders have a bloated recursion of subfolders, but they are in MY home folder and SHOULD all belong to me

what would happen if i do '**[COLOR="Red"]sudo chown <my_user>:<my_user> -R ~/'[/COLOR]**
would this break <snip>? would everything belong to me? would i finally be able to do a fracking backup without getting a **Masters Degree in Computer Engineering** on this operation system????

^ dont do that. You'll mess up dmrc and ICE authority files. You'll get errors logging in. As an aside you dont need sudo for your home directory

There must be a folder, for me it was .wine that is causing the problem.

This problem has niggled me for a while too.

---

### Post by audiomick on 2010-02-12
I agree with Phil. There will be a .something in there somewhere that belongs to root.
Did you do as I suggested and add an "owner" column  to the viewing options of nautilus? That and activate "view hidden files" and the ones belonging to root stick out like dog's bits.

---

### Post by fisheater on 2010-02-12
drama-free option: [http://backintime.le-web.org/](http://backintime.le-web.org/)

works well, easy, simple, tidy.

GL

---

### Post by philinux on 2010-02-12
> **audiomick said:**
> I agree with Phil. There will be a .something in there somewhere that belongs to root.
Did you do as I suggested and add an "owner" column  to the viewing options of nautilus? That and activate "view hidden files" and the ones belonging to root stick out like dog's bits.

It's worse than that. None of the files in my .wine were owned by root.

It's a mystery. :confused:

---

### Post by philinux on 2010-02-12
> **fisheater said:**
> drama-free option: [http://backintime.le-web.org/](http://backintime.le-web.org/)

works well, easy, simple, tidy.

GL

But I dont think it compresses files. The archive method would save space.

---

### Post by audiomick on 2010-02-12
> **philinux said:**
> It's worse than that. None of the files in my .wine were owned by root.

It's a mystery. :confused:
Hmmm, that is odd.

 In my case, and on another computer I look after for a friend, there were definitely .owned_by_root things in there causing exactly this problem...

---

### Post by philinux on 2010-02-12
> **audiomick said:**
> Hmmm, that is odd.

 In my case, and on another computer I look after for a friend, there were definitely .owned_by_root things in there causing exactly this problem...

I did a full chown on the darn folder too.

---

### Post by amac777 on 2010-02-12
Perhaps try running the tar command from the command line so you can see on which file it gives the error. Run this in your home directory to backup everything:

```
tar -cvzf backup.tar.gz --exclude=backup.tar.gz .
```

(note the exclude is there so tar doesn't try to backup the backup file as it's making it.)

---

### Post by SecretCode on 2010-02-12
qqqq, please run this command in a terminal window and list the results if any in a post here:

```
find ~ ! -readable
```

Don't use sudo.

The permissions error you get can only relate to read permissions, as far as I can see, and the above command should list exactly those files.

For comparison I get:
```
$ find ~ ! -readable
/home/joe/.wine/dosdevices/g::
/home/joe/.wine/dosdevices/e::
/home/joe/.wine/dosdevices/f::
/home/joe/.Xauthority
/home/joe/backups/home/joe/.mozilla/sunbird/dixzhjq0.default/lock
/home/joe/backups/home/joe/.mozilla/firefox/1694veco.One/lock~20100211-121842
/home/joe/backups/home/joe/.mozilla/firefox/1694veco.One/lock
/home/joe/.mozilla/firefox/1694veco.One/lock
/home/joe/.joe_state
```

---

### Post by qqqq1112 on 2010-02-12
```

~/.googleearth/instance-running-lock
~/.gnunet/fsui/gnunet-gtk
~/.google/picasa/3.0/drive_c/Program Files/wine_gecko
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/runtime
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/plugins
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/cdautorun
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/buttons
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/Picasa3.exe
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/PicasaPhotoViewer.exe
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/moviethumb.exe
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/GoogleUpdaterService.exe
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/qtsupport.dll
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/update
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/web
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/Uninstall.exe
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/PicasaUpdater.exe
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/i18n
~/.google/picasa/3.0/drive_c/windows/inf
~/.google/picasa/3.0/drive_c/windows/fonts
~/.google/picasa/3.0/drive_c/windows/profiles/All Users/Start Menu/Programs/Picasa 3
~/.google/picasa/3.0/generic.ppd
~/.mozilla/firefox/ux986lqa.default/lock

```hmm, picasa should be uninstalled

why are there items in my darn homefolder that I dont own anyway?
if its not mine it should go somewhere else on the bloody system!
who designed this ****?

Update:
deleted the entire ~/.google folder, so the list grew shorter
still errors out of the compression though and i am not sure i should delete the other ones

---

### Post by Dragonbite on 2010-02-12
Picasa runs in Linux under Wine which explains things some.

---

### Post by SecretCode on 2010-02-12
> **qqqq1112 said:**
> ```

~/.googleearth/instance-running-lock
~/.gnunet/fsui/gnunet-gtk
~/.google/picasa/3.0/drive_c/Program Files/wine_gecko
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/runtime
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/plugins
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/cdautorun
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/buttons
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/Picasa3.exe
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/PicasaPhotoViewer.exe
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/moviethumb.exe
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/GoogleUpdaterService.exe
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/qtsupport.dll
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/update
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/web
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/Uninstall.exe
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/PicasaUpdater.exe
~/.google/picasa/3.0/drive_c/Program Files/Google/Picasa3/i18n
~/.google/picasa/3.0/drive_c/windows/inf
~/.google/picasa/3.0/drive_c/windows/fonts
~/.google/picasa/3.0/drive_c/windows/profiles/All Users/Start Menu/Programs/Picasa 3
~/.google/picasa/3.0/generic.ppd
~/.mozilla/firefox/ux986lqa.default/lock

```

who designed this ****?
Google and Mozilla, by the looks of it...


> **qqqq1112 said:**
> deleted the entire ~/.google folder, so the list grew shorter
still errors out of the compression though and i am not sure i should delete the other ones

If you close firefox that lock file should disappear. I don't know anything about gnunet.

---

### Post by qqqq1112 on 2010-02-12
alright...

closed firefox, deleted entire .gnunet folder, deleted the lock in the google earth folder, and tried to compress with .7z

--> errored out with a fancy new error message (see picture)

tried again with ineffective .tar.gz and it worked, sort of, 

now i have a 300 mb settings blob, just as i like it ... well almost, coz it's not  .7z and i needed to delete the settings mentioned before to get to this point (not to mention the entire thread).

User friendlyness my ,<Snip>!

And why is .7z broken???

---

### Post by rHBa on 2011-01-08
WARNING: The following worked for me in Jaunty, YMMV!

I was trying (unsuccessfully) to backup my home folder today and didn't see any files/folders owned by root (or any other user) but, I suspect, some were 'locked' because they were still in use by Gnome or some other process.

I figured that if I could log in as another user with permissions to access the target user's home folder while that target user was logged out then those files/folders would be unlocked. As I only have one normal user configured on my installation I couldn't use sudo (because I would have to be logged in as the target user, meaning that users files could be locked) so my only choice was to create a password for the root user:

# sudo passwd root

The next problem was that (in Jaunty anyway) you can't just log in as root, you have to start as a normal user. The solution to this conundrum is to open tty1 with CTRL+ALT+F1 and log in as root (using 'root' as the username and the password you just created in the last step). Next, instead of forcing your normal user to logout (with pkill -KILL -u username) which will also kill the root user's login and send you to the Gnome login screen, you should stop Gnome with:

# /etc/init.d/gdm stop

Your normal user's Gnome session is now stopped (make sure you have quit any applications with unsaved documents before this point). Now you should be able to backup your normal user's home folder with:

# tar -cvsf /destination/path/username_home_backup.tar.gz /home/username/

Once the backup is done you will probably find that CTRL+ALT+F7 results in a blank screen because Gnome is stopped (not sure about this, I'd expect it to start itself but it didn't seem to in my case, maybe I just needed to be more patient) so you can restart Gnome with:

# /etc/init.d/gdm start

This will send you back to the Gnome login screen, you should login as your normal user.

Finally, in the first stage of this process we created a password for the root user which, security wise, is generally considered a BAD THING. So we should remove the root user's password with:

# sudo passwd -l root

Hope this helps somebody...

---

