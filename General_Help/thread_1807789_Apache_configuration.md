---
title: "Apache configuration"
date: 2011-07-19
forum: General Help
---

### Post by Mharugha on 2011-07-19
[COLOR=black][FONT=Verdana]Hi guys,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]First of all, i would like to congratulate you for this incredible space.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I am a Linux beginner, and recently we are studying this theme at school and i am getting some difficulties.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I am trying to solve some of the last year’s school tests but constantly i am getting stuck on something.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]At this moment i got a question asking what files should i configure to setup Apache and the client to access should insert something like [/FONT][/COLOR][COLOR=black][FONT=Verdana][[COLOR=#0000ff]http://10.0.0.10/mywebsite:8080[/COLOR]]("http://10.0.0.10/mywebsite:8080")[/FONT][/COLOR][COLOR=black][FONT=Verdana].[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have already installed APache2, and change the listen ports to 8080 at ports.conf(Listen 8080 | Name VirtualHost *:8080) and at /etc/apache2/default (VirtualHosts *:8080).[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I also found the index.html at /var/www folder.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I also changed IP address at /etc/network/interfaces.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]With this changings, now i can access using [/FONT][/COLOR][COLOR=black][FONT=Verdana][[COLOR=#0000ff]http://10.0.0.10:8080[/COLOR]]("http://10.0.0.10:8080/")[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]But the problem is, what about the "mywebsite" part????[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]thank you in advance for your cooperation.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Best Regards.[/FONT][/COLOR]

---

### Post by Mharugha on 2011-07-19
Anybody can help me.
 
Thank you.
 
Is this the right place to put this thread??

---

### Post by bodhi.zazen on 2011-07-19
[http://10.0.0.10:8080/mywebsite](http://10.0.0.10:8080/mywebsite)

---

### Post by Mharugha on 2011-07-19
> **bodhi.zazen said:**
> [http://10.0.0.10:8080/mywebsite](http://10.0.0.10:8080/mywebsite)
 
 
Hi bodhi.zazen,
 
but where do i set that location "mywebsite". Apache2.conf? default?
Where should i place the index.html
 
Do not forget i am a beginner.
 
Regards

---

### Post by Hugh971 on 2011-07-19
that's just the folder structure of the website. By default apache shares the** /var/www** directory so if that's the case in yours you'd save your website in **/var/www/mywebsite**.

Hope that helps.

---

### Post by mikejonesey on 2011-07-19
lol, add;
```
Liseten :8080
<VirtualHost *:8080>
    ServerName 10.0.0.10
    DocumentRoot /var/www/html
</VirtualHost>
```to;
/etc/apache2/sites-available/default

```
sudo /etc/init.d/apache2 restart
```

then;
```
sudo mkdir /var/www/html/mywebsite
```
then;
```
sudo echo "hello world!" > /var/www/html/mywebsite/index.html
```

ps port 8080 is usually used by applications not webpages... these applications relay content back to port 80 to display to the user... in the event the application crashes / reboots / is down for maintenance you still have a website on port 80... also dunno why you use ip when you can create a text based name to your liking...

enjoy...

---

### Post by Mharugha on 2011-07-20
> **mikejonesey said:**
> lol, add;
```
Liseten :8080
<VirtualHost *:8080>
    ServerName 10.0.0.10
    DocumentRoot /var/www/html
</VirtualHost>
```to;
/etc/apache2/sites-available/default
 
```
sudo /etc/init.d/apache2 restart
```
 
then;
```
sudo mkdir /var/www/html/mywebsite
```
then;
```
sudo echo "hello world!" > /var/www/html/mywebsite/index.html
```
 
ps port 8080 is usually used by applications not webpages... these applications relay content back to port 80 to display to the user... in the event the application crashes / reboots / is down for maintenance you still have a website on port 80... also dunno why you use ip when you can create a text based name to your liking...
 
enjoy...
 
That's it my friend.
Thank you all for your help

---

