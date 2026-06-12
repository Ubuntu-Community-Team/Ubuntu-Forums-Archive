---
title: "Munin seems to be broken in 10.04"
date: 2010-05-01
forum: General Help
---

### Post by sohail_zafar on 2010-05-01
Hi,
I just upgraded to 10.04 and munin seems to be broken. Looks like the graphs are being put in the wrong directory. In the old version the png files were in /var/www/munin/localdomain directory as file localhost.localdomain-XX.png but in the new version in /var/www/munin/localdomain/localhost.localdomain/XX.png. Here is a line from the log file,
 
2010/05/01 21:20:13 [RRD ERROR] Unable to graph /var/www/munin/localdomain/local
host.localdomain/acpi-month.png : Could not save png to '/var/www/munin/localdom
ain/localhost.localdomain/acpi-month.png'
 
I also tried to remove the old version and install new version by removing all related files. The new version does not even populate /etc/munin. Does not even put a default munin.conf or munin-node.conf files or put some default links in the plugin directory. As a result munin-node does not even start.
 
Sohail.

---

### Post by peter3 on 2010-05-04
Here's what I did.  It won't work if you require the history in your RRD files.  First, I found the problem when I went to look at [http://localhost/munin/](http://localhost/munin/)    I received a 403 Access denied error.  I figured this was a permissions problem, but could not find it.  Finally, I did:
apt-get --purge remove munin munin-node munin-common
to get rid of the old installation.  Then I ran 
updatedb
locate munin
to find any left over cruft.  There was some, which I removed. 
Then I reinstalled munin with
apt-get install munin
which automatically pulled in munin-node and munin-common
Unfortunately, I still had the 403 Access denied error.
Next, I replaced the line
Allow from localhost 127.0.0.0/8 ::1
with
Allow from all
in the file /etc/munin/apache.conf
This allowed me to see the munin graphs over an ssh tunnel.
I'm happy.

---

### Post by sohail_zafar on 2010-05-04
I do not want to loose the history in the first place. Secondly I did try to move the data to a temporary directory and then issued apt-get remove the three packages. I reinstalled these packages but still had a problem even with the new data that was being generated.

---

### Post by scovel on 2010-05-22
Seems like someone moved where the munin WWW folder is in the latest version.

vi /etc/apache2/conf.d/munin

find all the /var/cache/munin/www
and change them to /var/www/munin

fixed it for me.  No history lost.

---

