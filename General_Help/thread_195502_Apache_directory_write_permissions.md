---
title: "Apache directory write permissions?"
date: 2006-06-12
forum: General Help
---

### Post by dccool879 on 2006-06-12
I am very confused! Here's the deal. I have the ubuntu lamp server (linux apache mysql and php.) On it, I have php nuke and phpbb. There are some problems that i beleive have to do with write permissions. when a review is submitted, it says it is in the database but never shows up. But the real killer is when I upload an avatar, and it says sucessful, but then it is not there! it has the jpg location, and when i go to view image in firefox, i get a 404. So!! I did a chmod 777 for /var/www. Still, no luck. Help??

---

### Post by dccool879 on 2006-06-12
OK i think i solved it?? i chmod 777 /var/www/images/avatars. so does this mean if i chmod /var/www that it does not make these permissions for every folder/directory in /var/www ???

---

### Post by austen on 2006-07-30
> **dccool879 said:**
> OK i think i solved it?? i chmod 777 /var/www/images/avatars. so does this mean if i chmod /var/www that it does not make these permissions for every folder/directory in /var/www ???

You won't change the permissions for sub-folders or sub-files of /var/www with chmod 777. You need to use chmod -R to recursively change the permissions.

Be careful though that you aren't too liberal with your permissions. 777 permissions on /var/www and everything recursively will leave your system vulnerable to some exploits. You're basically giving everyone and their grandmother permission to read, clobber, and execute everything in /var/www and beyond.

Only set the specific directories with permissions you need writable by apache 775. Leave everything else 755.

Also, make sure you change the owner of a directory to include your user and apache's group with:
$ chown yourUser.www-data ./someDirectoryGoing2BeWritableByApache
$ chmod 775 ./someDirectoryGoing2BeWirtableByApache

Otherwise your only option is to use world permissions to grant anything to apache.

Then you and apache can read, write and execute ("cd" into) that directory, and everyone else can only read, and "cd" into the directory, but not write over/ delete or create new files in there.

Remember that permissions work like this:
(7)(7)(7) is
(421)(421)(421) sum the numbers, is
(rwx)(rwx)(rwx) in
(Owner)(Group)(World)

(7)(5)(5) is
(421)(4-1)(4-1) summed, is
(rwx)(r-x)(r-x)

That's a good start, but I'm sure others will also have some recommendations for permissions to use with your webserver. :)

---

