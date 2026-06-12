---
title: "3 questions 1) transfer app from one linux to another 2) what to do if halt"
date: 2009-12-02
forum: General Help
---

### Post by maximilianyuen on 2009-12-02
1) I got two ubuntu running, one on PC and one on notebook
 
and is it possible that i can copy the settings file from one to another, so i dont need to setup again? (like msn)

in Mac OSX, I can copy the plist which store settings, is there anything similar in ubuntu?

2)ubuntu had halted a few times recently, and I find that nothing I can do when i can;t call xkill or force quit when the screen is dead (only cursor moving, sometime cursor dead too)

[blazemore]("http://ubuntuforums.org/member.php?u=326352") kindly suggested dontzap, but in terminal it said this app doesn't exist....

any help?

3) I downloaded a screensaver deb from web:
rss-glx_0.8.1-8ubuntu4_amd64.deb
(I am using 64bit ubuntu 9.10)

when i tried to install, it said"Error: Dependency is not satisfiable: libmagick10"

what does that mean?
googled and the answers seems irrelevant to my screensaver...

---

### Post by mikeize on 2009-12-02
1.  You should be able to simply copy the relevant program folders from your home directory on your 1st computer to your 2nd one.  i.e., copy ~/.firefox from comp one to ~/.firefox on comp 2.  These folders are hidden by default but you can show them by pressing ctrl-h in your file browser.

2. My ubuntu does the same thing, so I can't help you there...  all I know is that there are a few possible reasons, and that mine has something to do with nvram.  It's pretty annoying, but I haven't been able to fix it.  Good luck.

3.  that error means that "libmagick" is either not available from your current repository list, or is only available in an incompatible version, ie libmagick9 or possibly libmagick11.  You can try to find and install this libmagick10 from elsewhere on the internet, then try again to install your screensaver.

---

### Post by sdowney717 on 2009-12-02
how big is your /home/user name directory?

all the settings are contained in that and are hidden. To view,load up places home folder and check off view hidden files. I dont know which folder you would need, but you could just copy your folders into your other pc. I have copied entire user folder and setup the user in the other pc before.

> when i tried to install, it said"Error: Dependency is not satisfiable: libmagick10"

it sounds like a file needed for the screen saver to function is missing and not available. you might be able to find that file on the web somewhere.
it is likely to be related to this where the file has changed names and the person who created the screen saver has not updated the deb install.
[https://bugs.launchpad.net/ubuntu/+source/imageinfo/+bug/348160](https://bugs.launchpad.net/ubuntu/+source/imageinfo/+bug/348160)

---

### Post by 3rdalbum on 2009-12-02
RSS-GLX screensavers already come preinstalled. It's even a later version than what you've got. Check Synaptic Package Manager if you don't believe me. (search for "rss-glx").

If your whole GUI freezes up, you can kill it by pressing Alt-Printscreen-K. Sometimes the "Print Screen" key is labelled "SysRq" - so it's Alt-SysRq-K.

It's not normal that it crash so often; maybe you might need to update your video card driver.

---

### Post by maximilianyuen on 2009-12-02
> **3rdalbum said:**
> RSS-GLX screensavers already come preinstalled. It's even a later version than what you've got. Check Synaptic Package Manager if you don't believe me. (search for "rss-glx").

If your whole GUI freezes up, you can kill it by pressing Alt-Printscreen-K. Sometimes the "Print Screen" key is labelled "SysRq" - so it's Alt-SysRq-K.

It's not normal that it crash so often; maybe you might need to update your video card driver.

now I officially don't believe you as it is not installed in package manager :P j/k
and now I did, thanks a lot!

and thanks for the kill GUI key:P

---

### Post by maximilianyuen on 2009-12-02
> **mikeize said:**
> 1.  You should be able to simply copy the relevant program folders from your home directory on your 1st computer to your 2nd one.  i.e., copy ~/.firefox from comp one to ~/.firefox on comp 2.  These folders are hidden by default but you can show them by pressing ctrl-h in your file browser.

2. My ubuntu does the same thing, so I can't help you there...  all I know is that there are a few possible reasons, and that mine has something to do with nvram.  It's pretty annoying, but I haven't been able to fix it.  Good luck.

3.  that error means that "libmagick" is either not available from your current repository list, or is only available in an incompatible version, ie libmagick9 or possibly libmagick11.  You can try to find and install this libmagick10 from elsewhere on the internet, then try again to install your screensaver.

thank you, let me google libmagick then :)

---

### Post by maximilianyuen on 2009-12-02
> **sdowney717 said:**
> how big is your /home/user name directory?

all the settings are contained in that and are hidden. To view,load up places home folder and check off view hidden files. I dont know which folder you would need, but you could just copy your folders into your other pc. I have copied entire user folder and setup the user in the other pc before.



it sounds like a file needed for the screen saver to function is missing and not available. you might be able to find that file on the web somewhere.
it is likely to be related to this where the file has changed names and the person who created the screen saver has not updated the deb install.
[https://bugs.launchpad.net/ubuntu/+source/imageinfo/+bug/348160](https://bugs.launchpad.net/ubuntu/+source/imageinfo/+bug/348160)

so i can really just copy the folder to another computer?

i mean when I look into the package it seems it installs things on so many location....

do I have to install first then copy, or can i just copy?

---

### Post by mikeize on 2009-12-02
Install the program first, and then copy the folder from home "A" to home "B".  This folder i.e, /home/mikeize/.firefox, contains your program configuration/preferences.

---

### Post by rudi009 on 2009-12-02
> **maximilianyuen said:**
> 1)

2)ubuntu had halted a few times recently, and I find that nothing I can do when i can;t call xkill or force quit when the screen is dead (only cursor moving, sometime cursor dead too)


don't use ext4 if you are.That's what my experience says.

---

### Post by maximilianyuen on 2009-12-04
> **mikeize said:**
> Install the program first, and then copy the folder from home "A" to home "B".  This folder i.e, /home/mikeize/.firefox, contains your program configuration/preferences.

thank you!

---

### Post by maximilianyuen on 2009-12-04
> **rudi009 said:**
> don't use ext4 if you are.That's what my experience says.

using ext3 happily ~

---

### Post by Vaphell on 2009-12-04
about **dontzap** - it should be in repositories (or **sudo apt-get install dontzap** in terminal)
and it allows to easily modify xorg.conf to allow killing/restarting X by CTRL-ALT-BACKSPACE, some time ago it was enabled by default but many users pressed that accidentally, losing the state of their current session so it got disabled.

---

### Post by maximilianyuen on 2009-12-04
> **Vaphell said:**
> about **dontzap** - it should be in repositories (or **sudo apt-get install dontzap** in terminal)
and it allows to easily modify xorg.conf to allow killing/restarting X by CTRL-ALT-BACKSPACE, some time ago it was enabled by default but many users pressed that accidentally, losing the state of their current session so it got disabled.

but it didn't work for me

instead the ctrl printscr alt is working :-k

---

