---
title: "Home folder"
date: 2009-06-30
forum: General Help
---

### Post by anw0625 on 2009-06-30
How do I make the home folder anything but the desktop?

---

### Post by lavinog on 2009-06-30
I don't understand your question. The home folder isn't the desktop.

---

### Post by michy99 on 2009-06-30
I don't understand the question. Your home folder is /home/Your-Username/
Your desktop is /home/Your-Username/Desktop.

---

### Post by anw0625 on 2009-06-30
When I click places and select my home folder it takes me to my desktop folder.  Something happened and I dont know what.  I used to have it as my user name.  I hope this helps.  Thanks!!

---

### Post by DeathMetal on 2009-06-30
Try looking in the column on the left under "Places" and click on your username.  Sounds like you have the desktop folder highlighted in the places column and not your actual home folder.

---

### Post by 73ckn797 on 2009-06-30
> **DeathMetal said:**
> Try looking in the column on the left under "Places" and click on your username.  Sounds like you have the desktop folder highlighted in the places column and not your actual home folder.


That confuses me as much as the OP's question.):P

There is no left column under Places in Ubuntu 9.04 that I can find.

---

### Post by DeathMetal on 2009-06-30
LOL go to Places>Home Folder and when the home folder opens look to the left and you will see a column there.  Click on your username and that should bring up the correct folder, instead of your desktop folder.  Sorry for being vague in the last post.

---

### Post by lavinog on 2009-06-30
open a terminal and post the output of:```
echo $HOME

```

---

### Post by lavinog on 2009-06-30
> **DeathMetal said:**
> LOL go to Places>Home Folder and when the home folder opens look to the left and you will see a column there.  Click on your username and that should bring up the correct folder, instead of your desktop folder.  Sorry for being vague in the last post.

Press F9 if you don't see the column

---

### Post by 73ckn797 on 2009-06-30
> **DeathMetal said:**
> LOL go to Places>Home Folder and when the home folder opens look to the left and you will see a column there.  Click on your username and that should bring up the correct folder, instead of your desktop folder.  Sorry for being vague in the last post.


"Well", as the door keeper to the City of OZ said, "That is a horse of a different color".:lolflag:

---

### Post by anw0625 on 2009-06-30
I have tried all of your susgestions with no luck.  My computer froze up one night and I turned it off and then this happened.  So, When I open up the home folder all I see to the left are the icons: Desktop, file system, network and trash.  Then there is a line break and the folders are A folder I created and a pictures and videos folder.  There used to be a folder above the desktop icon with my user name.  I hope that this is not confusing.  I hope someone knows what is wrong.  Thanks!!

---

### Post by lavinog on 2009-07-01
and what did echo $HOME produce?

---

### Post by anw0625 on 2009-07-01
lavinog it did not work.  I still click my home folder and it still pulls what is on the desktop.

---

### Post by lavinog on 2009-07-01
That wasn't the point. I was asking to see if $HOME was set to your home folder or to your desktop.

---

### Post by anw0625 on 2009-07-05
Sorry, How do I do that???

---

### Post by 73ckn797 on 2009-07-05
> **anw0625 said:**
> Sorry, How do I do that???

Go to Applications/Accessories/Terminal

Once there type:
```
echo $HOME
```

It ought to return:
```
/home/yourname
```

Post the results back here.

---

### Post by anw0625 on 2009-07-06
It said what you said it would, but it still pulled up what was on my desktop and has the desktop highlight on the left when I click my home folder.

---

### Post by lavinog on 2009-07-07
go to
System > administration > users and groups
double click on your user name
go to the advanced tab
what does it say for your home directory?

---

### Post by anw0625 on 2009-07-07
it says: /home/my name

---

### Post by scrooge_74 on 2009-07-07
I'm guessing nautilus has something broken and is pointing to the wrong place.

So if you open a terminal and type ls -la it gives you a long list of files and directories? If that so then definetly Nautilus went bonkers with the shortcuts to your folders.

---

### Post by lavinog on 2009-07-07
If you open nautilus and go to the desktop, can you press the up button on the toolbar and get to your home folder?

You may want to try purging the .nautilus folder
open a terminal
```
mv .nautilus .nautilus_old
```
See if that changes anything. 
Nautilus should recreate the .nautilus folder with the defaults

---

