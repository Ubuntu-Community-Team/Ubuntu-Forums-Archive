---
title: "sudo permanent password request"
date: 2006-06-19
forum: General Help
---

### Post by fopetesl on 2006-06-19
Whenever I use a sudo command I always get a password request.
How to override so sudo works without the request?
[COLOR="SeaGreen"]**/etc/sudoers**[/COLOR] has:```
root ALL=(ALL) ALL
user_me ALL=(ALL) NOPASSWD:ALL
apache ALL=(ALL) NOPASSWD:ALL
php4 ALL=(ALL) NOPASSWD:ALL
%www-data ALL=(ALL) NOPASSWD:ALL
%admin ALL=(ALL) NOPASSWD:ALL
``` and [COLOR="SeaGreen"]**/var/run/sudo/user_me**[/COLOR] exists.

---

### Post by metafile on 2006-06-19
I don`t actually know, if there is any way to override it (except logging in as root), but I think this is one of the things that "you shouldn`t want to be done" :). It`s quite obvious that when you want something to be done as root, you have to enter root password.

When I moved to Ubuntu from Windows, this had been freaking me out for a while, but then I got used :).

---

### Post by ajgreeny on 2006-06-19
Why do you want to avoid having to type your password for root actions?  This is one of the major security advantages of linux and Ububtu compared with windows.
As far as possible you should do everything as a normal user, the first of whom, by default is the only one able to do things as root using sudo.  Stick with it and you'll soon realise it works well.

---

### Post by Johnsie on 2006-06-19
I find that annoying too but it's true that it's more secure having to type a password in. 

Saying that... people should have an option of whether they want their computer to be secure or not :-)

IMO passwords should be deafult but optional but I'm not an O/S developer so they prolly have their reasons.

---

### Post by fopetesl on 2006-06-19
Ah! OK.  More explanation req'd.
I am trying to run a php script which will shut down the computer:```
<?php
`sudo halt`;
?>
```
It seems that the order in which sudo authentications are placed into the sudoers file is significant.
Note my first attempt failed but this one succeeds:```
# User privilege specification
root ALL=(ALL) ALL
user_me ALL=(ALL) NOPASSWD:ALL
apache2 ALL=(ALL) NOPASSWD:ALL # seems not to be significant?
php4 ALL=(ALL) NOPASSWD:ALL    # -------- " ---------------

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD:ALL
%www-data ALL=(ALL) NOPASSWD:ALL # [COLOR="Red"]IS[/COLOR] significant
```which is not particularly secure so I need to tidy that up.

---

### Post by cotcot on 2006-06-19
Once you have given your password after sudo it lasts for some 10 or 15 minutes, unless you go to another desktop.

---

### Post by Ramses de Norre on 2006-06-19
You could write the script without sudo in it and then run "sudo script", you can give that one script the nopasswd option in /etc/sudoers then.

---

### Post by metafile on 2006-06-19
Maybe I`m missing something, but isn`t that "sticky bit" thing used in such cases?

---

### Post by AirRaven on 2006-06-19
You could always try "sudo su". That switches you to root permanantly.

---

### Post by epikos on 2006-06-19
Or if you don't really care about security at this point, couldn't you also write the script with your password in it? Then have the script feed sudo the password as a redirect to stardard in? like:
var=password
sudo halt 
input=$var

Sorry, I know nothing about scripting... But besides the complete lack of syntax, wouldn't something following this general idea work?

---

### Post by Ramses de Norre on 2006-06-19
Yes that's possible with the -S option like this: ```
echo password|sudo -S command

```

---

### Post by marwal on 2006-06-19
sudo chown root:root file.php
sudo chmod 4755 file.php

and run it
./file.php

(don't forget the shbang in the php file - '#!/usr/bin/php -q')

---

