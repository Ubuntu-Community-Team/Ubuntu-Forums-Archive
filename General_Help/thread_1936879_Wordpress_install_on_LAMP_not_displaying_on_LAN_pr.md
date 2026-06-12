---
title: "Wordpress install on LAMP not displaying on LAN properly"
date: 2012-03-06
forum: General Help
---

### Post by XxionxX on 2012-03-06
I have a Wordpress install on a LAMP server installed on Ubuntu  10.04LTS. It works great when I visit is via the  [http://localhost/wordpress/](http://localhost/wordpress/) site on the local machine, but when I try  from another computer on the network using the hosting machine's ip  address like so: [http://192.198.1.108/wordpress/](http://192.198.1.108/wordpress/) It displays black and  white text with no CSS and no functionality of any kind. I tried using a  small site to see if there was a problem with my install, so I made a  site using some html, css, and php and it worked fine(I didn't know how  to test the sql). That site looked like this  [http://192.168.1.108/testsite/](http://192.168.1.108/testsite/) on the other computers, and it displayed  with no problems. I have spent a lot of time messing with file  permissions and looking at the sql database in relation to wordpress,  and everything seems to be set up right. I really can't find any way to  troubleshoot this on google, and I can't seem to find anyone else who  has had a similar problem. What am I doing wrong? Could someone please  point me in the right direction? I just want my coworkers to be able to  work on their Wordpress site on the LAN.

Please and Thank You.

---

### Post by XxionxX on 2012-03-06
OMG I FINALLY FIGURED IT OUT!! It took me 2 days, but I did it!

Just after I made this post, I made one last google in the hopes that I would find an answer. And after laughing about how MY post was at the very top of the search I looked at the other answers to my query. I [found this post]("http://ubuntuforums.org/showthread.php?t=1155225"), which was too old, but I gave it a shot anyway. AND I FIGURED IT OUT!!

So the solution I came to was:

_**Step 1:**_
Edit the httpd.conf file to reflect the IP address of your LAMP server. So I edited httpd.conf with this line in the terminal.
```
sudo gedit /etc/apache2/httpd.conf
```and then I changed the line in the file from
```
ServerName localhost
```to
```
ServerName <My-IP-Address>
```Don't keep the <> around your IP, or it won't work

**_Step 2:_**
In the settings Settings->General menu and change _**both**_ the "WordPress Address" and "Site Address" from [http://localhost/wordpress](http://localhost/wordpress) to [http://<your-IP-address>/wordpress]("http://localhost/your-IP-address")

Don't keep the <> around your IP, or it won't work

_**Step 3:**_
Restart Apache
```
sudo /etc/init.d/apache2 restart
```DONE! You should be able to see your website on the LAN now! I hope this helps someone! Please feel free to ask questions if I didn't make something clear, I am not a very good writer :(


[COLOR=Red]_**!!WARNING!!**_[/COLOR]
Step 1 and 2 can conflict with one another, so don't freak out if you  can't access your wordpress admin page during this process. If you get in trouble just  revert to the old settings and restart apache(described in step 3). You  may need to access the [http://localhost/phpmyadmin ]("http://localhost/phpmyadmin")page,  and reset the wordpress database field which holds the URL you changed in step 2.

This field holds  the URL which wordpress is pointed to, and the default setting is [http://localhost/wordpress](http://localhost/wordpress).  So log into phpmyadmin as root and click on the wordpress database (left hand  side or under 'databases') and navigate to wp_options and click  'browse'. In this database find the 'siteurl' and change it back to [http://localhost/wordpress](http://localhost/wordpress). It will be holding whatever value you changed it to in step 2.

---

### Post by x33a on 2013-02-27
Thanks a lot. I was having the same problem, but with nginx instead of apache.

Your solution worked perfectly fine. For those needing the steps for nginx, do the following:

1. In /etc/nginx/nginx.conf, under the server block, change localhost under ```
server_name  localhost
``` to the server ip.

2. The same as XxionxX's step 2.

3. Restart the nginx daemon.

---

