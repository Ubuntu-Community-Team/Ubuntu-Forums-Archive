---
title: "I do not regain space after deleting file"
date: 2011-02-10
forum: General Help
---

### Post by mrpenguin on 2011-02-10
I am using Ubuntu 10.10 and 10.04 on two different computers.
I have the same problem with both .... when I delete a file on my hard drive or a removable drive I dont get the space back even after I empty the trash.
The file is gone and deleted but its as if its only hidden from me seeing it and still sitting on my drive.

For example when I have files on a thumb drive and I delete them and try and put new files on there it will tell me I dont have enough disk space even though all files have been deleted, the only way for me to get the disk space back is to format the drive.

I have now realized I have the same problem with my hard drives, I delete files but I dont get any space back, eventually I will have a full hard drive but no files on there

Can anybody tell me how to fix this problem ... unless its something I am doing wrong

---

### Post by gandaran on 2011-02-10
> I am using Ubuntu 10.10 and 10.04 on two different computers.
I have the same problem with both .... when I delete a file on my hard drive or a removable drive I dont get the space back even after I empty the trash.
which drive, home or root system?

---

### Post by stoneage on 2011-02-10
> **mrpenguin said:**
> 
For example when I have files on a thumb drive and I delete them and try and put new files on there it will tell me I dont have enough disk space even though all files have been deleted, the only way for me to get the disk space back is to format the drive.


Did you empty the Trash?

---

### Post by cipherboy_loc on 2011-02-10
Use rm from the command line.

```

rm -f /path/to/magic/file

```


Cipherboy

---

### Post by gmargo on 2011-02-10
What tool are you using to delete the file?

---

### Post by eddiebongo on 2011-02-10
Hi,

This was happening to me aswell and all i had to do was press ctrl + H and this shows hidden files which in turn shows you the trash folder on disk where you can delete files permanantly...hope this helps

---

### Post by mrpenguin on 2011-02-10
Yes I delete the Trash
I right click on a file and click on send to trash, then I empty trash but I do not gain any megabytes back on my drive.

This is any type of file, like music and movies ... its easy to see with movies because they are big... around 800mb, after I deleted them there is no change in how many megabytes is left on my hard drive.

---

### Post by mrpenguin on 2011-02-10
> **cipherboy_loc said:**
> Use rm from the command line.

```

rm -f /path/to/magic/file

```
Cipherboy

I copied and pasted that into my terminal ... it just say command not found, I am prob doing something wrong, I never use the terminal.

> jaques@jaques-laptop:~$ rm -f /path/to/magic/file
jaques@jaques-laptop:~$ *******
*******: command not found
jaques@jaques-laptop:~$ 

What is it suppose to do ?

---

### Post by uRock on 2011-02-10
> **mrpenguin said:**
> I copied and pasted that into my terminal ... it just say command not found, I am prob doing something wrong, I never use the terminal.




What is it suppose to do ?

Put the path to your file that you want to delete in the command.

---

### Post by eddiebongo on 2011-02-10
Hi,

When your window is open showing your hard drive press ctrl+h which will show trash on that particular drive......the trash folder is hidden so you have to show hidden files on it

---

### Post by corncob on 2011-02-10
In the File Browser's Edit menu select preferences.  Then, in the Behavior tab, check 'include a Delete command that bypasses Trash'.  You can then choose to do this from the dropdown menu when you right-click the file.  I often hold down the SHIFT key while I press DEL to bypass the trash although someone reported that that didn't work for them.

When you have your pen drive displayed in the file browser check 'show hidden files' in the View menu.  Then open the .Trash folder and delete its contents.  I wasn't able to delete the .Trash folder itself until it was empty but that was several distros ago.

---

