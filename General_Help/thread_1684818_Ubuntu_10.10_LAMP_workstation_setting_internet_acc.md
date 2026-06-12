---
title: "Ubuntu 10.10 LAMP workstation setting internet access"
date: 2011-02-09
forum: General Help
---

### Post by DrReaper on 2011-02-09
Hi Everyone,
I have a Ubuntu 10.10 LAMP workstation and it's working good. I need people to see it from the internet. I assigned an IP address to it and added it to the DMZ list it in the router. My friend can't see it at all from his location. What should I do now? I can see it on my local network OK. I don't want to switch my domain over to it until I can see if from the internet.

I gave him my external IP address to try to connect to the system.
My external IP is 76.89.114.72

---

### Post by DrReaper on 2011-02-10
After some testing we have found if you connect to port 80 on the external IP address you can get the apache2 server test page. The website under /blog/ fails to load. 

Not sure what to change to make it come up.

---

### Post by gordintoronto on 2011-02-10
How do you expect Apache to discover that there is a web site under /blog? By default, it looks at /var/www

---

### Post by DrReaper on 2011-02-10
I am no apache2 expert. Should I copy everything from /blog into /var/www ?
I suppose I can do it after I image the install first.

---

### Post by gordintoronto on 2011-02-10
Using /var/www is actually quite awkward. And the official Apache2 manual is some of the worst writing I have ever seen. (My job title was "editor" for seven years...) I'm sure there is a way to tell Apache2 to use /blog, but 15 minutes in Google didn't reveal it.

---

### Post by DrReaper on 2011-02-10
Well I tried it and it didn't work. I think I need to edit the 000-default file but i am not sure what to put in it yet. Thanks for trying to help.

---

### Post by DrReaper on 2011-02-23
Important tip. Make sure your server is pointing to your WAN IP address. I ended up finding all ip's pointing to my local lan and pointing them to the WAN IP and it's fixed.

---

### Post by fragos on 2011-02-24
You can put a link to the /blog folder in /var/www then it will be accessible in http:/localhost. If there are no index.html or index.php files in /var/www your browser will give you a display of the available files and folders including the blog folder you linked to. Select a folder and web site in the folder will be rendered.

---

