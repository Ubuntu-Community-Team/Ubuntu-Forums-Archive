---
title: "Log in problem"
date: 2012-05-16
forum: General Help
---

### Post by ahsan08 on 2012-05-16
I am in a serious problem.  I use ubuntu 12.04

I just curiously transferred 'my-username' folder into "lost+found" folder(which is normally locked). so that anyone from other user account can not access my files.

BUT, after restart I JUST CAN'T LOGIN IN MY ACCOUNT. I have lots of important files and software installed. WHAT NOW???

Is there any way to recover that 'my-username folder' from "lost+found" folder??? HOW???

PLEASEEEEEEEE.............HELPPPPPPP..............

---

### Post by nizamibilal1064 on 2012-05-16
Where did you find My-username folder????

---

### Post by nizamibilal1064 on 2012-05-16
> **ahsan08 said:**
> I am in a serious problem.  I use ubuntu 12.04

I just curiously transferred 'my-username' folder into "lost+found" folder(which is normally locked). so that anyone from other user account can not access my files.

BUT, after restart I JUST CAN'T LOGIN IN MY ACCOUNT. I have lots of important files and software installed. WHAT NOW???

Is there any way to recover that 'my-username folder' from "lost+found" folder??? HOW???

PLEASEEEEEEEE.............HELPPPPPPP..............

Try to login as root ...put root as username and root password(you must have set during installation)....and then put back user folder in same place...hope it might help

---

### Post by Deepak J on 2012-05-16
When I googled the above problem I got an advice to open the terminal and then type the following command:

gksudo nautilus

which will open a file browser which can get into lost+found folder.

But in your case I don't know how to access the terminal nor how Ubuntu is going to verify the admin password.

Don't you worry. There will be something or the other that you might be able to do.

---

### Post by nizamibilal1064 on 2012-05-16
You can do one more thing ...from terminal using sudo move that my usrname folder to its correct place....

---

### Post by Los Frijoles on 2012-05-16
Another thing you can do is to boot into a live CD of any kind (Ubuntu, backtrack, partedmagic, whatever) and use that to look in that folder.

For future reference, to make your folder invisible you can do at least two things:
 - Turn on home folder encryption ([https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)). I personally dislike doing this, but for more mobile computers like laptops it is useful if you have sensitive data that you don't want someone accessing (without putting a bit of effort forth) even if they removed your hard drive and tried to look at the folder.
 - Run 'sudo chmod 700 /home/my-username'. This should make your directory invisible to other users on the computer except super users. You can also do this to folders in your home directory if you want parts of your home directory visible. Note: If you do 'chmod -R 700 /home/my-username' (note the -R) you will change the permissions on ALL the files in your directory to 700 which will give EVERYTHING executable privileges which I assume most people don't really want since that could mess up stuff. Leaving out the -R just makes it change the permissions on the home directory itself without changing the permissions on the files inside.

---

### Post by ahsan08 on 2012-05-16
I have just used a live cd and entered the hard drive but didn't find the lost+found folder. could you please tell me how to undo an action by using a live cd????

---

