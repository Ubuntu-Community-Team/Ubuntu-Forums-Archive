---
title: "HOWTO:Install PHP"
date: 2011-02-13
forum: General Help
---

### Post by linuxsyst on 2011-02-13
Step 1.Open up the Terminal (Applications > Accessories > Terminal).

Step 2. Copy/Paste the following line into Terminal and press enter:
```
sudo apt-get install php5 libapache2-mod-php5
```

[CENTER][SIZE="2"]Test PHP[/SIZE][/CENTER]

Step 1. In the terminal copy/paste the following line:
```
sudo gedit /var/www/testphp.php
```

Step 2. Copy/Paste this line into the phptest file:
```
<?php phpinfo(); ?>
```

Step 4. Now open you're web browser and type the following into the web address:

```
http://localhost/testphp.php
```

Good Luck

---

