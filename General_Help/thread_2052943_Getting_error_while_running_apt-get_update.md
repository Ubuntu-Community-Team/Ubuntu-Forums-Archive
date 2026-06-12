---
title: "Getting error while running apt-get update"
date: 2012-09-04
forum: General Help
---

### Post by soumoks on 2012-09-04
i recently tried adding the patch to minimize apps to launcher and am getting this error whenever i run apt-get update in terminal
```
 sourabh@sourabh-desktop:~$ sudo apt-get update
[sudo] password for sourabh: 
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/ojno
-unity-minimize-on-click-precise.list
E: The list of sources could not be read.

```
btw this is the patch i applied and it didnt work..
```


sudo add-apt-repository ppa:ojno/unity-minimize-on-click
sudo apt-get update && sudo apt-get upgrade

```
i am running ubuntu 12.04,pls help..thanks in advance..

---

### Post by soumoks on 2012-09-05
someone pls help me,software centre is also not working because of the same reason,i removed the concerned ppa,but still getting errors(update errors)..advice needed and fast..

---

### Post by raja.genupula on 2012-09-05
```
cat /etc/apt/sources.list.d/ojno -unity-minimize-on-click-precise.list
``` post that output here .

---

### Post by soumoks on 2012-09-06
> **raja.genupula said:**
> ```
cat /etc/apt/sources.list.d/ojno -unity-minimize-on-click-precise.list
``` post that output here .

I got this
```


sourabh@sourabh-desktop:~$ cat /etc/apt/sources.list.d/ojno -unity-minimize-on-click-precise.list
cat: invalid option -- 'i'
Try `cat --help' for more information.
sourabh@sourabh-desktop:~$ 

```

---

### Post by plucky on 2012-09-06
> sourabh@sourabh-desktop:~$ cat /etc/apt/sources.list.d/ojno -unity-minimize-on-click-precise.list
cat: invalid option -- 'i'


There is a space in the **ojno -unity-minimize-on-click-precise.list** command.

Post output for ```
ls -l /etc/apt/sources.list.d
```

---

### Post by soumoks on 2012-09-06
> **plucky said:**
> There is a space in the **ojno -unity-minimize-on-click-precise.list** command.

Post output for ```
ls -l /etc/apt/sources.list.d
```

this is the output for the above command
```


sourabh@sourabh-desktop:~$ ls -l /etc/apt/sources.list.d
total 88
-rw-r--r-- 1 root root 132 Sep  4 19:25 atareao-lenses-precise.list
-rw-r--r-- 1 root root 132 Sep  4 19:25 atareao-lenses-precise.list.save
-rw-r--r-- 1 root root 176 Sep  4 19:25 google-chrome.list
-rw-r--r-- 1 root root 176 Sep  4 19:25 google-chrome.list.save
-rw-r--r-- 1 root root   0 Sep  4 19:25 ikarosdev-unity-revamped-precise.list
-rw-r--r-- 1 root root  80 Sep  4 19:25 ikarosdev-unity-revamped-precise.list.sa
ve
-rw-r--r-- 1 root root 168 Sep  4 19:25 indicator-multiload-stable-daily-precise
.list
-rw-r--r-- 1 root root 168 Sep  4 19:25 indicator-multiload-stable-daily-precise
.list.save
-rw-r--r-- 1 root root   0 Sep  4 19:25 kokoto-java-omgubuntu-stuff-precise.list
-rw-r--r-- 1 root root  81 Sep  4 19:25 kokoto-java-omgubuntu-stuff-precise.list
.save
-rw-r--r-- 1 root root 138 Sep  4 19:25 narfss-proyectobs-precise.list
-rw-r--r-- 1 root root 138 Sep  4 19:25 narfss-proyectobs-precise.list.save
-rw-r--r-- 1 root root   4 Sep  4 19:25 ojno-unity-minimize-on-click-precise.lis
t
-rw-r--r-- 1 root root   4 Sep  4 19:25 ojno-unity-minimize-on-click-precise.lis
t.save
-rw-r--r-- 1 root root 150 Sep  4 19:25 otto-kesselgulasch-gimp-precise.list
-rw-r--r-- 1 root root 150 Sep  4 19:25 otto-kesselgulasch-gimp-precise.list.sav
e
-rw-r--r-- 1 root root 136 Sep  4 19:25 piotr-zagawa-ma2-precise.list
-rw-r--r-- 1 root root 136 Sep  4 19:25 piotr-zagawa-ma2-precise.list.save
-rw-r--r-- 1 root root 152 Sep  4 19:25 plushuang-tw-uget-stable-precise.list
-rw-r--r-- 1 root root 152 Sep  4 19:25 plushuang-tw-uget-stable-precise.list.sa
ve
-rw-r--r-- 1 root root 144 Sep  4 19:25 scopes-packagers-ppa-precise.list
-rw-r--r-- 1 root root 144 Sep  4 19:25 scopes-packagers-ppa-precise.list.save
-rw-r--r-- 1 root root 134 Sep  4 19:25 webapps-preview-precise.list
-rw-r--r-- 1 root root 134 Sep  4 19:25 webapps-preview-precise.list.save
sourabh@sourabh-desktop:~$ 

