---
title: "System is logging on as root"
date: 2011-03-07
forum: General Help
---

### Post by ewaynec on 2011-03-07
I am using Lucid lynx, 1 partition, Linux is the only OS, and I am the only user.
Everything is working fine until I click on "Places> File Browser" the system ask for root password.
 Then I enter the Root password and I can then go where ever I want. ( It does not do this every time, just most of the time.)
When I open File Browser the first things listed in the left pane are ROOT, DESKTOP, (which is the root desktop), then FILE SYSTEMS, etc.
I think all the little differences I am experiencing are a result of logging on as ROOT user. I think that when I open File Browser (I use this a lot) and it ask for the ROOT password I am then ROOT and remain ROOT until I log off (I never do, because I am the only user). When I am root, things will look and feel different than when I am logged on as Wayne, but there are some things that I cannot do as Wayne (such as open File Browser). I opened K3b to burn a disk and a window poped up saying "it is not wise to run K3b as root..."
If I am right, how do I fix it?

---

### Post by wojox on 2011-03-07
You'll have to read [RootSudo]("https://help.ubuntu.com/community/RootSudo"). Try disabling the root account. Did you give root it's own password?

---

### Post by ewaynec on 2011-03-08
I read the link you provided as well as some others. All of the articles talk about problems using "sudo", or what to do if sudo does not work. All the evidence says when File Browser ask for my password, I become root. If I create a folder the owner of that folder is "root". My problem is becoming root when I don't need to, or want to.

---

### Post by tredegar on 2011-03-08
I think your file associations are messed up. This seems to be easy to do with ubuntu.

Usually this is easy to fix, but because opening nautilus forces you to become root, you are going to have to edit the configuration file.

First, make sure you are not root (login as yourself, do not open nautilus)

Use gedit to open the file **~/.local/share/applications/mimeapps.list**

Find the line that starts **inode/directory=*something-that-it-should-not-be***
and edit so it reads as **inode/directory=nautilus-folder-handler.desktop**

Save the file.

Logout & back in again. Hopefully that will fix it.

---

### Post by tredegar on 2011-03-08
Just remembered the "clicky" way of doing this:

Open a terminal. Make sure you are *not* root. If you *are* root do ```
su - *yourusername*
``` Then you should be yourself.

Open a terminal. Start the file manager by typing **nautilus** on the terminal command line and pressing ENTER. When the file manager starts:

R-click any directory (folder)
Choose "Open with .... Other Application"
Choose "File Browser" from the list.
Click "Remember this". Click "Open"

Now close the windows. Should be fixed.

---

### Post by ewaynec on 2011-03-08
I tried your "clicky way", nothing changed, it still ask for the password when I open file manager.

 I tried the edit, I did not change anything because it looks sorta like what you said. Here is a copy of that line;

inode/directory=userapp-gksudo-VR2WQV.desktop;nautilus-folder-handler.desktop;firefox.desktop;nautilus

I remember when this happened, I was downloading some files that I was going to put on my USB thumb drive, and I noticed a file on the drive that I could not delete, so I decided to format. That got complicated, and we wont get into that but, finally got the drive formatted and started to copy files to it. I had file manager open in two windows one for the files I was copying and one for the USB drive. I was using drag and drop. Some where I think my finger stuttered while I was dragging, and everything went away. All the windows closed. I clicked on File Browser to start over and it ask for my password. Thats where I am now.
  Thanks, Wayne

---

### Post by tredegar on 2011-03-08
> I tried your "clicky way", nothing changed, it still ask for the password when I open file manager.
Did you logout, and back in again?
> I tried the edit, I did not change anything because it looks sorta like what you said. Here is a copy of that line;

inode/directory=userapp-gksudo-VR2WQV.desktop;nautilus-folder-handler.desktop;firefox.desktop;nautilus

In my post at #4 I said > Find the line that starts inode/directory=*something-that-it-should-not-be*
and edit so it reads as inode/directory=nautilus-folder-handler.desktop
Your line says ```
inode/directory=[COLOR="Red"]userapp-gksudo-VR2WQV.desktop[/COLOR];nautilus-folder-handler.desktop;firefox.desktop;nautilus
```
This is wrong. The reason you are being asked to log in as root is the red bit. Change the line as I suggested so it *only*  reads```
inode/directory=nautilus-folder-handler.desktop
```

Save the file, logout, login. See if it is better.

Let us know how you get on.

---

### Post by ewaynec on 2011-03-08
You have earned my undying gratitude. It now works as it should. What did I do, and if you can, what happened to cause it. (I know it is something I did, and I would like to not do it again).
  Again thank you.

---

