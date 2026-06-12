---
title: "How to view the php file which is located in hadoop path?"
date: 2011-09-21
forum: General Help
---

### Post by maria80e on 2011-09-21
Hi all,

I have copied my files using hadoop in the following path "/user/hadoop/input" path. Now i need to open the "index.php" file which located in the above path, so i configure that path in apache. Then i tried in Ubuntu using vim 000-default and edit the below two lines.

<i>DocumentRoot /user/hadoop/input
<Directory /user/hadoop/input></i>

 But my "index.php" not working because file(index.php) not viewed, Just throw an following error. 

<i>The requested URL /input/index.php was not found on this server.</i>

Kindly check and advise me how to solve this issue.


Thanks,
Mariaprabudass

---

### Post by mcduck on 2011-09-21
Did you restart Apache after editing the config file? ("sudo service apache2 restart")

Also, since your document root already includes full path to where your .php file is located you shouldn't add any path when trying to  open it in the browser, simple "http://localhost" (or "http://localhost/index.php" if you prefer it that way) should be enough as the address.

---

