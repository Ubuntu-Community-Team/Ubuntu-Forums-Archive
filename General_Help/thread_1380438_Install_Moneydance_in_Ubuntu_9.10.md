---
title: "Install Moneydance in Ubuntu 9.10"
date: 2010-01-13
forum: General Help
---

### Post by music.man on 2010-01-13
I just downloaded 
**Moneydance 2010r2 (build 735)**

and I cannot seem to get it installed on the computer. I am able to extract the files and run the program, but it does not appear to be installed under the Applications tab. I have combed all over these forums and the internet looking for clues and I cant find the magic. I have Sun Java 6 installed. I downloaded Moneydance without Java, and have tried the download with Java. What am I missing? I am new to Ubuntu so it would be no surprise if I'm missing an easy step. Thanks to anyone who can help.

---

### Post by Is Mise on 2010-01-13
So the program runs okay, it's just not in the Applications menu? If that's the case, just right-click Applications and select Edit Menus, and you can add it yourself.

---

### Post by music.man on 2010-01-13
Thanks! That is what I needed! I truly appreciate the help!

---

### Post by Antonbury on 2010-01-23
I'm struggling to get Moneydance installed too.  I've downloaded the Moneydance file with Java and extracted it.  It has all the files in a Moneydance folder, including the Java folder.  That's as far as I can get.  I've tried creating a 'launch button', but cannot find the appropriate icon within the Moneydance folder to get the application to run.

I'm currently having to use Moneydance in Windows7, but want to move away from Microsoft completely, but this issue with Moneydance not working in the latest version of Ubuntu is preventing me ditching Windows completely.

I'm using the 64bit version of Ubuntu 9.10 - I don't know if this is a problem with Moneydance?

As I'm fairly new to installing external programs in Ubuntu, can anyone help please? :confused:

---

### Post by music.man on 2010-01-23
See if you can open the Moneydance folder. There should be another item inside that folder named Moneydance. Click on that. It will ask if you want to run the item. Select RUN. Moneydance should then open up and be working.

---

### Post by dcstar on 2010-01-23
> **Antonbury said:**
> I'm struggling to get Moneydance installed too.  I've downloaded the Moneydance file with Java and extracted it.  It has all the files in a Moneydance folder, including the Java folder.  That's as far as I can get.  I've tried creating a 'launch button', but cannot find the appropriate icon within the Moneydance folder to get the application to run.


Wherever you installed it: Moneydance/moneydance_icon32.png is the launcher icon, the actual launcher application is just "Moneydance".

---

### Post by Antonbury on 2010-01-24
Thanks folks for the information.  I've 'double-clicked' on the file 'Moneydance' and that affords me the opportunity to 'Run', but on clicking on 'Run', sadly nothing happens.  I've used Moneydance on previous 32 bit versions of Ubuntu without any problem, but this is the first attempted use on my new 64 bit laptop, so wondered if there was a compatability issue.  Would value any further help.

---

### Post by saiprem on 2011-05-07
I just spend about 8 hours trying to get Moneydance and here's how I did it in the end.

Download the tarball and copy it to your desktop.  Use Alien to convert it to deb.  I wish I had written down how I did it and where I got the information how to do it.  Sorry I can't help there.

But once you have the deb package on your desktop here's how I did it:

Copy the Moneydance.deb (moneydance-linux-x86wj_1-1_all.deb) package to the desktop

Right click on the deb package and click on "Install using Ubuntu Software Center".

When the Ubuntu Software Center comes up click on "Install".

This will install a Moneydance folder on to the desktop.

Open the folder and there is a 10.0 Kb shell script called "Moneydance".  That's it!

Move that to the panel and click on it and it should open the program.

---

