---
title: "How to I run the program I just installed?"
date: 2012-02-20
forum: General Help
---

### Post by Worlds Tallest Engineer on 2012-02-20
I just installed Mathematica/8., but I'm not sure how to run it?  I am running Ubuntu 11.04 in classic desktop, so I checked under the "applications" drop down menu.  It was not there.  How can I find it?

This is what I did.

```




  user@computer:~$ cd ~/Downloads  
  user@computer:~/Downloads$ ls  
   Mathematica_8.0.4_LINUX.sh  
  

                                                                                          Wolfram Mathematica 8 Installer  
  -------------------------------------------------------------------------------------------------------------------------------------------------------------- 
  

  Copyright (c) 1988-2011 Wolfram Research, Inc. All rights reserved.  
  
  WARNING: Wolfram Mathematica is protected by copyright law and international treaties. Unauthorized reproduction or distribution may result in severe  
  civil and criminal penalties and will be prosecuted to the maximum extent possible under law.  
  
  Enter the installation directory, or press ENTER to select /usr/local/Wolfram/Mathematica/8.0:  
  > 

                         
 Create directory (y/n)?  
  > y  
  

  Now installing...  
  [*******************************************************************] 
  

  Type the directory path in which the Wolfram Mathematica script(s) will be created, or press ENTER to select /usr/local/bin:  
   >
   >sudo /usr/local/bin   
   
  Create directory (y/n)?  
  > y  
  
   Installation complete.  
  
  
```

---

### Post by 3rdalbum on 2012-02-20
Mathmatica should be installed into /usr/local/bin from what I can see. Try going into that folder and you should find it. Is this definitely a full GUI program? Usually a proper GUI program will put an entry into your Applications menu, but a terminal program will not.

---

### Post by Worlds Tallest Engineer on 2012-02-20
I tried 

user@Computer:~$ cd /usr/local/bin 
user@Computer:/usr/local/bin$ ls

but there's nothing in there.  I'm not sure what it means to be full GUI program.  :confused:  But the guys at wolfram are world class programmers, so I'd assume they'd cross all the t's and dot all the i's so to say.

---

### Post by Bobhuber on 2012-02-20
> **Worlds Tallest Engineer said:**
> I tried 

user@Computer:~$ cd /usr/local/bin 
user@Computer:/usr/local/bin$ ls

but there's nothing in there.  I'm not sure what it means to be full GUI program.  :confused:  But the guys at wolfram are world class programmers, so I'd assume they'd cross all the t's and dot all the i's so to say.
Did you type sudo /usr/local/bin ?? or hit the enter key and default ?? 
You might want to see if you have created a directory called sudo

---

### Post by Worlds Tallest Engineer on 2012-02-20
How would I check for a sudo file?  I tried it without the sudo, and I tried it just hitting enter.  In both cases it commented back to me that I may need root level clearance.

---

### Post by jacob.david on 2012-02-20
It looks like it was installed under /usr/local/Wolfram/Mathematica/8.0 and the scripts under /usr/local/bin (presumably to launch etc). But from your command, you ran the installation as a normal user and not using sudo (i.e. root). This is bit confusing because normal users usually don't have write access to /usr/ unless someone deliberately modified it. Or else the installation script itself is using sudo which is a bad practice. Eitherway the installation script seems to be wrong. Can you see if there is anything under /usr/local/Wolfram/Mathematica/8.0. If both /usr/local/Wolfram/Mathematica/8.0 and /usr/local/bin are empty then the script didn't install anything. In this case you may try one of the following
[LIST=1]
[*]Run the installation as sudo, for e.g. 
[FONT="Courier New"]sudo Mathematica_8.0.4_LINUX.sh [/FONT]
(ofcourse if you have ALL sudo access)
[*]Run the installation as a normal user and when it prompts for installation folder give something under your home folder for e.g. /home/user/Apps/
[/LIST]

---

