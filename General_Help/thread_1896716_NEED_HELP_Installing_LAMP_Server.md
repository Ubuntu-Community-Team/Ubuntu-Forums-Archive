---
title: "NEED HELP Installing LAMP Server"
date: 2011-12-17
forum: General Help
---

### Post by adamantasaurus on 2011-12-17
Hello 

I am following this tutorial given to me by one of the members here.....

[http://www.howtoforge.com/installing...-10.04-lamp-p2]("http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp-p2")

I'm on the step where it's telling me to add the info.php page onto my server..

I enter the code exactly as it says and when I hit enter a black screen  with a bunch of blue lines on the left side and in the bottom left of  the screen it says

 "/var/www/info.php" [New File]

And in the bottom right of the screen it says
0,0-1     All

Am I doing something wrong?

How do I fix this?

Any Advice is greatly appreciated.

Thanks

Adamantasaurus

---

### Post by Dangertux on 2011-12-17
> **adamantasaurus said:**
> Hello 

I am following this tutorial given to me by one of the members here.....

[http://www.howtoforge.com/installing...-10.04-lamp-p2]("http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp-p2")

I'm on the step where it's telling me to add the info.php page onto my server..

I enter the code exactly as it says and when I hit enter a black screen  with a bunch of blue lines on the left side and in the bottom left of  the screen it says

 "/var/www/info.php" [New File]

And in the bottom right of the screen it says
0,0-1     All

Am I doing something wrong?

How do I fix this?

Any Advice is greatly appreciated.

Thanks

Adamantasaurus

vi is kind of a complicated text editor for new users. You can use nano instead of vi. However if you want to use vi

Press i to activate insert mode.  Type in the code, then hit escape and : 

You will be presented with a : prompt at the bottom. Type wq! and press enter.

---

### Post by adamantasaurus on 2011-12-17
> **Dangertux said:**
> vi is kind of a complicated text editor for new users. You can use nano instead of vi. However if you want to use vi

Press i to activate insert mode.  Type in the code, then hit escape and : 

You will be presented with a : prompt at the bottom. Type wq! and press enter.

Thanks, so much it worked.

---

### Post by Dangertux on 2011-12-17
No problem, just so you know some exit options.

wq! (write output , and quit without prompt)
wq (write output and prompt if an overwrite will take place)
q! (quit with no prompt)
w (write with prompt)


Hope that helps.

---

### Post by MG&amp;TL on 2011-12-17
It might be easier to follow the official ubuntu documentation:

[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Always works for me. :)

---

### Post by perspectoff on 2011-12-17
You're kidding, right?

sudo apt-get install tasksel

sudo tasksel install lamp-server


Done!

---

