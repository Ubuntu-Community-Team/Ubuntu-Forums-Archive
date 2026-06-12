---
title: "I need some help getting perl pages to load!!"
date: 2009-12-24
forum: General Help
---

### Post by oospill on 2009-12-24
I've got Apache2 installed, and perl.. (perl -v verified this), I got my hello world script in /var/www and I have the permisions set to rwx for everyone.  But when I try to load the page (127.0.0.1/hello.pl) it just gives me a prompt to download the file or open it in a text editor.

Anyone have any ideas?

thanks

---

### Post by oospill on 2009-12-24
Well, I got it fixed.  I had to add these lines to apache.conf:

AddHandler cgi-script .cgi .pl
<Files ~ "\.pl$">
Options +ExecCGI
</Files>
<Files ~ "\.cgi$">
Options +ExecCGI
</Files>

I dono what that does.  But it works!!

---

### Post by efflandt on 2009-12-24
Regardless of file permissions, apache will not execute a script unless it knows it is CGI.  So typically whether it is a bash script or perl script, its file name should end with .cgi if you intend it to execute in apache.

Also it should typically have 755 permission (or maybe 705 minimum).  With 777 permission anybody on the system could modify it and you could get blamed (especially a machine you do not have control over, like an outside web host with multiple virtual hosts).

---

### Post by oospill on 2009-12-28
okay..  you lost me.. 755 permission? what does that mean?

thanks,
oospill

---

### Post by iponeverything on 2009-12-28
> **oospill said:**
> okay..  you lost me.. 755 permission? what does that mean?

thanks,
oospill

It's old-school but good to know:

[http://catcode.com/teachmod/numeric.html](http://catcode.com/teachmod/numeric.html)

7 = binary 111
5 = binary 101

the binary bits correlate to "rwx" which is for "**r**ead", "**w**rite" and "e**x**ecute"  and there are three numbers ie. 755 one for each set of permissions for "ugo" which stands for "**u**ser", "**g**roup" and "**o**ther".  And last but not least "1" is for true and "0" is for false. So 755 is:
```

user                group          other
read    = 1      read    = 1      read    = 1
write   = 1      write   = 0      write   = 0
execute = 1      execute = 1      execute = 1
111 = 7          101 = 5          101 = 5

```

---

### Post by oospill on 2009-12-28
Absolutely splendid!!  I learn something every day!!  =)

Viva la Ubuntu

---

