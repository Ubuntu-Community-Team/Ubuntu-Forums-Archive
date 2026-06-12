---
title: "permissions, is chmod the only way to change them?"
date: 2009-08-10
forum: General Help
---

### Post by rhythmiccycle on 2009-08-10
i making/hosting a website from my pc, running ubuntu desktop.

i already made a test site on my laptop and i am copying it into to my pc/server.

it seems for every page and every folder i copy into the /var/www folder i have to go into the terminal and use "chmod" to change, the permission for every file. Over and over again. its getting annoying.:x

is there a way to change the permissions of all the files in a folder?

or 

is there a way to make is so when i copy new file in to the /var/www folder their permissions are not removed?

every file i copy into the folder gets set to "u=rwx, g=, o=" but i need "o=r"

please tell me there is a better way than just using chmod on each-and-every-single-tedious file to change their particular-unique-specific permissions.

---

### Post by hetx on 2009-08-10
chmod xxx -r /path/to/folder

In my experience that sticks. The -r stands for recursive, it changes permissions of all files and all subfolders. Make sure you get the path right, you don't want to mess up permissions.

---

### Post by credobyte on 2009-08-10
chmod all files in a folder:
```
sudo chmod 755 /var/www/*

```

copy & don't lose permissions:
```
sudo cp -a /old/www /new/www
```

---

### Post by rhythmiccycle on 2009-08-10
> **hetx said:**
> chmod xxx -r /path/to/folder


i entered the code like this

```

sudo chmod a=r -r /var/www/functions

```

hoping to change all the files in the functions folder to have read permissions, but i get this error message

> chmod: cannot access `a=r': No such file or directory

whats the deal?

---

### Post by credobyte on 2009-08-10
> **rhythmiccycle said:**
> i entered the code like this

```

sudo chmod [COLOR=Red]**a=r -r** [/COLOR]/var/www/functions

```hoping to change all the files in the functions folder to have read permissions, but i get this error message



whats the deal?

```
sudo chmod a+r -r /var/www/functions
```

---

### Post by rhythmiccycle on 2009-08-10
> **credobyte said:**
> ```
sudo chmod a+r -r /var/www/functions
```

i still get the same error:

chmod: cannot access `a+r': No such file or directory

---

### Post by asmoore82 on 2009-08-10
the recursive option needs to come before the permission specifications;
also, not sure if it's absolutely necessary, but I'm used to seeing
a capital ``R'' used with `chmod` and `chown`

Whenever you used `chmod -R`, you should use diff and relative permissions and never absolute permissions ...
for example: +rw, go=u, o-w are all good; 755, 644, o=r are all bad.
The reason for this is ``-R'' will touch files **and** folders.
the capital X permission is an absolute life saver, it means
"add execute only on folders or if the file is already executable by anyone else"

this is probably what you should be running often: ```
sudo chmod -R +rX /var/www
```

I would bet from looking at your OP that the files were brought over
on a flash drive; that is one of the things that will cause all files
to get the improper `rwx------` permissions.

---

### Post by rhythmiccycle on 2009-08-10
> **asmoore82 said:**
> 
this is probably what you should be running often: ```
sudo chmod -R +rX /var/www
```



i copied that code and it worked, thanks.

but i don't really understand the "+rX" part

i would think the code would be like this:
```
sudo chmod -R a+r /var/www
```
i didn't run this code, but would it have the same effect?
would it change everything in the www folder to  read?

i'm just learning how to use chmod,

i learned from here: [http://catcode.com/teachmod/](http://catcode.com/teachmod/)
but there is nothing there about "-R" or "X" or a "+" with nothing in front of it.

do you know of a tutorial that explains those parts?

i'm trying to really understand this command line stuff.

> Give a man a fish; you have fed him for today. Teach a man to fish; and you will not have to listen to his incessant whining about how hungry he is.


> **asmoore82 said:**
> 
I would bet from looking at your OP that the files were brought over
on a flash drive; that is one of the things that will cause all files
to get the improper `rwx------` permissions.
you are correct i am copying the files over from a flash drive

---

### Post by gjoellee on 2009-08-10
> permissions, is chmod the only way to change them?...NOPE!

You can change permissions for you whole system if you use:
```
gksu nautilus
```
and right click on the folder you want to change permissions on, and select "Properties". You should find a permission tab with a lot of option in the new window the opens.

---

### Post by rhythmiccycle on 2009-08-10
thanks for that tip, gjoellee

---

### Post by colau on 2009-08-15
> **rhythmiccycle said:**
> i copied that code and it worked, thank
```
sudo chmod -R r+x /var/www
```
i learned from here: [http://catcode.com/teachmod/](http://catcode.com/teachmod/)
Cheers.

---

