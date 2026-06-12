---
title: "File Permission Errors"
date: 2012-08-20
forum: General Help
---

### Post by TWPEagle on 2012-08-20
Ok, So I am trying to install McMyAdmin, I am running the gui version of Ubuntu.
Here are the instructions provided by the dev. of mcmyadmin
> 
[LIST]
[*]Download the McMyAdmin 2 Updater/Loader from [http://mcmyadmin.com/Downloads/MCMA2_glibc25.zip](http://mcmyadmin.com/Downloads/MCMA2_glibc25.zip) and unpack it where you wish to install McMyAdmin.
[*]Download the McMyAdmin 2 supplemental files from [http://mcmyadmin.com/Downloads/etc.zip](http://mcmyadmin.com/Downloads/etc.zip) - copy the archive into /usr/local and unpack it there.
[*]Run the MCMA2_Linux_x86_64 binary via the command line or SSH. (Enter ./MCMA2_Linux_x86_64 in the directory you unpacked it)
[/LIST]
The issue I am having is extracting the zip files anywhere.
Trying to put the First one in var/mcmyadmin
and
The second on in /usr/local
And i get an error stating I dont have the required permissions to extract an archive there?
Please help!

---

### Post by raja.genupula on 2012-08-20
yeah you should have to be a root to do so .

you have two ways 1 .terminal
                                        2. gui

1 .TERMINAL 
       ```
sudo cp <source from where you are copying> <to your where you are copying>
```
2.GUI 
open your terminal 
     
   ```
sudo nautilus 
```

then do as you want to do .

---

### Post by TWPEagle on 2012-08-20
I will give that a try later! Thanks!

---

### Post by TWPEagle on 2012-08-20
Getting this when opening nautilus to extract the zip's



team@team-EG733AA-ABA-SR1620NX-NA540:/var/mcmyadmin$ sudo nautilus
Initializing nautilus-gdu extension
Nautilus-Share-Message:  Called "net usershare info" but it failed: 'net usershare' returned  error 255: net usershare: cannot open usershare directory  /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by raja.genupula on 2012-08-21
have you tried the terminal way ? 

for gui use this 

```
gksu nautilus
```

---

