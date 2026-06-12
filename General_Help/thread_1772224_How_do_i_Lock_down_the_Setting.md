---
title: "How do i Lock down the Setting"
date: 2011-05-31
forum: General Help
---

### Post by cdexter on 2011-05-31
Hello,
 
im looking at changing the computer systems over to Ubuntu, at a scout campsite im staff at. i have sorted some filtering out with dansguardian.
 
but how do i limit the powers of users, so remove all the administrative side and most importantly stop a user changing the network proxy setting.
 
i have used ubuntu before but not for a while, so im a bit of a newbie atm.
 
Cdexter

---

### Post by searchfgold6789 on 2011-05-31
It's easy to do, as I hear. Just go under User Accounts from the Admin menu.

---

### Post by cdexter on 2011-05-31
ok, i have tried this how ever the user still gets the administration options and can still change the network proxy settings

---

### Post by searchfgold6789 on 2011-05-31
I know that there is an option in there where you can change which exact permissions the account has. I think you have to select the user and then click Properties. Then there would be a tab which you can click on to get a list, and then you can check off the list which permissions you want each individual account to have.

---

### Post by cdexter on 2011-05-31
yes, i have tried this. still not working.
 
you go to the users, then advanced setting,  then user privileges and then you get a check list for you to edit.
 
i have unchecked everything and the user still can edit everything.
 
Cdexter

---

### Post by Azdour on 2011-05-31
Hi,

Not that I can offer a good solution, but I too have been hunting for months to stop the user from playing with the network proxy but I've had no real joy.

I do remember vaguely someone saying it cannot be done through gconf-editor (that's were I searched first), but I would like to be proved wrong.

I have been tinkering with the idea of removing the network proxy from the menu or identify the program it launches and make it accessible by root only. I've not done this so I do not know the consquences of doing this, but I have done it with gnome-terminal in the past.

---

### Post by cdexter on 2011-06-03
ok, if you can remember how or link me that would be great, im looking into how to limit the users completely so they can only browse the web. so locked terminal and/or menus and panels would be good.

---

### Post by Jordy_224 on 2011-06-06
How do I block a user from access to the following proxy websites, and others like them using a keyword: 

[CODE]
http://proxz.co//CODE]

This is not as easy as it seems. Both attempts at url block, and phrase block have failed. Please test it out, I need a good example to work with. 

Thanks


update: In the end I used an url block, to prevent access to the websites

---

### Post by Azdour on 2011-06-06
Hi,

To cdexter -> I believe the link is:

[http://ubuntuforums.org/showthread.php?t=751331](http://ubuntuforums.org/showthread.php?t=751331)

If that works for you then you could possibly apply the same principle to other applications like the network proxy - gnome-network-properties

---

