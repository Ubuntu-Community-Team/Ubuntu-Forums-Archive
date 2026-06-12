---
title: "Help Installing LAMP Server"
date: 2011-12-17
forum: General Help
---

### Post by adamantasaurus on 2011-12-17
Hello 

I am following this tutorial given to me by one of the members here.....

[http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp-p2](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp-p2)

I'm on the step where it's telling me to add the info.php page onto my server..

I enter the code exactly as it says and when I hit enter a black screen with a bunch of blue lines on the left side and in the bottom left of the screen it says

 "/var/www/info.php" [New File]

And in the bottom right of the screen it says
0,0-1     All

Any Advice is greatly appreciated.

Thanks

Adamantasaurus

---

### Post by Robertjm on 2011-12-30
Ahhh, vi. A great powerful little editor, but not as user friendly as something like gedit. :-)

You are creating a file from scratch called info.php. That is why it says "new file." Looking at the instruction on that page you need to type in the php block info and then save the file. To save a file that has been edited using the vi editor you need to hit the escape key and then type ":wq" (without quote marks).

Don't worry about the 0.0-1 all. That's just a coordinate within your file. Since it's brand new that's what it's going to say. You will notice as you type within you file, that number will be changingin accordingly.

If you're unfamiliar with the vi editor, here is a good page to check out online:

[http://www.cs.colostate.edu/helpdocs/vi.html](http://www.cs.colostate.edu/helpdocs/vi.html)

Good luck!!

Robert

> **adamantasaurus said:**
> Hello 

I am following this tutorial given to me by one of the members here.....

[http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp-p2](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp-p2)

I'm on the step where it's telling me to add the info.php page onto my server..

I enter the code exactly as it says and when I hit enter a black screen with a bunch of blue lines on the left side and in the bottom left of the screen it says

 "/var/www/info.php" [New File]

And in the bottom right of the screen it says
0,0-1     All

Any Advice is greatly appreciated.

Thanks

Adamantasaurus

---

