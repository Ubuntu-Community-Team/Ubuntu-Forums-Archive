---
title: "Copying something to JUST Home...not Home\Username"
date: 2009-11-13
forum: General Help
---

### Post by Stan_1936 on 2009-11-13
I'm trying to copy and paste something to my Home folder.  That's where I'm supposed to put the file.  The folder into which I want to paste it is Home.

It pastes it here, but then it automatically moves it to Home\UserName.  In this folder, there are also folders named Documents, Music, Desktop, etc.etc.

Is there a way to paste it into just Home and ensure that it says there, without moving to Home\Username?

---

### Post by blur xc on 2009-11-13
There is always a way

Are you doing in in Nautilus?  A the top of the window, there's a button hat toggles the path display.  In one mode it gives you those handy buttons to jump you up and down in your folders, in the other it displays the absolute path to whatever folder you are in /home/username etc...  You want to make sure you are in /home.  Also, in the side pane, you can toggle between a few modes there too.  If you are in "Places" mode, you can see general locations to store files, which is quick and easy.  You can switch to Tree mode and that will show you more about your actual file system.  Sorry if I'm a bit vague-

All that aside, I'm not 100% sure if you have permission to put files in the /home folder.  You might need root privileges to do that.

The *easy *way, would be to open a terminal, change to the directory where the file is and 
```
mv <filename> /home
```or if you need root powers
```
sudo mv <filename> /home
```If the source files is already in your home folder, when you open the terminal it should arleady be there, indicated by the ~ symbol (shorthand for home).  If not, just type cd and hit enter, and that will switch you to your home folder (ie. /home/username).  

BM

Edit- I just tested it out, and you need to use sudo to write anything to the /home directory...
Edit2- I also tried copying it, to verify what I already thought was true, so if you copy w/ sudo powers, the resulting files end up being owned by root, but moving them preserves file ownership.

---

### Post by magneze on 2009-11-13
Your "home folder" is generally /home/USERNAME. So if you paste a file into your home folder it will go there.

/home is the home for all your users home folders.

It is quite confusing tbh.

---

### Post by Stan_1936 on 2009-11-13
> **magneze said:**
> ...
It is **quite** confusing tbh.

**Very!**

Thanks for the explanations.

---

### Post by Neezer on 2009-11-13
> **blur xc said:**
> There is always a way

Edit2- I also tried copying it, to verify what I already thought was true, so if you copy w/ sudo powers, the resulting files end up being owned by root, but moving them preserves file ownership.

Just a note....If you use the -p tag with cp it will preserve ownership of the files being copied. and timestamps according to the man page.

---

