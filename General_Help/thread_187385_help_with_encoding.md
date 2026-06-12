---
title: "help with encoding"
date: 2006-06-02
forum: General Help
---

### Post by newhen on 2006-06-02
need help with this okay im trying to [run this~click here ]("http://atitd.com/dl/files/eClient-linux-i686.run")
so i save the url link to desk it downloads then i try to open it in text editor and it says text-editor doesnt regonize this encoding what do i do now thanks newhen~~](*,)

---

### Post by newhen on 2006-06-02
bump

---

### Post by disturbed1 on 2006-06-02
open a terminal and type
```

cd Desktop 
chmod a+x eClient-linux-i686.run

``` 
Replace Desktop with the location of the file

This will change the file to a binary file that can be ran. If it's a program that needs to be installed, you have to 
```

sudo ./eClient-linux-i686.run

```

---

### Post by newhen on 2006-06-02
[QUOTE=disturbed1]open a terminal and type
```

cd Desktop 
chmod a+x eClient-linux-i686.run

``` 
Replace Desktop with the location of the file

This will change the file to a binary file that can be ran. If it's a program that needs to be installed, you have to 
```

sudo ./eClient-linux-i686.run

```[/QUOTE]
thank god for you i praise you forwithout my game i would be lost in interity foreverrrrrrrrrrrrrrrrrrrrrrrrrrrrrrr

---

### Post by disturbed1 on 2006-06-02
I take it everything installed ok?

Post back and let us know how the game works out.

---

### Post by newhen on 2006-06-02
is it suppose to be doing this ? its starts umcompressing and right next to it the terminal windows shows this uncompressing files from _______.........................................................................................................................................................................................................
..................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
..............................................................................
..............................................................................
..............................................................................
..............................................................................
..............................................................................
..............................................................................
..............................................................................
v
v
..............................................................................

EDIT: or is that just showing progress?
EDIt : nevermind it went through thanks ill reply if i need anything else thanks very much friend

---

### Post by newhen on 2006-06-03
okay here is what is does it not working now

terminal
:```
admin@admin-desktop:~/Desktop$ sudo ./eClient-linux-i686.run
Creating directory eClient
Verifying archive integrity... All good.
Uncompressing ATITD linux i686 Client Install........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
To download client and play: cd ./eClient then hit the enter key, then type: ./elaunch and hit the enter key
admin@admin-desktop:~/Desktop$
admin@admin-desktop:~/Desktop$
admin@admin-desktop:~/Desktop$ ./elaunch
bash: ./elaunch: No such file or directory
admin@admin-desktop:~/Desktop$
admin@admin-desktop:~/Desktop$ sudo ./elaunch
sudo: ./elaunch: command not found
admin@admin-desktop:~/Desktop$  cd ./eClient
admin@admin-desktop:~/Desktop/eClient$ ./elaunch
Cannot open elaunch.bug for writingadmin@admin-desktop:~/Desktop/eClient$

```
here is screen shot 
[IMG]http://i40.photobucket.com/albums/e223/pinkman12/Screenshot.png[/IMG]

---

### Post by newhen on 2006-06-03
bump
[B]
EDIT: DO U THINK I SHOULD JUST USE WINE, WILL WINE WORK FOR THIS? ( IT COMES IN WINDOWS FORMAT WICH I HAVE USED AND ITS MUCH BETTER[/B]

---

### Post by disturbed1 on 2006-06-03
I just downloaded the file, did these steps, and it worked fine

(1) chmod a+x eClient-linux-i686.run
(2)./eClient-linux-i686.run
(3)cd eClient
(4)./elaunch

(1) changes eClient-linux-i686.run into a binary to launch
(2) launches the binary, which only extracts some files, and creates a dir. called eClient
(3) I changed into that dir that was just created
(4) I launch the program.

---

### Post by newhen on 2006-06-03
[QUOTE=disturbed1]I just downloaded the file, did these steps, and it worked fine

(1) chmod a+x eClient-linux-i686.run
(2)./eClient-linux-i686.run
(3)cd eClient
(4)./elaunch

(1) changes eClient-linux-i686.run into a binary to launch
(2) launches the binary, which only extracts some files, and creates a dir. called eClient
(3) I changed into that dir that was just created
(4) I launch the program.[/QUOTE]
thanks im gonna unistall then reinstall

---

### Post by newhen on 2006-06-03
didnt work i get this error message admin@admin-desktop:~$ chmod a+x eClient-linux-i686.run
chmod: cannot access `eClient-linux-i686.run': No such file or directory
admin@admin-desktop:~$
admin@admin-desktop:~$

---

### Post by disturbed1 on 2006-06-03
[quote=newhen]didnt work i get this error message admin@admin-desktop:~$ chmod a+x eClient-linux-i686.run
chmod: cannot access `eClient-linux-i686.run': [SIZE=18][COLOR=red]**No such file or directory**[/COLOR][/SIZE]
admin@admin-desktop:~$
admin@admin-desktop:~$[/quote] 
There's your sign. You have to be in the same directory as the file ;)

---

### Post by newhen on 2006-06-03
okay thanks okay so can you just tell me how to kill all the old egensis stuff then reload it plz srry for all the question

---

### Post by newhen on 2006-06-03
[QUOTE=newhen]okay thanks okay so can you just tell me how to kill all the old egensis stuff then reload it plz srry for all the question[/QUOTE]
bump

---

### Post by newhen on 2006-06-03
Help
MY
Problem

~

---

### Post by newhen on 2006-06-03
where do i go then its saved on disk ?!?!??!?!?!??!

---

