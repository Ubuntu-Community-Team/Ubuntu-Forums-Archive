---
title: "PHP webpages show blank page"
date: 2006-04-20
forum: General Help
---

### Post by flickerfly on 2006-04-20
My php websites are showing a blank white page when I try to access them. They have worked previously. I've tried clearing the cache. I've had php5 installed, but downgraded to php4. This is when the problem started occuring. I've used a2enmod and a2dismod to add and remove php from apache2.

No php is operating as expected (Drupal or Moodle) and both were operating, meaning the php was executing, before the downgrade to php4.

Do you have any idea what's causings this? There doesn't seem to be anything relevant in access.log or error.log in /var/log/apache2/

---

### Post by Ensnared on 2006-04-20
Did you restart apache?
```
sudo /etc/init.d/apache2 restart
```

You should also check your scripts - I used to only do "<?" and "?>" for my PHP code before, but when upgrading PHP one day I found all my scripts stopped working. Turned out the reason was a configuration-setting (which I don't remember what is anymore) which meant all PHP code had to be enclosed in "<?php" and "?>" instead (which is the proper way of doing it anyway). That was ages ago though, and on a completely different distro, but it's worth trying out as well.

---

### Post by flickerfly on 2006-04-20
Ensnared, yes. I have restarted. I've not actually hacked any PHP code. I've just installed php based programs so I assume the code is correct since it is running on many other servers without problem.

---

