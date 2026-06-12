---
title: "Could not update ICEauthority file /home/user/.ICEauthority in Ubuntu 11.10 &amp; log out"
date: 2012-01-27
forum: General Help
---

### Post by amitaadarsh on 2012-01-27
Help Please !! its urgent.

I was using Ubuntu 11.04 for past 5 months and this error message "  **[FONT=&quot]Could not update ICEauthority file /home/user/.ICEauthority[/FONT]**" appear with an OK/cancel button and after that every thing works fine. Now i updated to 11.10 and it was completed with errors but unfortunately i dont know the errors, it was just a message that appeared when installation was finished and then restarted the computer. My system rebooted and the new login screen appeared. I entered the password and then got the error message:


 "  
**[FONT=&quot]Could not update ICEauthority file /home/user/.ICEauthority [/FONT]**" with the button **Log Out** and as i click on it, log out happens.


here user is my user name. it is administrator account and a single account and one more guest account is there. 



now i am totally stuck in this problem coz its my official system.


i can login to Guest account but i have to work with my admin account that i was working and have the password too. i don't know how to fix this problem. Please give me step by step solution so that i can follow it coz i m not a super hi - fi computer expert, i just love ubuntu and think its better when it matters to keep my data virus free. plezzz help me soon. i really appreciate your help! :confused:

---

### Post by hal10000 on 2012-01-27
Hello,

if you can't log in to your graphical account, you have to try to log in to the non-graphical (terminal) screen. When you reboot and the error message appears, don't click it away, just press the following keys (all together at the same time):
```
[CTRL]+[ALT]+[F2]
``` 
then the terminal- login screen should appear.
Next is to log in to type your username and your password (the password does not appear on the screen, you have to type it "blind".
After you logged in, try the following:
```
ls -l /home/user/.ICEauthority
```

something similar to this should appear:
```
-rw------- 1 user user 2380 2012-01-19 21:18 .ICEauthority
```
this means that you (and only you) have read/write access (rw) to this file.
If this is not the case, then you have to do this:
```
sudo chown user user /home/user/.ICEauthority
```
(you have to type in your password again)

and then type:
```
chmod 0600 /home/user/.ICEauthority
```
that's all (i hope). Reboot and have fun.

---

### Post by amitaadarsh on 2012-01-28
Thanks hal10000, really thankful for me. Yes it worked for me and i just login and see this more beautiful Ubuntu version 11.10 and it looks really great. The problem i found after that i was unable to get into classic mode but fortunately i managed it by installing an application Gnome Panel by this command;

```
sudo apt-get install gnome-panel
```then when i restarted system and click on the icon right side on the password field and choose Gnome Classic, i get into my system.

Now another problem arises:

whenever i try to click on **Places** > **File System** to enter into see my drives there, i got the error message

**File Not Found**. I noticed that **Wine** application also executes and resides in the sidebar and i was unable to open documents, music, pictures, videos and downloads folder that was under the location Places in the top menu bar.

Although i was able to access my hard drives by getting into home folder and then using backspaces go to the root location and from there into Media and there was the main hard drive under there all the volumes were intact.

I then go for uninstall Wine and once i did and restarted my system "EUREKA" , i am now accessing everything just like before.  :guitar:  hey , i m on cloud nine and i am the first one in my office who is properly using Ubuntu 11.10 .. 

Thanks , very helpful.

---

