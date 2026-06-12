---
title: "in home directory &quot;mv file.txt Desktop&quot; Please rescue me"
date: 2010-05-06
forum: General Help
---

### Post by unckybob on 2010-05-06
Please rescue me, I'm in way over my head. 

In my home directory I typed in at a bash prompt: 

mv file.txt D*

Now I can't access anything on my Desktop. I can't access anything under "Places" on the panel on top of the desktop. 

I don't mind reinstalling Ubuntu, but I sure would like to rescue my files on the desktop. 

Please help

---

### Post by WorMzy on 2010-05-06
Open a terminal and post what these commands show:
```
ls ~
```
```
ls -d D*
```

---

### Post by unckybob on 2010-05-06
I now have an emergency, my dad is stuck in the middle of the road. 

Please wait 'til I can get back to you.

---

### Post by unckybob on 2010-05-06
Wait those commands are pretty quick. 

ls ~

Desktop
Downloads
examples.desktop
history.txt 
Music
Pictures
Public 
Templates
Videos 

ls -d D*

Desktop 
Downloads 

Now I have to run. Please wait for me to get back to you.

---

### Post by WorMzy on 2010-05-06
No problem. I'll post what I think has happened:

I think that initially you had multiple folders and files in your home folder that began with "D", so when you used a wildcard (*) it passed all of these as arguments to mv and used the last item that matched D* as the destination parameter. So, for example, say you have the following standard folders in your home folder: Documents, Desktop, Downloads. When you did ```
mv file.txt D*
``` it interpreted that as ```
mv file.txt Desktop Documents Downloads
``` which would move file.txt, Documents and Desktop into folder Downloads. To move them back again, all you would need to do is run ```
mv Downloads/Desktop Downloads/Documents Downloads/file.txt ~/
``` Then move the file.txt as you originally meant to with ```
mv file.txt Documents (or Desktop, or Downloads)
```

But you might not have moved everything to Downloads, but some other folder beginning with D, and files might have been moved too. So you'll need to determine which folder you moved everything to, and edit the above command accordingly. Also, you'll need to check that files haven't been moved too, and, if they have, you'll need to move them back using your own knowledge of where they should be.

---

### Post by WorMzy on 2010-05-06
I think I was right, and Nautilus has just generated a new Desktop folder for you. But to make sure, can you run ```
ls -d Downloads
``` and post the output here.

EDIT: Actually that command doesn't do what I thought it would, do ```
ls Downloads
``` instead.

---

### Post by unckybob on 2010-05-07
You were absolutely right. Everything was in my "Documents" folder. I copied everything back and everything is hunky-dory. Thanks WorMsy. You got me out of a jam.

---

### Post by WorMzy on 2010-05-07
No problem. Just be careful how you use wildcards in the future, they can cause more problems than you realise! :)

---

