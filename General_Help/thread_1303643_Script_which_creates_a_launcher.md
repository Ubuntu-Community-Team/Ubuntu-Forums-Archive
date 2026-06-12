---
title: "Script which creates a launcher"
date: 2009-10-28
forum: General Help
---

### Post by MrPingu33 on 2009-10-28
Hi guys,
I'm trying to write a script which runs on startup that removes everything on the desktop except for 1 launcher (Used to start up rdesktop).
What is the best way to do this?
Currently the script removes everything from the desktop, is there a way to do rm with an exception? Or can you create a launcher in command line?
I've tried searching google but found nothing :(
 
Any help would be hugely appreciated!
Thanks.
Steven

---

### Post by Eremis on 2009-10-28
You could just make another script that runs that program after the first one removes everything. Or at the end (after it removes everything) just make it run that particular program.

---

### Post by HLA91 on 2009-10-28
Make a note of the extensions of your files that you do not want on your desktop, eg .odt files
then 
```
rm *.odt
```
and you can add other file extensions onto that

```
rm *.odt *.xxx *.xxx
```

As long as you don't have any other launchers on the desktop then this will work for you but it isn't pretty. Also to create a launcher from command line I think its

```
ln -s /destination/destination /link/location
```

Destination is the file you want to link to and location would be /home/user/Desktop/my-link 

Hope that helps but check first as I might be wrong on some things


HLA91

---

### Post by John Bean on 2009-10-28
I assume you meant
```
ln -s /destination/destination /link/location
```A link isn't a launcher though. Open a launcher (usually called "someapplication.desktop") in an editor and all will be revealed. Writing a launcher file from a script is easy, but easier yet is have one made already and just copy it to the (now cleared) desktop.

---

### Post by sisco311 on 2009-10-28
Assuming that it's bash script you can use !(filename) to match anything except filename.

i.e.
```
shopt -s extglob
echo ~/Desktop/!(filename)
```

```
man bash | less --pattern\="extglob"
```

---

### Post by MrPingu33 on 2009-10-28
Thanks for all your replies, all good suggestions although yes I was looking for a launcher rather than a link. Sisco311's way of removing everything but a certain file is exactly what I was looking for, and works an absolute treat.
Thanks a lot!
:D
__

---

### Post by HermanAB on 2009-10-28
The correct way is to configure the /etc/skel directory with the stuff you want users to have.  When a user account is created, the default schtuff comes from there.

---

### Post by MrPingu33 on 2009-10-28
Thank you HermanAB, I didn't know that and it sounds like it will probably be quite useful, I'll have a look into it tomorrow.

---

