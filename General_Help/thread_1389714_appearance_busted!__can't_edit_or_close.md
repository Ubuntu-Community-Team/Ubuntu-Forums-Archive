---
title: "appearance busted!  can't edit or close"
date: 2010-01-24
forum: General Help
---

### Post by agingric on 2010-01-24
hi all,

i had just edited a picture in digikam that was going to be my new desktop wallpaper.  

when i went into system/preferences/appearance to make the new change it would not show the new picture that i had just edited as a choice to change my new wallpaper to.  

then i tried closing the appearance box and it would not close.  then i shut down and restarted and when i bring up the appearance box it does not let me click on anything within.  also can't close it.  seems like other applications are working normally.  

any thoughts?

thanks
andy

---

### Post by hawthornso23 on 2010-01-24
You clicked on `ADD' to add the new background? 

Apologies if this is not your problem. The interface is potentially confusing. It looks like it might be displaying everything in some wallpaper folder. In fact it isn't. Pictures don't show up in the preview window unless you add them by clicking on the ADD tab.

---

### Post by agingric on 2010-01-24
i am not sure what happened.  appearances is not working as it should.  i can't click on anything within the appearances box.  it simply won't do anything.  i can click on minimize and it immediately minimizes.  if i try to close it takes several minutes to close.

i think something got fouled up when i was opening the appearance preferences at the same time the picture was getting saved after being edited in digikam. 

in appearances i clicked on the name of the picture and tried to add but the appearances box became locked up and unresponsive.  upon reboot there was a gray background.  one more reboot produced a background which was the picture that i wanted.  however, the appearance preferences box continues to be unresponsive after opening it.

thanks
andy

---

### Post by agingric on 2010-01-24
actually seems like it does respond but it takes several minutes when it should be nearly instantaneous....hmmmmm.....

---

### Post by hawthornso23 on 2010-01-24
Your desktop backgrounds are stored in ~/.gnome2 in the file backgrounds.xml

Perhaps that file got messed up.

Rename it to  backgrounds.xml.bak
Then try changing your desktop background again.
It should regenerate a fresh version (like in a new install) and hopefully fix the problem.

---

### Post by agingric on 2010-01-24
how do i find this backgrounds.xml file??  i do not know the filepath....
thanks
andy

---

### Post by hawthornso23 on 2010-01-24
The quickest way is to open a terminal and copy/paste the following

```
mv ~/.gnome2/backgrounds.xml ~/.gnome2/backgrounds.xml.bak
```
Alternatively the graphical method is as follows. Open a file browser. Open up the view tab and click on `show hidden files'. You should now see a whole lot of stuff in your home directory that was previously invisible. This is all your configuration data. You will notice all the new stuff has names that start with a dot - any file or folder name that starts with a dot is treated as hidden.

Click on the .gnome2 folder. You will then be able to see the backgrounds.xml file. Right click and rename it by appending .bak.

Once you've done that, try changing your desktop background again.

---

### Post by agingric on 2010-01-24
solved!  changing to gnome2/backgrounds.xml.bak worked to perfection.  thanks so much!

andy

---

### Post by hawthornso23 on 2010-01-24
You are welcome. Glad to be able to help. Now I've got a smile on my face too. Isn't it a beautiful day!

---

### Post by pablo180 on 2010-01-24
> **hawthornso23 said:**
> The quickest way is to open a terminal and copy/paste the following

```
mv ~/.gnome2/backgrounds.xml ~/.gnome2/backgrounds.xml.bak
```
Alternatively the graphical method is as follows. Open a file browser. Open up the view tab and click on `show hidden files'. You should now see a whole lot of stuff in your home directory that was previously invisible. This is all your configuration data. You will notice all the new stuff has names that start with a dot - any file or folder name that starts with a dot is treated as hidden.

Click on the .gnome2 folder. You will then be able to see the backgrounds.xml file. Right click and rename it by appending .bak.

Once you've done that, try changing your desktop background again.

Brilliant! Thank you! Had the same problem, Appearance would just hang when opened and I used to have to wait a couple of minutes before I could click anything. A PITA when adding new themes. Now it is instantly responsive again, thank you.

---

