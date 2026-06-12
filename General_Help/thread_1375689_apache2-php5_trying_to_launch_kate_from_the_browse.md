---
title: "apache2-php5: trying to launch kate from the browser."
date: 2010-01-08
forum: General Help
---

### Post by rene197705 on 2010-01-08
I'm working on a better var_dump ([]("http://skatescene.biz/htmlMicroscope/")[http://mediabeez.ws/htmlMicroscope/](http://mediabeez.ws/htmlMicroscope/), LGPL), and want to launch my kate editor when i click in the browser on a line in my trace-log.

I'm trying to exec() this line, but it returns 1 (which is i believe a general error)

echo "eeeehhh" | sudo -u rene -S /bin/sh -c "export HOME=/home/rene/ && kate -l 21 -u /media/500gb/data2/www/htdocs/naaah/maintenance/maintenanceLogic.php"

if i open a terminal, do 

  sudo su www-data

and then execute the line above, 
then kate actually jumps to the right file, or opens it, etc.

but from the browser, it won't work. exec($str,$o,$r); $r===1.
i could use some help here..

---

