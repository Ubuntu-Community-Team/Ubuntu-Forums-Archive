---
title: "Automatically Login can't select user"
date: 2011-06-19
forum: General Help
---

### Post by Faks on 2011-06-19
*Hi everybody i having really bad problem can't select user for *[I]Automatically Login
here is a picture as proof what is my problem ![/I][B]
As we see i can't select user in login as :confused:
image is in attachment !
[/B]if somebody knows how to bypass it trout terminal i will be glad to fix this problem my self any way thanks for attention !:popcorn:

---

### Post by Elfy on 2011-06-19
Hi - sudo nano /etc/gdm/custom.conf 

mine looks like this 

```
[daemon]
DefaultSession=xubuntu
TimedLoginEnable=false
AutomaticLoginEnable=true
TimedLogin=hobgoblin
AutomaticLogin=hobgoblin
TimedLoginDelay=30
```

Please also either edit your image or attach it instead of leaving the large image in the post. Thanks.

---

### Post by Faks on 2011-06-19
sad but this doesn't helps me bug still present and auto login not working :confused:..
**Update**
odd seems i found a problem,i need a conf file content to fill it in 
**/etc/gdm/gdm.conf  **
because it is empty that's odd by the way !

---

### Post by Elfy on 2011-06-19
Did you try tailoring mine to suit you?

---

### Post by Faks on 2011-06-19
> **forestpiskie said:**
> Did you try tailoring mine to suit you?
yes i did :D

---

### Post by Elfy on 2011-06-19
Not sure then. 

I'll try and find something to help. 

Just out of curiosity what does your file look like now?

---

### Post by Faks on 2011-06-19
> **forestpiskie said:**
> Not sure then. 

I'll try and find something to help. 

Just out of curiosity what does your file look like now?
Update 1
check my previous post i did updated with images in attachments !
Update 2
Tried all ways to manipulate with conf files both of them set them same but same issue still appears login panel and ask for password this is really annoying and problematic i hope you can help me resolve the problem !
update 3-4-5
1.i configure user and edit with login without password helped but still must press enter to user to login sad :( 
2.then appeared error could not update iceauthority file fixed it with ---> chown username:username/home/username/.ICEauthority if it fails then use in case of problem use also --> chmod 644 /home/username/.ICEauthority
3.then when finished with both lines then enter  sudo service gdm restart
4.login panel appear wasn't asking password but was needed to press enter to login as user .
5.sad news broke my startup :D hot damm ^_# it can be bypassed but it takes very much time !

---

### Post by Faks on 2011-06-20
bump !

---

### Post by Elfy on 2011-06-21
Bump to catch different timezone.

---

### Post by Faks on 2011-06-21
can close thread this is bug if home dir is encrypted then autologin won't work that's it sow only solution is to make another user or reinstall os :) 
thanks for time and attention i hope it helps other in near future or far it doesn't matter :)

---

### Post by Elfy on 2011-06-22
That makes sense. Wouldn't say it was a bug though.

---

