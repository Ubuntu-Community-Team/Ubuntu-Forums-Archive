---
title: "Help with Nagios install"
date: 2009-12-11
forum: General Help
---

### Post by KLStringer on 2009-12-11
I'm trying to install Nagios on a 9.04 sever with the 9.04 desktop, I've less than no experience with any form of Linux so its a crash course in figuring it out for myself. :-?

I've been following the quickstart [here]("http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html"), during step 3 I run the:

"./configure --with-command-group=nagcmd


Compile the Nagios source code.

make all"

And as far as my not having a clue what I'm looking at eye see's it looks like it did what ever it was suppose to do successfully. The next step was to run the make install-init command but when I do that I get the error below and I have no clue why or what I do to correct it. 

"
make install-init
/usr/bin/install -c -m 755 -d -o root -g root /etc/init.d
/usr/bin/install -c -m 755 -o root -g root daemon-init /etc/init.d/nagios
/usr/bin/install: cannot create regular file `/etc/init.d/nagios': Permission denied
make: *** [install-daemoninit] Error 1
"

On a completely unrelated note how do I turn off auto hide of the task bar? 

Thanks for any insight into my problem(s) in advance.

---

### Post by KLStringer on 2009-12-14
Still can't get passed this error message, any help is appreciated.

---

### Post by aktiwers on 2009-12-14
Make install requires root:
```
sudo make install-init
```You might want to use checkinstall instead:
```
sudo checkinstall
```which creates a .deb and then installs that. This way the software will be a lot easier to remove
if you want to do that someday.

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by KLStringer on 2009-12-14
Do I use "sudo checkinstall" instead of "sudo make install-init" or do I use both of them one after the other? I didn't have much time to read the reference you linked or really work on it at all today, the more information I have when I do get the chance the better.

---

### Post by KLStringer on 2009-12-15
Still wondering what I need to do here "sudo check install" or "sudo make install-init"
 
 Thanks

---

### Post by aktiwers on 2009-12-16
checkinstall should be enough.

Just make sure you have it installed first.
```

sudo apt-get install checkinstall
```

[https://help.ubuntu.com/community/CompilingSoftware#Installing%20the%20Package](https://help.ubuntu.com/community/CompilingSoftware#Installing%20the%20Package)

---

### Post by KLStringer on 2009-12-17
I ended up getting another tech here to help me with it, he knows a little bit more about linux and used the synaptic manager. We think it's installed everything but when we try to go to the [http://localhost/nagios/](http://localhost/nagios/) page we get a 404 error.  

Is there no easy way to install programs on Ubuntu without having to jump through so many hoops? I'd like to think I'm smarter than the average bear, but the figure it out for myself learning cure seams a little steep, or is that just all the M$ brainwashing. :???:

---

### Post by KLStringer on 2009-12-18
We figured out that the URL in the quickstart wasn't the right one, but now when we try to login to [http://localhost/nagios3/](http://localhost/nagios3/) we get a 500 Internal Server Error and can't get the login prompt to pop again so we can retry to login.

---

