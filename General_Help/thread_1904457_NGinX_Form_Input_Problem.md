---
title: "NGinX Form Input Problem"
date: 2012-01-04
forum: General Help
---

### Post by DenerB on 2012-01-04
I have just recently set-up a new LEMP in Ubuntu 11.10 (64-bit) and running NGinX ver 1.0.5. the server is running fine but I cannot seem to get any forms to work. On my old server (windows) the forms worked fine, but now I get the following error "502 Bad Gateway".
 
NGinX was installed with apt-get install, it is not a version that I compiled myself. Also I am running PHP5-Fastcgi.
 
I have tried setting the forms to work in two different ways, one to write to a text file and also to write to MySQL database.....but with no luck.
 
Any ideas on how to get the forms working again??

---

### Post by DenerB on 2012-01-04
> **DenerB said:**
> I have just recently set-up a new LEMP in Ubuntu 11.10 (64-bit) and running NGinX ver 1.0.5. the server is running fine but I cannot seem to get any forms to work. On my old server (windows) the forms worked fine, but now I get the following error "502 Bad Gateway".
 
NGinX was installed with apt-get install, it is not a version that I compiled myself. Also I am running PHP5-Fastcgi.
 
I have tried setting the forms to work in two different ways, one to write to a text file and also to write to MySQL database.....but with no luck.
 
Any ideas on how to get the forms working again??
 
 
So the only thing that I have found is this HttpFormInputModule.......looks like I will have to uninstall the rpm version and then download the source code and recompile/reconfigure nginx.  
The last time I did this I had added the http_flv_module but during that recompiling I could not get the http_xslt_module to compile at all and did it without_http_xslt_module.
I really didn't want to do this but as far as the mechanics goes for my site I am almost there......just need to be able to accept data from forms.
Does this sound like I am on the right path???

---

### Post by DenerB on 2012-01-05
> **DenerB said:**
> So the only thing that I have found is this HttpFormInputModule.......looks like I will have to uninstall the rpm version and then download the source code and recompile/reconfigure nginx. 
The last time I did this I had added the http_flv_module but during that recompiling I could not get the http_xslt_module to compile at all and did it without_http_xslt_module.
I really didn't want to do this but as far as the mechanics goes for my site I am almost there......just need to be able to accept data from forms.
Does this sound like I am on the right path???
 
Okay it was brought to my attention to try a test to see if any php page would display.....the result is no php pages would display.  So a very bright individual suggested that PHP was not running.  He was right!  After retracing my installation of PHP I had failed to start it......(go figure)!  Now......!!!!!!All my forms are working and I am able to collect the data in a MySQL database!!!  Wonderful!!!!

---

### Post by poa on 2012-01-05
The software has been created as general program for surveillance cross platforms running at the same time with wireless and wired IP webcams, TV-boards, capture cards, power-line, and USB cameras.[URL="http://paran.software4design.com/stores/paran/277140pgabout.html"]

---

