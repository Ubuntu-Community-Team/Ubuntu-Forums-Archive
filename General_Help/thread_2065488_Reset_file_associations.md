---
title: "Reset file associations?"
date: 2012-10-02
forum: General Help
---

### Post by Stonecold1995 on 2012-10-02
For some reason a lot of my files have really weird or duplicate file associations, like .jpgs with Wine and some audio files with Mono Develop.  Is there any way I can reset all the file associations back to default?

[IMG]http://www.pictureshack.us/images/70471_wine_lolwut.png[/IMG]

---

### Post by coldraven on 2012-10-02
I don't know of a global reset.
But try this. choose "Open with > Other" then choose the correct application and check the "Remember this" box.

---

### Post by westie457 on 2012-10-02
The closest thing to a global reset goes something like this.


Select a file, for example a picture *.jpg

Right-click and choose properties.

Go to the 'Open with' tab.

In here you can set the default app to open all jpg files.

To remove an association pick one you do not want, right-click and click the only option presented. Do this for each one.


Screenshots attached for clarity.

---

### Post by lechien73 on 2012-10-02
You can easily manage file associations with Ubuntu Tweak, it can be downloaded from their [website]("http://ubuntu-tweak.com/").

A screenshot is attached.

---

### Post by Stonecold1995 on 2012-10-02
> **westie457 said:**
> The closest thing to a global reset goes something like this.


Select a file, for example a picture *.jpg

Right-click and choose properties.

Go to the 'Open with' tab.

In here you can set the default app to open all jpg files.

To remove an association pick one you do not want, right-click and click the only option presented. Do this for each one.


Screenshots attached for clarity.

Uh, how do I do that in Kubuntu?  I don't use Unity, only KDE...

---

### Post by coldraven on 2012-10-03
Read what I said before

---

### Post by Stonecold1995 on 2012-10-03
> **coldraven said:**
> Read what I said before

Yes I know how to change the file associations, but I want to *reset* them.  The current associations are correct (JPEG opens with Gwenview), but it contains "old" associations cluttering the selection menu (like two copies of "Wine Core exe" to open JPEG).

---

### Post by bra|10n on 2012-10-03
Logically, you might start with SystemSettings. Note the sub-section FileAssociations.
Here you can choose application associations for every filetype, including removing and moving each up/down the list to designate priority.

---

### Post by Pletched on 2012-10-03
If I have read from here correctly [http://askubuntu.com/questions/16580/where-are-file-associations-stored](http://askubuntu.com/questions/16580/where-are-file-associations-stored)

You must edit a file from the directory /usr/share/applications

---

### Post by drmrgd on 2012-10-03
> **bra|10n said:**
> Logically, you might start with SystemSettings. Note the sub-section FileAssociations.
Here you can choose application associations for every filetype, including removing and moving each up/down the list to designate priority.

Yes to this!  It's the easiest way to reconfigure your associations without having to dig around the config files.  Just remove those that you no longer want to associate with .jpg (for example), and that should do it!

---

### Post by Stonecold1995 on 2012-10-03
> **drmrgd said:**
> Yes to this!  It's the easiest way to reconfigure your associations without having to dig around the config files.  Just remove those that you no longer want to associate with .jpg (for example), and that should do it!

I tried that before, but there are a huge amount of file associations and I spent hours correcting it but still had a huge number more to go.  That's why I'm looking to reset them, rather than going through and manually reviewing thousands of file associations.

---

### Post by deadflowr on 2012-10-04
When you right click on the file, go to properties. Then on the General tab where the file type is, should be a wrench, click on that, from there you can do what you want with those, however I don't think resetting them from there is possible.

---

### Post by Pletched on 2012-10-04
You can't completely reset because programs such as text editors are text\plain. Nearly all files will have a text editor program in the open with menu.

---

### Post by Stonecold1995 on 2012-10-04
If it's not possible to reset them using a GUI, then where's the config file or directory that contains the info for file associations?  Because if I delete that and replace it with the files from a fresh install that might reset them to default.

---

### Post by bra|10n on 2012-10-05
> **Stonecold1995 said:**
> If it's not possible to reset them using a GUI, then where's the config file or directory that contains the info for file associations?  Because if I delete that and replace it with the files from a fresh install that might reset them to default.

You might want to look at the contents of ~/.local/share/applications/mimeapps.list and compare the entries in this file are also those you wish to delete.

---

