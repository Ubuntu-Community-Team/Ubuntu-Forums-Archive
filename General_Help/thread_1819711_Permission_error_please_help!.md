---
title: "Permission error please help!"
date: 2011-08-06
forum: General Help
---

### Post by Techmate on 2011-08-06
If this information excists here so sorry I was not able to find it. 

How to change permissions in Unbuntu for those people who are trying to change persmissions in a subdirectory.

Open the terminal and then type: 

> sudo chmod yourpermission number /thenameofyourdirectory 

Example:

> sudo chmod 755 /directory

---

### Post by juhaszjozsef on 2011-08-06
I think it's not Ubuntu related problem more a php related issue...
Try checking your web folders and:
chmod 777 your_upload_folder

On a standard ubuntu install it should be somewhere /var/www/yoursite/images
so as an example:
sudo chmod 777 /var/www/myGallery/Watermark2/images

Please also check (and read about) absolute and relative paths.
php.net is a good place to start.

---

### Post by galvatron408 on 2011-08-06
don't ever change your permissions to 777 and don't tell people to do it either.

this opens up all your files to all sorts of security issues

---

### Post by Morbius1 on 2011-08-06
> **Techmate said:**
> If this information excists here so sorry I was not able to find it. 

How to change permissions in Unbuntu for those people who are trying to change persmissions in a subdirectory.

Open the terminal and then type: 
```
 sudo chmod 755 /directory                      
```
I don't understand the question. After you run that command does it not change permissions?

Or is the question specifically about the files and subdirectories within /directory?

If you want to apply read/write to owner and read only to everyone else for everything within /directory then you need to do something like this:
```
sudo chmod -R a+rwX,go-w /directory 
```What that will do is make all folders executable which you must do to have them open, it will give the owner r/w permissions to everything, it will give read only permissions to everyone else, and it will not make any files executable that are not executable to begin with.

What you want to avoid doing is this:
```
sudo chmod -R 755 /directory
```Octal mode settings ( i.e., 755 ) aren't smart enough to differentiate between a directory and a file so that command would make every file executable and that would not be a good thing.

Since the first person who responded talked about php and web folders there's a good change I misunderstood the original question ;)

---

