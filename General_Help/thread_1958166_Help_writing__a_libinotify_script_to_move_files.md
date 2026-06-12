---
title: "Help writing  a libinotify script to move files"
date: 2012-04-13
forum: General Help
---

### Post by RabidFangs on 2012-04-13
Hi ):Peveryone, 
Ive been trying to tackle this problem for a few days now, 
I finally decided to put down my google goggles and ask the experts.
what I am trying to accomplish is:

Setup a libinotify event to monitor my downloads directory and 
move any nzb files it finds, to a shared directory on my 
NAS device that runs debian squeeze and sabnzdb.

Ive looked around and I can find examples but nothing gets moved.

Any help with this will be greatly appreciated.
Thanks all.

---

### Post by matt_symes on 2012-04-13
Hi

Could you post what you have written between code tags.

Your using inotify-tools ?

Kind regards

---

### Post by RabidFangs on 2012-04-14
Hi and thank you for your reply
I have adapted this from the following page:
[http://andries.filmer.nl/kb/Monitoring%20file%20system%20events%20with%20inotify,%20incron%20and%20authctl/129]("http://andries.filmer.nl/kb/Monitoring%20file%20system%20events%20with%20inotify,%20incron%20and%20authctl/129")
here is what i have so far:

I ssh into the server and I create the file
```

sudo nano /home/tavj/inotify.sh

```I comment out what(I think) I dont need:


```

#!/bin/sh
 
# Create a inotify backup dir (if not exists)
#
#mkdir /var/backups/inotify
 
# Make a copy off the full path and file
#
#cp -p --parents $1  /var/backups/inotify
 
# move the file to a file with datetime-stamp
#
mv /home/tavj/Downloads/*nzb \\DLINK-49CCF9\Volume_1\Downloads\

```Then I make the file executable:
```

 chmod 755 /home/tavj/inotify.sh


```Then I open 
> 
incrontab -e
```

/etc IN_CLOSE_WRITE,IN_MODIFY /home/tavj/inotify.sh 
/home/tavj/Downloads/*nzb IN_CLOSE_WRITE /home/tavj/inotify.sh

```I write the file, 
I downloaded another .nzb file, its downloaded to my local downloads directory
but nothing happens.

Thanks again

---

### Post by Habitual on 2012-04-14
[http://www.ibm.com/developerworks/linux/library/l-inotify/index.html](http://www.ibm.com/developerworks/linux/library/l-inotify/index.html)
[http://www.cyberciti.biz/faq/linux-inotify-examples-to-replicate-directories/](http://www.cyberciti.biz/faq/linux-inotify-examples-to-replicate-directories/)

---

### Post by matt_symes on 2012-04-14
Hi

You're using incrontab then.

The example from the tutorial....

```
/etc IN_CLOSE_WRITE,IN_MODIFY /root/inotify.sh $@/$# 
/home/andries/myProject IN_CLOSE_WRITE /root/inotify.sh $@/$#
```Yours is...
[FONT=monospace]
[/FONT]```
/etc IN_CLOSE_WRITE,IN_MODIFY /home/tavj/inotify.sh
/home/tavj/Downloads/*nzb IN_CLOSE_WRITE /home/tavj/inotify.sh
```Yours should be.....
[FONT=monospace]
[/FONT]```
/etc IN_CLOSE_WRITE,IN_MODIFY /home/tavj/inotify.sh  **$@/$#**
/home/tavj/Downloads/*nzb IN_CLOSE_WRITE /home/tavj/inotify.sh **$@/$#**
```**HOWEVER,** Are you sure you want to be monitoring /etc ?

I would be looking at this, if i understand what you want correctly, in your incrontab.

```
/home/tavj/Downloads/*nzb IN_CLOSE_WRITE,IN_MODIFY /home/tavj/inotify.sh **$@/$#**
```And for your inotify.sh script

```
#!/bin/sh[FONT=monospace]
[/FONT]mv $1 \\DLINK-49CCF9\Volume_1\Downloads\
```I'm pretty sure the above inotify.sh script will work as i think **$@/$# **passed into the script is the full path to the file and is then, obviously, $1 in the script. However ii have not tested this so you may want to double check.

Also have you made sure the inotify.sh script is executable after you have created it ?

```
sudo chmod 755 /path/to/inotify.sh
```And remember to use full paths when using cron. Set up any environmental variables cron may require for the script.

If you want to use inotify-tools then look at the two excellent links from habitual.

**EDIT:**
[FONT=monospace]
[/FONT]\\DLINK-49CCF9\Volume_1\Downloads\

Is the above path valid ?

Kind regards

---

### Post by RabidFangs on 2012-04-18
Thank you matt_symes
It took a couple of days and alot of beer but,
You guided me in the right direction with this,
With a little editing you put me back on track.
One of the problems I encountered was the path for the nas, 
You were right the \\DLINK..\..\.. was wrong but it was the path I got from samba. 
That didn't work.

So grabbed a beer, and another, and another(YUM), 
put my google goggles back on and found that I can 
mount a folder on the NAS under the /mnt directory, let see if that works...YAAY!! it does!!
I can now download an .nzb file, incron will see it and will send it to the mounted directory on my NAS.

Its monitored by Sanbzbd and gets qued for download, turn off the main pc and let the NAS do its thing.
SET IT AND FORGET IT!!!....gawd I love linux.


All credit goes to matt_symes.
My setup is 
Ubuntu 11.04 x64
Firefox
NAS DNS-325, 2x 3Tb drives (NAS) Network Attached Storage 
For those interested in accomplishing a similar setup Here is the final product, 



Replace 
[username] with your username
[password] your pass
Open Terminal:


Install inotify

apt-get install incron
apt-get install inotify-tools

Type
```
Sudo nano /home/[username]/inotify.sh
```Type
```

#!/bin/sh
mv /home/[Username]/Downloads/*nzb /mnt/Nas_Disk1/NZBs

```Save the file

Make the file executable 
```
chmod 755 /home/[username]/inotify.sh
```open

```
incrontab -e
```Type
```
/home/[username]/Downloads IN_CLOSE_WRITE,IN_NO_LOOP /home/[username]/inotify.sh $@/$#
```Save the file.


Then I Created a directory under /mnt

```
sudo mkdir /mnt/Nas_Disk1
```Then I mounted the sabnzbd's "watched" directory Using the IP address of the NAS.

```
sudo mount -t cifs //192.168.1.2/Volume_1/Downloads -o username=[username],password=[password] /mnt/Nas_Disk1/
```Open firefox and download a nzb file, as long as its downloaded into the default Downloads directory it will get moved to whatever directory you set on the nas device.

1 step closer to a totally automated media center.:popcorn::guitar:saweeeet.

---

