---
title: "is there a way to separate home folders from configuration folders?"
date: 2011-02-16
forum: General Help
---

### Post by tanoloco on 2011-02-16
Hi guys,

I would like to separate somehow all configuration files (those hidden staff) from home folders.

I have two partitions with ubuntu installed and I created a third partition to store my homes in common between them. So I created same users in both ubuntus and moved users homes into the third common partition following this clear howto

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

so now I boot into firts ubuntu and I can reach the same users folders I could reach as I booted into the second ubuntu.

The "problem" is that I only wanted to move those visible folders as Pictures, Videos, Documents, Download .. and user folder itself ... but I have moved in this manner ALL the hidden folders as well .. those are created and managed by programs installed for configuration purposes I guess .. but I don't want to move them!

I would like to leave them in their original partition, simply because I can have different version of programs installed between the two ubuntus, as well as ubuntu version itself could be different, or I can plan to completely re-format one ubuntu and install it again, or to install a different distro from which I would love to continue pointing to the same home folders and so on ... there could be a lot of conflits!

So I think it's better to move only my staff as jpg, mp3, doc whatever but leave configuration back stored within their original os.

As far as I can imagine there could be two solutions:
a) tell somehow ubuntu to store all its configuration not under /home/user folder but under let's say /conf/user folder and then move only the visible folders to the common partition which will be mounted as /home and leave back hidden folders under /conf.
Is it a good idea? How could it be done?

b) tell somehow ubuntu a new path for each folder I would like to move. So for example I can say the Document path is not more /home/user/Documents but /media/common-partition/user/Documents and so on for all the other folders I want to move as Pictures, Music etc .. and then fstabbing to have common-partition auto-mounted on boot.
In this way configuration files will be stored under /home/user on the boot partition and I can have the other folders stored on the third common partition. But how can I set the path for those folders I want to move (and have them correctly listed under the places menu)?

Any suggestion, or other ideas, greatly appreciated! :)
Sorry for my long post

---

### Post by mikewhatever on 2011-02-16
Configuration files must be in the home folder. If you want to have Documents, Photos and Videos elsewhere, store them on a separate partition, aka data partition.

---

### Post by tanoloco on 2011-02-16
> **mikewhatever said:**
> Configuration files must be in the home folder. If you want to have Documents, Photos and Videos elsewhere, store them on a separate partition, aka data partition.

Hello,

thank you for you reply.
so your vote is for my "b" option :) .. in this case, do you know how to tell ubuntu the new path for those folders. I tried with symbolic links but still no luck on it.

I mean: I can create a user folder on a separate common partition and store Documents, Photos and so on in it, and leave configuration files under my original home folder, as you say.
But then how to have those folders correctly listed under the "places" menu for example?
It would be nice to have something as a symbolic link: if someone try to reach /home/user/Documents he will be pointed to /media/common-partition/user/Documents ..
but I cannot make it work

---

### Post by tanoloco on 2011-02-16
So I solved in this way (still not sure it's the best solution):

1. modified fstab in order to auto-mount a common-partition on boot.

2. created new directories on the common-partition, aka /media/common/user/Documents

3. changed accordingly ~/.config/user-dirs.dirs

4. edited and changed accordingly the nautilus bookmarks opening a window and go to Bookmarks > Edit Bookmarks

5. rebooted

now I have all my data stored on the common partition, while my hidden configuration folders still remains back in their original install partition.

Cheers

---

### Post by gandaran on 2011-02-16
> But then how to have those folders correctly listed under the "places" menu for example?
bookmark them in nautilus file browser, you can have any drive or partition and folders on the places menu.
I use a disk partition for all my files, the home folder is only for work and keep a backup of important configurations in the file partition and if I have to reinstall ubuntu I reformat the root and home partition without worrying loosing anything.

---

### Post by tredegar on 2011-02-16
> It would be nice to have something as a symbolic link: if someone try to reach /home/user/Documents he will be pointed to /media/common-partition/user/Documents ..
but I cannot make it work

First, make sure your files are backed up.
Then try these steps:

1] Connect the drive. I am _assuming_ the partition has a linux filesystem. If not stop now.

2] Make a directory on it to hold the shared **Documents** **Pictures** etc.
```
mkdir /media/common/shared
```
3] Make the permissions so everyone can access the **shared** directory
```
chmod 777 /media/common/shared
```
4] Copy your Documents there
```
cp -a /home/username/Documents /media/common/shared
```
5] Make sure they are really there
```
ls /media/common/shared/Documents
```
6] If so you can now completely remove your Documents directory from your home
```
rm -r /home/username/Documents
```
7] Now make a link from your home to the shared directory
```
ln -sT /media/common/shared/Documents /home/username/Documents
```
Now you should see your documents in /home/username/Documents even though they are on the common partition.

Do the steps 4-7 for your other usernames and directories you wish to have in common.

Edit: I type too slowly. Looks like you have the problem fixed.

---

### Post by tanoloco on 2011-02-16
Thank you all for sharing your tips!

So I can add a "point 6" to my previous list:

6. remove old unwanted folders under home and create a symbolic link instead

```

cp -av /home/user/Documents /media/common/home/user
sudo rm -R ~/Documents
ln -sT /media/common/home/user/Documents /home/user/Documents

```

that complete the scenario I suppose.

Thanks again! Good brainstorming! :)

