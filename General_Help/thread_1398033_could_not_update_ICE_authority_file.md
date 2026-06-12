---
title: "could not update ICE authority file"
date: 2010-02-04
forum: General Help
---

### Post by rflores2323 on 2010-02-04
I was trying to install freenx on my ubuntu machine and messed up somewhere. Now I cant login to the system.  I get these errors

Could not update ICEauthority file /home/xbmc/.ICEauthority

I tried to login with CTRL-ALT-F2 and putting this command in 
sudo chown test:test /home/test/.ICEauthority 

and i get invalid user: 'test:test'

I also tried this 

$chown user -R /home/user

"user" being xbmc which is my user name

and I get a permission denied on a bunch of command lists

I also am getting the below error also.   

There is a problem with the configuration server (/usr/lib/libgconf2-4gconf-sanity-check-2 exited with status 256)

the I get a message saying. nautilus could not create the following required desktop folders: /home/xbmc/Desktop, /home/xbmc/.nautilus.
Before running nautilus, please create these folders, or set permissions such that nautilus can create them.  

****banging head against desk****

---

### Post by rflores2323 on 2010-02-04
Any help?

---

### Post by Dimarchi on 2010-02-04
A Google search points to the following page, among others:

[http://ubuntuforums.org/showthread.php?t=949750&page=2](http://ubuntuforums.org/showthread.php?t=949750&page=2)

It may be helpful. The search string used was:

```
could not update ICEauthority file
```

---

### Post by rflores2323 on 2010-02-04
well after the whole afternoon trying to fix this I was unsucessful..  I am going to reinstall.  ](*,)


:cry:

---

### Post by firey205 on 2010-02-04
Try this:

[http://ubuntuforums.org/showthread.php?t=1061084](http://ubuntuforums.org/showthread.php?t=1061084)

---

### Post by IanVaughan on 2010-03-23
[None of this worked for me]("http://ubuntuforums.org/showthread.php?p=9016355")!?

---

### Post by rflores2323 on 2010-03-26
I had to reinstall with a fresh install because I could not figure it out.  sorry couldnt be of help however I also tried to find an answer with no success.

---

### Post by Flos Headford on 2010-04-08
This worked for me:
Use a Ubuntu Live CD to boot up, and choose a command-line (shell) option.
With this, set your $HOME directory (/home/username) permissions to something appropriate (I used 755) and make sure all directories can be listed with the "ls" command. Then remove nautilus with ```
sudo apt-get remove nautilus
``` and delete the .ICEauthority entry in $HOME, and possibly in /var/lib/gdm. Then reboot with ```
sudo shutdown -r now
``` When you choose the same option on boot-up, from the command line you can use ```
sudo apt-get install nautilus
sudo shutdown -r now
``` and retrieve the CD a bit smartish. I do hope you get a clean straight boot and login, as I did!
With thanks to all who helped me,
Phil

---

