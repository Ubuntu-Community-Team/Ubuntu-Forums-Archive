---
title: "Add additional mount point in 11.04"
date: 2011-04-08
forum: General Help
---

### Post by YeeP on 2011-04-08
Hello, I just installed 11.04 beta yesterday and was following along with this article so I could setup a "Storage" partition and always have access to the same files in win 7 or ubuntu.
[http://lifehacker.com/#!5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/#!5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

The problem happens when you try to install and use ntfs-config and run it.
Here is the description from the article:

[QUOTE=lifhacker article]Finally! Head to the Applications menu and pick the Ubuntu Software Center. In there, search for "ntfs-config," and double-click on the NTFS Configuration Tool that's the first result. Install it, then close the Software Center. If you've got the "Storage" or Windows 7 partitions mounted, head to any location in Places and then click the eject icon next to those drives in the left-hand sidebar. Now head to the System->Administration menu and pick the NTFS Configuration Tool.

You'll see a few partitions listed, likely as /dev/sda1, /dev/sda2, and the like. If you only want your storage drive, it should be listed as /dev/sda3 or something similar--just not the first or second options. Check the box for "Add," click in the "Mount point" column to give it a name (Storage, perhaps?), and hit "Apply." Check both boxes on the next window to allow read/write access, and hit OK, and you're done. Now the drive with all your stuff is accessible to Windows and Linux at all times.[/QUOTE]

When I try to run the ntfs-config, I get the following.


[IMG]http://i440.photobucket.com/albums/qq123/YeeP79/ntfs-config_error.png[/IMG]

However, in the software center there is a note below the ntfs-config download saying:
[QUOTE=Software Center]It just so happens that this program is a newer and improved version, but very few people know about it. It's better to install the disk-manager.[/QUOTE]

So I downloaded the Disc Management program. When I run it I get the following:
[IMG]http://i440.photobucket.com/albums/qq123/YeeP79/disk_management_error.png[/IMG]

Any help would be much appreciated. I know there are errors in a beta, but if I can just do what I was trying to with the mount on boot, that would be much appreciated. I am not sure what ntfs-config has in it that is helpful.

Thanks.

---

### Post by seawolf167 on 2011-04-08
> **YeeP said:**
> I know there are errors in a beta


If you are using a pre-release non-stable version you could very easily have problems that no one here could solve. 

In a stable version, the general process is to


[LIST=1]
[*]resize a current partition creating room for a new partition
[*]format the new partition in NTFS (so Windows can read it)
[*]mount the new partition in /etc/fstab so it automatically mounts at boot
[*]profit
[/LIST]
In your screenshots, the ntfs program you listed just adds the correct /etc/fstab line for you. As for the user mount tool, you'll need to run that as root

```
gksu *program-name-here*
```

---

### Post by YeeP on 2011-04-08
Thanks for the info. I do have a partition that is strictly for this purpose. It is NTFS and I have taken all the other associated steps in that article. The reason why I listed that info, was in hopes there was a file to modify, instead of "needing" ntfs-config. I was unaware as to what I could modify to make the partition mount on every boot. That would take care of the problem at this point. 

Thanks for the good info, I will start working on it.  Also, I did try to report the error, but was told it could not report (see image). Where should I go to give this info? I just want to help the developers if I can.  :D

---

### Post by seawolf167 on 2011-04-08
Not sure about the reporting problem.

Once you format the "data" partition, all you need to do to automount it is add that /etc/fstab line.

If you want to try it, click the fstab link in my sig, else post the output of 

```
blkid
sudo fdisk -l
mount
```

here so we can help you.

---

### Post by Morbius1 on 2011-04-08
[1] Run the following command to see how the system sees your partitions:
```
sudo blkid -c /dev/null
```You'll get something that looks like this ( as an example ) :
> /dev/sdc1: LABEL="BACKUP" UUID="66E4DC83E4DC56C1" TYPE="ntfs" [2] Make a permanent home for the partition to live in:
```
sudo mkdir /media/Backup
```[3] Edit fstab as root:
```
gksu gedit /etc/fstab
```[4] Add the following line to the end of fstab:
```
UUID=66E4DC83E4DC56C1 /media/Backup ntfs defaults,nls=utf8,uid=1000,umask=000 0 0
```[5] Save fstab, exit gedit, and back in the terminal run the following command to test for errors and mount the new partition:
```
sudo mount -a
```If you get an error post it back here but if you got no output then it mounted it successfully.

---

### Post by YeeP on 2011-04-08
I got no error at the mount step (last step), but it looks like there may be some other issues after editing gedit. They dont look like anything I touched.

Going to reboot now to see if it mounts. Here is the process I ran, the media 

fstab file lines that are not commented out
```
UUID=a74711f9-5043-4157-bd3a-9f73a7bcce90 /               ext4    errors=remount-ro 0       1
UUID=29A8076B7C4B22EF /media/Storage ntfs defaults,nls=utf8,uid=1000,umask=000 0 0
```

errors I got after exiting gedit:
```
ryan@YeeP:~$ sudo blkid -c /dev/null
[sudo] password for ryan: 
/dev/sda1: LABEL="System Reserved" UUID="A8DC3DD9DC3DA30C" TYPE="ntfs" 
/dev/sda2: UUID="DE0E40C20E409585" TYPE="ntfs" 
/dev/sda3: UUID="a74711f9-5043-4157-bd3a-9f73a7bcce90" TYPE="ext4" 
/dev/sda4: LABEL="Storage" UUID="29A8076B7C4B22EF" TYPE="ntfs" 
ryan@YeeP:~$ gksu gedit /etc/fstab

(gedit:9333): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.574ETV': No such file or directory

(gedit:9333): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:9333): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.WA3DTV': No such file or directory

(gedit:9333): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:9333): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.Q199SV': No such file or directory

(gedit:9333): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```

Thoughts?

---

### Post by YeeP on 2011-04-08
Reboot works, mounts right away. Thanks for the help. 

One more thing, if you read that article, he has you removing the Documents, Pictures and so on from the left side of natilus. Then remaking them in the new "Storage" partition. I did this. I even deleted the original Documents and so on folders.  It remade the folders:

[IMG]http://i440.photobucket.com/albums/qq123/YeeP79/home_view.png[/IMG]

As you can see, if I clock on the documents in the center of the screen:
[IMG]http://i440.photobucket.com/albums/qq123/YeeP79/original_docs.png[/IMG]

Versus if I click on the new one that I made, which is on the "shared" parition
[IMG]http://i440.photobucket.com/albums/qq123/YeeP79/new_docs.png[/IMG]


Any way I can stop the OS from remaking these folders and force it to use the ones on the ntfs partition?


Thanks again for the help.

---

### Post by tredegar on 2011-04-08
Running linux from an NTFS partition, either for **/home** or **/** is just _not going to work_ properly.

Linux needs a linux-formatted filesystem (ext2,3,4, whatever) to function correctly. Not NTFS please.

Additionally, you are running 11.04 which has not been released yet, so it's not for the non-experts.

I think you need to read up on the basics before you are ready to manage the "cutting edge".

Best wishes.

---

### Post by YeeP on 2011-04-08
Maybe you should read my post. I did not say I was running linux from an ntfs partition. It is sitting on multiple partitions, one of which is ext4, another is ext3 and a swap. Maybe you shouldn't ASSume you know my setup from the small amount of information I have given.

Glad you got it figured out that you are an expert there champ.):P

---

### Post by seawolf167 on 2011-04-08
If you move the /home folder to an NTFS drive things won't work (example: NTFS doesn't store permissions), but you can move your Documents/Pictures/etc. to an NTFS drive.

I think the way to do this would be to copy the contents to the destination folder, then delete everything from the source folder and make a sym link connecting the two

```
ln -s /media/Storage/Documents ~/Documents
```

You should be able to do the same for your Pictures, Downloads, etc. folders (I wouldn't move your Desktop folder though)

---

### Post by Morbius1 on 2011-04-08
I'll be honest with you I couldn't quite follow what you or the link you provided are trying to do with the Documents, Pictures, etc....

If you have a Documents folder at /media/Storage/Documents and you want everthing to go to that partition when you use in in your home directory I would suggest "binding" them together.

Let's take an example and use the terminal to see if this is what you are trying to achieve:
```
sudo mount --bind /media/Storage/Documents /home/ryan/Documents
```This will "bind" the Documents folder on Storage to the Documents folder in your home folder.
[COLOR=Blue]*EDIT: Sorry there has to be a sudo in front of that mount command*[/COLOR]

If this is not what you want then unmount it:
```
sudo umount /home/ryan/Documents
```If that is what you want then one way to have this done at boot is to place that line ( [COLOR=Blue]without sudo[/COLOR] ) above the "exit 0" line in /etc/rc.local:

For example, in /etc/rc.local:
> mount --bind /media/Storage/Documents /home/ryan/Documents
mount --bind /media/Storage/Pictures /home/ryan/Pictures
mount --bind /media/Storage/Music /home/ryan/Music

exit 0

---

### Post by Morbius1 on 2011-04-08
Seawolf, I seem to be constantly stepping on your posts. My apologies. I have a bad habit of not checking to see if there were any other posts when I finish one of my rants. ;)

---

### Post by seawolf167 on 2011-04-08
> **Morbius1 said:**
> Seawolf, I seem to be constantly stepping on your posts. My apologies. I have a bad habit of not checking to see if there were any other posts when I finish one of my rants. ;)

Not a problem - besides, I like seeing other methods; always up for learning new things!

---

### Post by YeeP on 2011-04-08
> **seawolf167 said:**
> If you move the /home folder to an NTFS drive things won't work (example: NTFS doesn't store permissions), but you can move your Documents/Pictures/etc. to an NTFS drive.

I think the way to do this would be to copy the contents to the destination folder, then delete everything from the source folder and make a sym link connecting the two

```
ln -s /media/Storage/Documents ~/Documents
```

You should be able to do the same for your Pictures, Downloads, etc. folders (I wouldn't move your Desktop folder though)

Thats a good idea man. All I really wanted to do was have the "links" if you will, from inside the home view I have shown, point toward the Storage partition. I know that I have the storage ones already setup on the left side of the view and that should be good enough. Call me lazy, I just thought it would be cool to figure out how to get the OS to use those folders for the same process. I will try your idea. Thanks again.

---

### Post by YeeP on 2011-04-08
> **Morbius1 said:**
> Seawolf, I seem to be constantly stepping on your posts. My apologies. I have a bad habit of not checking to see if there were any other posts when I finish one of my rants. ;)

I just saw this, good thinking. I will give it a shot. Thanks for your awesome help guys. I love learning this stuff.

---

