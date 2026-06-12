---
title: "Mounting and CD problems"
date: 2012-04-18
forum: General Help
---

### Post by DeathByLinux on 2012-04-18
Hello,
          I am running ubuntu on a broken laptop. Most things on it don't work, but the computer still does the job. The CD rom is busted, so I have to use ISO files of my previous games to install things. So, let me explain what I am having problem with right now.

I have the ISOs for my diablo 2 install disc, cinematic disc, and the play disc. I installed Gmount to help me mount these ISOs in order to get them to work. 
So, here is what I do and let me know what I am doing wrong:

1. Start-up Gmount
2. Mount install ISO on Desktop folder named "d2install". Gmount says "An error occured /home/usr/Desktop/d2install seems to be mounted read-only." It says this for every mount I do for the other discs.
3. Go to terminal, type 
```
 wine /home/usr/Desktop/d2install/install.exe 
```
The computer asks me to "Please insert CD labelled 'Install Disc.'"

Now, I thought that I have already mounted the disc by using Gmount. Where am I going wrong, here? I should have the thing mounted and ready to go, should I not? Is there a better way of doing this? Please let me know what you guys think.


-DeathByLinux

P.S: For the admins at Ubuntuforums:I do legitimately own Diablo 2. If you guys want, I can post pictures of the original copy if you guys want proof.

---

### Post by Toz on 2012-04-23
Try this:
```
ln -s /home/USER/Desktop/d2install ~/.wine/dosdevices/e\:
ln -s /PATH/TO/diablo2.iso ~/.wine/dosdevices/e\:\:
```
...where:
- USER = your userid
- /PATH/TO/ = the path to the actual iso file.

Then start the install via:
```
wine "e:\install.exe"
```

---

### Post by DeathByLinux on 2012-04-25
Hello Toz,
                 thank you for your concern. I have solved the problem and it was not related to mounting at all. Turns out that the reason that the program was asking me to insert  a CD is because I did not have a cd-rom drive being emulated in WINE. Meaning, I had a C drive and a Z drive, but neither were cd rom drives and the computer did not recognize the mounted copies of my game's iso. I don't know if you understand, but the problem was related more to WINE than anything. Anyway, I solved it by going to WINE configuration, then the "Drives" tab and then making it so that the Z drive (or whatever you want it to be) would reference the folder that I mounted the iso on. It was THEN that the computer, under WINE, could locate the iso.
Haha, it was a great learning experience, I cracked this problem on my own and had a blast! Thank you for your concern, Toz. I am going to close this thread, now.

-DeathByLinux

---

