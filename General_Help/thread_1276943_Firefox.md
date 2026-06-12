---
title: "Firefox"
date: 2009-09-27
forum: General Help
---

### Post by cowboy7305 on 2009-09-27
[I] have just downloaded firefox 3.5.3 ,but its downloaded as a tar.bx2 file any help to install this please on ubuntu 9.04
many thanks

---

### Post by t0p on 2009-09-27
What you've downloaded is a tarred archive.  You need to extract it, by right-clicking on it and selecting Extract here...

Once we know what the contents are, we can advise further.

---

### Post by Mercury_Alpha on 2009-09-27
You can just download "Shiretoko" from the repositories instead. It's Firefox 3.5.x, only without branding.

Some sites will recognize the browser by its user agent string, so you'll want to grab the addon that allows you to change that. (It's helpful to have that addon anyway.)

---

### Post by Earl_Maroon on 2009-09-27
I hate to disagree with everyone else, but I strongly suggest you look into the Ubuntuzilla.py script which will install the latest Mozilla build automatically.

[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by Mercury_Alpha on 2009-09-27
That option doesn't sync with the repositories. Shiretoko is the exact same thing, just with a different label.

---

### Post by scouser73 on 2009-09-27
**1** - Move the file to your **/home/yourname**

**2** - Rick click and extract the file

**3** - Go to **System > Preferences > Main Menu**

**4** - Click on **New Item**

**5** - In the **Command** field enter **/home/yourname/firefox/firefox**

**6** - In the **Name** field enter Firefox 3.5

---

### Post by Catarina on 2009-09-27
> **t0p said:**
> What you've downloaded is a tarred archive.  You need to extract it, by right-clicking on it and selecting Extract here...

Once we know what the contents are, we can advise further.

Yeah, tar.bx2 is just like a .rar file in Windows, for example.

Once extracted there should be a README file that will help you in the process of getting Firefox on your computer right.

And I think there's a easier way out there, a PPA repository, I think. In Launchpad maybe? :confused:

---

### Post by lovinglinux on 2009-09-27
Follow method #1 of the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567).

I do not recommend extracting it to home, since there is no need of root permissions to change or replace the files, including the binaries. As far as I know, applications extracted from tar are better placed in the /opt directory.

---

### Post by scouser73 on 2009-09-28
> **lovinglinux said:**
> Follow method #1 of the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567).

I do not recommend extracting it to home, since there is no need of root permissions to change or replace the files, including the binaries. As far as I know, applications extracted from tar are better placed in the /opt directory.

Thank you for the advice about placing extracted tar files in **/opt**.

---

