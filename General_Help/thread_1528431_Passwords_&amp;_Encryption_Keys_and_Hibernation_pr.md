---
title: "Passwords &amp; Encryption Keys and Hibernation problems."
date: 2010-07-10
forum: General Help
---

### Post by LiamCH on 2010-07-10
Hello. I've found the fact that every time my computer turns on and connects to my wireless internet, I have to enter my password into the encryption keys box. Is there any way of removing this feature?

More significantly, in a stupid attempt to disable this feature I went into Passwords & Encryption Keys and deleted all the keys I could...

Since then, Hibernation will not work. It doesn't appear on the menu any more, and there doesn't seem to be any way of re-enabling it. Can anyone tell me how I would bring this back, as it is a feature which I found extremely useful.

Finally, is there any way that I can disable my screen being locked automatically every five minutes? I appreciate that 10.4 has an increased emphasis on security, but I find the fact that a lot of these security features seem to be either difficult or impossible to disable rather frustrating.

Thanks very much for your help.

---

### Post by garvinrick4 on 2010-07-10
First go to screensaver in Preferences and uncheck the box that locks your screen and adjust your display times for going idle and such.

Second read this post:
                                 Keyrings  
 

    1. Open up your Home Folder by clicking Places>Home Folder  
    2. Press CTRL-H (or click View>Show Hidden Files)  
    3. Find a folder called .gnome2 (it has a period at the beginning of the name) and open it by double clicking on it  
    4. In side of the .gnome2 folder, there is another folder called keyrings.  Open it up.  
    5. Delete any files you find within the keyrings folder  
    6. Restart the computer  
 

 After you restart and login (if you&#8217;re automatically logging in) you&#8217;ll probably be asked to enter your wireless networks WPA/WEP encryption key.  After you type that password in, the keyring manager will appear to let you know that it would like to handle the storage of that password and lock it away with a new keyring password.  
 

 Instead of typing in a new password, leave both boxes completely empty and click Create.  
 

 You&#8217;ll then be asked if you know what the hell you&#8217;re doing:  
 

 Go ahead and click Use Unsafe Storage.  
 

 WARNING: Doing this creates a new file in your ~/.gnome2/keyrings/ folder called default.keyring and it will now house passwords IN CLEAR TEXT and not in an encrypted form.  So it is imperative that you are certain no untrustworthy persons can access your user account (either physically or by remote) or they will be able to easily open and read this file and obtain many passwords (for things such as FTP accounts, SSH, e-mail accounts, etc).  Proceed with caution.  
 

 From here on all keyring stored passwords you enter will not safeguarded behind a master password or encryption.  Whether or not you want to do this is entirely up to you.  I personally have had enough of the keyring manager and consider it kind of annoying.  But as I said before, you may have certain environmental factors that make having a master password over the rest of your passwords a good idea.  Keep in mind that the keyring password manager has absolutely nothing to do with your administrative/root privilages password that has to be entered any time you want to apply updates, or add/remove software.  You will still have to type your account password in for these actions, and that is something I am quite comfortable with.

---

### Post by LiamCH on 2010-07-11
Thanks very much! That pretty much solved my problem with the Encryption Keys. Does anyone have any idea about the lack of Hibernation facility though?

---

