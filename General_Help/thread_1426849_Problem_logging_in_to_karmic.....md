---
title: "Problem logging in to karmic...."
date: 2010-03-10
forum: General Help
---

### Post by Th3_Matr1x_Has_Y0u on 2010-03-10
Hi guys/gals. Have a wee bit of a problem.

O.k so decided i wanted to change my username, it appears though that this is no easy task, as it will not allow you to do it, going to user account settings on karmic. So i created a new user account, (e.g test2) i called it a different name from the previous user (obviously;) and set the home directory to the same directory as the last username i was using. (e.g test1) So anyways i had allready changed the "login" settings to "do not ask for password" and log straight in sorta thing. (no login screen), and changed the default user to the new user name i had created. O.k cool so rebooted and boosh, loadsa little error mesasges come up, and it fails to load up the new user account. It loads but to a completely blank orange screen (im guesing the default background) no icons or anything clickable. 
    What i am asking for is basically this, is there any way to change the default user login (which is now (test2) which doesnt work) back to the original user (test1) which im sure will work fine, and then i can remedy the whole scenario (delete the new user haha and stick with the old one) by being logged in as that user. I can logout using ctrl alt F1, F2 or whatever and get to a login screen. I then try and login as the old user (test1) which works fine, and opens up a command line shell. I do not then know how to boot the GUI so that i can simply and easily rectify my problem. I would assume that i could do it via CLI but it would involve locating a bootup configuration file of some sort and changing the user back to the original one.....Any help or thoughts would be greatly appreciated...


Cheers - Dan.

---

### Post by chaanakya_chiraag on 2010-03-10
try
```
sudo userdel test2
```
once you are logged in as test1 in the text console.

---

### Post by chaanakya_chiraag on 2010-03-10
That should delete the user test2 and gdm should automatically work again.  I can't say for sure, though, because I use startx myself after gdm stopped accepting my password (It would just freeze and then return me to the user selection screen :( ).

---

### Post by Th3_Matr1x_Has_Y0u on 2010-03-10
You are legend dude. That solved my problem. Dropped to root shell deleted new account, and boom password screen comes back, and i can login via original account. Many thanks man! - 

Dan =)

---

### Post by chaanakya_chiraag on 2010-03-11
No problem :)

---

