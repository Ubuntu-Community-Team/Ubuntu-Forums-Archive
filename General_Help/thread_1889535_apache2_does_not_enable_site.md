---
title: "apache2 does not enable site"
date: 2011-12-01
forum: General Help
---

### Post by spindler on 2011-12-01
I have created a number of websites on my development webserver.    I am creating a new virtual host but when I run apache2 reload it does not enable to virtual host.

This is what I am doing.

1.  open an virtual host file and edit the ServerName and Server Alias. 

ServerName  newdev.mysite.com
ServerAlias  newdev.mysite.com

DocumentRoot /home/mysites/newdev

.....

2. I then run the following commands

sudo a2ensite newdev
sudo service apache2 reload
sudo service apache2 restart

I should be able to just go to the website and find my site.   newdev.mysite.com
but this is not happening.
 
3. I did some testing.

3a. using ping I was able to find the server so I know that the domain is set up correctly.

3b.  Using firefox from my server i was able to get the site using   localhost/newdev


4. _I removed the newdev virtual host file and started over._  Once I finished saving the file I got the following error.

**(Gedit:1911): Gtk-WARNING **: Unable to retrieve the file for 'file:///etc/apache2/sites-available/newdev' : Error stating file '/etc/apache2/sites-available/newdev':  No such file or directory**

However the newly created file does exist. 

Any ideas?

Thanks,

spindler

---

### Post by spindler on 2011-12-01
Something weird is going on......

When I navigate to the IP address, I can see the new site not my default index page.   Why is that?

---

