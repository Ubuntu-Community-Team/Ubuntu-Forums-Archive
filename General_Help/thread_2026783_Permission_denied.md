---
title: "Permission denied"
date: 2012-07-15
forum: General Help
---

### Post by UltimateCat on 2012-07-15
After reading this thread:
ubuntuforums.org/showthread.php?t=1698319
I understand that I should not change the permissions or ownership of any of the systems directories. It could cause the system to become inoperable or worse unrepairable.

I found the command
```
gksudo nautilus

```
But I still don't understand how to work with the files that are associated with this file that is on my desktop.  It's locked on my desktop with a padlock above the icon.  It's all related to the hplip-3.12.6.run that I used to install my new HP Printer with.

Where or how can I find more info. to learn?

---

### Post by Bucky Ball on 2012-07-15
'gksudo nautilus' launches you as root to the Nautilus file manager. Be careful! As you are root you can change anything. This should allow you to change permissions, or are you saying you've tried that and it's not working?

What exactly is the problem with the HPLip file???

---

### Post by UltimateCat on 2012-07-17
> **Bucky Ball said:**
> 'gksudo nautilus' launches you as root to the Nautilus file manager. Be careful! As you are root you can change anything. This should allow you to change permissions, or are you saying you've tried that and it's not working?

What exactly is the problem with the HPLip file???

The hplip file is locked onto my desktop ( with a padlock over the file icon) and it won't let me move, cut, copy or otherwise drag it off my desktop.

Maybe I should not of ran the .run as root.....is that why it's locked to my desktop?
Anyway:
I get this error message if I attempt to move it
```
Error while moving "hplip-3.12.6"
Error moving file: permission denied

```
I really do not understand how to change permissions and I am taking heed to you telling me...Be Careful....so I will do nothing until you advise; as I can tell that  you know better than I-

---

### Post by Bucky Ball on 2012-07-17
You have installed the printer? If so, open a terminal, use the 'gksudo nautilus' command, navigate to the HPLip file and delete or change permissions. Nothing else. Then close the file manager (Nautilus) in the usual way. Keep an eye on the terminal while you're doing this and it should show a read out for any errors that are thrown up and give you some idea of why you can't delete, if you can't in this scenario. 

If you haven't installed the printer, you are going to need this file. Have a read of the 'Read Me' file inside the HPLip folder. That tells you exactly how to install. 

Good luck. ;)

PS: You might also try the install wizard here if you haven't installed yet:

[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

PPS: I just looked in the repositories and it should be in the software centre. Install hplip from there.

---

### Post by UltimateCat on 2012-07-17
Bucky Ball:
I have successfully installed the printer. Did so a few days ago; So that's good.

I wrote down your instructions so I follow them correctly.

I'm just not sure on one thing.  Once I have navigated to the file I don't know how to change the permissions....How do I do just that?:confused:

---

### Post by Bucky Ball on 2012-07-17
You don't need that file if you've installed the printer. Kill it. ;)

---

### Post by UltimateCat on 2012-07-17
> **Bucky Ball said:**
> You don't need that file if you've installed the printer. Kill it. ;)

Thanks

---

### Post by techvish81 on 2012-07-17
> **UltimateCat said:**
> Bucky Ball:
I'm just not sure on one thing.  Once I have navigated to the file I don't know how to change the permissions....How do I do just that?:confused:

go to desktop folder , right click on the particular file and go to "properties" ,  then in the permissions tab you will have three sections out of which you can change the 2 options not the ownership. i mean you can add your username which is there when you click on the second option. 

see the below screenshots.

---

### Post by UltimateCat on 2012-07-18
> **techvish81 said:**
> go to desktop folder , right click on the particular file and go to "properties" ,  then in the permissions tab you will have three sections out of which you can change the 2 options not the ownership. i mean you can add your username which is there when you click on the second option. 

see the below screenshots.

Tried what you posted and I am locked out of those 2 options that you mentioned.  Looks like the only way I'm going to be able to get rid of this folder/file is to execute the 
```
gksudo nautilus

```

---

