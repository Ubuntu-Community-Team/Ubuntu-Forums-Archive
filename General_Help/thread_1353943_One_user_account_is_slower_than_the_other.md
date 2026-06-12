---
title: "One user account is slower than the other"
date: 2009-12-13
forum: General Help
---

### Post by tcchris on 2009-12-13
Hi
I have two user accounts , "chris " is the main account and "boo" is a second account . I have a 9600xt ATI card , after editing xorg , I get 13000 in glxgears and games play as well as can be expected . The problem is that in the boo account games play very slow and choppy , and glxgears is about 800 . With both accounts logged in , I can switch back and forth and consistently get this performance difference . Using Metacity for both .

---

### Post by tcchris on 2009-12-14
anyone know , is this a bug or normal behavior ?

---

### Post by Fafler on 2009-12-14
I couldn't reproduce the problem. However, i managed to crash my system the 10th time i changed users with different settings. It might be related to the ATI drivers. Maybe someone else with a ATI card out there can try to reproduce it?

---

### Post by tcchris on 2009-12-15
Can someone tell me how to submit this as a bug , if no one has a fix for me .

---

### Post by tcchris on 2009-12-17
Update 
I read on another sight that if the user is not a member of the video group , it will not use hardware acceleration . 
I added boo to the video group , but no joy .
glxinfo reveals that user boo is indeed not using hardware acceleration though .
So the problem is why is user boo not using hardware video acceleration ?

---

### Post by bruno9779 on 2009-12-17
You may need to activate ATI proprietary drivers locally for every user.

Alternatively, maybe the driver do not support two users logged in at the same time. (and that would suck)

What happens if you reboot and log in only with boo?

---

### Post by tcchris on 2009-12-17
This is very interesting ,
If I restart and login as boo , still software , but when I login as chris second , it is also software .
I then rebooted and logged in as chris first , it was hardware and boo still software . Perhaps it is both of the problems you noted .
How do I enable the radeon drivers for both users ?

---

### Post by Techsnap on 2009-12-17
> How do I enable the radeon drivers for both users ?

fglrx and X will be loaded before anyone logs in, it's activated for all users.

Check System>Preferences>Sessions for both users and see if the slower one has more on the list.

If you definitely think it's a graphics problem, go to System>Administration>Users & Groups and make sure the slower user is added to the video group.

---

### Post by tcchris on 2009-12-17
They are both in the video group , boo was not originally but I added today with no effect .boo is a new account nothing changed from creation except adding to video group
boo was added as unpriveleged user , if that is an issue .
I wanted this as a childs account , but they play video games so I need the hardware acceleration .

---

### Post by Techsnap on 2009-12-17
What happens when you run fglrxinfo on the new account? Does it give you any errors?

---

### Post by Leppie on 2009-12-17
for some reason when I use the users and groups applet, modifications I make after unlocking the applet are not always saved. if i do the modifications from the cli, they always are saved though.

have you checked the group file:
```
$cat /etc/group | grep video
```

if user boo is not present in the displayed line, add the user:
```
$sudo adduser boo video
```

---

### Post by tcchris on 2009-12-17
There are no ATI  drivers for the 9600xt . I use the radeon drivers .
glxinfo just shows that boo uses sofware renderer , rather than DRI

---

### Post by tcchris on 2009-12-17
Leppie
output is video:x:44:chris,boo
Would adding boo as unpriveleged user be a factor , I don't know what that means , I just wanted an account where a child couldn't mess up anything . They like to click everything you know .

---

### Post by Techsnap on 2009-12-17
Ah right, okay. Yes try Leppie's suggestion. Did you check the sessions menu by the way just to make sure nothing extra was running?

---

### Post by Leppie on 2009-12-17
> **tcchris said:**
> Would adding boo as unpriveleged user be a factor , I don't know what that means , I just wanted an account where a child couldn't mess up anything . They like to click everything you know .

i've never had issues with that. unprivileged users could use graphics drivers normally.
have you tried creating another account (use the same permissions as you're using for boo) to see if the same thing happens?

---

### Post by tcchris on 2009-12-17
Leppie I will give that a try later today

---

### Post by tcchris on 2009-12-17
Created another user , same as boo . restarted and had the same results .
Deleted boo and new user , then created a new user as desktop user , still no hardware acceleration .
I guess I will either get a seperate computer for the grandkids to play on or just watch them closely on mine . It appears having two users on my computer is not possible .

---

