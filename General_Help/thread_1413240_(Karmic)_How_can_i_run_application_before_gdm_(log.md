---
title: "(Karmic) How can i run application before gdm (login screen or auto login)"
date: 2010-02-22
forum: General Help
---

### Post by zhawzhank on 2010-02-22
I have program that work like Fedora Firstboot it's run only one time after finish installation. I have two questions to ask.

1. How can I start this application before gdm start (login screen or auto login)
2. How can I start this application in fix display resolution (800x600)
 
My method now is
(This is a part of script , this script execute from /etc/init.d/myfirstboot , I create symlink to /etc/rc2.d/S1myfirstboot for start it before anything)
 
 gdm-stop # first time I use /etc/init.d/gdm stop 
 DISPLAY=:1
 export DISPLAY
 /usr/bin/Xorg :1 &
 /usr/bin/metacity --display=:1 &
 /usr/bin/python /usr/share/myprogram/myprogram.py
 
 /usr/bin/killall -9 metacity
 sleep 2
 /usr/bin/killall -9 Xorg
 /usr/sbin/update-rc.d -f myfirstboot remove
 /etc/init.d/gdm start

I don't understand why first time firstboot start the system will auto loging in but not complete yet and then my script is start and it's work does not fine I think that is another user is already login , but if I re run my firstboot again and again (by setting something that can revoke my firstboot and restart) it's work before auto login and every things is ok! :confused: 
  
Sorry about my English ;)

---

### Post by raktarok on 2010-02-22
Hi,

For your second problem, you can add this line in the script, just before you start your program:
```
xrandr -s 800x600
```
This changes the resolution to 800x600, you want to do that, right?

And for your first problem, I am not sure what is wrong. But instead of making the init script, you can try placing the script's lines in the file /etc/gdm/Init/Default. See if this helps. If you do this, you won't need to stop gdm and then start X like you do in the above script. 
Actually, if you use this method, the script will run everytime you restart the computer, but you can make the script run your program only during the first boot by adding a suitable if statement in the script. If you are not sure what to add to the script, then post here again. I will try to help. 
This is not a proper solution, but it should do the job if you are desperate.

Other people in the forum should know better solutions or why your method is not working, so you can wait for more answers. 
    
Good luck, and no need to be sorry about your English, I think I understood what you are trying to do :)

---

### Post by zhawzhank on 2010-02-24
Thanks a lot for your help!
Finally, I use /etc/gdm/Init/Default and xrandr with my script follow your suggestion :)

---

### Post by raktarok on 2010-02-24
Glad it worked for you! feel free to post again if you have any other problems!

---

