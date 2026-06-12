---
title: "Reset to original fonts"
date: 2010-07-29
forum: General Help
---

### Post by Winalways on 2010-07-29
Long back when I started using ubuntu 9.10 in my dual-boot machine, I copied my windows fonts to ubuntu. I don't remember exactly how did I do it. It was something like copying fonts from windows folder and pasting into fonts folder in ubuntu. Now I am using ubuntu 10.04 and want to get rid of all those. 

In fact I would be happy to have restored my ubuntu to freshly downloaded 10.04 settings. But I want the installed software to remain, as there are quite a lot.

Thanks in advance!

---

### Post by uRock on 2010-07-29
Here are what the original font settings look like.

---

### Post by Ordes on 2010-07-29
> Fonts:
depending on where u installed the fonts. in your or /home/.fonts or in /usr/share/fonts/

> if in /home, u can just get rid of the fonts in that folder, and than refresh the font cache >>  fc-cache -f -v

> if in /usr/share/fonts; depending if u made a extra folder for your fonts, like "myfont", than get just rid of that one. otherwise u can only scan manualy go through the folder and delete out the fonts. and than refresh font cache

>> Settings:
to get rid of all your user settings. just create a new user account, and your settings will start fresh. than copy over your need files and documents. ever looked in /home and show hidden files? those folders u see there are moslty settings and configs of all the apps u using. so in case u want to keep some settings, like a firefox profile, you need to copy that folder in your new account. and your firefox will just look like before.
> or instead of creating a new account, you could also delete out the folders & setting files of your /home. but i prefer making a new account and than just copy over what i need.

---

### Post by Winalways on 2010-07-30
I actually couldn't find any fonts in my home folder. In usr/share/fonts again there were three folders but which are found in openoffice like adobe fonts weren't there. I believe those adobe fonts and others like wide latin etc. are windows fonts. 

Can anything be done as even creating a new user account did not help!

---

### Post by dino99 on 2010-07-30
look at their dates (all the oldish might be wondoz's fonts)

---

### Post by Ordes on 2010-07-30
it doesnt matter if they are windows fonts..


search for wide latin to find the font location...

> as the new user account didnt reset your fonts, means u did install them in the ubu system and not into /home/.fonts, so u gotta find the loco first, and than begin deleting...

---

### Post by exXplode on 2010-12-02
> **uRock said:**
> Here are what the original font settings look like.[...]

Thanks, that worked for me.
I googled "ubuntu reset fonts" to find this thread.

---

