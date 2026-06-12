---
title: "extract .deb"
date: 2006-03-28
forum: General Help
---

### Post by thunderfox933 on 2006-03-28
how do i open or extract .deb to install a program

---

### Post by Qrk on 2006-03-28
You install them by suding dpkg.

First, change directory (in terminal) to where you downloaded the .deb. If it is in your Desktop, do (change the username to your username)

```
cd /home/username/Desktop
```

Then install the package with this command:

```
sudo dpkg -i package.deb 
```

You can just type the first bit of the package name and press tab as well.

---

### Post by thunderfox933 on 2006-03-28
where would the file be its not in the desktop

---

### Post by Mustard on 2006-03-28
[QUOTE=thunderfox933]where would the file be its not in the desktop[/QUOTE]

Probably in HOME folder then.

```
cd /home/username/
#change directory to /home/username
```

---

### Post by AndrewCaul on 2006-03-28
If you haven't downloaded it, it's probably available in the repositories.
Type **sudo apt-get install [whatever]** at the console to install it or use the Synaptic Package Manager.

---

### Post by thunderfox933 on 2006-03-28
i mean i extracted the files but i cant the install file or file

---

### Post by AndrewCaul on 2006-03-28
That's because there isn't one. You install it with dpkg.

---

### Post by Mustard on 2006-03-28
[QUOTE=thunderfox933]i mean i extracted the files but i cant the install file or file[/QUOTE]

When the above example was given to you, it was an example.

There is no 'package.deb' and you don't extract .debs to install them.  That is just an example of how you do use the dpkg command to install .deb packages.

If your package was called xyz.deb then you would install it using this command 

```
sudo dpkg -i xyz.deb
```

---

### Post by Qrk on 2006-03-28
A .deb isn't like a zip or rar file. You don't extract it before installing it.

Breezy's gnome likes to think as a .deb as an archive even though it really isn't. That can be confusing. Instead a .deb needs to be processed by Ubuntu's automagic installer, dpkg. 

The best way to install software in ubunut is a gui called synaptic. Get it by System->Administration->Synaptic Package Manager

This tool will automagically download, install and update just about all of the software you need.

---

### Post by Mustard on 2006-03-28
[QUOTE=Qrk]A .deb isn't like a zip or rar file. You don't extract it before installing it.

Breezy's gnome likes to think as a .deb as an archive even though it really isn't. That can be confusing. Instead a .deb needs to be processed by Ubuntu's automagic installer, dpkg. 

The best way to install software in ubunut is a gui called synaptic. Get it by System->Administration->Synaptic Package Manager

This tool will automagically download, install and update just about all of the software you need.[/QUOTE]

This is a good point really. :)

What is this .deb package you are installing, thunderfox?  Have you tried installing it from the Synaptic Package Manager at all?

---

