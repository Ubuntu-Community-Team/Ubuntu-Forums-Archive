---
title: "LAMP Server missing"
date: 2009-08-24
forum: General Help
---

### Post by bhuffer on 2009-08-24
Just installed Ubuntu 9.04 server, selected LAMP during the installation, and upon completion, Apache is there, but nothing for MySQL or PHPMYADMIN. I was prompted for the new MySQL password during install . . . What may I have missed?
 
Thanks in advance!!!

---

### Post by ibutho on 2009-08-24
Hi and welcome to the forum.

I don't think the default LAMP install includes phpyadmin. There is a lot of info on this [page]("https://help.ubuntu.com/community/phpMyAdmin") to help you install phpmyadmin.

---

### Post by lykwydchykyn on 2009-08-24
When you say they aren't there, how did you come to that conclusion?  

What do you get from:
```

aptitude show mysql-server phpmyadmin |grep State

```

---

### Post by bhuffer on 2009-08-24
Thanks for the replies. Here is the output of the command:

# aptitude show mysql-server phpmyadmin |grep -i state
State: installed
State: not installed
 * execute any SQL-statement, even multiple queries; 

I was informed all of the LAMP install/config was already done with the Ubuntu/LAMP installation, is this not the case?

I suppose I need to revert  back to installing phpmyadmin manually, and perform a basic lamp install procedure?

Thanks!

---

### Post by lykwydchykyn on 2009-08-24
> **bhuffer said:**
> Thanks for the replies. Here is the output of the command:

# aptitude show mysql-server phpmyadmin |grep -i state
State: installed
State: not installed
 * execute any SQL-statement, even multiple queries; 

I was informed all of the LAMP install/config was already done with the Ubuntu/LAMP installation, is this not the case?

I suppose I need to revert  back to installing phpmyadmin manually, and perform a basic lamp install procedure?

Thanks!

Well, mysql is clearly installed, but phpmyadmin is not. So I guess ibutho was correct that it's not part of the default LAMP install.  Just do 
```

sudo aptitude install phpmyadmin

```

That should get you what you need.

---

