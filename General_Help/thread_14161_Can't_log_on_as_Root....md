---
title: "Can't log on as Root..."
date: 2005-02-05
forum: General Help
---

### Post by Kimimaro on 2005-02-05
Although i should be able to  (in theory)
My problem is quite a specific one...
When i boot my computer, and a login screen goes up and I want to log on as 'root' I can't do it :(.   >in login i type 'root', in password I type the right pasword, but when I hit enter after the pasword, the login bar returns (!). I guess I type everything right. Because when I would not, the password bar would 'freeze' for a sec, and then return to login...and it doesn't freeze, everything happens fast  <
I'm the only user on my computer, I installed Ubuntu on it, and created one aditional account (just as reccomended on install). Ok. I can log onto my other account without a problem. From this account I can acces root on terminal (with 'su', so I know the password to root... well it's the same password as to the other account anyway ), but I can't do so from login screen (I guess I'm repeating myself  :wink: ).
I ask for help... the reason is obvious - I am new to Ubuntu and just can't handle it  :confused:

---

### Post by hashimoto on 2005-02-05
Login as normal user. Go to Desktop > Administration > Login screen setup. Select the "Security" page and check "Allow  root to login with GDM". You should now be able to login as root. Be careful...

BR
Hashimoto

---

### Post by Kimimaro on 2005-02-05
Thank You, I can now log on as root :) This was annoying, because I could not access sources.list . Well.. now I can, thanks one more time!

---

### Post by hashimoto on 2005-02-05
Well, actually you can access your sources list by opening ternimal and writing "sudo gedit /etc/apt/sources.list". That way you have root privileges to the file and you can edit and save it and you would be much safer (not messing the system with excessive rights by being root to everything at the same time). I would recommend this way. And in any case when you need root privileges do it rather by usig the "sudo command" way.

BR
Hashimoto

---

### Post by Kimimaro on 2005-02-05
Wow... I have not had any idea about it ! I guess it's a long way for me in understanding ubuntu linux ... :) That way seems safer indeed, thanks again  :D

---

### Post by hashimoto on 2005-02-05
Well, now you know. And you will learn a lot more, too...
Hope that you know about the [http://ubuntuguide.org/index.html](http://ubuntuguide.org/index.html)

BR
Hashimoto

---