---

### Post by tanoloco on 2011-02-16
So the complete howto could be:

1. create a new partition into where store your home folders, let's say it's labeled "home"

2. create a mounting point under /media to mount home partition
```
sudo mkdir /media/home
```chown and chmod it according to your taste

3. modify fstab to auto-mount home partition at boot

```
gksudo gedit /etc/fstab
```add a line like:
```
/dev/sdb5 /media/home ext3 defaults,errors=remount-ro 0 1 
```change it according to your case
I point at it using sdb5 instead of uuid to avoid listing it twice under places menu (it's a known bug)

mount it:
```
sudo mount -a
```4. create as many folders as you need onto home partition
```
cd /media/home
sudo mkdir user
cd user
sudo mkdir Documents
sudo mkdir Music
...
```5. change default paths to new paths
```
gedit ~/.config/user-dirs.dirs
```change for example
```
XDG_DOCUMENTS_DIR="$HOME/Documents"
```to 
```
XDG_DOCUMENTS_DIR="/media/home/user/Documents"
```6. edit and change accordingly the nautilus bookmarks opening a window and go to Bookmarks > Edit Bookmarks

7. move your data if any
```
cp -av /home/user/Documents/ /media/home/user
```8. make symbolic links which can be useful while browsing using a nautilus window
```

sudo rm -R ~/Documents
ln -sT /media/home/user/Documents /home/user/Documents
```9. reboot and enjoy :)

---

### Post by tredegar on 2011-02-16
Once you have made the link(s) you do not need to mess with **~/.config/user-dirs.dirs** because **$HOME/Documents** is a still perfectly valid path, except that it is a link to a directory, not a directory, and this is transparent to the user.

To be picky, step 9 (reboot) isn't needed. This is linux, not windows. Pleased you got it sorted.

---

### Post by tanoloco on 2011-02-16
> **tredegar said:**
> Once you have made the link(s) you do not need to mess with **~/.config/user-dirs.dirs** because **$HOME/Documents** is a still perfectly valid path, except that it is a link to a directory, not a directory, and this is transparent to the user.

To be picky, step 9 (reboot) isn't needed. This is linux, not windows. Pleased you got it sorted.

mmm .. from a working point of view you're right: I can do symbolic links as you've shown, and change nautilus bookmarks, to have everything working right, without having to change users-dirs.dirs, but I think this is needed to change the icons of the folders.
At least that's my experience: if you want/need to change the folder icons of the new path as they are shown under the (old) home folder you need to set their new path in users-dirs.dirs 

So I thought I need to reboot (or end session) to make user-dirs.dirs reload, but in this case you're completely right: it's not needed! :) any change on user-dirs.dirs is done while saving.

So, just forget to reboot!

I already noticed there's some more to deal with the trash-can behaviour and the ubuntuone folder but I'll check that on my next free time!

Cheers

---

### Post by tanoloco on 2011-02-16
mmm .. you made me be wrong!
Reboot (or end session) is needed to make Desktop refresh with the content on the new path, according to new settings on user-dirs.dirs.
I don't know if there's a command to refresh the desktop, so I simply reboot or end my session.

---

### Post by tredegar on 2011-02-16
Trash is in a dot-directory.
Mine is at```
/home/tred/.local/share/Trash/expunged
/home/tred/.local/share/Trash/files
/home/tred/.local/share/Trash/info

```
So you'll have to copy over those files one at a time, then delete the originals, then make links in your home directory pointing to the ones on the shared partition. But I do not use trash or ubuntu one.
> I don't know if there's a command to refresh the desktop, so I simply reboot or end my session. 
Just logout, then login again, should do it.

---

### Post by tanoloco on 2011-02-16
Hey! Thank you for all your help!

I found some extra time to fix what I noticed:

a)
I think it's better to mount home partition under /mnt rather than /media
to avoid it to be listed under places menu and a link created on the desktop

b)
for the trash the root of home partition must be writable so I did
```
sudo chown root:users /mnt/home
sudo chmod 770 /mnt/home
```
while all my users are members of users group .. you can choose 775 if you prefer

c) 
to change ubuntuone folder I
stopped the daemon
```
[FONT=monospace]u1sdtool -q[/FONT]
```
and changed the config file
```
gedit ~/.config/ubuntuone/syncdaemon.conf
```
added
```
root_dir = /mnt/home/user/UbuntuOne
```
under [__main__]

(of course I created this folder before)
as explained here:

[http://ubuntuforums.org/showthread.php?t=1291425&page=2](http://ubuntuforums.org/showthread.php?t=1291425&page=2)

and rebooted :D

while the idea to tweak around user-dirs.dirs is given by
[http://ubuntuforums.org/archive/index.php/t-955432.html](http://ubuntuforums.org/archive/index.php/t-955432.html)
and
[http://ubuntuforums.org/showthread.php?t=1001206&page=3](http://ubuntuforums.org/showthread.php?t=1001206&page=3)

just for credits ..

---

### Post by tredegar on 2011-02-16
You worked hard at this one (& didn't need much help).
Thanks for posting the follow-up.
Pleased you got it working!

---

### Post by tanoloco on 2011-02-16
thinking together just make things easier!

\\:D/

---

### Post by tanoloco on 2011-02-16
sadly ubuntuone seems not syncing out of home folders at the moment!

---

