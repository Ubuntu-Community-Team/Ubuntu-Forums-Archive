---
title: "Lamp cannot find files"
date: 2011-02-15
forum: General Help
---

### Post by samishal on 2011-02-15
i have isntalled lamp following these isntructions : [http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.10-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.10-lamp)

however i cannot access my web content when i have put it in the WWW folder.

can you please help?

sam

---

### Post by asmoore82 on 2011-02-15
Those instructions can be shortened: ```
sudo tasksel
```

Could you provide more details?
Did you ever get the "It Works" page?

---

### Post by clgy15 on 2011-02-15
All right lets see. So you have a LAMP box and followed this guide. Okay so did you get all the way to the bottom with absolutly no problem? Did everything work including accessing all of the Apache and PHP stuff on the Web?

If so then try looking through PHPAdmin and see if there isnt a setting you forgot. 
If that doesnt work, may I ask what file your trying to display in the web browser? It may be the file itself

---

### Post by lisati on 2011-02-15
When the tutorial says:
> Now direct your browser to [http://192.168.0.100](http://192.168.0.100)
use the IP address of your server on your local network, and you should see the "It works" page.

---

### Post by samishal on 2011-02-16
hi

i managed to get it to find the files in the end i had to create a folder in www then transfer the files from the other folder into that one.

however when i click on the file it downloads it rather than viewing it so i assume that means that the php isnt working :( how do i solve please?

---

