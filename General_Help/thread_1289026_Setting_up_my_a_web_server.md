---
title: "Setting up my a web server"
date: 2009-10-12
forum: General Help
---

### Post by Linux Lover on 2009-10-12
I worked on XAMPP on windowz. I need exactly similar server which will run on my local computer on Linux. I am using Kubuntu 9.04.

I already installed the Apache, PHP, My SQL using the following command.
```
sudo aptitude install apache2 php5 mysql-server
```

Now, if I go to [http://localhost/](http://localhost/)

it is dysplaying "It works".

Now, how do I access my php MyAdmin? 
Also, what is the directory which is similar to 'htdocs'? I mean where do I put my installation folders to run the set up?

I am a newbie. Please help me.

regards
Anindya

---

### Post by Dejai on 2009-10-12
If you open a terminal an type the following:
cd /var/www/ 
You will be moved to the location where you can add your files etc for the webserver this is common with all Unix systems. You can only edit files here as root aka by using the sudo command. You can use chmod to change permissions etc. 

As for setting it up why not take a look at this video tutorial:
[http://www.dailymotion.com/video/xabhr9_lamp-stack-plus-phpmyadmin-on-ubunt_tech](http://www.dailymotion.com/video/xabhr9_lamp-stack-plus-phpmyadmin-on-ubunt_tech)

---

### Post by jpmelos on 2009-10-12
You can change the root directory of your Apache server as well, by editing the /etc/apache2/sites-available/default file (need root powers) and replacing every /etc/www occurence with another folder. That folder needs to allow others to access and read the files.

For phpMyAdmin, just download it from [http://www.phpmyadmin.net/home_page/index.php]("http://www.phpmyadmin.net/home_page/index.php") and put it in a folder in your root directory. Then, you can use the browser to reach that folder and use it.

---

### Post by Linux Lover on 2009-10-12
> **Dejai said:**
> 
As for setting it up why not take a look at this video tutorial:
[http://www.dailymotion.com/video/xabhr9_lamp-stack-plus-phpmyadmin-on-ubunt_tech](http://www.dailymotion.com/video/xabhr9_lamp-stack-plus-phpmyadmin-on-ubunt_tech)

Very glad to let you know that as per the link you have provided, it is completed successfully without any problem. Everything went like a sharp knife on butter. :D

Thank you jpmelos too for your answer, but as it is already completed successfully, I have not tried further.

My best and sincere regards to both of you.

---

