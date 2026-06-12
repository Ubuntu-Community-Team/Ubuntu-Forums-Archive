---
title: "perl script in cgi-bin cannot load library"
date: 2011-01-25
forum: General Help
---

### Post by bleutyler on 2011-01-25
Hello,

This is an Apache / Perl problem that I am having.  

I am using a CPAN Module in my perl CGI application.  It is Spreadsheet::ParseExcel

I have installed the cpan module NOT with 
```
perl -MCPAN -e shell
```because the network is blocking the shell terminal from accessing the internet.  Therefore, manual installations with tar.gz files was in order.  
I have installed the dependencies.
However, I did do so as a non-root user.  The library that contains these files is under a user folder, /home/user/lib

Now, I have successfully configured Apache2 on this box.  The html directory is /var/www/html and the cgi folder is /var/www/html/cgi-bin.  I have verified they work because all of the scripts in that folder that do not require the special modules work in my firefox browser.

However, when I try to run the scripts that use "Spreadsheet::ParseExcel", I get the error that the module cannot be found in @INC.  However, I have a "use lib" statement at the beginning of the script that adds the library.  

The scripts can be run in PUTTY without problem.  Only when running the script from the browser am I getting the issue.

Any insights on the issue?

---

