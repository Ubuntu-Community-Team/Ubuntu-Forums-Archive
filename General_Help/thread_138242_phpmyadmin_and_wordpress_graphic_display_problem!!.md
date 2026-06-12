---
title: "phpmyadmin and wordpress graphic display problem!!!"
date: 2006-03-01
forum: General Help
---

### Post by moutraji on 2006-03-01
Hey guys!!! I don't know why i have this problem but i gave up on it!!! whe i go to my localhost on ubuntu, i have no problem opening phpmyadmin and wordpress!!! They just open nice and clean!!! But when i try to open my localhost from a windowes computer, both phpmyadmin and wordpress would display but without their graphics and missed up arrangment. I was trying to solve this problem but i couldn't and give up on it!!! So, if any one of you guys know how to fix that i would really appreciate it!!! By the way how can i install Ruby On Rails 1.8.4 and get it runing if any one knows!!! Thank you all in advance!!!

---

### Post by moutraji on 2006-03-01
Hello Guys!!!! Any one there!!! lol I need help here!!

---

### Post by kmi on 2006-03-04
Concerning Wordpress, are you sure your URL is defined (in Admin panel/Option) in a way it can be operational remotely ? i.e if you have "http://**localhost**/wordpress" and the host IP is **1.2.3.4** then the remote computer will access it through "http://**1.2.3.4**/wordpress" which will result in a partial display of the actual page : words appear but no CSS and links are broken (they say "http://**localhost**/wordpress/anypage.php...).

Edit the Option page to match the actual address of WP and, if necessary, the /etc/hosts...

Hope I'm clear (but not sure...) and it helps. :)

---

