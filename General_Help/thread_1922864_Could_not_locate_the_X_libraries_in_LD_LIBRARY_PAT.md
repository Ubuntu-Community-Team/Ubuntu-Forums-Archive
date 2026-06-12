---
title: "Could not locate the X libraries in LD_LIBRARY_PATH"
date: 2012-02-09
forum: General Help
---

### Post by alkopop79 on 2012-02-09
I've installed Actel's Libero SOC environment and when I try to run the application with this command:

<Libero_Installation_Folder>/Libero/bin/libero

I get the following error:

Could not locate the X libraries in LD_LIBRARY_PATH

Where are the X libraries and how can I add them to the PATH?

---

### Post by hwttdz on 2012-02-09
X libraries most likely refers to the X11 graphical libraries.  Unfortunately there are a lot of those.  They usually live in places like /usr/lib.

I might run 
```
find / -xdev -name "libX11*.so*" 2>/dev/null
```
which should tell you where some x11 libraries live.  Probably /usr/lib, /usr/lib32, /usr/lib/`arch`, and string all the directories (not the full path to the libraries, just the directory they are in) together like thus:
```
export LD_LIBRARY_PATH="dir1:dir2:dir3"
```
and put that line in your .bashrc, then source .bashrc and try again. You might have more or less than 3, don't worry about that at the moment.

---

### Post by alkopop79 on 2012-02-09
Will try it, thank you for your help!

---

### Post by hwttdz on 2012-02-09
> I've found the X libraries but have not much idea about bash. How can I open and edit the bash? I have used vi editor before, does that help? Is the bash specific to an application? How can I find it? Thank you for your kind help!

In your home directory there is likely a file named .bashrc, you won't see it when you do an ls because it starts with a dot character making it a hidden file.  But open it up with the text editor of your choice (I use gedit because I like graphical editors).  And add the "export LD_LIBRARY_PATH" line to the end of the file and save and close.  Then at the command line run, "source .bashrc" and it will add those directories to your LD_LIBRARY_PATH variable (you can check this by doing "env|grep -i path".

---

### Post by ktpi on 2012-05-09
Did adding the libraries to LD_LIBRARY_PATH resolve the issue?  I am having the same issue with Libero SoC.  I followed the above steps to add those libraries to the path, but am still getting the error "Could not locate the X libraries in LD_LIBRARY_PATH".

---

