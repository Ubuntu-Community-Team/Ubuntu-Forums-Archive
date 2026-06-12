---
title: "Problem with mounting hd partitions"
date: 2009-12-12
forum: General Help
---

### Post by kpfuser on 2009-12-12
Just finished installing Xubuntu 9.10 in an older laptop whose hd was wiped clean before the Xubuntu installation. The partition picture is as follows: One extended partition where Xubuntu is installed plus two empty primary ext2 partitions (sda1 & sda3) containing nothing at present and meant to be used for storing data. Unfortunately, when I boot Xubuntu, the primary partitions sda1 and sda3 do not appear on the desktop, which does not allow me to use them as intended. They both appear as /dev/sda1 and /dev/sda3, where it is shown that they belong to root.

1. How can I mount them so that I can use them as a non-root user?

2. Can I arrange for them to be mounted automatically each time I boot Xubuntu with permissions that allow their use by all users?

---

### Post by lmarmisa on 2009-12-12
First of all, I think that you sould reformat theses partitions using ext4 (or ext3) file system. Ext2 is a too old file system, IMHO.

If you want to mount automatically these partitions at startup, type the following commands:

```

sudo bash
mkdir /media/DATA1           #change DATA1 with other label if you wish (apply this change if fstab too)
mkdir /media/DATA2           #change DATA2 with other label if you wish (apply this change if fstab too)
gedit /etc/fstab

```Append these two lines at the bottom of file

```

/dev/sda1 /media/DATA1 ext4 errors=remount-ro 0 1
/dev/sda3 /media/DATA2 ext4 errors=remount-ro 0 1

```Save the file and close the editor.

When you restart your system the two partitions wll be automatically mounted.

---

### Post by kpfuser on 2009-12-14
lmarmisa,

I did as instructed. The two partitions do get mounted at bootup. However, their icons do not appear on the Desktop. Going through Applications-->Settings-->Xfce Settings Manager-->Desktop-->Icons shows that there is little, if any, hope to make separate icons for DATA1 and DATA2 appear on the Desktop. Ah well, I can live with this. In addition, files transferred to DATA1/2 come under root's ownership with permissions rwxr--r--. Of course using sudo chmod can change this but it would be more convenient if they were rwxrwxrwx or rwxrwxr-- from the start. Does this relate to 'ro' in the command

/dev/sda1 /media/DATA1 ext4 errors=remount-ro 0 1

Can this command be modified so as to produce rwxrwxrwx or rwxrwxr-- permissions automatically for the files saved/transferred in DATA1/2?

---

### Post by Leppie on 2009-12-14
to create the desktop icons, right click on the desktop and select "Create Launcher...", put desired "Name" and "Comment" and as "Command" put "Thunar /media/DATA1" and then click on icon to select an "Icon" to your likings, click "Create" and enjoy your desktop shortcut.

for the permissions part, try to add fmask and dmask to the mount:
```
/dev/sda1 /media/DATA1 ext4 errors=remount-ro,fmask=775,dmask=775 0 1
```

---

### Post by lmarmisa on 2009-12-14
GNU/Linux partitions have owners, groups and privileges. But this is not bad. Simply, you have to accept its rules. In this case, do not change the /etc/fstab, because it's correct.

If you want to define a directory MyData1 where you are the owner this is very easy:

```

sudo mkdir /media/DATA1/MyData1
sudo chmod your_user:your_group /media/DATA1/MyData1

```Done.

This new directory /media/DATA1/MyData1 is completelly equivalent to any other directory of your personal folder.

If you want to create a lynk in your Desktop pointing to this directory, type:

```

ln -s /media/DATA1/MyData1 $HOME/Desktop/MyData1

```Feel free to define other symbolic links if you want to insert your new dir in a different point of the structure of your personal folder.

According to the commands defined in this example, MyData1 could be addressed in two ways:

**/media/DATA1/MyData1**
**$HOME/Desktop/MyData1**


Best regards,

Luis

---

### Post by kpfuser on 2009-12-16
Leppie, lmarmisa,

Thank you for your replies

Leppie,

Following your instructions, I was able to create icons for DATA1 & DATA2 not on the Desktop, where I do not like to see icons, but in the top panel. Btw, is there some way to add a launcher for Terminal to this panel and transfer the Desktop icons there as well?

