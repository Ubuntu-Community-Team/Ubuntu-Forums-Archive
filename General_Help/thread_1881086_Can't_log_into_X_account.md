---
title: "Can't log into X account"
date: 2011-11-14
forum: General Help
---

### Post by Lyuokdea on 2011-11-14
Odd Problem here, 

I had some problems with x, and tried to restart (from command prompt). It failed, and I ended up restarting the computer, but now I can't log into an X session (for my user) at all. 

When i put in the password the screen goes blank for a minute, and then returns to the password screen (doesn't say the password is wrong or anything, just returns). I can log into any other users Xwindows fine (with the same driver/video settings etc.). I can also log into the terminal or su over to my user once I'm in their account (so the account itself is fine).

I tried installing fluxbox and logging into that instead, but it also failed. Is there a setting somewhere I can try to reset?

Thanks,

~Lyuokdea

---

### Post by Lyuokdea on 2011-11-15
Does anybody have any suggestions for this? Is there a file i can destroy which would reset the X settings to default for this user? It seems odd that it works perfectly for every other user on the OS.

Thanks,

~Lyuokdea

---

### Post by 2F4U on 2011-11-15
The X settings are stored in a folder in your home directory, but since I use Xubuntu I can't tell you the name of the folder. In Xubuntu it is named .config (note the "." in front of the name) and the folder is hidden.

---

### Post by Toz on 2011-11-15
> I can also log into the terminal or su over to my userHave a look in your home directory at the the files **.ICEauthority** and **.Xauthority**. If you do not have ownership of those files, change it so you do and try again. Sometimes when something goes worng, root ends up owning those files and it interrupts the login process for a user.

If that doesn't work, post back the contents of your ~/.xsession-errors file.

---

