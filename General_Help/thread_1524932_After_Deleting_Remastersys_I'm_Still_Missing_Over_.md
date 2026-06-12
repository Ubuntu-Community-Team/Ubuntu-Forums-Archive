---
title: "After Deleting Remastersys I'm Still Missing Over 25GB!"
date: 2010-07-06
forum: General Help
---

### Post by giddyup306 on 2010-07-06
When I clicked on the make it happen button, I accidentally made a full copy of my system.  I went to manually delete this mammoth file, and it still wouldn't regain the memory.  I then tried to delete the entire program from the synaptic, then the terminal.  I would have deleted it from the software center, but now it's gone (but I'm still missing over 25GB).  I've been through a similar delima before, and after searching, I can't find a solution.  All I want to do is completely delete the program including all of the files that it created.  I used sudo apt-get autoremove which I thought should delete everything...  I even deleted everything in the /home/Remastersys folder and it's still not gone.

AHHHHHH!

Please help and thanks in advance.

---

### Post by ankspo71 on 2010-07-06
Hi,
Is there any files in /tmp ?

Have you tried this?
```
sudo apt-get remove --purge remastersys && sudo apt-get autoremove
```

Have you rebooted yet? This is the only thing I'm aware of that will free cached memory. 

Are you sure you didn't move the files to the trash? (Root has its own trash too)
Look in the root directory for /.local/share/Trash/ (it's a hidden directory)
gksudo nautilus will give you access to it (use Shift+Delete to avoid sending the files back to trash)(and be careful not to delete anything else)

Hope this helps.

---

### Post by giddyup306 on 2010-07-06
> **ankspo71 said:**
> Hi,
Is there any files in /tmp ?

Have you tried this?
```
sudo apt-get remove --purge remastersys && sudo apt-get autoremove
```Have you rebooted yet? This is the only thing I'm aware of that will free cached memory. 

Are you sure you didn't move the files to the trash? (Root has its own trash too)
Look in the root directory for /.local/share/Trash/ (it's a hidden directory)
gksudo nautilus will give you access to it (use Shift+Delete to avoid sending the files back to trash)(and be careful not to delete anything else)

Hope this helps.


Hello,

The code you gave me only removed 26 MB.  I have rebooted, and I had changed the file's permission from root to my user.  So it should have been deleted in the trash?  One of the first things I did was look in the synaptic for residual packages.  There wasn't anything in there. Within the .local/share folder there is no Trash even when I enable "show hidden files".  *shrugs*

Thanks

---

### Post by marshmallow1304 on 2010-07-06
Look in /root/.local/share/Trash

---

### Post by giddyup306 on 2010-07-06
> **marshmallow1304 said:**
> Look in /root/.local/share/Trash
Even with the option of showing hidden folders, it does not show me a trash option.  Am I doing something wrong?  I am viewing it with the gksudo nautilus command.

---

### Post by ankspo71 on 2010-07-06
> **giddyup306 said:**
> Hello,
I have rebooted, and I had changed the file's permission from root to my user.  So it should have been deleted in the trash?   *shrugs*
Thanks
If you changed the permissions then it should have gone to your own personal trash. The root's trash folder doesn't exist unless the root user moves something into trash for the first time, so that's why you aren't seeing any trash folder for root

Some people move their home folder contents to /etc/skel for new user's home folder customizations... Did you or remastersys move anything into there? I doubt anything as large as 20+gb would have been moved there though. 

You might be able to locate a directory or a bunch of files with the following commands in the terminal:
```
sudo updatedb
locate remastersys
locate Remastersys
locate *.iso
```
etc
Hope you find it.

---

### Post by giddyup306 on 2010-07-06
> **ankspo71 said:**
> If you changed the permissions then it should have gone to your own personal trash. The root's trash folder doesn't exist unless the root user moves something into trash for the first time, so that's why you aren't seeing any trash folder for root

Some people move their home folder contents to /etc/skel for new user's home folder customizations... Did you or remastersys move anything into there? I doubt anything as large as 20+gb would have been moved there though. 

You might be able to locate a directory or a bunch of files with the following commands in the terminal:
```
sudo updatedb
locate remastersys
locate Remastersys
locate *.iso
```etc
Hope you find it.

Okay now I am quite confused.  Here's a screenshot of the terminal using one of the commands that you posted.  Why am I not seeing a /.local/share/trash.. in the GUI?  It shows the ISOTMP file that I manually deleted.  I think we're getting a lot closer.    

[IMG]http://i169.photobucket.com/albums/u219/giddyup306/trash.png[/IMG]

---

### Post by ankspo71 on 2010-07-06
Hi Again,
I think these are the files you're looking for.

Try this:
```
sudo rm -rf /home/giddyup306/.local/share/Trash
```

then run the locate command again to see if it is gone 
```
sudo updatedb
locate remastersys
```

The trash folder will be recreated again after then next time it is needed.

---

### Post by giddyup306 on 2010-07-06
Okay there are two .locals.  What the hell?  I think I heard this before, but WTH?

The files were in /home/giddyup306/.local/share/Trash/expunged/1264223685. I changed the permissions to giddyup306 so that I could delete them. It does not show up in the trash can, or as freed space.  I will reboot and try again.

---

### Post by giddyup306 on 2010-07-06
> **ankspo71 said:**
> Hi Again,
I think these are the files you're looking for.

Try this:
```
sudo rm -rf /home/giddyup306/.local/share/Trash
```then run the locate command again to see if it is gone 
```
sudo updatedb
locate remastersys
```The trash folder will be recreated again after then next time it is needed.

Hi and thanks for all your help!


I was typing when you posted this.  I think this should get it!!!

---

### Post by giddyup306 on 2010-07-06
I ran the code, and I went from about 150MB of free space to about 950MB.  As you can see I was running quite low on space and that did help. I restarted the system and I still have just over 900MB of free space. :/

---

