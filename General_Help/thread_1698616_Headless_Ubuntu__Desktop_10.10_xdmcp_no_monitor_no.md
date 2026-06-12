---
title: "Headless Ubuntu  Desktop 10.10 xdmcp no monitor no keyboard server"
date: 2011-03-02
forum: General Help
---

### Post by Rizla21 on 2011-03-02
First off i am not realy good at linux or ubuntu so this is just how i did it. Im a windows user and have no real knowledge of linux.

You may ask:
should i follow this guide from a obviously non tech savvy person?.. probably not.
Is this method safe and secure ? probably not
Will it work on my system? Who knows ... well you may.. if you try it. :p
Well it works for me.

First off BIOS

Check bios for the phrase "Halt on: All errors" or something like it.
Change to No errors ( may not be needed, some bioses seem to not like having no monitor or keyboard) probably not very safe.
Boot ubuntu desktop.
Next
Grub2
Open Terminal and paste this:
```
gksudo gedit /etc/grub.d/00_header
``` 
in menu click search -> find  -> enter this : recordfail and click find 4 times :p
Here is the code u need to find : 
```
if [ "\${recordfail}" = 1 ]; then
  set timeout=-1
```
Change "timeout=-1"  to "timeout=1" (just delete -) probably not safe..
This will save you alot of trouble if u decide to use the reset button.
then save..
Then in new or same Terminal paste this :
```
gksu gedit /etc/default/grub
```
Change the line to GRUB_HIDDEN_TIMEOUT=2  (it's probably set to 0 or-1 can't remember. ) 
save..

Then in new or same Terminal paste this :
```
sudo update-grub
```

Next WDM (WINGS Display manager)
Open synaptic package manager -> search -> wdm
install and choose WDM as default when asked... (i think it's needs to be default but don't know)
Open Terminal and paste this:
```
gksu gedit /etc/X11/wdm/wdm-config
```
Find 
```
# Don't listen for XDMCP
DisplayManager.requestPort:	0
```
Change to :
```
# Don't listen for XDMCP
DisplayManager.requestPort:	177

```
save...
Side note to change background image find this line :
```
DisplayManager*wdmBg:
``` and change the stuff after it to:
```
pixmap:/home/fatman/Pictures/Wallpaper/nerd.png
``` or something like it :p
This is my line:
```
DisplayManager*wdmBg:           pixmap:/home/bedwetter/Pictures/Wallpaper/fatgirl.png
```
save...

The login screen will be old style but with nice background depending on picture of course.

Then in new or same Terminal paste this :
```
gksu gedit /etc/X11/wdm/Xaccess
```

find : 
```
#*					#any host can get a login window
```
change to this :
```
*					#any host can get a login window
```
And this : 
```
#*		CHOOSER BROADCAST	#any indirect host can get a chooser
```
To this:
```
*		CHOOSER BROADCAST	#any indirect host can get a chooser
```
in other words remove the #
Tha lines may already be correct... and they may also be totally insecure.

Well i think thats it.. i use Xming to login from my windows pc
The only things connected to my headless "server" is power and lan cable.

All the settings i set here is what i use myself it can ofcourse be changed
to a degree and still work.

there can be problems with automounting , forcing you to press a key before u can log in with xdmcp so i added nobootwait to my disks in fstab.
I also removed the disk check with " 0 0 " on all disks, but this may not be needed (or safe) since we edited the grub to load ubuntu in 2 second even if there was a fail of some sort last boot or shutdown.


To edit fstab paste this to terminal:
```
gksu gedit /etc/fstab
```



This is my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# / was on /dev/sdb6 during installation
# swap was on /dev/sdb5 during installation
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
UUID=467e5794-b934-4752-8dde-5dd5c9328c64  /            ext4  errors=remount-ro    0  0  
UUID=5337131a-b513-4f81-8e7a-784a1caef21a /boot        ext3 defaults,nobootwait  0  0  
UUID=aa9df663-ef9d-48b8-9a44-7dffc22db4af  none         swap  sw                   0  0  
/dev/disk/by-uuid/bd827c09-75cb-40b6-8f6e-a5c4996d6873	/media/Bigdisk	ext4 user,nobootwait      0  0
/dev/disk/by-uuid/e5483550-b50f-4c81-8757-8a975383b013	/media/Biggerdisk	ext4 user,nobootwait      0  0
/dev/disk/by-uuid/de6b08f5-ac4f-442c-b30b-da75a0b6eb08	/media/Notsobigdisk	ext4 user,nobootwait      0  0
```

---

