---
title: "Help Removing Cinelerra"
date: 2009-09-14
forum: General Help
---

### Post by chessnerd on 2009-09-14
Okay, so I installed Cinelerra because it was recommened as a good video editor by several people on this forum, but I didn't care for it much once I started to work with it. Basically, it was too complicated for the basic stuff I was looking to do (the same reason I often use KolourPaint over GIMP when cropping pictures).

However, I went to uninstall it and it seems to have broken Synaptic. Here are the errors I'm getting:

When trying to uninstall in Synaptic: E: cinelerracv: subprocess post-removal script returned error exit status 1
When trying to uninstall from the terminal, the output is this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  cinelerracv
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 22.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 121548 files and directories currently installed.)
Removing cinelerracv ...
Description:	Ubuntu 9.04
locale "en_US.ISO-8859-15" not in archive
locale "ru_RU.KOI8-R" not in archive
rm: cannot remove `/usr/bin/Cinelerra': No such file or directory
dpkg: error processing cinelerracv (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 cinelerracv
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Now, whenever I try to open the Update Manager, I get an error suggesting I do a partial upgrade (which doesn't work) and then I get this:
> Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

Whenever I try to run "sudo apt-get install -f" it tries to remove Cinelerra first and gives me the same errors as above.

Does anyone know how to fix this? If not, I'll have to do a reinstall, which wouldn't be that bad, except that it's only been on my laptop for four days. I'd like to think that I can't break Ubuntu that quickly after working with it for over 8 months. :)

---

### Post by chessnerd on 2009-09-15
I tried to reinstall it just to get the errors to stop, but they haven't gone away. This is pretty annoying to say the least. It is letting me install things again, but after every install it gives me an error about Cinelerra. 

Any help would be greatly appreciated.

---

### Post by ~dr,j on 2009-12-10
hey all~
i'm having the same problem. this is crazy....anyone have a solution? i've tried to reinstall it (didn't work) i've tried removing it using apt-get, aptitude an synaptic....all give me that similar error....HELP! i can't even update anyother software...:S
~j

---

### Post by Rytron on 2010-02-08
Edit [B]sudo gedit /var/lib/dpkg/status
[/B]
Remove all paragraphs with cinelerra in them.
Save & exit.
Remove cinelerra from synaptic.
Done!

---

### Post by benplanet on 2010-04-09
> **Rytron said:**
> Edit [B]sudo gedit /var/lib/dpkg/status
[/B]
Remove all paragraphs with cinelerra in them.
Save & exit.
Remove cinelerra from synaptic.
Done!

nice, now synaptics and update manager won't start. why did i follow this blindly.. damn it

---

### Post by lisati on 2010-04-09
> **benplanet said:**
> nice, now synaptics and update manager won't start. why did i follow this blindly.. damn it

Please run the following from the command line and post the output back to us. Perhaps someone will be able to help.
```
sudo dpkg --configure -a
```

---

### Post by benplanet on 2010-04-09
```
sudo dpkg --configure -a
``` ^^ that did not output anything.

I was however able  to run the following commands and fix it:

```
# cd /var/lib/dpkg/
# mv status status.broken
# cp status-old status
```

I still can't get rid of the cinelerra related errors in update manager and synaptic, how do i   get rid of it for good?

thanks for the help!

---

### Post by Drenriza on 2010-04-09
if you installed it using apt-get package manager try using
```
sudo apt-get --remove Cinelerra && sudo apt-get --purge Cinelerra
```

If the package name differs from Cinelerra, then just replace Cinelerra with the correct package name.

---

### Post by benplanet on 2010-04-09
tried the command above, it doesn't work (invalid operation) even tho the name of the package is correct.


This is the error i keep getting in synaptic > E: cinelerra: subprocess installed post-removal script returned error exit status 1

---

### Post by benplanet on 2010-04-09
Ok I went back and deleted any lines pertaining to Cinelerra in sudo gedit /var/lib/dpkg/status

make sure you don't just delete any lines, but the whole paragraph. 

SOLVED the issue. thanks.

---

### Post by Rytron on 2010-04-10
> **benplanet said:**
> Ok I went back and deleted any lines pertaining to Cinelerra in sudo gedit /var/lib/dpkg/status

make sure you don't just delete any lines, but the whole paragraph. 

SOLVED the issue. thanks.

Exactly as I said earlier.

---

### Post by shaka_zulu on 2010-04-10
Then put [SOLVED] in theme title. ;)

---

### Post by chessnerd on 2010-04-10
> **shaka_zulu said:**
> Then put [SOLVED] in theme title. ;)

Actually, this was my old thread. I'd upgraded to Karmic by the time that the solution came around, so I didn't have the problem anymore, but I'll mark it as solved now. 

I'm glad someone did figure out how to remove that thing. It bugged me and bugged me until I wiped Jaunty for Karmic.

---

### Post by benplanet on 2010-04-14
> **chessnerd said:**
> Actually, this was my old thread. I'd upgraded to Karmic by the time that the solution came around, so I didn't have the problem anymore, but I'll mark it as solved now. 

I'm glad someone did figure out how to remove that thing. It bugged me and bugged me until I wiped Jaunty for Karmic.

yes cheers, this thing bugged the hell out of me, to the point where i almost ripped all my hair out. good thing a solution came around, just in time to keep this mohawk on my head. :)

---

