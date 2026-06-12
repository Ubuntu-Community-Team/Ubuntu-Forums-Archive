---
title: "Transmission keeps changing the download directory"
date: 2012-06-07
forum: General Help
---

### Post by J V on 2012-06-07
Transmission keeps changing the download directory to ~/Downloads/D after an unfortunate mistype a while back.

Now changing it to downloads in the GUI has no change and editing the settings file just results in it setting it back afterwards. Even deleting the entire .config/transmission directory doesn't help.

What's wrong and how do I fix it?

---

### Post by blueshead on 2012-06-07
I'm also looking for a fix to this.

---

### Post by J V on 2012-06-10
This is really annoying, blueshed could you check which version you have?

```
$ transmission-gtk --version
transmission-gtk 2.51 (13280)
```

---

### Post by oklokl on 2012-06-10
bug...

Photo Folder
 Music folder
or.. 
Check  
(So... Status is unknown.)  -> change of image will occur. (The folder Directory image will Varies.)
Exit
( Transmission ... -> Completely quit)
Transmission.. Turn on again after completion.
So
 As a return to normal.

---

### Post by blueshead on 2012-06-10
> **J V said:**
> This is really annoying, blueshed could you check which version you have?

```
$ transmission-gtk --version
transmission-gtk 2.51 (13280)
```

Transmission 2.52 (13304)

I've been using Tran since my old OSX days.. But this is too much.

I've switched over to qBittorrent and it's pretty damn nice..

---

### Post by J V on 2012-06-12
> **oklokl said:**
> bug...

Photo Folder
 Music folder
or.. 
Check  
(So... Status is unknown.)  -> change of image will occur. (The folder Directory image will Varies.)
Exit
( Transmission ... -> Completely quit)
Transmission.. Turn on again after completion.
So
 As a return to normal.
Sorry I don't follow you

---

### Post by oklokl on 2012-06-12
To work out the bugs.
 Advice.
 If you will be directed to the same folder.(A similar path)
 Bug occurs.

Please select a different folder

Please lnk clear the data
Download the new .

By repeating the same behavior.
 Does not solve the problem.

 n,.n

and..
Select the folder to auto add... Do not select.
[ATTACH]219562[/ATTACH]
Sorry, the image is the Hangul.

---

### Post by scouser73 on 2012-06-12
Go to your home folder, press CTRL & H, click on the folder **.config** and delete the folder **transmission**.

Then start Transmission and set up your directories as if starting from new.

---

### Post by J V on 2012-06-12
> **scouser73 said:**
> Go to your home folder, press CTRL & H, click on the folder **.config** and delete the folder **transmission**.

Then start Transmission and set up your directories as if starting from new.
Tried that, no dice.

> To work out the bugs.
 Advice.
 If you will be directed to the same folder.(A similar path)
 Bug occurs.

Please select a different folder

Please lnk clear the data
Download the new .

By repeating the same behavior.
 Does not solve the problem.

 n,.n

and..
Select the folder to auto add... Do not select.
[Attachment 219562]("http://ubuntuforums.org/attachment.php?attachmentid=219562")
Sorry, the image is the Hangul.The option you marked on the image is deselected here too.

---

### Post by oklokl on 2012-06-13
Sorry we couldn't help you Answer.
I think Nautilus new bug.

---

### Post by oklokl on 2012-06-13
Found the cause. -> Folder bookmarks coupling bug

Please remove the Folder bookmark link.
Manual pencil connection
[ATTACH]219646[/ATTACH]

[ATTACH]219647[/ATTACH]
  To change the folder display.
Connect from the parent folder.


   When you add a bookmark is the same bug persists

---

### Post by J V on 2012-06-15
This has nothing to do with bookmarks or nautilus, this is about transmission

---

### Post by oklokl on 2012-06-18
Connection has to do with ...
 Folder bookmarks ..Go to this connection are bugs and problems.
How to solve this problem  I took a long time.
Workaround is not perfect.
So it seems there is no association. But are related.

---

