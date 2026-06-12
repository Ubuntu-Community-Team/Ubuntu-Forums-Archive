---
title: "Copy files to var/www"
date: 2012-05-06
forum: General Help
---

### Post by dpuk44 on 2012-05-06
hi all, iv got a website iv built in php from my windows system and want to put inside var/www so it will connect to my LAMP iv just set up, but I am getting an error message saying:

"The folder "BournemouthBobcats" cannot be copied because you do not have permissions to create it in the destination."

how do you get around this simply?

Thanks

---

### Post by dragonfly41 on 2012-05-06
Right click on /var/www/

Properties > Permissions

set access permissions

---

### Post by Lars Noodén on 2012-05-06
You can get around it by either taking ownership of the folders or by setting group permissions:

[http://ubuntuforums.org/showpost.php?p=11714082&postcount=2](http://ubuntuforums.org/showpost.php?p=11714082&postcount=2)

---

### Post by dpuk44 on 2012-05-06
thanks folks, managed to get the folder BournemouthBobcats into var/www by taking the second approach as the first wouldnt let me as was greyed out.

now when i access localhost/BournemouthBobcats in firefox I am getting the following, but am unser why?

You don't have permission to access /BournemouthBobcats/ on this server.

---

### Post by Lars Noodén on 2012-05-06
Is it in /var/www?  Then you can be sure that the web server is able to read it by setting Other to read:

```

sudo chmod o=rx /var/www/BournemouthBobcats/ 

```

Also, how much have you changed the web server's default configuration file?  If you've turned off [Indexes](https://httpd.apache.org/docs/2.2/mod/core.html#options) in the Options, then it will return an error if you are missing the index file (usually index.html).

---

### Post by dpuk44 on 2012-05-06
lars...no changes to default had been made. if entered and it works fine now. what does that line do exactly?
chmod o=rx /var/www/BournemouthBobcats/

---

### Post by dpuk44 on 2012-05-06
also any ideas why a small little padlock icon is appearing on BournemouthBobcats folder?

---

### Post by Lars Noodén on 2012-05-06
> **dpuk44 said:**
> lars...no changes to default had been made. if entered and it works fine now. what does that line do exactly?
chmod o=rx /var/www/BournemouthBobcats/

[chmod](http://manpages.ubuntu.com/manpages/precise/en/man1/chmod.1.html) sets the file permissions for directories and files.  /var/www/BournemouthBobcats/ is the target for those changes.  The [permissions o=rx](https://help.ubuntu.com/community/FilePermissions) mean, for anyone that is not an owner of the directory and not in the group either, that write access is not given but it is possible to read files' content and see the names of the files.  

You can see the details by using the -l option on [ls](http://manpages.ubuntu.com/manpages/precise/en/man1/ls.1.html).

For your web server to work, it must be able to read the files and directories under /var/www.  For the web server to be safe, it should not be able to write to the files and directories under /var/www.

---

