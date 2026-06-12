---
title: "Manipulating files"
date: 2010-01-25
forum: General Help
---

### Post by antobbo on 2010-01-25
Hi there, I am new to Ubuntu and I am trying to get my head around the terminal, performing very basic operations. I am reading this guide, which seems really helpful and easy [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php). Now, I was trying to move a file called this_is_a_test.odt from the Desktop to another folder on the Desktop called "test". Now, in the shell I run: antonio@ubantu:~$ mv this_is_a_test.odt test
but it came back with "mv: cannot stat 'this_is_a_test.odt': no such file or directory
so I run: antonio@ubantu:~$ mv home/antonio/Desktop/this_is_a_test.odt test
but again to no avail...what am I doing wrong?
Thank

---

### Post by wojox on 2010-01-25
Open your terminal and go to the Desktop directory:

```
cd desktop
```

Then 

```
mv this_is_a_test.odt /test
```

---

### Post by howefield on 2010-01-25
Try doing a cd Desktop first.

---

### Post by J V on 2010-01-25
In the first case, you are in your home (~) not your desktop, in the second, you specify the absolute path, but forget the root slash!

mv Desktop/this_is_a_test.odt test
(or)
cd Desktop
mv this_is_a_test.odt ~/test
(~ is your home...)
(or)
cd Desktop
mv this_is_a_test.odt ../test
(.. is up one directory)
(or)
mv /home/antonio/Desktop/this_is_a_test.odt test

---

### Post by antobbo on 2010-01-25
oh silly me!! thanks guys that works. I went into the desktop directory and then typed mv this_is_a_test.odt test (without the / because with it it kept saying "permission denied"). I will also try J V's, I might post again in case I get stuck.
Thanks

---

### Post by Ordes on 2010-01-25
when u r in /home/Desktop you dont need the "/" anymore, as the file is inside desktop.

When working with files in terminal, it is always important to have to right pathing. In the beginning it might be the best to always go inside the folder where cd files are. In this case the following command will always just have the file name as path. For example your tst.txt is in /home/Documents
1) cd /home/Documents
2) mv tst.txt

---
about "/" and absolute pathing
absolute pathing is very confenient when u used to it. As u dont need to "cd" between directories
> "/" in the beginning refers to root
> so your command mv /tst.txt  would assue location root , file tst.txt
> your command mv home/antonio/Desktop/tst.txt, would assume, home is subfolder from the currrent folder, and from there keep on the path antonio etc... which is wrong too so u need >> /home/antonio/Desktop/... 
as we want root , home , antonio , desktop , file
> if however your would have used 1) cd / 2) mv home/... than the command would have worked, as your current directory is "/" and home is a path starting from root... 

--- help
1) cd   >>just enter cd and u will always go directly to your home
2) ~/   >>will always autofill the path with /home/username/
3) [tab] when typing a command / filename etc; u can hit tab to autofill the command.. try cd/h [tab] and it will become cd /home
4) if [tab] does not autofill, the path is wrong or there are multiple choices, which u will see when u hit tab again; in this case, the terminal needs more letters in order to know where u want to go;
e.g cd /s [tab] [tab]  u will get a list of s*** files /folders than are for choice if u enter one more letter, cd /sy [tab] it will become cd /sys.. as there should be no other choice for /sy**; and so on

---

### Post by antobbo on 2010-01-26
thanks for your reply and help. I copied the file from my desktop to the test folder and then back again and all good. Then I tested it again and i run the command (as it is on the terminal)
antonio@ubanto:~/Desktop$ mv this_is_a_test_.odt ~/test
 to again move my file this_is_a_test.odt from the desktop to the folder "test" on the desktop and my filed disappeared...it is nowhere, I can't find it even with "search for files" option...what happened? where is my file gone?
Thanks

---

### Post by michy99 on 2010-01-26
Your file is now in your home directory, but it is now named "test" The directory you were trying to move it to is ~/Desktop/test, not ~/test. If the second argument of mv is a directory, it will move the file to that directory. If it is not a directory, it moves the file to a new file with the given name. WARNING. If a file exists with that name, mv will overwrite it and the file which originally had that name will be gone.

---

### Post by antobbo on 2010-01-27
thank you!

---

