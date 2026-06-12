---
title: "EyeOS"
date: 2009-07-29
forum: General Help
---

### Post by afroman10496 on 2009-07-29
Can someone tell me how to install EyeOS on Ubuntu 9.04:confused:? I tried their instructions for Gutsy, but it didn't work (and messed up my Firefox) :(. Thanks!:popcorn:

---

### Post by zzzBrett on 2009-07-30
Do you have a PHP / Apache setup already?

If I recall correctly, I think you just extract the eyeos archive into your public folder, and it just works.  ...but maybe this has changed.

---

### Post by afroman10496 on 2009-07-30
> **zzzBrett said:**
> Do you have a PHP / Apache setup already?

If I recall correctly, I think you just extract the eyeos archive into your public folder, and it just works.  ...but maybe this has changed.
The Wiki was for Gusty ([http://wiki.eyeos.org/HOWTO_Install_eyeOS_on_Ubuntu_Gutsy](http://wiki.eyeos.org/HOWTO_Install_eyeOS_on_Ubuntu_Gutsy)), and I followed all the steps; it didn't work for me.

---

### Post by zzzBrett on 2009-07-30
> **Afroman10496 said:**
> The Wiki was for Gusty ([http://wiki.eyeos.org/HOWTO_Install_eyeOS_on_Ubuntu_Gutsy](http://wiki.eyeos.org/HOWTO_Install_eyeOS_on_Ubuntu_Gutsy)), and I followed all the steps; it didn't work for me.

Open synaptic package manager and see if apache2 is installed. (A green box next to it = installed)

If it is, try opening firefox and go to [http://localhost/](http://localhost/), and post back with what you find.

---

### Post by afroman10496 on 2009-07-30
[SIZE=5]**It works!**[/SIZE]

But I still don't know how to get EyeOS:(

---

### Post by zzzBrett on 2009-07-30
> **Afroman10496 said:**
> [SIZE=5]**It works!**[/SIZE]

But I still don't know how to get EyeOS:(

Now you know that your web server is working.  Now try this:

```
sudo nano /var/www/test.php
```

This will open the file test.php in the default public folder for your web server.

Now copy this line into that:

```
<?php phpinfo(); ?>
```

Press Control + O, Enter to save the file, then press Control + X to exit.

Note: You can also create this file with the text editor of your choice, ie gedit, leafpad, etc.

This php script will output information about your php installation -- if PHP is working.

So.. try going to [http://localhost/test.php](http://localhost/test.php) in firefox, and see what you get.

---

### Post by afroman10496 on 2009-07-30
I got <?php phpinfo(); ?> . Now what?

---

### Post by zzzBrett on 2009-07-30
> **Afroman10496 said:**
> I got <?php phpinfo(); ?> . Now what?

Did you just see the text "<?php phpinfo(); ?>"  when you visited it in firefox?  If so, PHP isn't working correctly, or may be not installed.

To install PHP5,

```
sudo apt-get install php5
```

---

### Post by afroman10496 on 2009-07-30
> **zzzBrett said:**
> Did you just see the text "<?php phpinfo(); ?>"  when you visited it in firefox?  If so, PHP isn't working correctly, or may be not installed.

To install PHP5,

```
sudo apt-get install php5
```
Ok, I don't really know so mush about servers :). I get a download prompt for test.php and it shows me the:
```
 <?php phpinfo(); ?> 
```
stuff. Not in Firefox, just a download.

---

### Post by zzzBrett on 2009-07-30
> **Afroman10496 said:**
> Ok, I don't really know so mush about servers :). I get a download prompt for test.php and it shows me the:
```
 <?php phpinfo(); ?> 
```
stuff. Not in Firefox, just a download.

Alright.  Try installing PHP5 and see if that changes.

---

### Post by afroman10496 on 2009-07-30
> **zzzBrett said:**
> Alright.  Try installing PHP5 and see if that changes.
I did, but it doesn't do anything different.

---

