---
title: "HELP! Cannot log into phpmyadmin :'("
date: 2011-04-23
forum: General Help
---

### Post by spirit.986 on 2011-04-23
I have XAMPP on my local pc runnung ubuntu that i use it for testing purposes...

During the initial XAMPP Security configuration  the password i put for the phpmyadmin was the same as my main Ubuntu password so i wanted to change into something different.. *[COLOR="DimGray"](I had to share phpmyadmin with others so i didn't wanted to reveal my Ubuntu password)[/COLOR]*

I changed the password but now i can't log into PHP my admin!
Somebody help me.. is there any way i can reset the password or add another root user with all DB privileges?

**Here is what I did** (I am writing this only by remembrance cause now i can't access phpmyadmin :S ):
1. Clicked on the Privileges tab
2. Selected the root user
3. Changed the password 
**[COLOR="Red"]*4[/COLOR]**. After several unsuccessful attempts to change the root password i repeat the same steps above and additionally I **checked the field that said something like: **  ***"Delete the user and create a new one with the new password*"**

And after that i was doomed :(

---

### Post by dragonfly41 on 2011-04-23
I had a problem recently with installation of phpmyadmin

[http://ubuntuforums.org/showthread.php?t=1736569](http://ubuntuforums.org/showthread.php?t=1736569)

I uninstalled using System > Administration > Synaptic Package Manager

.. followed the default uninstall options which come up (including odd ones such as "retry")

Then reinstall.

---

### Post by spirit.986 on 2011-04-23
I dont want to reinstall i'm simply lookin for a way to reset the mysql root password...

---

### Post by dragonfly41 on 2011-04-24
In the thread I gave you there was this link ..

[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

In my case..  it was easier to uninstall phpmyadmin .. then reinstall.

[EDIT]

You could try first .. 

sudo dpkg-reconfigure phpmyadmin

---

### Post by spirit.986 on 2011-04-24
OK... lets say i reinstall everything...
How can i backup the mysql database?

Back in windows i was using WAMP... the DB was located in one of the folders in .bin files so if i reinstall I will have to move those files into the newly installed xampp?

Did someone knows where i those files located?

UPDATE:
Ok i've found them.. they are located in /opt/lampp/var/mysql
I guess i am reinstalling after all... :S
I never thought that one day i will have to reinstall this... Everything was working perfectly :'(

---

