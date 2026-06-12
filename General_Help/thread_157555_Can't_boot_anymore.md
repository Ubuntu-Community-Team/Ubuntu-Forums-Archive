---
title: "Can't boot anymore"
date: 2006-04-09
forum: General Help
---

### Post by WillFerrellLuva on 2006-04-09
The last time I logged into ubuntu I made two changes.

1) I set the login manager (gdm?) to use a random login screen.
2) I deleted the Circles theme

Now when I try to boot into ubuntu it gets to the point where the login screen should come up and I get an error message saying that it cant open the file
/usr/share/gdm/themes/circles/circles.xml

Then it says thats its going to try to start the gtk login thing, but it just sits there and does nothing.

Any suggestions? (maybe I can somehow get that file of the net and put it in that folder using the live cd?)

---

### Post by Ramses de Norre on 2006-04-09
How did you delete the theme? 
I attached my version, you probably can just paste it (remove the .txt extension).

---

### Post by WillFerrellLuva on 2006-04-09
In the login manager thing under amdininstration i think (cant be sure since i cant boot into it) there was a button to delete the theme.  Didnt think it would be a problem to remove it if there was a button to delete it right there.

Thanks for the file, gonna try to put in my system via the live cd

---

### Post by Ramses de Norre on 2006-04-09
Seems like a correct way to delete it.. you can also download the file somewhere (on a win partition or a floppy or something), press ctrl+alt+F1 before gdm breaks, then sudo mv /path_to_file/circles.xml.txt /usr/share/gdm/themes/circles/circles.xml && sudo /etc/init.d/gdm restart

---

### Post by WillFerrellLuva on 2006-04-09
I put the file on a seperate partition and copied in the directory using the recovery mode, but when I boot now its saying that it cant find a .png file in that directory.

Looks like i need all of the files in that directory  :-(

---

### Post by Ramses de Norre on 2006-04-09
It's attached.
EDIT: new file, for some reason it contained all the folders of the path..

---

### Post by WillFerrellLuva on 2006-04-09
thank you, hopefully this will work now :-)

---

### Post by WillFerrellLuva on 2006-04-09
Oh, one more thing....

How do you uncompress and unpackage that file using the command line again?  

(yes im a noob)

---

### Post by Ramses de Norre on 2006-04-09
tar -xvzf /path_to_file/circles.tar.gz && sudo mv circles/* /usr/share/gdm/themes/circles/ 
Use the file I uploaded a minute a go, it's better as the previous one.

---

### Post by WillFerrellLuva on 2006-04-09
That did it.

Im back in Ubuntu.

Thanks for the help.

---

