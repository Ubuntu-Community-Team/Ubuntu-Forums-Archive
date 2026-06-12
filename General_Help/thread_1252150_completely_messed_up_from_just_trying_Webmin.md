---
title: "completely messed up from just trying Webmin"
date: 2009-08-28
forum: General Help
---

### Post by infocom on 2009-08-28
My Ubuntu has been running fine. I decided to try Webmin today, and Virtualmin. Took ages setup, mainly Virualmin sayiong things werent setup (one at a time) so had to set them up. Then only to only be faced with a "Forbidden You Dont Have Permission To Access /" message. Could not fix it. So uninstalled. Still Forbidden. So uninstalled Apache, reinstalled, changed Doc root to my home/user folder and now works OK. But then mySQL wont start. Restarted computer now hangs on startup for ages at "starting kernel log daemon" then FAILS and MySQL FAILS then I get a command prompt login which does not work with root. 

So its completely messed up. If anyone has seen this before please let me know. 

Thanks

---

### Post by infocom on 2009-08-29
OK turns out in the process of trying to get my websites to work, I changed some persmissions on /var/ and /home/myuser/. This is because some other threads said not only to change web direcotry permissions, but the parent folder also. So I tried changing a few permissions of /var/ so web server can read it. Nothing worked, still have forbidden. 

But my whole system just messed up, it would not boot and kept hanging on startup processes. After ages searching one thread implied some startup process hang if it cant read the filesystem, and it mentioned /var/. That got me thinking because I changed permissions. So I changed /var/ to 755 then it boot up. But then my User had issues it would not load the GUI with permissions erros on $HOME files. So changed permissions on my user directory too.

Now I can log in. As per another thread ([http://ubuntuforums.org/showthread.php?t=1252250](http://ubuntuforums.org/showthread.php?t=1252250)), I could not even copy files from LiveCD to a USB or Email in the event of never fixing this, it would not even let me read these files to recover my Documents from LiveCD or Windows using Ext reader software. This makes me worried in the event of a crash and I cant get the system to start again, how are you supposed to get your files using another computer to connect to this drive and read them? 

Anyway, its working again, and I backed up my files, so I am going to re-install this as I dont know what I messed up trying to get a website to show using vhosts. 

It would be good if startup process hangs gives the error "cannot read from /var/xxxx permission denied" instead of just not loading. 

This will teach me not to mess with folder permissions outside my home folder, but then I cant get /var/www/ to work, it says Permissiosn Denied. So I will have to just use Document root in my HOME folder.

---

