---
title: "Google Chrome for Ubuntu 11.10"
date: 2012-03-31
forum: General Help
---

### Post by bouncedmrhappy on 2012-03-31
How can I transfer all of my bookmarks/saved passwords from Win7 Chrome to Ubuntu 11.10 Chrome?

I'm almost done deleting my Windows stuff and this is one of the last things I need to do before booting from the disc and installing.

 I'm also very new to Linux and this is my first time. My apologies if this isn't in the right board.

---

### Post by farmerjohn73 on 2012-03-31
Chrome has an option to export all your bookmarks to a .html file. Click on the wrench button, click bookmarks->Bookmark Manager.  A new window will open with all your bookmarks.  Now click Organize-> Export bookmarks to html file. 

copy this html to a place where you want to keep it and Import the html file in the same way mentioned above.

Done.  :-)

---

### Post by josephmills on 2012-03-31
Have you tried the import option on chrome ? On my brother-in-law computer I had to mount the windows drive and go in and manual take each one and make a new bookmark. to do this 
open terminal (ctrl+alt+t)
then 
```
sudo fdisk -l 
```

you should see something that looks like this 
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400   de  Dell Utility
/dev/sda2   *      206848    30926847    15360000    7  HPFS/NTFS/exFAT
/dev/sda3        30926848   537342053   253207603    7  HPFS/NTFS/exFAT
/dev/sda4       537343998   976771071   219713537    5  Extended
/dev/sda5       537344000   778094591   120375296   83  Linux
/dev/sda6       968798208   976771071     3986432   82  Linux swap / Solaris
/dev/sda7       778096640   968796159    95349760   83  Linux


```  


as you can see on mine that windows is on the sda3 drive so I mount it 
```
sudo mount /dev/sda3 /mnt 
```

then 

```
cd /mnt/
```
start looking for your bookmarks and move them or open them in chrome and save. 


to  un-mount 
```
cd ~
```
then 
```
sudo umount /mnt/
```

hope that this helps :)

---

### Post by howefield on 2012-03-31
You can also use the built in sync options in Chrome.


[http://support.google.com/chrome/bin/answer.py?hl=en&answer=165139](http://support.google.com/chrome/bin/answer.py?hl=en&answer=165139)

---

### Post by bouncedmrhappy on 2012-03-31
> **farmerjohn73 said:**
> Chrome has an option to export all your bookmarks to a .html file. Click on the wrench button, click bookmarks->Bookmark Manager.  A new window will open with all your bookmarks.  Now click Organize-> Export bookmarks to html file. 

copy this html to a place where you want to keep it and Import the html file in the same way mentioned above.

Done.  :-)

 Thank you, by signing in with my Google account will I be able to keep all my saved passwords?

 Also, is it possible for me to make the switch without deleting all of my scripts/extensions?

 Never mind, looks like my problem is pretty much solved.

---

### Post by farmerjohn73 on 2012-03-31
> **bouncedmrhappy said:**
> Thank you, by signing in with my Google account will I be able to keep all my saved passwords?

 Also, is it possible for me to make the switch without deleting all of my scripts/extensions?

 Never mind, looks like my problem is pretty much solved.

well, I am sure upto exporting the bookmarks.  I am not sound with saved passwords part.  But I found these links on google.  plase see if you can use it.

[http://stackoverflow.com/questions/2540026/how-to-export-google-chrome-passwords](http://stackoverflow.com/questions/2540026/how-to-export-google-chrome-passwords)

[http://www.intowindows.com/how-to-backup-saved-passwords-in-google-chrome-browser/](http://www.intowindows.com/how-to-backup-saved-passwords-in-google-chrome-browser/)

---

