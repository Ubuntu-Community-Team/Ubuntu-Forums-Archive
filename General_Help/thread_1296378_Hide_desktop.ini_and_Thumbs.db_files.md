---
title: "Hide desktop.ini and Thumbs.db files"
date: 2009-10-20
forum: General Help
---

### Post by Martje_001 on 2009-10-20
So you've finally setup a partition shared between Windows and Ubuntu, but everytime you log in to Ubuntu you keep seeing those nasty desktop.ini and Thumbs.db files? Then this tutorial is for you!

This tutorial only applies for those who are using nautilus as their file-manager. Previously hidden files (.*, *.hidden) were hardcoded in the Nautilus source code. With this little hack nautilus imports every time it starts patterns to hide files from gconf. I would like to thank [dfalk]("https://launchpad.net/~dfalk") for writing the patch.

**Written for:** Ubuntu 9.04

**Step 1**
The first thing you should do is add [my PPA]("https://launchpad.net/~hmb1/+archive/ppa") to your sources.list. I assume you know how to add a PPA to your system. If you don't, please look [over here]("https://help.launchpad.net/Packaging/PPA/InstallingSoftware") for instructions.

**Step 2**
The second thing is installing the modified Nautilus. You only have to update your system and the modified Nautilus will automatically be installed. You can check you've got the correct version install by fireing up Synaptic and by search for 'Nautilus'. If it says; "*Current version: 1:2.26.2-0ubuntu2**~ppa1***", it should be OK.

**Step 3**
The third step is to add the patterns you want to hide to gconf. Go to a terminal and typ:
```
gconf-editor
```
Navigate through until you reach **/desktop/gnome/file_views**. Then; right click on the white space above 'Key Documentation'. Then choose **New Key..**. Fill in:
```
Path: /desktop/gnome/file_views
Name: hidden_file_patterns
Type: list
```
Add anything you want to hide. Here are a few examples:
```
*.ini
*.db
desktop.ini
thumbs.db
```
Click 'OK'.

**Step 4**
Log off and in to apply the changes. You could also restart Nautilus.

**Notes**
[LIST=1]
[*]You can check whether I did or did not include malicious code by downloading the source.
[*]You may be unable to get updates for nautilus after adding my PPA. I'll try my best to keep up with the MOTU's, but I can't promise anything.
[*]Instead of logging off you could also restart Nautilus.
[/LIST]

---

### Post by Junosix on 2009-12-05
Fantastic, going to give this a try later as I've set my mum up on Ubuntu and this is the final tweak she needs to hide ~$*.* temporary files that Word creates.

If this sorts it out she's going to be delighted to have switched to Ubuntu!

---

### Post by Martje_001 on 2009-12-08
OK! Let me know how it went!

---

### Post by MC707 on 2009-12-08
> **Written for:** Ubuntu 9.04

I really don't care about those files, but do you know if it works for Karmic (9.10)? I'm sure many people will wonder.

---

### Post by vittorelli on 2009-12-28
> **MC707 said:**
> I really don't care about those files, but do you know if it works for Karmic (9.10)? I'm sure many people will wonder. I have it working on 9.10, but nautlius crashes whenever I try to open the preferences-dialog..

---

### Post by Wardje on 2009-12-28
> **vittorelli said:**
> I have it working on 9.10, but nautlius crashes whenever I try to open the preferences-dialog..

I guess that would count as "not working":lolflag:

This does seem interesting though. Not so much for the thumbs stuff since I dont use winblows, but just in general :)

---

### Post by PhX89 on 2010-03-23
Doesn't work! :( I have already installed nautilus 2.28.

---

