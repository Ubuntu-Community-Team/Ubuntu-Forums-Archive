---
title: "I screwed up Help! Uninstalled gnome!!!"
date: 2011-04-25
forum: General Help
---

### Post by Reduced_Oxygen on 2011-04-25
I tryed out the new gnome shell and removed it now I don't have any login options (except for user defined and recovery console but they don't work either)

Anyone know a fix or a way to retrieve my data?

---

### Post by TeoBigusGeekus on 2011-04-25
You can boot with a live cd/usb and backup your data.
Can't you select recovery mode from grub?

---

### Post by Reduced_Oxygen on 2011-04-25
Tryed recovery mode with no luch

---

### Post by TeoBigusGeekus on 2011-04-25
Unless anyone else thinks otherwise, I think you should back up your data and reinstall.

---

### Post by WorMzy on 2011-04-25
What do you get when you boot up? Blank login screen? Nothing? Command prompt?

If you get a login screen or nothing, try pressing Ctrl+Alt+F1 to get to a command prompt. Then log in to that and run
```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by Reduced_Oxygen on 2011-04-25
In that case what would be the best way to back up every thing (Inc apps etc)

---

### Post by Reduced_Oxygen on 2011-04-25
> **WorMzy said:**
> What do you get when you boot up? Blank login screen? Nothing? Command prompt?

If you get a login screen or nothing, try pressing Ctrl+Alt+F1 to get to a command prompt. Then log in to that and run
```
sudo apt-get install --reinstall ubuntu-desktop
```
Ok so that worked exept now only the gnome shell option works

---

### Post by Reduced_Oxygen on 2011-04-25
can anybody help me restore the unity interface?????

---

### Post by WorMzy on 2011-04-25
Can you remove gnome-shell without losing all your other gnome packages?

```
sudo apt-get remove gnome-shell
```

How did you install it in the first place?

Oh, Unity? Try reinstalling it.

```
sudo apt-get install --reinstall unity
```

---

### Post by coffeecat on 2011-04-25
@Reduced_Oxygen, have a look at this thread from about post #12:

[http://ubuntuforums.org/showthread.php?t=1726755](http://ubuntuforums.org/showthread.php?t=1726755)

It seems that people have been successful by installing the ppa-purge package to purge the ppa used for gnome 3.

---

### Post by Reduced_Oxygen on 2011-04-25
> **WorMzy said:**
> Can you remove gnome-shell without losing all your other gnome packages?

```
sudo apt-get remove gnome-shell
```

How did you install it in the first place?

Oh, Unity? Try reinstalling it.

```
sudo apt-get install --reinstall unity
```
didnt work, gnome shell is still the only thing that works

---

### Post by Reduced_Oxygen on 2011-04-25
> **coffeecat said:**
> @Reduced_Oxygen, have a look at this thread from about post #12:

[http://ubuntuforums.org/showthread.php?t=1726755](http://ubuntuforums.org/showthread.php?t=1726755)

It seems that people have been successful by installing the ppa-purge package to purge the ppa used for gnome 3.
thanks that is quite helpfull

---

### Post by Reduced_Oxygen on 2011-04-25
SOLUTION!!!: [http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3](http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3)

Thanks everyone for the help everything is now back to normal :)

---

