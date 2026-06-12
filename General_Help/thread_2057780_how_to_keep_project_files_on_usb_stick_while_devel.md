---
title: "how to keep project files on usb stick while developing with lamp"
date: 2012-09-14
forum: General Help
---

### Post by RanZo on 2012-09-14
Hi, I am running  a lamp stack installed (with a script) on a live  CD.

I would like to store all my project files on my usb flash drive. 

This is for security reasons,  so when I surf the net I can disconnect my usb, so nothing can get to my project files.  And when I turn of the computer, any malware must be deleted, as OS is running from CD.  Sort of belt-and-braces insurance against viruses.

The issue is that since usb flash drive is formated with fat-32 file system, it cannot be chmod-ed to 777.  So  when I try to use browser to show the website I work on it shows: You don't have permission to access / on this server.


This I guess is because I am a root user, and the usb process is  run by ubuntu user.
Something like that, I don't actually understand why it does not display the site like it would if I kept my project files on /var/www.
The virtual host and everything else  has been created as before when I was using the /var/www (but using the path to the usb www folder ofcourse).


Is there any way of solving this problem?

---

### Post by Lars Noodén on 2012-09-14
You'll have to leave FAT behind and use EXT, XFS or something in order to keep the POSIX file permissions.

---

### Post by RanZo on 2012-09-14
I have not seen an option to format a usb stick with anything other than fat-32.
And I need to be able to run Ubuntu from a live CD.

Is it not possible to solve this?

---

### Post by Primefalcon on 2012-09-14
1. install gparted
2. insert and unmount the usb stick via gparted
3. format the usb to ext4 (ext3, btrfs and others will do.. but I'd say go with ext4)
4. copy everything from /var/www to the usb stick
5. create a symlink called /var/www that points to the usb stick

---

### Post by Primefalcon on 2012-09-14
btw be very careful in the dropdown menu on the top right that you are doing the right device..... you don't want to format any of your hard drives!

also make sure you dont have anything on the usb stick yo want before you format!

---

### Post by RanZo on 2012-09-14
thanks Primefalcon

That will be the thing to do then. Is is possible to create a partition with gparted for ext4 and keep fat-32 on usb as well? I have a xampp and some other windows apps I would like to keep on the same stick.

---

### Post by Primefalcon on 2012-09-14
> **RanZo said:**
> thanks Primefalcon

That will be the thing to do then. Is is possible to create a partition with gparted for ext4 and keep fat-32 on usb as well? I have a xampp and some other windows apps I would like to keep on the same stick.
sure..... resize the fat-32 partition and create a smaller ext4 partition.... effectively turning your usb into 2 smaller devices... be aware of how much space you have on your usb though... and how much you will need each partition to be

---

### Post by RanZo on 2012-09-14
I have created a smaller partition with ext4 successfully.
But now I have  a problem accessing it. I am not been given permissions to open folders inside it, although I can create them using sudo in terminal. 
Also text editor will not open it.

I did :   sudo chown root -R   /media/new-partition
and still will not give me rights to the folder.

---

### Post by Lars Noodén on 2012-09-14
You need to assign it to the user you are logged in as, not root.

```

 sudo chown  ranzo  -R /media/new-partition

```

---

### Post by RanZo on 2012-09-14
Done that, now I have access to all files and folders, but the browser still displays :
You don't have permission to access / on this server.
I have corrected the paths to the new directory in sites-available/ sites-enabled and restarted the apache.

In var/log/apache2/error.log I can see this:
Permission denied: /media/new-partition/www/mysite/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable

This suggests permissions still not being set somewhere, I guess?

---

### Post by Lars Noodén on 2012-09-14
Then it's a matter of setting the right permissions in your web server's configuration file.  Can you post an excerpt from that configuration file that concerns your usb stick?

Also, what mount point is the usb stick mounted under?

---

### Post by Primefalcon on 2012-09-15
you might want to run an ```
ls -la /usb/device
```

---

### Post by SeijiSensei on 2012-09-15
> **RanZo said:**
> In var/log/apache2/error.log I can see this:
Permission denied: /media/new-partition/www/mysite/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable

This suggests permissions still not being set somewhere, I guess?

Add the www-data to the group associated with whichever username owns these directories, presumably ranzo.  The quickest way is to edit (as root with sudo) the file /etc/group and add "www-data" after the final colon (":") in the line that begins with ranzo.  Save the file, then run

```

sudo chmod g+rx /media/new-partition/www
sudo chmod g+rx /media/new-partition/www/mysite
cd /media/new-partition/www/mysite/
sudo chmod g+r * \.*

```

to insure all the directories are group-listable, and the files in the mysite directory are group readable.  The last command grants group readable rights to both normal files and hidden files like .htaccess.

---

