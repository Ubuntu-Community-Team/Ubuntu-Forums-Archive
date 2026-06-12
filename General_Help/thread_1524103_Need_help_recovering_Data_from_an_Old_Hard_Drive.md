---
title: "Need help recovering Data from an Old Hard Drive"
date: 2010-07-04
forum: General Help
---

### Post by DeathByLinux on 2010-07-04
Hello, 
        I have recently gotten hold of a device that helps me plug my old ATA/IDE hard drive to my computer and view my old files that I wish to recover. I am using Ubuntu and the harddrive that I wish to retrieve the data from also has an Ubuntu install on it. The files I wish to recover are old .doc files, which I want to keep to remember my old writings. 
         The problem I have encountered arises when I wish to open some of the files. The icon for some of the files, which happen to be my best writings, has an X on the top right, indicating that I cannot view the contents. When I click on the files, the following error message pops up: "Access to /media/c885571b-a6e5-4a2d-937a-78af7050910/george/Courses/hist388/Passion.doc was denied."
Now, I am guessing that I need to be able to log in as superuser or something to be able to access these files, so I logged in my terminal as super user by following the instructions outlined on this page:
[http://www.junauza.com/2009/10/how-to-enable-root-super-user-in-ubuntu.html](http://www.junauza.com/2009/10/how-to-enable-root-super-user-in-ubuntu.html)
I still did not have the sufficient access required to be able to open the files that I would like to retrieve. 
Is there anyone that could help me with this? I hold my earlier writings very dear and would like to revisit them, but this very small but insistent problem is standing in the way. I would welcome any help.
-Thank you for your time and consideration.

---

### Post by ezsit on 2010-07-04
You can use the chown command to change ownership of files and directories. Just to be sure, you are using an Ubuntu system with an older internal hard drive connected via a USB adapter cable to the new system? And the old hard drive has partitions that were formatted with a Linux filesystem? Correct so far?

You can change the ownership and group permissions of the files to your current username. For example:

sudo chown username:username -R /media/c885571b-a6e5-4a2d-937a-78af7050910/george

Will change the ownership of the folder /george and all of the files and folders below /george to your current username. Afterwich, you should be able to access them again and copy them over to your new /home folder.

---

### Post by DeathByLinux on 2010-07-04
Thank you, sir.
                     Your advice has resulted in salvaging some of my best writing. This case is solved. :)
-Thank you for your time and swift reply.

---

