---
title: "gedit httpd.conf in ubuntu"
date: 2011-07-17
forum: General Help
---

### Post by itba on 2011-07-17
hi,
I tried to open httpd.conf using gedit, so I typed the following command
```

sudo gedit /etc/apache2/httpd.conf

```and I got the following errors before an editor opened up with an empty httpd.conf file.
this is the error message:
```

(gedit:15088): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.YM5YYV': No such file or directory

(gedit:15088): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```should i just ignore the error messages? but then why is httpd.conf empty?

---

### Post by bhinderm on 2011-07-17
You can ignore this message, it is harmless. Just trying to store the list of recently opened files files and it fails.

Alternative is to:

1) Use gksudo instead of sudo (apt-get install gksu)
2) Use a command line tool such as vim instead of gedit

---

### Post by itba on 2011-07-17
thanks for your response bhinderm,
I tried gksudo gedit /etc/apache2/httpd.conf
 
and it opens up the file without the error messages, but the httpd.conf is still empty? Is it supposed to be empty?
If not, what should it contain - I can type the contents and see if that works.

---

### Post by mikewhatever on 2011-07-17
> **itba said:**
> thanks for your response bhinderm,
I tried gksudo gedit /etc/apache2/httpd.conf
 
and it opens up the file without the error messages, but the httpd.conf is still empty? Is it supposed to be empty?
If not, what should it contain - I can type the contents and see if that works.

If you just want to see the content of a file, there is no need to open it for editing, use gedit, less or cat, for example:

gedit /etc/apache2/httpd.conf

less /etc/apache2/httpd.conf

On the other hand, if you want or need to edit the file, use 'gksudo gedit', but it's also advisable to know what to put there, and if you don't, chances are, you don't need to edit it.

---

### Post by bhinderm on 2011-07-17
They changed the configuration file from httpd.conf to apache2.conf. Try editing /etc/apache2/apache2.conf 

httpd.conf is empty by default now.

---

### Post by itba on 2011-07-17
thanks bhinderm that's good to know. I do see contents in the apache2.conf. I am learning how to setup a webserver, so one of the sites had suggested editing the httpd.conf file and I was following instructions. However, it was only basics, and its obviously not updated. If you have any suggestions for a good site for beginners (other than the apache documentation), that'll be helpful :-)

---

### Post by bhinderm on 2011-07-17
No problem! 

Config files keep changing between software revisions and it can be confusing. The apache documentation is the best place to go to for updated information. Other than that Linux home networking  might be of use:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch20_:_The_Apache_Web_Server](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch20_:_The_Apache_Web_Server)
[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html) (outdated)

---

### Post by linuchsan on 2011-07-17
Put your sites in: /etc/apache2/sites-available and run a2ensite after.

---

### Post by itba on 2011-07-17
cool,
thx for the links bhinderm, that's good to know regd. the config files
and thx for the suggestion linuchsan...
:-)

---

