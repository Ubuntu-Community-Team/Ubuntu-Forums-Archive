---
title: "R plots from browser using perl-cgi (urgent)"
date: 2010-12-16
forum: General Help
---

### Post by sukhdeepsingh on 2010-12-16
Hi,
I am working on interfacing R with PERL-CGI.
Everything is working fine, but I am not able to produce plot using Cairo library in R as a png file. The problem is the R script is not able to produce a file when called from perl script in browser but if I run that locally, it produces the graph file.
I have granted the 777 permission to the 'plots' folder which will contain the produced plots and have aslo given www-data ownership to it using 

```

sudo chmod 777 /var/www/plots
sudo chown -R www-data:www-data /var/www/R/plots
sudo chmod 755 /var/www/cgi-bin/Rh.cgi

------------
# my perl cgi file(Rh.cgi)
#!/usr/bin/perl -w
 
use strict;  
use CGI;  
use CGI::Carp qw ( fatalsToBrowser );  
use File::Basename;  

print "Content-Type: text/html\n\n";
# this line calls the R script using vanilla under R
system('R --vanilla --slave <../R/t1.R');

-------------------
#my t1.R script
d=as.data.frame(cbind(c(1:10),c(11:20)))
print (d)
require('Cairo')
CairoPNG('a.png')
plot(d)
dev.off()

```I have used it last year same way but again got struck now

Urgent help required , Thank you very much :)
Bless

---

### Post by sukhdeepsingh on 2010-12-17
Update,
If I replace Cairo with bitmap, then the plot is produced but not with Cario (which has x11 support).
So to my understanding till now, its x11 problem on server.
Can anyone help in this case.
The permissions are all fine.

Thanks

---

