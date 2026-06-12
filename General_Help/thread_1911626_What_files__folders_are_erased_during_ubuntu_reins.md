---
title: "What files / folders are erased during ubuntu reinstallation/repair?"
date: 2012-01-19
forum: General Help
---

### Post by dragonfly41 on 2012-01-19
Recently I just could not get ubuntu-10.10 to break out of a "hung" status (stuck on splash and not launching into desktop).  I had to resort to repairing ubuntu-10.10 installed in separate root and home partitions.
I made sure that the two partitions were not formatted when reinstalling from Live CD hoping that applications (such as apache2, php5 and tomcat) would remain intact.

On restarting I noted that documents and Firefox bookmarks and desktop were intact as hoped.

But apache2, php and tomcat servers seem to have gone.

During reinstallation from Live CD I did note a warning message that "system files" would be erased in /etc, /lib, /usr, /var.

But are apache, php5, tomcat regarded as "system files"?

Is there a tutorial pointing out exactly what is is deleted/lost when ubuntu "repairs" a previous installation in separate root and home partitions?

Are the contents of these folders /etc, /lib, /usr, /var completely erased then overwritten during reinstallation?

---

### Post by saneearth on 2012-01-19
If you have a seperate home partition, this would be the only thing that can be kept in tact during a reinstall. Your root partition which contains all of your additional programs is formatted. Your settings are in your home folder, so a quick install of your extra programs from synaptic will bring you back to the way you were before. During install you also have to select other for install and pick the particular partitions on which you want to install. Just make sure you don't check the format box for your home partition.

---

### Post by dragonfly41 on 2012-01-22
To anyone still interested .. this is just a note of expansion (and for my future reference if I come back to this).

I did reinstall ububtu-10.10 into / (root) and /home partitions .. without formatting .. but even so some files were lost in root folder.

I had to reinstall apache2, php5, mysql, tomcat 7, and some others (Thunderbird, jedit, etc.).

If you are running apache or tomcat localhost servers which are in /root partition ensure that your www files are located in /home partition by changing the localhost directory from /var/www/ to public_html in home partition.

Keep a copy of php.ini (and other server config files) in /home partition.

This article explains ....

[http://maketecheasier.com/install-and-configure-apache-in-ubuntu/2011/03/09](http://maketecheasier.com/install-and-configure-apache-in-ubuntu/2011/03/09)

Similarly place tomcat webapps in /home partition and edit server.xml to different tomcat "appBase".

In my case I lost some tomcat war's and files which were in webapps folder in /root partition.

...

It *is* safer all round to backup the / (root) and /home partitions before "repairing".

---

