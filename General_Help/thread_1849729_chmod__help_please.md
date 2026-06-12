---
title: "chmod  help please"
date: 2011-09-25
forum: General Help
---

### Post by sadam20 on 2011-09-25
I was waching cbtnuggets LPIC 101, instructor made something couldnt work for me

first he made a file :**root@cbt:~# cat > pinkbunny**
**echo Hello**
**root@cbt:~# **
(first i dont how he saved "echo Hello"to the file, which key he used to save that and get **roo@cbt:~#** on the screen)
but i made it using this command :
root@cbt:~# echo Hello > pinkbunny 
then he used :
**root@cbt:~#chmod +x pinkbunny** (to make the file executable) 
and when he tried to execut it using this command :
 root@cbt:~#/root/pinkbunny 
it displayed Hello, but for me didnt work and i get this :
**/pinkbunny :1: Hello not found**
then i went with him and change the variables enviroment PATH hoping this to work 
fianlly he could open the file using :**root@cbt:~#pinkbunny **
but me still have the save output : 
**/pinkbunny :1: Hello not found**

---

### Post by patryk77 on 2011-09-25
[preach]Running all this as root is unnecessary.

This code may be safe, but it's bad practice to run as root all the time.

Read: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[/preach]

Now, onto the actual problem:
You can either run:
cat > pinkbunny
echo Hello
# Ctrl+D
# This writes "echo Hello" to the file and Ctrl+D sends an End-Of-File

# or:
echo 'echo Hello' > pinkbunny

Since you want the script to run "echo Hello", the file needs to contain "echo Hello".

If you run "echo Hello > pinkbunny" the file only contains "Hello", which is not a valid command.

Hope that is clear

---

### Post by sadam20 on 2011-09-25
It`s working :p
thanks so much for that and for the review too i really was about to be crazy about my root password, i thought that i forget it or did amistake when i created 
thanks again :)

---

### Post by mörgæs on 2011-09-25
Good, please mark the thread 'solved'.

---

