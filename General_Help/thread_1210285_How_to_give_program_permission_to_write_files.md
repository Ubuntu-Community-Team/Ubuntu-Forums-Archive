---
title: "How to give program permission to write files??"
date: 2009-07-11
forum: General Help
---

### Post by boon4376 on 2009-07-11
I've installed Apache2, PHP, MySQL and PHPMyAdmin to get a webserver up and running.

I've installed imagemagick and magickwand (allows me to edit images with PHP code).. The problem is when I go to save the edited image, I get an error:

*Fatal error: magickwriteimage(): C API cannot write the image at MagickWand index 0 to filename "logo.jpg" (reason: unable to open image `/var/www/logo.jpg': Permission denied @ blob.c/OpenBlob/2480) [on C source line 374] in /var/www/testrotate.php on line 11*

Basically if I set the security permissions on the www folder to allow anyone to make changes / read & write the program works fine... If I set security to normal I get the error above. Do I need to create a new user for the imagemagick program? How do I give it access to save images to the folder without letting "everyone" do it.

---

### Post by Celauran on 2009-07-11
You can either alter the permissions on /var/www or create virtual hosts in Apache with a DocumentRoot inside your home directory.

---

### Post by ibuclaw on 2009-07-11
I **think** what needs to be done is to create a directory inside /var/www with the user "www-data" as the owner or group with write access.
Then save the file in there, rather than directly in the root of /var/www.

ie:
```
sudo mkdir /var/www/data
sudo chgrp www-data /var/www/data
sudo chmod 2775 /var/www/data

```
Then update your code accordingly to save in that directory.


But as said above, virtual hosts may be the better way to go from a security view.

Regards
Iain

---

### Post by boon4376 on 2009-07-12
> **tinivole said:**
> I **think** what needs to be done is to create a directory inside /var/www with the user "www-data" as the owner or group with write access.

But as said above, virtual hosts may be the better way to go from a security view.

Regards
Iain
Thanks Iain, I'm a little bit of a newb when it comes to setting up a webserver in ubuntu, I havnt used virtual hosts before, but i've done some reading to understand them better.

Updating the security for www-data wasnt effective, nor when I created a folder inside of the www directory to assign permissions to, but still if permissions are set so Everyone has read / write capability, it works. Thus I dont think www-data is the correct user for the job?

Could you also go into further detail on how I would use virtual hosts to accomplish this task?

---

### Post by jskandhari on 2009-07-12
run the app as root "sudo" or open the saving directory as root and provide the permissions

---

### Post by Celauran on 2009-07-12
> **boon4376 said:**
> Could you also go into further detail on how I would use virtual hosts to accomplish this task?

Make a copy of /etc/apache2/sites-available/default, let's call it 'mysite'

```
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mysite
```

Now you'll nee to edit the new file to point to your home directory. I've included a sample.

```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
       ServerName mysite.example.com

	DocumentRoot /home/username/mysite
	<Directory /home/username/mysite/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>

	ErrorLog /var/log/apache2/mysite/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/mysite/access.log combined

</VirtualHost>
```

Once you've saved these changes, you'll need to enable the site.

```
sudo a2ensite /etc/apache2/sites-available/mysite
```

Almost there. We've specified a separate directory for storing log files, so we'll need to create that.

```
sudo mkdir /var/log/apache2/mysite
```

Finally, we need to add the site to your hosts file. Edit /etc/hosts and add the following:

```
127.0.0.1    mysite.example.com
```

Now we restart Apache

```
sudo /etc/init.d/apache2 restart
```

You can now store all your work in /home/username/mysite and navigate to it by pointing your browser to [http://mysite.example.com](http://mysite.example.com)

---

### Post by boon4376 on 2009-07-12
> **jskandhari said:**
> run the app as root "sudo" or open the saving directory as root and provide the permissions

Well its not really an app, its a PHP library for image processing, and I start nautilus with "sudo" before going in to apple permissions.

Thanks celaruan, I'll start working on that and see how it goes \\:D/

---

### Post by boon4376 on 2009-07-12
> **Celauran said:**
> 
Once you've saved these changes, you'll need to enable the site.

```
sudo a2ensite /etc/apache2/sites-available/mysite
```
Im getting an error when I try to do this
```

Error: No site found matching /etc/apache2/sites-available/records!

```

I've tried creating the "records" file a few times from copying the default one... Is there an extension I'm supposed to be using? When I navigate to the folder I can see that the file exists.

---

### Post by Celauran on 2009-07-12
Navigate to /etc/apache2/sites-available and execute it there.

```
cd /etc/apache2/sites-available
sudo a2ensite records
```

Not sure why you can't call it with a path, but apparently you can't. Sorry.

---

### Post by boon4376 on 2009-07-12
> **Celauran said:**
> Navigate to /etc/apache2/sites-available and execute it there.

```
cd /etc/apache2/sites-available
sudo a2ensite records
```

Not sure why you can't call it with a path, but apparently you can't. Sorry.

ok that fixed that problem... I now have the virtual host working and can get to the images / files through the web browser, however I still cannot use imagemagick to write images to that directory and still get the error. (thanks for teaching me how to setup virtual hosts \\:D/

[code]Fatal error: magickwriteimage(): C API cannot write the image at MagickWand index 0 to filename "logo.jpg" (reason: unable to open image `/var/records/logo.jpg': Permission denied @ blob.c/OpenBlob/2480) [on C source line 374] in /var/records/testrotate.php on line 11[code]



_**UPDATE:**_ ok so changing the permissions on the folder is not working, If I make the owner of "records" www-data and hit "apply permissions to enclosed files" It doesnt actually apply the permissions to the images in there. For example, after hitting to apply to enclosed files, I opened an image inside the folder, and the image's owner has not changed....  If I manually changed that image's owner to www-data, the code executed flawlessly and the image was altered and saved over itself like its supposed to do....

So I have 80,000 images (These are archived records in the format of tiff images being stored on a local intranet server), I cant very well go through and apply permissions separately to each one for www-data, So how do I apply permissions to all of them at the same time?

---

### Post by boon4376 on 2009-07-12
> **boon4376 said:**
> 
So I have 80,000 images (These are archived records in the format of tiff images being stored on a local intranet server), I cant very well go through and apply permissions separately to each one for www-data, So how do I apply permissions to all of them at the same time?

ok I think I have it figured out, I went to this thread 
[http://ubuntuforums.org/showthread.php?t=1122716](http://ubuntuforums.org/showthread.php?t=1122716)

And think this is the code I need to execute
```

sudo chown &#8211;R www-data:www-data /directory
sudo chmod 770 &#8211;R /directory

```
replacing "directory" with the path of the top most i need the permissions for.... And that should give www-data full ownership and editing capabilities correct?  Great, Now I just need to add my user to the www-data "group" so that I can manage the files inside nautilus.

BTW im really impressed by how fast everyone is helping me, its great, Thanks!

---

### Post by Celauran on 2009-07-12
> **boon4376 said:**
> 
And think this is the code I need to execute
```

sudo chown –R www-data:www-data /directory
sudo chmod 770 –R /directory

```
replacing "directory" with the path of the top most i need the permissions for.... And that should give www-data full ownership and editing capabilities correct?  Great, Now I just need to add my user to the www-data "group" so that I can manage the files inside nautilus.

You can just change the group and leave yourself as the owner.

```
sudo chown -R you:www-data directory
chmod -R 770 directory
```

---

### Post by boon4376 on 2009-07-12
> **Celauran said:**
> You can just change the group and leave yourself as the owner.

```
sudo chown -R you:www-data directory
chmod -R 770 directory
```

ahh great, all of my problems have been solved, thanks

---

