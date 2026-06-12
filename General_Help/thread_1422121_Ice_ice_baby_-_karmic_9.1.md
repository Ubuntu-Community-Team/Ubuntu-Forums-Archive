---
title: "Ice ice baby - karmic 9.1"
date: 2010-03-05
forum: General Help
---

### Post by vikrang on 2010-03-05
There have been some posts for this , but I am unable to find a solution for my problem...On Log On, I get an error - " Could not update /home/vikram/.ICEauthority"..As suggested in some forums I tried Chown , chmod etc from recovery console, but it didnt work...Some one had said that this file is useless and does not serve any purose and that if you delete it Ubuntu will automatically re-create the file. Based on this I deleted the file, Still getting the same error,..Also, I am unable to try other alternatives now, as the file is gone!! 
 
I tried installing Xfce- Xubuntu Desktop 9.1 from GNOME  hoping it would start , but I am not at all able to boot into Xfce with my current GNOME User name and Password in XFCE Environment...The welcome screen pops up a few bubbles come down at the bottom (graphics) then after I enter user name and password, monitor blacks out for a moment and again the same blue screen with bubbles pops up...It seems to go in a loop when I enter the password (which I use in GNOME) ..I am damn sure that the pwd is right....In the options in the bar below, under sessions  there is Gnome, Xfce , Xterm and Failsafe (Gnome)".
 
I tried booting into Xterm (strangely this bopots with my GNOME pwd!)and typing "startxfce4" ....I am getting the same error "Could not update /home/vikram/.ICEauthority"..
 
But apart from this irritating msg, there is no loss of functionality and GNOME apperars to run normally
 
Please advise how to get rid of themessage and login to Xubuntu....

---

### Post by rnerwein on 2010-03-05
hi
may be it's a silly question: but how does the permissions of your home directory looks like:
do a: ls -ld ~/
ciao

---

### Post by vikrang on 2010-03-05
I get the below output

drwxr-xr-x 38 root root 4096 2010-03-04 18:10 /home/vikram/

---

### Post by vikrang on 2010-03-05
I stumbled upon a review which suggested to create a new user..i have created a new user (vikram1) and when I switch to the new user the error msg does not appear...I think the problem is partly solved...I have modified the "/etc/group.conf" file to replace my existing user name (vikram) to the New user ID (vikram1)...By doing this I am getting admin rights and am able to 'su".
 
My doubts are 
 
1. Will new software/hardware driver installations in the old user name be affected If I delete the old user ID (Vikram). (Using sudo userdel Vikram in [EMAIL="root@vikam1"]root@vikam1[/EMAIL])
 
2. Without deleting can i make the new User to be the default ??- meaning that at bootup ,the new user (vikram1) should login automatically..By this way i can make the old as a dummy user.

---

### Post by hawthornso23 on 2010-03-06
Never delete stuff when trying to fix things. Rename instead.

---

### Post by flippo on 2010-03-06
You should```
sudo chown vikram:vikram /home/vikram
```
Your home directory should be owned by you, I don't remember the permissions it needs off hand, but it definitely needs to be owned by you.

If that doesn't fix it try ```
touch /home/vikram/.ICEauthority
chown vikram:vikram /home/vikram/.ICEauthority
```

---

### Post by whiskers75 on 2010-03-06
I used to be getting something like this message too! All I can remember is "Could not update ICEauthority" and then something else. I am now re-installing Linux to see if this problem goes away. If it does not then I shall try the fixes in this post.:KS:KS:KS

---

### Post by vikrang on 2010-03-06
Flippo , Thanks Will try and let you know and btw your signature line is fantastic...This is one of the best I have come across
 
You have symbolically suggested that how much you love linux (This could also be interpreted as if you would elevate the position of Linux by giving it wings) ...All this expressed in a linux- like command...
 
Very thoughtful

---

### Post by vikrang on 2010-03-06
Well the problem is SOLVED...Not exactly the best way but okay...As mentioned earlier , I created a new  User, Gave Su rights by modifying the /etc/group.conf file, Chown the home folder to the new user name., logged in and deleted the old user, i had created a backup of the file group.conf just in case...luckily it went off well...i am also able to log in to Xfce without a problem...

---

### Post by flippo on 2010-03-06
Glad you got it solved.  Thanks for the input on my sig, I actually stole it from someone on the postgres forums.  I just liked it too much.

---

