---
title: "Open With &quot;Wine Internet Explorer&quot; in file manager"
date: 2012-07-17
forum: General Help
---

### Post by Marzata on 2012-07-17
I've recently noticed that when I'm trying to open a JPEG or a PNG image in Thunar (or in Nautilus) there is an option to "Open With "Wine Internet Explorer"" (see the attached screenshot). If I click that option nothing happens. I don't have Wine installed and I've never had. I have Google Earth installed, if this matters. Any idea what is this, where it came from and how to delete it? Thank you! 

OS: Xubuntu 12.04 LTS, Xfce 4.8

---

### Post by Paddy Landau on 2012-07-17
Wine is an applicatiion to run Windows programs in Linux. So, it is in fact possible to install Internet Explorer (via Wine) and run it.

To remove that option from Nautilus, right-click the item > Properties > Open with > select the Wine option and delete it.

Before you get too excited about Wine, bear in mind that it is far from perfect. Most Windows programs do not work; some work with flaws; and a few work perfectly.

If you want to try out Wine, I strongly recommend [PlayOnLinux]("https://help.ubuntu.com/community/PlayOnLinux") (a front-end to Wine).

---

### Post by Marzata on 2012-07-17
Thank you. I don't want to install Wine. I want to know where this option in the menu came from and how to delete it?

---

### Post by Paddy Landau on 2012-07-18
> **Marzata said:**
> I want to know where this option in the menu came from ...?
Where it came from: You possibly have Wine already installed. Otherwise, I don't know.
> **Marzata said:**
> ... how to delete it?
> **Paddy Landau said:**
> To remove that option from Nautilus, right-click the item >  Properties > Open with > select the Wine option and delete it.I see that my solution does not work (sorry, I was not at my computer when I posted that response). So, now I'm confused. It used to work.

---

### Post by Marzata on 2012-07-18
I understand you but I have never had Wine installed.

---

### Post by Grenage on 2012-07-18
I'm going to go out on a limb here and suggest that you do have WINE installed; whether you directly installed it, or it was a dependency for something else, is another matter.

---

### Post by Marzata on 2012-07-18
Synaptic doesn't show that Wine is installed even as a dependency for something else. What next?

---

### Post by Grenage on 2012-07-18
```
dpkg -s wine
```

What does that give you?

---

### Post by Marzata on 2012-07-18
> **Grenage said:**
> ```
dpkg -s wine
```

What does that give you?
user@host:~$ dpkg -s wine
Package `wine' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
user@host:~$

---

### Post by Grenage on 2012-07-18
Odd, I'm at a bit of a loss as to why the menu option would appear if wine ha not been installed.  Is there anything 'wine-esque' in synaytic?  Anything such as wine tricks, or wine gecko?

---

### Post by Hungry Man on 2012-07-18
Simple. HE installed Google Earth, which is just a Google Earth Windows packaged into WINE. Or some other package like Picasa or TeamViewer.

Those are all just WINE ported apps.

You can remove the context menu entries manually my removing some files in ./wine/ but I can't remember which.

edit: It probably should be listed as a dependency but possibly not.

---

### Post by Toz on 2012-07-18
See: [http://ubuntuforums.org/showpost.php?p=10767563&postcount=15]("http://ubuntuforums.org/showpost.php?p=10767563&postcount=15") for instructions on how to remove those entries.

---

### Post by Marzata on 2012-07-18
> **Hungry Man said:**
> Simple. HE installed Google Earth, which is just a Google Earth Windows packaged into WINE. Or some other package like Picasa or TeamViewer.

Those are all just WINE ported apps.

You can remove the context menu entries manually my removing some files in ./wine/ but I can't remember which.

edit: It probably should be listed as a dependency but possibly not.
I have Google Earth installed but it is not because of it as I have it on another machine and those lines are not presented there. Must be something else.

---

### Post by Paddy Landau on 2012-07-18
Did [post=12111703]Toz's post[/post] help?

---

### Post by Marzata on 2012-07-18
Don't know yet. But before that I want to know where it came from.

---

### Post by mc4man on 2012-07-18
Browse to ~/.local/share/applications/ and see if there are any wine-extension-XXX.desktop files there
If so delete them all

Also see if there is a  image/jpeg= line in  ~/.local/share/applications/mimeapps.list, if so remove

---

