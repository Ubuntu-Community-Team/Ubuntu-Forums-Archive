---
title: "Use ifuse instead of gvfs to mount device"
date: 2010-05-29
forum: General Help
---

### Post by Jim Danner on 2010-05-29
I installed **ifuse** (a utility to mount your iPhone or iPod touch via the USB cable) and I want this to be the default way my iPhone is mounted when I connect it.

Currently, when I connect it, it gets mounted by the gvfs (Gnome virtual file system) at ~/.gvfs/iPhone.

Either one change should be made (the 'default command to execute when this device is connected') or two changes (tell gvfs not to mount, and tell ifuse to automount). I don't know how I can get this to work.

---

### Post by Jim Danner on 2010-06-11
I got sort-of halfway with this, but I'll **need some help** to get the rest done.

What works is using ifuse to mount the device automatically when it is connected to the computer's USB port. What doesn't work is unmounting properly when I click on the eject button (or choose 'Unmount' in the context menu). I still have to enter the unmounting command *fusermount -u ~/iPhone* manually. Who knows **what happens when you click the eject button** next to a mounted file system in Nautilus?

Here are instructions to get mounting to work (all of this is only useful for jailbroken devices).
[LIST=1]
[*]Install ifuse:```
sudo apt-get install ifuse
```
[*]Create a script that does the mounting:```
sudo gedit /usr/local/bin/imount
```
[*]In that file, put the following command:```
sudo -u *jimdanner* /usr/bin/ifuse --root /home/*jimdanner*/iPhone/
``` but replace both occurrences of *jimdanner* with your own user name
[*]Save the file and close the text editor
[*]Make the file executable: ```
sudo chmod +x /usr/local/bin/imount
```
[*]Open the AFC mount settings file (as root):```
sudo gedit /usr/share/gvfs/mounts/afc.mount
```
[*]Edit the line that starts with *Exec=* by replacing */usr/lib/gvfs/gvfsd-afc* with */usr/local/bin/imount*
[*]Save the file and close the text editor
[*]Create the mount point: ```
mkdir ~/iPhone
```
[*]Restart the computer
[/LIST]

---

### Post by xtian88 on 2010-06-25
Works great but after doing this, I lost the ability to sync my iPhone to Rhythmbox and Fspot. Is there a way to make both work? I am using your method to transfer .IPAs.

Thanks!

Update:

I was able to fix this by unmounting the iphone first before running imount. I can now sync the iphone to rhythmbox and f-spot and at the same time access root.

---

### Post by martah26 on 2010-07-02
Hi 

Have been having a problem getting my iPhone 3G to mount in Lucid - not found in Rhythmbox or Amarok, then came across your thread. I have followed all your directions to the letter - but I keep getting this error

Unable to mount iPhone 

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

My system continues to try to connect but comes back with the same error - I don't know what the problem is but are there other settings I need to check? Or could it be due to the 'Tethering' issue? 

Many thanks for the Help.

---

### Post by martah26 on 2010-07-02
Hi again 

Mea culpa - I didn't read the start of your advice did I - that it was only for Jailbroken devices.

Now I shall have to reset for gvfs or can I stay with ifuse? If I can stay with ifuse what would I need to modify to make it work with the changes that I have done from following the earlier advice?

Many thanks

---

### Post by osarusan on 2011-01-25
If you have trouble (i.e. a dbus error) mounting your iPhone/iPad, run this in a terminal:

```
idevicepair unpair
```

That fixed it for me.

---

