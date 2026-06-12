---
title: "ubuntu / XP dualboot using same folders"
date: 2010-07-24
forum: General Help
---

### Post by Rowanmf on 2010-07-24
Ok ,now that i have real internet at home I have formatted and reloaded XP and added a dualboot for ubuntu , what i now want to do is have documents link in ubuntu pointing to c:\......\My Documents on the XP partition .
I know it involves dynamic links , BUT i have no idea how to replace the link in my home folder with such a link .Once i do that one i will do the rest .. 
Also wanted to ask , i have a 1TB drive ntfs that ubuntu can see but when i go back to XP it does not see it anymore on the fresh install of XP ,(yes i know it's not a ubuntu thing but we all know there is no forum for XP like this ) I do know the when i added the drive it set it up as a dynamic ..any thoughts would be most welcome on that one .
Tomorrow i will load thunderbird on both and make them both point to the same data , have done that plenty of times , no sweat .

Thanks

---

### Post by robsoles on 2010-07-24
Seems sort of nutty and risky to me but I guess it is less risky to access your Windows installed 'documents and settings' from Ubuntu than it is to access Ubuntu home folder from Windows - Linux is less likely to randomly 'step' on your Windows permission(s) and ownership(s) than a variety of things in Windows is likely to step on Linux permission(s) and ownership(s) so...

If your Ubuntu installation came after your Windows installation you could have manually partitioned during Ubuntu install to have that Windows partition mounted by /etc/fstab already but if it isn't already mounted then you should read [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) for a how to on that one.

Then you can use 'ln -s' in terminal to create a softlink to the appropriate directory in your Windows installation from where-ever you want in your ~/ home directory.


As to drive not being recognised in Windows: Please check "Control Panel"->"System"->[tab]>"Hardware"->[button]>"Device Manager" dialog box for entries with symbols of failure on them - Google is your friend, if I am right you just have SATA device that is not recognised by standard XP setup and you should be able to find a driver for it using Google (mind all the 'driver detective' downloads though!!!)

---

### Post by Rowanmf on 2010-07-25
Thanks , thats why i want to do it , ubuntu is much better looking at the windows stuff and not messing it up than XP in to ubuntu.

However there seems to be a small problem :

ln -s (sourse)(target) 

does not seem to like the spaces in windows folder names !!

So i played and fiddled and this is what i came up with , 
Go to the folder in xp you want ,right click and use -make link 
copy the link to where you want it ie. in your home folder 
delete the folder thats empty and rename your link to the exact name of the old folder .. hey presto and you even get the nice little icon showing ..

Thanks also for the heads up on the drive , i had thought it was a driver issue but just needed the preverbial second oppinion.

What i generally do is have same programs in XP and Ubuntu and have the ubuntu programs configs and data look at the XP data ,so when you do something in one program ie.write a email when you are in ubuntu that email is there as well same for browsers etc .

Thanks 
Rowan

---

### Post by robsoles on 2010-07-25
Very welcome.

If I ever make another machine capable of booting Windows (whatever version) alongside my primary OS, instead of just keeping it in a VM in virtualbox under it instead, then I think I might pursue the options you have - I got no reason to right now but who knows what will ever make me do what in the future!

Did you 'escape' the space characters in the Windows folder names that had them in your 'ln' commands? If you don't know for sure what the [Tab] key does in terminal then please open terminal, 'cd' to the root of your Windows installation and type in
```
cd Docum[Tab]
``` and check out (1) auto-completion and (2) escapement of space characters in filenames for Linux.

(My 'code' example assumes you don't have anything but 'Documents and Settings' that starts with 'Docum' in the root of your windows file-system, it also (now after edit) assumes that the 'd' is capitolised on it)

---