```
i just copy pasted the command,so i dont know between what words there is space and thanks for taking an interest in my problem..

---

### Post by soumoks on 2012-09-06
[IMG]http://i.imgur.com/6kZoE.png[/IMG]I don't know if this helps but i am getting the following output when i run apt-get update in the terminal,i have attached an image as well..
```


sourabh@sourabh-desktop:~$ sudo apt-get update
E: Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/ojno-unity-minimize-on-click-precise.list
E: The list of sources could not be read.

```

---

### Post by raja.genupula on 2012-09-06
> **soumoks said:**
> I got this
```


sourabh@sourabh-desktop:~$ cat /etc/apt/sources.list**.d/ojno -unity**-minimize-on-click-precise.list
cat: invalid option -- 'i'
Try `cat --help' for more information.
sourabh@sourabh-desktop:~$ 

```


Hi you left a space there  , Bold area 

```
cat /etc/apt/sources.list.d/ojno-unity-minimize-on-click-precise.list
```Just paste this in terminal

---

### Post by soumoks on 2012-09-06
> **raja.genupula said:**
> Hi you left a space there  , Bold area 

```
cat /etc/apt/sources.list.d/ojno-unity-minimize-on-click-precise.list
```Just paste this in terminal

ok,i got this when i pasted the above command in the terminal
```


sourabh@sourabh-desktop:~$ cat /etc/apt/sources.list.d/ojno-unity-minimize-on-click-precise.list
ain
sourabh@sourabh-desktop:~$ 

```

---

### Post by plucky on 2012-09-07
> sourabh@sourabh-desktop:~$ cat /etc/apt/sources.list.d/ojno-unity-minimize-on-click-precise.list
ain

> E: Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/ojno-unity-minimize-on-click-precise.list
E: The list of sources could not be read.

The contents of the file is incorrect,so delete the file and your problem should go away.

```
sudo rm /etc/apt/sources.list.d/ojno-unity-minimize-on-click-precise.*
``` will remove the two files.

> -rw-r--r-- 1 root root   4 Sep  4 19:25 ojno-unity-minimize-on-click-precise.lis
t
-rw-r--r-- 1 root root   4 Sep  4 19:25 ojno-unity-minimize-on-click-precise.lis
t.save

Good Luck

---

### Post by soumoks on 2012-09-07
> **plucky said:**
> The contents of the file is incorrect,so delete the file and your problem should go away.

```
sudo rm /etc/apt/sources.list.d/ojno-unity-minimize-on-click-precise.*
``` will remove the two files.



Good Luck

Thanks a lot :) :),fixed my problem..and lastly is there a proper working patch for minimize on click for unity?

---

