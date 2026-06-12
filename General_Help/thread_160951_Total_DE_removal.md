---
title: "Total DE removal"
date: 2006-04-16
forum: General Help
---

### Post by truNWA on 2006-04-16
I installed KDE and XFCE for experimentation and i want to know.... is there a way to remove these and all software installed along with them?

---

### Post by Sutekh on 2006-04-16
You can remove Kubuntu fully this way

[HowTo: Fully uninstall the kubuntu-desktop meta-package](http://www.ubuntuforums.org/showthread.php?t=96048)

There might be a thread similar to this for Xubuntu, otherwise you will need to determine what was installed and remove them manually.  

You can use Syanptic's history (File -> History -> Date/Time) to find out what was installed.

---

### Post by truNWA on 2006-04-16
Ok i did that and it took away the KDE login screen.... I thought no big deal, I have some in gnome.... well i Gnome when I:

System > Administration > Login Screen Set up

I click and it says starting, but nothing happens.....



please help me.... i'm scared:(

---

### Post by truNWA on 2006-04-16
WEll i do that and it takes away the kubuntu login screen... and when i try to fix it in gnome by going to: 

System > Administration > Login Screen set up

nothing happens when i click

help?

P.S.---- All this happened after i deleted  a KDE Deamon or something

---

### Post by Sutekh on 2006-04-16
Was the KDE display manager (Login screen) the default one?

Try this command to make the GNOME one the default
```
sudo dpkg-reconfigure gdm
```

---

### Post by truNWA on 2006-04-16
* Reloading GNOME Display Manager configuration...  * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.



?

---

### Post by Sutekh on 2006-04-16
Oh okay.  Do you know what display manager was controlling your login screen?  I assume it was the KDE one.

Make sure you're finished with all you applications, we are heading to the command line.

Press Alt+Ctrl+F1, this will switch to a virtual console.  Log in using your user and password.  Now use this command to stop the X Windows session (the GUI)
```
sudo /etc/init.d/kdm stop
```
Then use ```
sudo dpkg-reconfigure gdm
```to make the GDM the default.

Afterwards use```
sudo /etc/init.d/gdm restart
```to start things again.

---

