---
title: "How-To: Create a Unity Launcher to Mount (Jailbroken) iOS Root Filesystem"
date: 2011-12-05
forum: General Help
---

### Post by nyteryder79 on 2011-12-05
So you jailbroke your iOS device and want to browse the iPhone's root filesystem.  Well, with Ubuntu, you're in luck.  After using this guide, you'll be able to browse your iPhone's filesystem in Nautilus the way you browse your own computer's filesystem.

Example: 
[IMG]http://i.imgur.com/kEbbN.png[/IMG]

And I'll show you how to make a Unity Launcher to do this easily in the future, like so:

[IMG]http://i.imgur.com/SZEFI.png[/IMG]

If you have not done so, you will need to install the package, "afc2add" to enable root filesystem access through afc.

Before we begin with your Ubuntu desktop, you'll need to install ifuse to mount your iOS device.  Just run the following:

```
sudo apt-get update && sudo apt-get install ifuse
```

Next, download the following package I made which has the icon, scripts, and application launcher for Unity:

[http://www.mediafire.com/?5aea7faznnaqd48]("http://www.mediafire.com/?5aea7faznnaqd48")

Extract the files to your desktop, then navigate to the iPhone-Unity-Launcher folder.  We will need to make some edits here to get everything working properly on your system.  Before we edit though, let's move some things around.  Open a terminal and run the following:

```
sudo mv ~/Desktop/iPhone-Unity-Launcher/pixmaps/iPhone1.png /usr/share/pixmaps/

mkdir ~/.scripts

mv ~/Desktop/iPhone-Unity-Launcher/Scripts/* ~/.scripts/

chown 775 ~/.scripts/mount_iPhone.sh

chown 775 ~/.scripts/unmount_iPhone.sh
```

OK.  Now that we have the files where we need them, we need to edit the launcher appropriately.  All you need to do is open gedit, and drag the file "Mount iPhone Root Filesystem" into gedit, or run the following:

```
gedit ~/Desktop/iPhone-Unity-Launcher/iPhone.desktop
```

You need to change "[USERNAME]" to your own user name in the "Exec" path under the Mount Shortcut Group and Unmount Shortcut Group.  For example, if your username was "linus", you would change:

```
Exec=/home/[USERNAME]/.scripts/mount_iPhone.sh
```

To:

```
Exec=/home/linus/.scripts/mount_iPhone.sh
```

When finished, click save, then run the following:

```
mv ~/Desktop/iPhone-Unity-Launcher/iPhone.desktop ~/.local/share/applications/
```

And lastly, we need to make a mount point for your iPhone.  So run the following:

```
mkdir ~/iPhone
```

Now, all we have to do is add the application to the launcher:

```
nautilus ~/.local/share/applications
```

Select the app which will either have the name, "Mount iPhone Root Filesystem" or the name, "iPhone.desktop".  Drag that to the Unity launcher and drop it in.

You should now have an iPhone icon in the launcher.  All that's left is to connect your jailbroken iOS device (with afc2add installed), right-click the launcher and select "Mount iPhone".

---

### Post by squigish on 2011-12-19
What iOS devices (and firmware versions) have you tested this on?  Everything I can find about afc2add is at least a year old, and refers to hardware like the first generation iPhone.  Does this still work with newer hardware?

---

