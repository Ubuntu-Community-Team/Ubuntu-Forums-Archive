---
title: "Can't copy files to /var/www"
date: 2010-05-09
forum: General Help
---

### Post by letseatfood on 2010-05-09
Hello. I am completely new to Linux and just installed Ubuntu 10.04. I have successfully installed Apache2, PHP5, and MySQL. I cannot copy files or directories into /var/www. Sorry I know this is a super-basic issue, but I can't figure it out.

Can somebody tell me how I can enable copying of files and directories into /var/www?

Thanks!

---

### Post by LoneWolfJack on 2010-05-09
> sudo cp ...

other than that, it is probably a good idea to move your www directory to your home folder so you don't have to use sudo.

---

### Post by letseatfood on 2010-05-09
@LoneWolfJack: thanks. I was able to move the directory and the subdirectories and files. The more specific issue is that I am using [fireftp]("http://fireftp.mozdev.org/") in Firefox and when i attempt to get files from the server I receive an error:

Failed to save '/var/www/simpleims_3/bio_text_edit_form.php' locally.

I figured this had to do with permissions on /var or /var/www

Can you help with this?

Thanks!

---

### Post by LoneWolfJack on 2010-05-09
well, you can always chmod the directory to 777...

> chmod 777 /var/www

BUT be aware that this isn't to great an idea because /var/www is a system directory and with 777 you grant write access to this directory to all applications on your system.

like I said, I would just use a directory that is located in your /home folder, you should have no problems with permissions then.

---

