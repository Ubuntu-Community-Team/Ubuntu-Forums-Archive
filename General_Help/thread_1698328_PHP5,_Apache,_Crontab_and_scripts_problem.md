---
title: "PHP5, Apache, Crontab and scripts problem"
date: 2011-03-02
forum: General Help
---

### Post by microtechno on 2011-03-02
Hey Guys

I am having the most random problem, well it isn't random as I am sure it has a completely logical reason just not know to me.

I am writing a web page that extracts information from log files that are updated by another program running as the user burnside. This part works and the files go where they are meant to.
Burnside user doesn't have any sudo permissions and the log files are placed into the admin dir -> /home/admin/cfs_scan/logs. This part works as the files are updated.

What doesnt work, sometimes is the the php script I have called extract.php, this scrip/webpage works when I run it through firefox from another computer. Outputting the correct information, as does running it from the cli using, as the user admin
```
 php5 /home/admin/cfs_scan/extract.php >> /home/admin/cfs_scan/logs/extract.log

```what doesnt work is running it in crontab as the user admin
```
admin@pagerServer:~/cfs_scan$ crontab -l
# m h  dom mon dow   command
*/5 * * * *     php5 /home/admin/cfs_scan/extract.php >> /home/admin/cfs_scan/logs/extract.log

```I thought it was the user permissions so in my log I made it output the user that php was running the script (extract.php) under, from which it shows both manually and crontab are the same users. The problem is that the extract script doesn't want to open the file.

The file error is a state I wrote into the script, telling me where it ends. This is returned from phps, file() command as false. I am assuming this is a user/group access issue.

```
11-03-02 19:30:02   admin File Error Occured
11-03-02 19:35:03   admin File Error Occured
11-03-02 19:40:01   admin File Error Occured
11-03-02 19:45:02   admin File Error Occured
11-03-02 19:46:37   admin Added - 1924063 Added - 1925582 Added - 1925592 Added
```This is the user/group of it all
```
admin@pagerServer:~/cfs_scan$ ls -l
total 48
..
-rwxrwxrwx 1 admin www-data 4554 2011-03-02 09:29 extract.php
drwxrwxrwx 2 admin www-data 4096 2011-03-02 19:45 logs
..

``````
admin@pagerServer:~/cfs_scan$ ls -l logs/
total 492
-rw-rw-rw- 1 www-data www-data   3769 2011-03-01 22:46 110225.log
-rw-rw-rw- 1 burnside www-data  34208 2011-03-01 23:56 110301.log
-rw-rw-rw- 1 burnside www-data 188368 2011-03-02 20:01 110302.log
-rw-rw-rw- 1 admin    www-data  55917 2011-03-02 20:00 extract.log
-rw-rw-rw- 1 www-data www-data 194431 2011-03-01 17:05 filters.ini
-rw-rw-rw- 1 admin    www-data    484 2011-03-02 12:04 permissions.log

```I hope that all of that makes sense. I dont know why the script runs manually but not using crontab. As I see it its the same user, as i ran 'crontab -e' from the user admin.

Cheers ubuntu folk,

---

