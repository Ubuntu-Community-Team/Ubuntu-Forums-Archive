---
title: "Cannot upload file or edit a apache2 files remotely"
date: 2012-03-10
forum: General Help
---

### Post by spindler on 2012-03-10
I am having a problem accessing my server remotely and editing system files like Apache2 virtual host file.

I am able to log in as the ROOT using SSH to get to the terminal of the server.  I can also transfer general files using WINSCP.

I am attempting to create a new virtual host file but I cannot do it remotely.   When I attempt to open the default file to edit it I use the following command.

sudo gedit  default

However I get an error.

(gedit:2087): Gtk-WARNING **: cannot open display:

So I downloaded the default file, edited it and then attempted to upload the new file using WINSCP and I get an access denied error.  When I transfer other file types the transfer works just fine.

There is clearly a permission issue transferring Apache2 files.

1. Why can't I edit this file? 

2. How do I clear this permission issue?

---

### Post by josephmills on 2012-03-10
for running graphical programs as root try ```
gksudo <name of gui program >  
```

---

### Post by josephmills on 2012-03-10
> **spindler said:**
> 

So I downloaded the default file, edited it and then attempted to upload the new file using WINSCP and I get an access denied error.  When I transfer other file types the transfer works just fine.

look at the permissions and what group they belong to. You can read more about file permissions here 
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

not a good idea on apache (security) best to upload to a ~/folder then to try and do it to a root owned dir. Then just move after upload and set permissions and group 

hope this helps

---

### Post by spindler on 2012-03-10
I tried to move the file into the root home directory but I could not as the same error appeared. 

Is there a way to edit files remotely.  For some reason Gedit does not work.  I am able to use VI but it only displays the file.

The file has the following properties.


-rwxrwxrwx 1 root root   952 2012-03-10 08:12 portal

I attempted to use ** gksudo gedit portal**  but I got the following error.


(gksudo:2402): Gtk-WARNING **: cannot open display:

---

### Post by josephmills on 2012-03-10
> **spindler said:**
> I tried to move the file into the root home directory but I could not as the same error appeared. 

Is there a way to edit files remotely.  For some reason Gedit does not work.  I am able to use VI but it only displays the file.

The file has the following properties.


-rwxrwxrwx 1 root root   952 2012-03-10 08:12 portal

I attempted to use ** gksudo gedit portal**  but I got the following error.


(gksudo:2402): Gtk-WARNING **: cannot open display:

with vi you have to press all sorts of hot keys to get it going. 
I would say check out nano first. 

like 

sudo nano /home/name/name-of-file.txt 

edit it then press ctrl+x to exit (the menu is at the bottom of the screen )

I think in vi q to start inputing to the file then escape to get back to command mode and out of insert mode. 

Do you have a gui or want one ?

---

### Post by spindler on 2012-03-10
I was able to copy the file when it had a permission of 777 and I was able to reload it onto my server.

Thanks for your help,

Spindler

---

### Post by josephmills on 2012-03-10
> **spindler said:**
> I was able to copy the file when it had a permission of 777 and I was able to reload it onto my server.

Thanks for your help,

Spindler

you might want to change back(permissions) right after uploading just a suggestion.

Glad that you got it working thou :)

---

