---
title: "installed Hamachi2 and haguichi, but it won't load up?"
date: 2011-01-28
forum: General Help
---

### Post by acornty on 2011-01-28
i followed this guide([http://www.webupd8.org/2010/10/insta...i-gui-for.html]("http://www.webupd8.org/2010/10/install-hamachi2-and-haguichi-gui-for.html")) step by step, but when i open haguichi, nothing happens.

i could run hamachi on this same computer when it had windows on it so hardware shouldn't be a problem. can anyone help me?

---

### Post by ztefn on 2011-01-29
What do you expect to happen?

---

### Post by acornty on 2011-01-31
> **ztefn said:**
> What do you expect to happen?
i was under the influence that a GUI would show up for hamachi because i installed haguichi.

---

### Post by ztefn on 2011-01-31
You can launch Haguichi from the main menu (Applications -> Internet -> Haguichi) or set it as startup program in System -> Preferences -> Startup Applications.

---

### Post by acornty on 2011-02-02
> **ztefn said:**
> You can launch Haguichi from the main menu (Applications -> Internet -> Haguichi) or set it as startup program in System -> Preferences -> Startup Applications.
yes. i did that already, hence my original post's question.

---

### Post by ztefn on 2011-02-03
Great. Then, if you are not connected click on "Connect".

When you are connected click on "Client" -> "Join Network..." to join an existing network or "Client" -> "Create Network" to create a new network.

---

### Post by acornty on 2011-02-03
> **ztefn said:**
> Great. Then, if you are not connected click on "Connect".

When you are connected click on "Client" -> "Join Network..." to join an existing network or "Client" -> "Create Network" to create a new network.
sigh. i appreciate your help, but could you please read my original post? i said that the GUI wouldn't show up.

---

### Post by ztefn on 2011-02-04
> **acornty said:**
> sigh. i appreciate your help, but could you please read my original post? i said that the GUI wouldn't show up.

Nope, you said "when i open haguichi, nothing happens". Just try to be a little more descriptive, thank you.

Anyway, what's the output when you start Haguichi from the terminal? Go to "Applications" -> "Accessoires" -> "Terminal" then type in "haguichi -d" (without the quotes) and hit enter.

---

### Post by acornty on 2011-02-04
> **ztefn said:**
> Nope, you said "when i open haguichi, nothing happens". Just try to be a little more descriptive, thank you.

Anyway, what's the output when you start Haguichi from the terminal? Go to "Applications" -> "Accessoires" -> "Terminal" then type in "haguichi -d" (without the quotes) and hit enter.
right, sorry my bad. this is what i get when i put that into the terminal ```
haguichi -d

** (/usr/lib/haguichi/Haguichi.exe:2093): WARNING **: The following assembly referenced from /usr/lib/haguichi/Haguichi.exe could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=2)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/haguichi/).


** (/usr/lib/haguichi/Haguichi.exe:2093): WARNING **: Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: Could not load type 'Haguichi' from assembly 'Haguichi, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'.

```

---

### Post by ztefn on 2011-02-04
That's strange, it seems one or more dependencies have not been installed along with Haguichi. Please run the following line in the terminal to install any missing dependencies and let me know the output:
```
sudo apt-get install mono-runtime libmono-system2.0-cil libmono-posix2.0-cil libgtk2.0-cil libglib2.0-cil libgconf2.0-cil libndesk-dbus1.0-cil libnotify0.4-cil
```

---

### Post by acornty on 2011-02-05
> **ztefn said:**
> That's strange, it seems one or more dependencies have not been installed along with Haguichi. Please run the following line in the terminal to install any missing dependencies and let me know the output:
```
sudo apt-get install mono-runtime libmono-system2.0-cil libmono-posix2.0-cil libgtk2.0-cil libglib2.0-cil libgconf2.0-cil libndesk-dbus1.0-cil libnotify0.4-cil
```
oh, when i do that I'm pretty sure it says i already have those. check it out ```
sudo apt-get install mono-runtime libmono-system2.0-cil libmono-posix2.0-cil libgtk2.0-cil libglib2.0-cil libgconf2.0-cil libndesk-dbus1.0-cil libnotify0.4-cil
[sudo] password for tyler: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgconf2.0-cil is already the newest version.
libglib2.0-cil is already the newest version.
libgtk2.0-cil is already the newest version.
libmono-posix2.0-cil is already the newest version.
libmono-system2.0-cil is already the newest version.
libndesk-dbus1.0-cil is already the newest version.
mono-runtime is already the newest version.
libnotify0.4-cil is already the newest version.
libnotify0.4-cil set to manually installed.
The following package was automatically installed and is no longer required:
  mesa-utils
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 115 not upgraded.

```

i tried running haguichi again from the programs list and also through the terminal with the command you gave me again and i got the same error.

---

### Post by ztefn on 2011-02-05
What is the output when you run the following command?

```
cli-gacutil -l  | grep gtk-sharp
```

---

### Post by acornty on 2011-02-05
> **ztefn said:**
> What is the output when you run the following command?

```
cli-gacutil -l  | grep gtk-sharp
```


this: ```
cli-gacutil -l  | grep gtk-sharp
gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.10.gtk-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.4.gtk-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.6.gtk-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.8.gtk-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f

```

all these commands are greek to me...

---

### Post by ztefn on 2011-02-06
That command lists all entries containing gtk-sharp references in the "Global Assembly Cache". It seems that gtk-sharp is listed perfectly fine. So I don't know why your system reports "The assembly was not found in the Global Assembly Cache".

Are you able to run other Mono applications on your system like Banshee, Tomboy, F-Spot or GNOME Do?

---

### Post by acornty on 2011-02-06
> **ztefn said:**
> That command lists all entries containing gtk-sharp references in the "Global Assembly Cache". It seems that gtk-sharp is listed perfectly fine. So I don't know why your system reports "The assembly was not found in the Global Assembly Cache".

Are you able to run other Mono applications on your system like Banshee, Tomboy, F-Spot or GNOME Do?
well now that you mention it no i can't. i never used any of those applications and i just tried F-spot and it said starting F-spot in the taskbar but then no window or anything popped up. I'm on a dual boot system with wubi right now if that's any help.

---

### Post by ztefn on 2011-02-06
That sucks. Let's see if reinstalling gtk-sharp will fix it. Run this command:
```
sudo apt-get install --reinstall libgtk2.0-cil
```

When asked "Do you want to continue?" press enter.

When it's finished reinstalling try running Haguichi again:
```
haguichi -d
```

---

