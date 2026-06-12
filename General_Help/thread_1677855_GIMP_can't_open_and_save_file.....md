---
title: "GIMP: can't open and save file...."
date: 2011-01-29
forum: General Help
---

### Post by Harve on 2011-01-29
Dear Ubuntu Friends,

My OS is Ubuntu 10. 
Ever since the last update of GIMP, that program refuses to open and save files. Opening a file in Gimp fails. And when I click a JPG or GIF and launch GIMP with that action, I have an image open in GIMP but can't save any changes. 

I deleted GIMP entirely and installed it newly, but the problem remains the  same.

Hope that anyone can help me solve this problem.

Kind regards,
Harve

---

### Post by AlphaLexman on 2011-01-29
Can you confirm you have read / write permissions on the files?

Are they in your $HOME directory or ~/Pictures ?

---

### Post by Harve on 2011-01-29
Thanks [AlphaLexman]("http://ubuntuforums.org/member.php?u=810079"),

I did some tests following your guidelines, but it doesn't make any difference from where I recall the pics. The pics are 100% mine by the way.

---

### Post by 101011010010 on 2011-01-29
Hello. Did you delete the .gimp file  (configuration file) in your Home folder before you tried to reinstall? (It's .gimp-2.6 in my Home folder).
If you can't see it press "ctrl+h".
A.

---

### Post by Harve on 2011-01-29
Hi 101011010010,

Thanks for the suggestion.

I deleted GIMP throwing 
sudo apt-get remove gimp
in the terminal.

But there's a whole lot of files remaining; a folder named
gimp-2.7.1
cramped with folders and files.

I couldn't find the file you mentioned.

Is it necessary to delete all of these folders and files to make a fresh start?
And if so, how do I I delete the remaining parts of GIMP? 

Thanks

---

### Post by 101011010010 on 2011-01-29
Hello again. I would use:

> sudo apt-get purge gimpThis should remove any configuration files as well. Then check your Home folder to see if .gimp-2.7.1 has been deleted. You can always make a copy first (.gimp-2.7.1) and then uninstall gimp. You could also run a search for "gimp" in Nautilus, just to make sure that everything's gone and then try to reinstall. I hope this helps.
A.

---

### Post by Harve on 2011-01-29
Thanks again for al your help!

I tried the purge command; then the terminal replied:

Package gimp is not installed so not removed.
The following packages were automatically installed and are no longer required:
python-pexpect libgnomescan0 libgnomescan-common
use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 60 not upgraded

Does it make sense to do that?
But then I still got stuck with a lot of GIMP files

Thanks!
Harve

---

### Post by 101011010010 on 2011-01-29
Hi, I don't have space problems, so I wouldn't worry about " libgnomescan0 or libgnomescan-common".If you want to check, then open up Synaptic Package Manager (System/ Administration menu) and check that libgnomescan-common etc were installed with Gimp. Click on "File, then History" and the information will be in there. If they weren't installed with Gimp, leave them alone.:)
What Gimp files are left and what locations are they in?

---

### Post by Harve on 2011-01-29
Hi again,

Those 2 files have something to do with Gnome scan access library. 

The after deleting GIMP a directory named 'gimp-2.7.1' with some 20 sub-directories and hundreds of files still remain. What do you think, do I need to remove them all to be able to re-install GIMP again?

regards,
Harve

---

### Post by 101011010010 on 2011-01-30
Hello again, I would rename the file e.g."gimp-2.7.1-BAK" and then just to make sure either log out and in again or reboot. Then try to install Gimp again. I hope this works for you.:)
A.

---

### Post by Harve on 2011-01-30
Thanks a lot for all your help!

If I search my entire home directory for .gimp-2.7.1 nothing is to be found.
The only object with the name gimp-2.7.1 (without .) is the folder with that name.

I have all these folders and files of gimp-2.7.1, the version of Gimp I deleted was named GIMP-2.6.1.... I recall now. Could it be that 2.7 was not installed properly at all?

---

### Post by 101011010010 on 2011-01-31
Hello again Harve,
I am really running out of ideas, so I had another look to see if there were any known bugs in Gimp 2.7. Nothing. I then looked at the website and found this (not sure how old this is):> GIMP 2.7 is in no way a final product. A lot of new features are incomplete and some things may even be completely broken. If you need to get work done, please use the stable version, GIMP 2.6So the only thing that I can suggest is the same as the website advice, install Gimp 2.6 and hope that 2.8 works better for your system in the future. If you have trouble getting "2.6 try this site and choose your release and Gimp 2.6 is under Graphics. (I found it under Maverick, but I'm not sure which release you are using.:))
I hope this helps.

---

### Post by Harve on 2011-01-31
Thanks again,

I'm going to give 2.6 a try again.

..... installed GIMP 2.6..... result.... still the same.... pfffff....

Anyhow, thanks for al the help. You did what you could. 
Hope someone is able to throw in some new ideas.

Harve

---

