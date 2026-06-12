---
title: "Basic terminal commands"
date: 2011-07-16
forum: General Help
---

### Post by rockerguy on 2011-07-16
Im new to ubuntu and I was wondering if someone could list some basic terminal commands and
explain what they do, and when and why you would use them.

---

### Post by Bizko1288 on 2011-07-16
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

I find the info command very helpful for learning command line i.e.


```
info bash
```
```
info java
```

---

### Post by raja.genupula on 2011-07-16
what ever the thing 

if it is a program to invoke it just type that pgm name in terminal , it will invoke . 
if you want any info then type " man " and program name or command name . it will provides complete information for you .

---

### Post by SoFl W on 2011-07-16
[Linux Commands]("http://linuxcommand.org/learning_the_shell.php")

[Linux command wallpapers]("http://www.google.com/search?q=linux+commands+wallpaper&hl=en&prmd=ivns&tbm=isch&tbo=u&source=univ&sa=X&ei=KloiTuxxjt-BB_y70b4L&ved=0CBgQsAQ&biw=1253&bih=828")
Use the images as your wallpaper, has the most important commands.  Different wallpapers show different commands.

---

### Post by japq7b on 2011-07-16
The commands are endless but one very useful one is
```
man
```
Usage is fairly simple.  When you install a program and have questions as to how to use them via command line you can type
```
man programname
```
for detailed information on usage.

A few other basic commands:

cd -basic navigation
Move into the specified folder
```
cd foldername
```
Move out of the folder you are in up the hierarchy
```
cd ..
``` 
Move to your home directory
```
cd ~
``` 

ls -display folder contents(man ls) for all the things it can do

ifconfig -Network Connection Information

mkdir -Make a folder
```
mkdir newfoldername
```
rmdir -Deletes an EMPTY folder
```
rmdir foldername
```
rm -Removes a file or can be used to remove a non empty folder
```
rm filename
```
```
rm -r foldername
```

Unfortunately most commands are ment to be used in conjunction with others. Such as 'sudo' and 'apt-get'.  For example  
```
sudo apt-get install yakuake
```
would install a drop down terminal.  Yakuake could be replaced by any program in the repo.

Best advice is to just experiment.  If you really want to be a command line junkie learn a command line editor as well.  VIM is my personal favorite.

---

