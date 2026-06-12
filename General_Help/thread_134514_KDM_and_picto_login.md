---
title: "KDM and picto login?"
date: 2006-02-22
forum: General Help
---

### Post by awakatanka on 2006-02-22
Is it possible for KDM to login with selecting a pictogram (still type pass )and not the normal typing name/pass. I want the login screen a little more like windows xp does. The reason is for average users so they can easly see there name and there picto, its to hard for them to remember there own name ;). 

I realy need this so i can convert those people to linux, the only thing they do is browsing and a little messenger/emailing and some typing. And for this things they better can use linux. And i can secure there system beter with less options.

i choose kde because its more and easy tweakable for me so i can turn off/on options i think they don't need.

---

### Post by ElijahLofgren on 2006-02-22
Yes this is possible. :) 

1st you have to turn off the Kubuntu theme in KDM.

Open /etc/kde3/kdm/kdmrc and find:

```
UseTheme=true
```

change it to:

```
UseTheme=false
```


Now you can make the usernames be listed and assign pictures:
1. Open "kcontrol" (The KDE Control Center). 
2. Under "System Administration go to "Login Manager"
3. Click the "Administrator Mode" button.
4. Enter your password
5. Go to the "Users" tab.
6. Under the "Users" section check the "Show List" box.
7. Choose pictures for the users under the "User Images" section by selecting the username from the drop-down and clicking on the square box under the list.
8. Click "OK"
9. Log out to see the new users list in KDM.

---

### Post by awakatanka on 2006-02-24
Thxs. its working. pitty that it doesn't work with a theme

---

### Post by dresnu on 2006-02-24
Maybe this? [http://www.kde-look.org/content/show.php?content=21124](http://www.kde-look.org/content/show.php?content=21124)

---

### Post by sammydee on 2006-02-24
Have you tried checking out xpde.com?

sam****

---

### Post by awakatanka on 2006-02-25
[QUOTE=dresnu]Maybe this? [http://www.kde-look.org/content/show.php?content=21124](http://www.kde-look.org/content/show.php?content=21124)[/QUOTE]
That was the one i choose to use but it didn't work, but if set UseTheme to false in the kdmrc file it works perfect, i can't get it to work with a theme atm.

---

### Post by awakatanka on 2006-02-25
[QUOTE=sammydee]Have you tried checking out xpde.com?

sam****[/QUOTE]
hehe i have tought about it , to fool the users in thinking they using win xp, but then again if they going to use windows prg's i'm in trouble.

But i choose kde so they now and see its different, only the login part i want to make easier because somehow typing a name is to diffecult for them (the same thing they had in windows to) , so i use the monkey approche and use a picture, some how thats easier to remeber for them.

Have converted some people that only use the windows for surfing and typing and simple games. Put some eyecandy on top and they switch. And if they see a windows prg they wanna use i try to find a alternative on linux for them.

Only hard part atm is voice / webcam on a msn like prg. But luckly they not in to that ( its more a problem for myself atm ;) )

---

