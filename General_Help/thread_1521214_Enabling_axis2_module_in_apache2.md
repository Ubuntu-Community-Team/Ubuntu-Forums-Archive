---
title: "Enabling axis2 module in apache2"
date: 2010-06-30
forum: General Help
---

### Post by stevebu56 on 2010-06-30
Could someone direct me to the correct mailing list or forum please.  I'm running 10.04 and trying to install Axis C++.  I searched the repositories & installed the following 
```
libaxis2c-bin
libaxis2c-dev
libaxis2c0
libxerces-c3.1
libxerces-c-dev

```I tried to enable the apache module with a2enmod axis2c but when I restart apache2 it errors so no such file.  Looking in /usr/lib/apache2/modules there is a libmod_axis2.so so I just made a link there to mod_axis2.so and then I was able to restart apache2.  My question is now how do I test the installation.  Is there a webpage for axis that will tell me it's working?  [http://localhost/axis](http://localhost/axis) returns not found.  Any documentation or instructions on installing axis on Ubuntu using the repos would be helpful.  

Thanks
Steve

---