Unfortunately the command

/dev/sda1 /media/DATA1 ext4 errors=remount-ro,fmask=775,dmask=775 0 1

did not produce the advertised result. Copied as is (no space between comas and fmask/dmask), made all the files on DATA1&2 vanish. When a space was added to separate the comas from fmask/dmask, the files in DATA1&2 became visible again but their permissions remained unchanged, i.e., -rwxr--r--


lmarmisa,

I understand what you try to do but the command

sudo chmod your_user:your_group /media/DATA1/MyData1

fails to execute returning the error message

chmod: invalid mode: `kenxxx:kenxxx'

where kenxxx is my user name as well as the name of the group I belong by default. Did I miss something here? Can this be corrected somehow?

---

### Post by lmarmisa on 2009-12-16
I am sorry a lot, but I made a stupid mistake. The correct command is **chown**, not **chmod**.

Try this other command

```

sudo chown kenxxx:kenxxx /media/DATA1/MyData1

```

---

### Post by Leppie on 2009-12-16
> **kpfuser said:**
> Btw, is there some way to add a launcher for Terminal to this panel and transfer the Desktop icons there as well?
not sure what you mean, do you want an icon to open a terminal in your panel?

> **kpfuser said:**
> did not produce the advertised result.
have you tried just adding the rw or noacl options?

---

### Post by smilingfrog on 2009-12-16
If you want to put a Terminal Launcher icon in the panel, go to Applications>Accessories>Terminal and right click on the Terminal. Then choose 'Add this launcher to panel' and it will appear on your panel.

This will work for all programs. You can also experiment by right clicking on the panel itself and choosing 'Add to panel'. Lots of custom stuff if you want it.

You can add a 'Drawer' to the panel and then drag your desktop icons into that. Easy to access, not on your desktop.

G

---

### Post by kpfuser on 2009-12-18
Thank you all for your helpful responses!

lmarmisa,

The chown command went through without a hitch. Now I have DATA1/2 as icons in my top panel plus Data1/2 as icons on my Desktop. When I transfer a file from a different OS (Puppy Linux live CD) running in my laptop to Data1/2, I can access it when I run Xubuntu from the Desktop icon of Data1/2 or, for that matter, from the panel icon for DATA1/2. The permissions for such files remain -rwxr--r--! Well, so much for that. The laptop and the little green men inside win! Having 'read' permission as a limited user turns out to be good enough. If I need to modify such a file, I can save the modified version using 'save as,' which causes the saved file to be owned by the limited user. So I consider this issue as more or less "solved." Thank you very much for your help!

Leppie,
> have you tried just adding the rw or noacl options?
No I haven't because I am not too terribly well versed in such matters. It seems that to try the rw option, I should replace ro with rw when editing fstab. Is it so? What about the noacl option? Replace ro/rw with noacl?

smilingfrog,

Your suggested fixes are good but not for my old and cranky laptop (Presario 1500). When I go through the steps you outlined and then right-click on Terminal, a Terminal window opens just the same way as when I left-click on Terminal! The only way to add launchers to the panel is via right-clicking the panel,etc. Unfortunately to complete the steps, I need the command that launches the Terminal (Xfce Terminal Emulator 0.4.2). If you know this command and/or the command to create drawers, do let me know. How about a list of the commands to launch anything under 'Applications?"

Btw, I REALLY LIKE your avatar!!!

---

### Post by lmarmisa on 2009-12-18
If you don't like completely the present solution and you prefer to mount the disks with 777 privileges, try these options in the fstab file:

```

...
/dev/sda1 /media/DATA1 ext4 rw,nosuid,nodev,uhelper=hal 0 1
/dev/sda3 /media/DATA2 ext4 rw,nosuid,nodev,uhelper=hal 0 1

```

Now, you will be able to create your own new directories in /media/DATA1 and /media/DATA2 without root privlieges.

---

### Post by kpfuser on 2009-12-22
lmarmisa,

Thank you for your post. I put it to the test and it worked fine! So I deleted the subdirectories and symlinks for Data1/2 and now I am left with the automatically mounted DATA1/2 partitions, with file permissions -rwxrwxrwx, accessible through panel icons. This brings this whole affair to a very satisfactory conclusion. Thanks again for your help!

---

