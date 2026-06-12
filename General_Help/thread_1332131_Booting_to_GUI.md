---
title: "Booting to GUI"
date: 2009-11-20
forum: General Help
---

### Post by dgohn on 2009-11-20
After installing ubuntu, removing the CD and then rebooting it booted to a command prompt.  Since I didn't know the root password I had to use the admin account I created during install and login under that.  It logged me into a command line interface.  How do I make it boot up into the GUI?


Thanks

---

### Post by lisati on 2009-11-20
Try logging in with the user you set up during the installation process. Then try the following command and let us know how you get on: ```
startx
```

One question: Did you install the server edition or the desktop edition?

---

### Post by dgohn on 2009-11-20
Server edition, I did the startx and got 
Xinit: No such file or directory (errno2): unable to connect to x server
Xinit:No such process (errno3): sever error

also tried sudo gdm like I saw in another post and that returned no such command

---

### Post by dgohn on 2009-11-20
Also how do I gain root access if I don't know the default password?

---

### Post by lisati on 2009-11-20
Ok, got it. When you install the server edition, it doesn't normally install a gui. One option is as follows:
```
sudo aptitude install ubuntu-desktop
```
It will ask for your password. Don't worry if it doesn't show when you type, this is a normal Ubuntu secrurity precaution.
All going well, all the necessaries for a "standard" Ubuntu GUI will be installed.

edit: don't worry too much about the root password, Ubuntu's approach is to use the "sudo" command whenever you need to do something that needs admin privileges. Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by dgohn on 2009-11-20
Awesome. installing now, how about the root password?  Is there a standard default password?   Thanks a ton.

sorry didn't refresh before I posted this... reading your link now...

---

### Post by dgohn on 2009-11-20
However, I still would like to have the password for root.  Is there a way to do this?  I never do regular things under root, but there are times that I log into the root account.  I had it set up before the hard drive change but I don't remember how to gain access to it.

Thanks  (still installing ubuntu desktop FYI)

---

### Post by lisati on 2009-11-20
Have a look here: [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

If you *really* have a need to be able to log in as "root", there are ways mentioned in the forums.....

---

### Post by dgohn on 2009-11-20
Ahhhhhh ok, I did not know that policy existed and I appologize for asking for that information.  Obviously I figured it out before, I'll figure it out again :)  Thanks for all of your help, I am going to go ahead and assume your help for the ubuntu-desktop worked since its still installing and I will mark this thread solved as soon as it boots to the GUI.   Thanks again, what a GREAT forum for us beginner Ubuntu users!

---

### Post by dgohn on 2009-11-20
By the way, like a user earlier on another thread stated... "Google is your friend"  With one google attempt I figured out and "remembered" how to enable root.   Thanks a ton and I can definitely see why Ubuntu would have this policy.  Thanks a ton to all of the users on this forum.

---

