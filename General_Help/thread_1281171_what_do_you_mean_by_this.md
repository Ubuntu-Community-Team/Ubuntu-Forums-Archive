---
title: "what do you mean by this?"
date: 2009-10-03
forum: General Help
---

### Post by meluzi02 on 2009-10-03
[B]Can't load /etc/samba/smb.conf - run testparm to debug it


any idea?
[/B]

---

### Post by akakingess on 2009-10-03
Sounds like your samba config file has been or gotten corrupted (obviously), could you possibly open it and copy and paste the contents into a backup file and reinstall samba? Or stop samba (if it's even running) and try editing it that way and then restarting and see if you get the same message?

---

### Post by meluzi02 on 2009-10-03
yes i think that my samba conf was being corrupted, i think this is the worst problem that i ever encountered since using this kind of desktop...

i really don't know what to do....i am just a new user of such distribution so i am not familiar of those commands and i think i hitted commands which is not the solution to my problem...

---

### Post by akakingess on 2009-10-03
Don't worry, we can work through it, although I may have some trouble explaining where to go as I am not in front of one of my Ubuntu machines right now. Can you at least locate your smb.conf file? If you can, then just enter " sudo gedit /pathto/samba/smb.conf " then enter your password and it should open the config file within gedit (I assume that you are using Gnome), see if we can get that far and we'll take it one step at a time.

---

### Post by swerdna on 2009-10-03
If you open a terminal window and run this command:```
testparm -s
```then  it will tell you what is wrong, and you can copy/paste the output back here.

OTOH if you just want to replace the corrupted file with an original, then [here's the original on this link:]("http://ubuntu.swerdna.org/lanprimer/smb.conf.txt")

---

### Post by akakingess on 2009-10-03
I wasn't suggesting he just replace it with a new one, but at least wanted him to save the corrupted one before creating a new one, I hope you didn't think that's what I was suggesting, I was just trying to go one step at a time per the language barrier.

---

### Post by swerdna on 2009-10-03
> **akakingess said:**
> I wasn't suggesting he just replace it with a new one, but at least wanted him to save the corrupted one before creating a new one, I hope you didn't think that's what I was suggesting, I was just trying to go one step at a time per the language barrier.

Yes of course, I agree replacing smb.conf is a last resort (or for advanced users who know what to do with a new one). IMO the first thing to do would be to get a statement about the error/corruption from the testing module by running the command 'testparm -s'.

---

### Post by meluzi02 on 2009-10-04
thanks for your help..

I have already run the code but i only get this report

[B]marvz@MARVZ:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
params.c:OpenConfFile() - Unable to open configuration file "/etc/samba/smb.conf":
    No such file or directory
Error loading services.[/B]

oh no...

and actually i accidentally moved the path of my samba conf file to home folder and its original location was at the etc folder

i used this code:

**sudo mv /var/lib/dpkg/info/samba.postinst /etc/$USER**

---

### Post by swerdna on 2009-10-05
Maybe if you uninstall it and reinstall it -- it might all reposition itself correctly.

---

### Post by meluzi02 on 2009-10-05
i tried all the moves, removing but it cannot be removed...

---

### Post by swerdna on 2009-10-05
> **meluzi02 said:**
> i tried all the moves, removing but it cannot be removed...

Somehow you have to reinstall Samba correctly. Perhaps start a new thread asking how to uninstall and reinstall a damaged application.

---

### Post by meluzi02 on 2009-10-09
thanks for all your replies...

---

