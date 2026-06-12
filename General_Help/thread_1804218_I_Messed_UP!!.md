---
title: "I Messed UP!!"
date: 2011-07-14
forum: General Help
---

### Post by jmacx81 on 2011-07-14
I just upgraded to 11.04 and decided to open compiz and added the 3d windows in.... After that I only have a desk top. No menus, No icons, No bars nothing. Anyone know how I can get this back to the original setup of 11.04?

---

### Post by jmacx81 on 2011-07-14
FYI I am booted up in the recovery mode. Is there a way to revert it back to the way it was when I first downloaded it?

---

### Post by ~!geek!~ on 2011-07-14
There seems to be a trouble with the compiz and unity(the left and top panel in ubuntu 11.04). Many compiz plugins just seem trying to break this unity thing. 

The whole idea to solve your problem is reset compiz settings to the defaults (You will lose all your compiz settings doing that, so follow only if u r ready for that)

First of all, When you are on this blank desktop with no accessible features. press ctrl+alt+(F1 or F2 or F3), whichever you like. Login using your user name and password. Now create a new user say test or something with some password (Add user using "adduser username" command on this terminal. Also add this user to all the groups to which old user belonged using intuitive commands addgroup or groupadd, Oh **** I don't remember but you may try. Its to give this new user ability to use sudo command). Now press ctrl+alt+(f7 or f8 ) (which ever works) to go to GUI. Login with the new user you  created. Everything will work fine with this user. Now you have two choices: 
1) You can be happy with this newuser and remove old user. 
2) But since you upgraded from one version to another, So I think you would like to have all your settings back. So you may try to remove all compiz settings present in homefolder of olduser. To do this you may use google or delete the files and folder having compiz in their name.
See If it helps you. :D

---

### Post by jmacx81 on 2011-07-14
Thanks, I got a new user set up. It has been so long since I've used ubuntu that setting up a new user isn't an issue with me I haven't used it since 8.10 and just now wanting to get back into it.. All I need to do now is delete my old user name. Will my new user name become the root name?

---

### Post by Blasphemist on 2011-07-14
I have 2 things for you to keep handy.

This is the reset of compiz.
```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
sudo reboot
```

THis is the best I've seen for tutorials on the cube and more.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by ~!geek!~ on 2011-07-14
Edited version of this post is there below it

---

### Post by ~!geek!~ on 2011-07-14
As I mentioned in my earlier post, choosing new user and deleting the old user will make you lose all the precious settings which you were having over a long period of time. So its more appropriate to delete the files n folders containing word compiz in them or wait I think there is one more way out: 
You may try to use this solved thread. Its old so m not sure if it still helps [http://ubuntuforums.org/showthread.php?t=681048](http://ubuntuforums.org/showthread.php?t=681048)
Or search for resetting compiz using tty1 or tty2 using: It was something like
 screen 0: compiz --reset . Sorry I don't remember. But u may use this as keyword in google search. 

Or if the old settings are not precious for you, you may convert new user same as old user using terminal:
first check the groups old user belong to using 
> groups oldusername
It will show u output as 
> oldusername: oldusername adm something something something something something something......
Now check for the groups newuser belong to using:
> groups newusername
It will show output as
> newuser: newuser something...

The aim is to make newuser part of everygroup olduser belonged to:
To do this : you will have to use ctrl+alt+f1 again and login with old user credentials in that because the following command will need sudo capability which newuser doesnot have. 
Now use this command again and again to add newuser to group1,2,3,.... olduser belonged to: > groupmod newusername group1  then repeat same command using group2 and so on until olduser and newuser groups' become same. You should check after finishing above commands using: > groups olduser and then>  groups newuser to confirm if both outputs as olduser:olduser xyz abc ... and newuser:newuser xyz abc ... 
Congrats your newuser is equivalent to olduser now.
Now you may safely remove olduser using userdel command if you wish (although Idon't recomment olduser in haste as its not causing any problem to you now. Think about it later)

---

### Post by jmacx81 on 2011-07-14
Ok, thanks! I got everything restored... One problem though, I lost the application launcher in the side bar... any idea how to get that back?

---

### Post by wildmanne39 on 2011-07-14
> **jmacx81 said:**
> Ok, thanks! I got everything restored... One problem though, I lost the application launcher in the side bar... any idea how to get that back?Hi, click on reset unity in my signature below this text and follow the directions for resetting unity.

Then you can use the guide in the previous post for setting up the cube and effects.

---

### Post by jmacx81 on 2011-07-14
Thanks all, I got it all fixed and even on to the cube. Any other ideas of things to mess around on with 11.04?

---

### Post by wildmanne39 on 2011-07-14
> **jmacx81 said:**
> Thanks all, I got it all fixed and even on to the cube. Any other ideas of things to mess around on with 11.04?Hi, there are many things you can do, look in my signature and click on power user and see what you like, Here are some links, and here is a screenshot of my desktop.

[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)
[http://askubuntu.com/questions/35488/list-of-custom-launchers-quicklists-for-unity](http://askubuntu.com/questions/35488/list-of-custom-launchers-quicklists-for-unity)
[http://theravingrick.blogspot.com/2011/04/video-demonstraton-of-few-things-i-like.html](http://theravingrick.blogspot.com/2011/04/video-demonstraton-of-few-things-i-like.html)
[http://blip.tv/jorge-castro/how-i-use-the-unity-dash-5016298](http://blip.tv/jorge-castro/how-i-use-the-unity-dash-5016298)
[http://blip.tv/jorge-castro/how-i-multitask-in-unity-5015448](http://blip.tv/jorge-castro/how-i-multitask-in-unity-5015448)
[http://askubuntu.com/questions/30334/list-of-application-indicators](http://askubuntu.com/questions/30334/list-of-application-indicators)
there are other things as well but I do not want to give you to much information at one time.
Always be careful when trying out new things.

---

### Post by jmacx81 on 2011-07-15
Anyone know how I can access my music and pictures from my windows side?

---

### Post by wildmanne39 on 2011-07-15
> **jmacx81 said:**
> Anyone know how I can access my music and pictures from my windows side?
Hi, you may be able to use this link to get that working.
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

---

### Post by jmacx81 on 2011-07-15
> **wildmanne39 said:**
> 

[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)
[http://askubuntu.com/questions/35488/list-of-custom-launchers-quicklists-for-unity](http://askubuntu.com/questions/35488/list-of-custom-launchers-quicklists-for-unity)
[http://theravingrick.blogspot.com/2011/04/video-demonstraton-of-few-things-i-like.html](http://theravingrick.blogspot.com/2011/04/video-demonstraton-of-few-things-i-like.html)
[http://blip.tv/jorge-castro/how-i-use-the-unity-dash-5016298](http://blip.tv/jorge-castro/how-i-use-the-unity-dash-5016298)
[http://blip.tv/jorge-castro/how-i-multitask-in-unity-5015448](http://blip.tv/jorge-castro/how-i-multitask-in-unity-5015448)
[http://askubuntu.com/questions/30334/list-of-application-indicators](http://askubuntu.com/questions/30334/list-of-application-indicators)
there are other things as well but I do not want to give you to much information at one time.
Always be careful when trying out new things.

Great Stuff here, Thanks!

---

### Post by wildmanne39 on 2011-07-15
Hi, your welome! and when you are done with that stuff you can install ubuntu tweak and customize some more but you need to be careful with ubuntu tweak.

---

