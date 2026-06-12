---
title: "Songbird - tar.gz install?"
date: 2009-11-07
forum: General Help
---

### Post by LeetNeo on 2009-11-07
I've extracted the tar.gz file, and went into the terminal and typed "cd path of the file" and typed in ./configure and says "No such file or directory". I'm not sure what to do, can anyone help me out?

-LeetNeo.

---

### Post by michy99 on 2009-11-07
Sometimes there isn't a configure file. Is there a make file? In that case you go straight into the make step.

---

### Post by LeetNeo on 2009-11-07
I don't see any make install file in the folder. I'm not sure what to do now.

-LeetNeo.

---

### Post by Szise on 2009-11-07
Use getDeb, no more complications
[http://www.getdeb.net/updates/?q=songbird](http://www.getdeb.net/updates/?q=songbird)

---

### Post by Olav on 2009-11-07
You practically don't need to do anything. If you downloaded Songbird from their website where it says "Download Songbird 1.2.0 for Linux i686 (17.2 MB)" in a huge green button then it is already a compiled program, ready to run. Just extract the archive, go into the Songbird directory, execute ./songbird (or make a launcher on your desktop).

---

### Post by scouser73 on 2009-11-07
**1** - Right click & Extract the Songbird tar.gz

**2** - Enter **gksudo nautilus** in Terminal

**3** - Copy & paste the Songbird file that you have just extracted to **/opt**

**4** - Right click on the Ubuntu start logo, select **Edit Menus**, 

**5** - Highlight the Sound & Video sub menu & click New Item

You will now see a small dialogue box appear

**6** - In the Name field, type **Songbird**

**7** - In the Command field type **/opt/Songbird/songbird**

**8** - In the Comment field type **Songbird**

You will now have Songbird installed.

---

### Post by LeetNeo on 2009-11-07
scouser73, it says: Could not launch 'Songbird"

Failed to execute child process "/opt/Songbird/songbird" (Permission denied)

That's what it says, I'm not sure what to do.

Szise, whenever I tried to install the Songbird from GetDeb, it says could not find Songbird or something like that.

Olav, I'm not sure what you're talking about.

Anyone else help?

-LeetNeo.

---

### Post by scouser73 on 2009-11-07
Ok, what you need to do is log in as root using **gksudo nautilus** now go to **/opt/Songbird** and check that you are the owner of the files. right click on any file select **Properties** and then click the **Permissions tab**.  Set the Folder Access user in Owner to your name & do the same to Group.  Check every file in Songbird and apply the same.

Then delete the Songbird menu item you created and recreate it following the steps I provided.

---

