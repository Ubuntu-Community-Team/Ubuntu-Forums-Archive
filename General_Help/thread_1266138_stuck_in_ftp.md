---
title: "stuck in ftp"
date: 2009-09-14
forum: General Help
---

### Post by nandagopal on 2009-09-14
i am inside ftp,and i want to execute some commands
like 
delete x
delete y
i have stored these commands in a text file in my dir from which i am calling the ftp,
how do i now call this text file??

Please enlighten me.

---

### Post by viktara on 2009-09-14
Hi,

This shows you how:
[http://www.linux.com/archive/feature/119510](http://www.linux.com/archive/feature/119510)

Regards



Vik

---

### Post by nandagopal on 2009-09-15
Hey thanks [viktara]("http://ubuntuforums.org/member.php?u=477852"),
i had looked at the site before,the piping did not work,but the macro definitely do work,
thanks for pointing me in the right directions,let me just put my code in ~/.netrc so that others might not have trouble

#without putting the machine it's unable to recognise the macdef command.
machine xxx.xxx.xxx.xxxx
macdef update
cd Dropbox
ls



///////////////////////////////////////

And then inside ftp just call
$update
to call the macros.
/////////////////////////////////////////////


That's all , thaks a lot ,

---

