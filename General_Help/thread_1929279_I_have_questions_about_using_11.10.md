---
title: "I have questions about using 11.10"
date: 2012-02-21
forum: General Help
---

### Post by CProgramming on 2012-02-21
Hello guys!
I have number of questions about using Ubuntu 11.10:

1. How do I set dash home will not search in hidden directories?
I mean, for example, I have ".hidden" directory who contains "file.txt". when I search on dash home "file.txt" , this file will be shown. how can I hide files who contained by hidden directories at dash home?

2. When I resuming from suspend I get black screen which makes me have to restart . how can I fix that problem?
I have to note that hibernate mode resuming as well.

3. Can I drag the left programs bar to the bottom?

4. for some reason , Ubuntu doesn't detect my monitor.

[IMG]http://www.myg.co.il/uploads/php4x6vZ3.png[/IMG]

Does anybody know why? however I can use the monitor normally.

however , when I'm using CD Live , Ubuntu detects my monitor normally.

5. What is the terminal command to change file's icon?

6. when I create CShell script file and set execute permission ,
when I execute the script , Ubuntu ask what to do : run in terminal , edit, run or cencel.

How can I set run the script as default?

Thank you very very much!

---

### Post by Frogs Hair on 2012-02-21
2. For some reason with my dual boot desktop , Ubuntu has never responded to the mouse as a means to wake from sleep although it does when running Windows .

I have to depress the power button slightly but not enough to restart. I think this may be due to the OC software and power management on the Windows side. This would be the exception and not the rule.  


3.The Unity bottom launcher is not official , use at your own risk .

[http://www.webupd8.org/2011/11/install-ubuntu-unity-bottom-launcher.htm](http://www.webupd8.org/2011/11/install-ubuntu-unity-bottom-launcher.htm)

4. If you have installed a proprietary Graphics driver the monitor and GPU information will appear in Nvidia X Server settings , ATI or Intel equivalent .

5.I have never used a terminal command to change a file icon , so I'm not sure what you mean .  

Scripts can be added to startup programs .

---

### Post by yetiman64 on 2012-02-21
To address some of your questions,

**3.** It is not as easy as "just dragging" the Unity sidebar, but it can be moved to the bottom with the use of a PPA. [[COLOR=Blue]--webupd8 instructions and link to PPA--[/COLOR]]("http://www.webupd8.org/2011/11/install-ubuntu-unity-bottom-launcher.html"). I have found this method works well here, follow the instructions on webupd8 carefully.
[B]
4.[/B] Not really an answer, but that has always been the case here, although the application has never fully identified my monitor, it has always detected and used the correct resolution.

If it doesn't detect the resolution correctly you may need to use the proprietary drivers for your install and their monitor tool ( eg. nvidia-settings for an nvidia card and proprietary drivers).

**5.** There may be terminal command I'm not aware of, but I've always changed an Icon on a file by right clicking the file and opening the properties box. Clicking on the icon in the properties dialog allows for you to set a different icon. If a launcher file (.desktop or "desktop configuration file") I usually alter the Icon= line in the file (I store the icons in /home/<user>/.icons, and put the icons filename (including extension) in the launcher.
[B]
6.[/B] Open any nautilus window, (your home folder will do), go to the "Edit" menu > Preferences > Behaviour tab, under the heading "Executable Text Files" set your preference for the behaviour. I think you would want the top option going by your earlier post.

---

### Post by CProgramming on 2012-02-21
> **Frogs Hair said:**
> 2. For some reason with my dual boot desktop , Ubuntu has never responded to the mouse as a means to wake from sleep although it does when running Windows .

I have to depress the power button slightly but not enough to restart. I think this may due to the OC software and power management on the Windows side. This would be the exception and not the rule.  


3.The Unity bottom launcher is not official , use at your own risk .

[http://www.webupd8.org/2011/11/install-ubuntu-unity-bottom-launcher.htm](http://www.webupd8.org/2011/11/install-ubuntu-unity-bottom-launcher.htm)

4. If you have installed a proprietary Graphics driver the monitor and GPU information will appear in Nvidia X Server settings , ATI or Intel equivalent .

5.I have never used a terminal command to change a file icon , so I'm not sure what you mean .  

Scripts can be added to startup programs .

thank you friend .. I respond about your responding:

2. At my laptop , which have dual boot of ubuntu 11.10 and windows7 , resuming from suspend works normally .. on the desktop , It's not.

3. its not critical. I wont try.

4. Thanks. so Ububntu does detect my motiner , right? :)

5. mm .. I have directory with 14 songs. there is a default icon for music file , right?
I want to set on each mp3's icon to set new icon which be the album's picture.
If i use the graphical interface - its can be hours to complete it (I have another 100 files)

I thought to do this in for each loop using cshell script .. 

Thanks again bro:)

sorry about the english..

---

### Post by 3rdalbum on 2012-02-21
1. Look up Zeitgeist blacklisting on Google. There is a program you can get that lets you tell Zeitgeist to ignore certain folders (Unity uses Zeitgeist for its search).

I can't remember the name of the program. Zeitgeist Log Settings or Manager or something like that.

---

### Post by yetiman64 on 2012-02-21
> **3rdalbum said:**
> ...I can't remember the name of the program. Zeitgeist Log Settings or Manager or something like that.
I think that is "Activity log manager". :)

---

### Post by CProgramming on 2012-02-22
> **yetiman64 said:**
> To address some of your questions,

**3.** It is not as easy as "just dragging" the Unity sidebar, but it can be moved to the bottom with the use of a PPA. [[COLOR=Blue]--webupd8 instructions and link to PPA--[/COLOR]]("http://www.webupd8.org/2011/11/install-ubuntu-unity-bottom-launcher.html"). I have found this method works well here, follow the instructions on webupd8 carefully.
[B]
4.[/B] Not really an answer, but that has always been the case here, although the application has never fully identified my monitor, it has always detected and used the correct resolution.

If it doesn't detect the resolution correctly you may need to use the proprietary drivers for your install and their monitor tool ( eg. nvidia-settings for an nvidia card and proprietary drivers).

**5.** There may be terminal command I'm not aware of, but I've always changed an Icon on a file by right clicking the file and opening the properties box. Clicking on the icon in the properties dialog allows for you to set a different icon. If a launcher file (.desktop or "desktop configuration file") I usually alter the Icon= line in the file (I store the icons in /home/<user>/.icons, and put the icons filename (including extension) in the launcher.
[B]
6.[/B] Open any nautilus window, (your home folder will do), go to the "Edit" menu > Preferences > Behaviour tab, under the heading "Executable Text Files" set your preference for the behaviour. I think you would want the top option going by your earlier post.

Thank you! I'm verry sorry I didnt reply about your reply. I didnt see that.

well ..

3. Thank you. I'll try .. 
4. Thanks. That problem has got solution .. :)
5. mm .. I need the terminal command because I want to make CShell script which set same icon for all the directory's files.
6. thank you very very mach!! 


> **3rdalbum said:**
> 1. Look up Zeitgeist blacklisting on Google. There is a program you can get that lets you tell Zeitgeist to ignore certain folders (Unity uses Zeitgeist for its search).

I can't remember the name of the program. Zeitgeist Log Settings or Manager or something like that.


  thanks .. I'll try:)


> **yetiman64 said:**
> I think that is "Activity log manager". :)

I'll try and reply soon =D

Thank you friends  , so 1, 3 and 5 still didn't get solution ..

---

