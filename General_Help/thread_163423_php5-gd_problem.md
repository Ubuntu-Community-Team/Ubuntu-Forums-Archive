---
title: "php5-gd problem"
date: 2006-04-20
forum: General Help
---

### Post by schmidty on 2006-04-20
Hi...I'm using Breezy and I installed Apache2, php5, php5-gd and the php5-cli and am having problems with the GD module. I get the following error at the command line with "php -m" or just plain "php";

PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20041030/gd.so' - libt1.so.5: cannot open shared object file: No such file or directory in Unknown on line 0

I checked the /usr/lib/php5/20041030/ directory to make sure gd.so was there and I re-installed Apache2, php5 and the php5-gd packages and am still having the same problems. Any suggestions or fixes?

Schmidty

---

### Post by schmidty on 2006-04-20
Well...I guess I was able to fix my own problem. Awesome!!!

I simply installed the libt1.so.5 file from this site using 'dpkg -i'

[http://packages.debian.org/unstable/libs/libt1-5](http://packages.debian.org/unstable/libs/libt1-5)

...and it works fine now!!

If anyone has the same problem with php5-gd then here is the solution. Take care all!! I love Ubuntu!

Schmidty

---

