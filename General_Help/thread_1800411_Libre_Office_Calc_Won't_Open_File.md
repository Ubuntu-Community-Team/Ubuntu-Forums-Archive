---
title: "Libre Office Calc Won't Open File"
date: 2011-07-08
forum: General Help
---

### Post by calebi on 2011-07-08
Okay so I have a file that I always save and close properly and get in my Ubuntu One folder for backup that will not open. Its called "Income.ods" and is quite important and I cannot seem to recover it. When I double click it, it shows the Libre Office Calc splash screen shows up then goes away and the nothing, no error messages, no nothing. I tried to open it on my Windows Vista machine and it said it was corrupted and could not open in Office Word. I tried a few recovery tools but to no avail. Any thoughts?

Thanks,
Caleb

---

### Post by amanchesterman on 2011-07-09
Have you tried opening it with Gnumeric spreadsheet? That handles open document spreadsheet (.ods) file format as well as Open Office and Libre Office.

---

### Post by calebi on 2011-07-09
I tried using it and it says the file type is not supported.

---

### Post by SoFl W on 2011-07-09
From the terminal type ```
soffice -calc
``` **OR** ```
libreoffice -calc Income.ods
``` and post the results.

---

### Post by amanchesterman on 2011-07-09
> I tried using it and it says the file type is not supported.

Well that's very odd. Gnumeric definitely does support the .ods file type: see [here]("http://projects.gnome.org/gnumeric/doc/sect-file-formats.shtml"). Maybe the file header is corrupted and the program doesn't know how to open it.

You could try:
1) Make a **copy** of the corrupted file
2) Rename the **copy** 'income.txt'
3) Start gnumeric
4) Go to Data > Get External Data > Import Text file and see if it will read 'income.txt'

Good luck anyway
John

---

### Post by calebi on 2011-07-09
This code;
```
sudo libreoffice -calc Income.ods
```Returned this;
```
terminate called after throwing an instance of 'com::sun::star::lang::WrappedTargetRuntimeException'

```

---

### Post by calebi on 2011-07-09
> **amanchesterman said:**
> Well that's very odd. Gnumeric definitely does support the .ods file type: see [here]("http://projects.gnome.org/gnumeric/doc/sect-file-formats.shtml"). Maybe the file header is corrupted and the program doesn't know how to open it.

You could try:
1) Make a **copy** of the corrupted file
2) Rename the **copy** 'income.txt'
3) Start gnumeric
4) Go to Data > Get External Data > Import Text file and see if it will read 'income.txt'

Good luck anyway
John

This didn't do anything just 1 cell of jibberish

---

### Post by gmargo on 2011-07-09
For a very simple test to see if your *.ods file is corrupted, use "unzip -v file.ods" and "unzip -t file.ods" from the command line.  A zip file's directory is stored at the end of the file.  If the file is truncated at all, then the directory portion gets lost or corrupted.

---

### Post by SoFl W on 2011-07-09
> **calebi said:**
> This code;
```
terminate called after throwing an instance of 'com::sun::star::lang::WrappedTargetRuntimeException'

```


These two threads:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=9606](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=9606)
[http://ubuntuforums.org/showthread.php?t=948294](http://ubuntuforums.org/showthread.php?t=948294)
suggested deleting the ".libreoffice" directory from your home directory and trying again.
I would RENAME the directory to ".libreofficeBACKUP" and try it again, if it works, great!  If it doesn't rename that directory back to ".libreoffice"

---

### Post by calebi on 2011-07-09
> **SoFl W said:**
> These two threads:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=9606](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=9606)
[http://ubuntuforums.org/showthread.php?t=948294](http://ubuntuforums.org/showthread.php?t=948294)
suggested deleting the ".libreoffice" directory from your home directory and trying again.
I would RENAME the directory to ".libreofficeBACKUP" and try it again, if it works, great!  If it doesn't rename that directory back to ".libreoffice"

When I did this I got a thing that said "General Input Error" but I closed it and didn't read the rest for whatever reason and can't get it to come up again.

---

### Post by TinEllus on 2011-12-30
I have exactly the same problem as does Calebi in his first post:

>  When I double click it, it shows the Libre Office Calc splash screen  shows up then goes away and the nothing, no error messages, no nothing.Also Gnumeric gives the same result:

> says the file type is not supportedAny luck yet?

I also have a .ods file that I update regularly, at least once a week, for at least four years now.

I noticed however that its size is 1,5 kB, where it should be a least 500 kB; i have a backup file made 4 months ago which is 500 kB.

Something must have happened to it, I guess erasing all data(?)

Strange though that Oo-calc doesn't report a corrupt file.

I can do with the backup file, but would like to recover the data from the missing 4 months.

Any thoughts anybody?

I'm using Open Office 3.2 on Ubuntu Lucid 10.04 LTS
Might be of interest: this happened immediately after installing backported Kernel 2.6.38-13 (Natty) because of frequent GPU lockups / X-server freezes.
Other .ods, .odt files, etc..., seem however fine...

Corrupted hd??

:confused:

---

### Post by xijun on 2012-04-23
Hi, I have the same problem: the calc and writer doesn't work, it show nothing after libreoffice splash screen --- the worst experience I ever met since I turned to ubuntu 3 year before. 

Ubuntu: 10.04.3
Libreoffice: 3.5.2.2, installed from PPA

More information about the problem:
1. Base, impress, draw works fine;
2. I tried to remove and re-install the libreoffice, no working;
3. I purged openoffice completerly, no working;
4. I tried to go back to open office, so I purged libreoffice*, and try to install openoffice, it tells me:

> 
ackage dependencies cannot be resolved

This error could be caused by required additional software packages  which are missing or not installable. Futhermore there could be a  conflict between software packages which are not allowed to be installed  at the same time.
But I do not know how to solve this problem either since I do not know which softwares are conflicting. 

So defrustrated with ubuntu now! Libreoffice is trying all effort to replace openoffice, but it seems that it is not ready yet.

---

### Post by drpaul on 2012-05-07
I just installed 12.04 so I got Libreoffice. Now I have a file that LibreOffice says has a Read error, but it opens fine under OpenOffice.

Anybody hves an idea?

Paul

---

