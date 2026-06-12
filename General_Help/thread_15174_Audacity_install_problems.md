---
title: "Audacity install problems?"
date: 2005-02-12
forum: General Help
---

### Post by bigkahuna on 2005-02-12
I'm having problems installing Audacity (the sound editor) on Ubuntu Warty.

First off, I do not have internet access on this system, so I downloaded Audacity from the Debian site.  Then I passed the file over to my Ubuntu system.

I managed to open the "Debian package" which resulted in several folders and a binary, but when I click on the binary nothing happens.  What am I missing?  I searched the archives here and on the Audacity site and didn't find any help.

Thanks!

---

### Post by WW on 2005-02-12
Instead of getting the Debian package, you will make your life easier by getting the Ubuntu package from Ubuntu universe:
   [http://archive.ubuntu.com/ubuntu/pool/universe/a/audacity/](http://archive.ubuntu.com/ubuntu/pool/universe/a/audacity/)
Once you get this copied to your Ubuntu computer, you should be able to install it (assuming all its dependencies are met) with the command

   dpkg -i  audacity_1.2.1-1_i386.deb

(That's assuming you grabbed the i386 version.)

Edit:  Be sure you grab version 1.2.1-1.  The version 1.2.3-1 is for hoary.

---

### Post by bigkahuna on 2005-02-12
...aaaahhh, perfect!  Part of my problem could have been that I was trying to use the 1.23 version from their site.

Any idea if there's a binary for Cinellerra (the video editing app)?  I'm trying to set up my system for multimedia production...

Thanks,

Paul

---

### Post by bigkahuna on 2005-02-12
[QUOTE=WW] ...you should be able to install it (assuming all its dependencies are met)... [/QUOTE]

I got a series of error messages saying that these files were not found:

libid3tag0
libsndfile1
libwxgtk2.4

Where do I find these and install them?  Or worse case:  how do I uninstall my failed Audacity install?

Thanks.

---

### Post by WW on 2005-02-12
Those are additional packages that you can find in the Ubuntu repository.  The first two might even be on the CD. If not, you'll have to go back to the computer with internet access and get the packages from Ubuntu.  Try looking here:

[http://archive.ubuntu.com/ubuntu/pool/main/](http://archive.ubuntu.com/ubuntu/pool/main/)

and here:

[http://archive.ubuntu.com/ubuntu/pool/universe/](http://archive.ubuntu.com/ubuntu/pool/universe/)

Those pages are split into subdirectories, using the first letter(s) of the package name.

I have warty installed, and according to Synaptic, the versions that you want for warty are:

libid3tag0:   0.15.1b-1
libsndfile1:   1.0.10-1
libwxgtk2.4:  2.4.2.4ubuntu1

Now, *these* might also have dependencies.  If so, well, I think you can see what you'll have to do. :)

If you used dpkg to attempt to install the audacity .deb file and it failed, then you shouldn't have to uninstall anything.

---

### Post by bigkahuna on 2005-02-13
I figured most of this out, but got the packages from the Debian site.  I've since installed these 3 packages and the "dependent" packages that were reported in error messages.  But now when I run Audacity (and it sort of runs) it says it cannot read or write files.

I looked at the Debian site again, and on that site they list files "related" to Audacity 
[http://packages.debian.org/testing/sound/audacity](http://packages.debian.org/testing/sound/audacity)
included in this list are the three that were reported in the error message. 

My question is this:  do I have to install all of these packages and all the files that are associated with them?  I'm guessing that I do.

I'm sure that Synaptic would have automated this process, but sure wish there were an easier way to do this manually.  By comparison, installing Audacity for Win XP is a single archive  :-?

---

### Post by Mute on 2005-02-13
Kahuna, quick question, why don't you just run the Synaptic Package management system?  Make sure under -> Settings -> Repositories (that all are enabled - universe) and then go to Multimedia  (Universe) and there is audacity 1.2.1-1, just click it apply and you have audacity installed *Note I just performed this myself, and Synaptic finds all necessary dependencies for you.  

-Mute

Then we can work on the other part of the post Cinerella.

---

### Post by bigkahuna on 2005-02-13
Dear Mute,

I -wish- I could run synaptic, but as I said in my first post of this thread I don't have internet access on my Linux system.  So I have to download the files on a Win XP system and then transfer the files over.

I just finished downloading all the files...  jeez, that was a pain.  I don't look forward to doing this very often.  I definitely have to get a Linux friendly modem...

---

### Post by Mute on 2005-02-13
/me = doofus, should have read the post more clearly...hrm...yeah I can see as how that might be rather difficult.

My apologies.

-Mute

---

### Post by WW on 2005-02-13
While some packages will probably work fine, I think mixing Debian packages with Ubuntu is asking for trouble.  And since these packages are available in Ubuntu, why bother with the Debian versions?

Here's an unofficial site for Ubuntu packages, organized like packages.debian.org:
[http://higgs.djpig.de/ubuntu/www/](http://higgs.djpig.de/ubuntu/www/)
(Many thanks to Frank Lichtenheld for putting that together!)

---

### Post by bigkahuna on 2005-02-13
Thanks WW,

Had I known there was a package repository like this for Ubuntu I would have used them instead.  In my defense I've got to say that I didn't find any info about manually installing packages anywhere on any of the Ubuntu sites, and I didn't find anything in past posts here in the forums.  Not to say they don't exist, just that I never found them.  Thanks for the link!

New question:  Now that I've installed about 50% of the dependencies for Audacity from the Debian site, can I now just "dpkg -i" the Ubuntu packages right on top of them (thus replacing the Debian with the Ubuntu files)?

Thanks!

---

### Post by bigkahuna on 2005-02-13
I've re-installed all the packages and dependent packages with Ubuntu replacements and Audacity behaves a bit  weird.  Sometimes when I launch it it seems to work OK, other times I get this error:

"There was an error initializing the audio i/o layer.  You will not be able to play or record audio."

But if I relaunch it, it seems to work fine.   ](*,) 

Any ideas?

---

### Post by bigkahuna on 2005-02-13
I found the problem:  system sounds needs to be turned off before launching Audacity...

---

