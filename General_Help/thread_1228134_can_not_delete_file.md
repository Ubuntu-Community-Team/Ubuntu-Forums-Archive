---
title: "can not delete file"
date: 2009-07-31
forum: General Help
---

### Post by rajanm1 on 2009-07-31
quite a simple problem really as the title suggests. basically i have a folder in the deleted items folder that will not delete (when i right click the deleted items waste bin thing and click empty the deleted items folder it appears to come up with a box deleting it but after that goes away it is still there!) is there another way of deleting it?

thanks

---

### Post by michy99 on 2009-07-31
Try opening nautilus as root and see if you can delete it.```
gksudo nautilus
```

---

### Post by iponeverything on 2009-07-31
You could also check to see if the folder has any extended attributes that is preventing its deletion.

 ```
lsattr <foldername>
```

---

### Post by rajanm1 on 2009-08-02
nope neither worked. when i try and delete the folder it comes up with an error box saying that there was an error deleting ..... and then when i click the drop down menu to show more options all that is displayed is "error removing file: permission denied"  :-s

---

### Post by credobyte on 2009-08-02
```
sudo rm -r /path_to_folder

```

---

### Post by measekite on 2009-08-02
> **rajanm1 said:**
> quite a simple problem really as the title suggests. basically i have a folder in the deleted items folder that will not delete (when i right click the deleted items waste bin thing and click empty the deleted items folder it appears to come up with a box deleting it but after that goes away it is still there!) is there another way of deleting it?

thanks

We do not know what version of Ubuntu you are using and if you also dual boot with Windows.

If you dual boot and it is a Windows File boot windows as admin and delete it there.  If not check permissions.  If you are not the owner then do a gksu nautilus and go in as root.  Change the permissions to you as owner and then try and delete the file.

---

### Post by rajanm1 on 2009-08-13
> **measekite said:**
> We do not know what version of Ubuntu you are using and if you also dual boot with Windows.

If you dual boot and it is a Windows File boot windows as admin and delete it there.  If not check permissions.  If you are not the owner then do a gksu nautilus and go in as root.  Change the permissions to you as owner and then try and delete the file.

i don't dual boot, only have ubuntu 8.04lts on here.
how do i find out if i am the owner? and when i type gksu nautilus in terminal it loads fine but when i click on trash from the menu on the left i get an error message saying that the folder contents could not be displayed. operation not supported error message.

really annoying me now because it is on my netbook and i have only about 500mb of space free now :(

---

### Post by wojox on 2009-08-13
Try:
```
gksudo nautilus &#8216;/root/.Trash/&#8217;
```

Open both folders and highlight Shift+Delete

---

### Post by michy99 on 2009-08-13
What is the output from this command?```
ls -l ~/.local/share/Trash/files
```

---

### Post by rajanm1 on 2009-08-13
> **wojox said:**
> Try:
```
gksudo nautilus ‘/root/.Trash/’
```Open both folders and highlight Shift+Delete

it doen't find the trash (its actually called wastebasket on this version)

is there a way to "restore" the folders like you can in xp?

---

### Post by wojox on 2009-08-13
If it doesn't find trash then that means you didn't delete anything as root. No restore folders that I know of.

---

### Post by credobyte on 2009-08-13
```
sudo rm -rf ~/.local/share/Trash/files
```
[COLOR=Red]**WARNING :: Do NOT use this command for anything else!**[/COLOR]

Restart your PC and let us know your current situation ..

---

### Post by rajanm1 on 2009-08-13
> **wojox said:**
> If it doesn't find trash then that means you didn't delete anything as root. No restore folders that I know of.

but i'm the only person on this.:confused:

ok i have found out that the problem is that the permission on the folders is set to access files and when i try and change it comes up with permissions could not be changed. operation not supported by backend.

---

### Post by rajanm1 on 2009-08-18
> **credobyte said:**
> ```
sudo rm -rf ~/.local/share/trash/files
```[color=red]**warning :: Do not use this command for anything else!**[/color]

restart your pc and let us know your current situation ..

thanks it worked great!!! :p

---

