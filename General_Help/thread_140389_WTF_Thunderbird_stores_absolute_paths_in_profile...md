---
title: "WTF: Thunderbird stores absolute paths in profile...?"
date: 2006-03-06
forum: General Help
---

### Post by el3ktro on 2006-03-06
Damn, now this honestly really sucks:

I wanted to change my username, and I knew this worked before with KDE, because ALL directories in config files etc. are stored as ~/blabla, but now I just saw that e.g. Thunderbird (and possibly other programs) store directories like /home/user/blabla instead of the "universal" ~/blabla. This makes it really hard to rename a user & it's home dir. Is there any way to get around this? I basically want to do this to have two identical usernames on my two machines, that makes it easier to SSH between them - among other stuff.


Tom

---

### Post by WretchedSpawn on 2006-03-06
have you tried just changing a user's name to see if the absolute paths resolve themselves?

---

### Post by kaamos on 2006-03-06
Try```
sudo ln -s /home/newusername /home/oldusername
```
Or just for thunderbird: dig through the config files and change the path..

---

### Post by el3ktro on 2006-03-09
Yes well I guess I have to dig trough Thunderbird's user files. I hope TB/FF are the only programs who do this. Well perhaps I could try to substitute /home(user with ~in FF/TB config files - perhaps it works.

Tom

---

### Post by justleen on 2006-03-09
another work around would be to rename the user, start TB to create a profile, and then simply copy all the data files from TB to the new location.. 
(data will be in some cryptic folder name ~/TB/Profile/GB3452a/  on top of my head.. @work:running MS$)

not goodlooking, but that works

edit: copy the data first to a backup dir... rename, then copy back

---

### Post by el3ktro on 2006-03-09
[QUOTE=justleen]@work:running MS$)[/QUOTE]

Poor guy :-( Well luckily they allowed me to install Ubuntu @work hehe ... well thanks for your hint, thats indeed a good idea, I'll try that!

---

### Post by justleen on 2006-03-09
[QUOTE=el3ktro]Poor guy :-( Well luckily they allowed me to install Ubuntu @work hehe ... well thanks for your hint, thats indeed a good idea, I'll try that![/QUOTE]
hehehe, our goverment isnt keeping up with technology at the same pace as yours is ;)

---

### Post by el3ktro on 2006-03-09
[QUOTE=justleen]hehehe, our goverment isnt keeping up with technology at the same pace as yours is ;)[/QUOTE]

Maybe, but this hasn't to do with our government - I just have been lucky that the admins at my work place are allowed to install whatever they want as an OS - but still out of 70 workers 25 run Linux :-) (all the devs of course)

Tom

---

### Post by justleen on 2006-03-09
[QUOTE=el3ktro]Maybe, but this hasn't to do with our government - I just have been lucky that the admins at my work place are allowed to install whatever they want as an OS - but still out of 70 workers 25 run Linux :-) (all the devs of course)

Tom[/QUOTE]

sorry, bad joke..:-k 
My employer is the dutch goverment.. i know that some german goverment departments run linux - i was referring to that

---

