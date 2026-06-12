---
title: "editing the windows registry via ubuntu"
date: 2011-09-09
forum: General Help
---

### Post by RFRFG on 2011-09-09
i'm using windows vista ubuntu dual boot on a dell latitude D410. on vista i recently attempted to create a hidden admin account via regedit and removed the admin privileges from the original account. now when i try ctl+alt+delete on the login screen, it does nothing. when i try doing anything involving admin's privileges on the standard account, it asks for an admin's password, but doesn't allow for me to enter the password. instead it says to insert a smart card. i do not believe my computer can use smart cards... this version of windows vista was installed after i received the computer because it was running ubuntu previously and i wanted windows as well. i can't run the command prompt as an admin because of the aforementioned and the admin account doesn't show in safe mode. i believe i may have somehow made windows forget completely about the admin account, because there is no folder in users, hidden or otherwise... even when trying to type the full extension in the address bar, it says the path does not exist...

i was wondering if there was some way that i can alter the registry for windows using ubuntu without requiring the use of a windows admin via a third party application or by file replacement. 

thank you for your time

---

### Post by raja.genupula on 2011-09-09
[http://ubuntuforums.org/showthread.php?t=624943](http://ubuntuforums.org/showthread.php?t=624943)


go with this

---

### Post by RFRFG on 2011-09-09
... the system restore was never on... i feel ashamed... is it possible to get the necessary files from someone who has the windows default/unaltered ones?

---

### Post by Bodsda on 2011-09-09
Probably best to use a password reset cd. They can list valid accounts and then reset the password for it. 
 
[http://www.howtogeek.com/howto/windows-vista/reset-your-forgotten-password-the-easy-way-using-the-ultimate-boot-cd-for-windows/](http://www.howtogeek.com/howto/windows-vista/reset-your-forgotten-password-the-easy-way-using-the-ultimate-boot-cd-for-windows/)
 
I think you've probably figured this out by now, but always create an export of the registry hive you are working on before oyu start fiddling.
 
Hope this helps,
Bodsda

---

### Post by RFRFG on 2011-09-09
yeah.. i believe i have realized that...

---

### Post by Bodsda on 2011-09-09
> **RFRFG said:**
> yeah.. i believe i have realized that...
 
Wouldnt it be so much better if there was a system that didnt rely on an archaic registry to store system critical information...... oh, wait. :)

---

### Post by RFRFG on 2011-09-09
and i don't have a cd drive... but i have an idea involving editing the registry with chntpw... if i can figure out how to save my changes

---

### Post by RFRFG on 2011-09-09
> **Bodsda said:**
> Wouldnt it be so much better if there was a system that didnt rely on an archaic registry to store system critical information...... oh, wait. :)
now if only that os had full support for executable files. then i'd never have to use windows.

---

### Post by Bodsda on 2011-09-09
> **RFRFG said:**
> now if only that os had full support for executable files. then i'd never have to use windows.
 
It does... your confusing executable files with binaries compiled to run on win32 based machines. 
 
You don't have to use a cd, create a live usn stick with the iso and boot off that.
 
Bodsda

---

### Post by RFRFG on 2011-09-09
BIG sigh of relief and accomplishment... chntpw came through for me!!! have to say... it was a good thing i had ubuntu installed, otherwise i may have just formatted and re installed. and a very big thanks to raja.genupula. that thread helped me do what i needed

as you can tell i have a basic understanding of how both windows and ubuntu work, but my ignorance limits me. anyway...

i used chntpw to access the registry made my alterations, and after a little snooping in the help, figured out how to properly quit and save. when i logged on, the admin account was once again accessible. i wasn't wanting my account to be THAT hidden...

---

### Post by RFRFG on 2011-09-09
and yes you are correct about my confusion, however i was referring specifically to the ".exe" files

---

### Post by Bodsda on 2011-09-09
> **RFRFG said:**
> and yes you are correct about my confusion, however i was referring specifically to the ".exe" files
 
yeah, .exe doesnt mean 'all executables' in the same way windows doesnt mean 'PC' :)
 
Bodsda

---

