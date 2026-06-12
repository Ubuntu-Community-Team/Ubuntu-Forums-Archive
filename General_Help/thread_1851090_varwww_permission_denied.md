---
title: "var/www permission denied"
date: 2011-09-27
forum: General Help
---

### Post by Matt Ridge on 2011-09-27
I am looking to change the var/www folder to ownership to me.

I am logged in as an Administrator right now, I even gave myself temporary root permissions and it is telling me that I don't had ownership of var/www.  I can't test anything out, upload or delete anything. 

Can someone help me out? 

I have the latest version of Ubuntu...

---

### Post by mac666 on 2011-09-27
> **Matt Ridge said:**
> I am looking to change the var/www folder to ownership to me.

I am logged in as an Administrator right now, I even gave myself temporary root permissions and it is telling me that I don't had ownership of var/www.  I can't test anything out, upload or delete anything. 

Can someone help me out? 

I have the latest version of Ubuntu...

you could try this, dont know if its legit or not:
chmod 776 -R /var/www

or 
chmod -R 776 /var/www

or try these with "-r" instead of "-R"

This would change the permissions, but not the owner. the owner should be www-data IIRC

---

### Post by geo909 on 2011-09-27
> **Matt Ridge said:**
> I am looking to change the var/www folder to ownership to me.

I am logged in as an Administrator right now, I even gave myself temporary root permissions and it is telling me that I don't had ownership of var/www.  I can't test anything out, upload or delete anything. 

Can someone help me out? 

I have the latest version of Ubuntu...

You can change the ownership of a folder by doing:
```
sudo chown yourusername:yourusername foldername
```

This will change the folder's owner to you and your group.

Hope that works

---

### Post by Dangertux on 2011-09-27
If you can't mess with the permissions even as root, you might want to look into[ chattr]("http://linux.die.net/man/1/chattr") and [lsattr]("http://linux.die.net/man/1/lsattr"). 

Check for the i flag. Also you should not chown /var/www to root. Nor would I give any file in their permissions higher than 750, if you can't mess with the files even as root somehow it was made immutable with chattr. I'm guessing this is not exactly your server and probably a VPS host?

---

### Post by cgroza on 2011-09-27
If you look into hosting or developing a website, you can have Apache use another folder instead. I know I did this a few weeks ago and I was storing and editing my files in my home folder.

---

### Post by Matt Ridge on 2011-09-27
> **Dangertux said:**
> If you can't mess with the permissions even as root, you might want to look into[ chattr]("http://linux.die.net/man/1/chattr") and [lsattr]("http://linux.die.net/man/1/lsattr"). 

Check for the i flag. Also you should not chown /var/www to root. Nor would I give any file in their permissions higher than 750, if you can't mess with the files even as root somehow it was made immutable with chattr. I'm guessing this is not exactly your server and probably a VPS host?


Actually this is my server, I am new to the linux world again, the last time I used linux Ubuntu was at version 5...

That being said I am a Mac user, I figured the ability to change it wouldn't be much different, but it is.

---

### Post by Dangertux on 2011-09-27
No you're right it should work, but if it's saying permission denied even as root, it led me to believe it's immutable.

I guessed at the VPS, because I know if a web app is using too much resources a lot of VPS hosting companies will chattr it.  Was just a shot in the dark. 

Now back to the topic at hand, if the file is not in fact immutable, what command are you trying to run that is giving you permission denied

does the following command work

```

sudo cat /var/www/index.html

```

if there is no index.html be sure to choose a file that is in that directory (there should be one by default if this is a fresh install). 

That should give you the contents of the file.

---

### Post by Matt Ridge on 2011-09-28
> **Dangertux said:**
> No you're right it should work, but if it's saying permission denied even as root, it led me to believe it's immutable.

I guessed at the VPS, because I know if a web app is using too much resources a lot of VPS hosting companies will chattr it.  Was just a shot in the dark. 

Now back to the topic at hand, if the file is not in fact immutable, what command are you trying to run that is giving you permission denied

does the following command work

```

sudo cat /var/www/index.html

```if there is no index.html be sure to choose a file that is in that directory (there should be one by default if this is a fresh install). 

That should give you the contents of the file.

laptop:~$ sudo cat /var/www/index.html
<html><body><h1>It works!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been added, yet.</p>
</body></html>


I don't know, it seems to work, so I'm not sure what is going on.

---

