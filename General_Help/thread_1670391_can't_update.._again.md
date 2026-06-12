---
title: "can't update.. again"
date: 2011-01-18
forum: General Help
---

### Post by Tadcrazio on 2011-01-18
I get this error.


Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-cli_5.3.3-1ubuntu9.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-cli_5.3.3-1ubuntu9.2_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-mysql_5.3.3-1ubuntu9.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-mysql_5.3.3-1ubuntu9.2_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-gd_5.3.3-1ubuntu9.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-gd_5.3.3-1ubuntu9.2_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.3.3-1ubuntu9.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.3.3-1ubuntu9.2_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.3.3-1ubuntu9.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.3.3-1ubuntu9.2_i386.deb) 404  Not Found [IP: 91.189.92.167 80]

---

### Post by Old_Grey_Wolf on 2011-01-18
The mirror server that you have selected is not responding. Select a different mirror server.

Try going to "System > Administration > Synaptic Package Manager". When the Synaptic window opens, select the menu "Settings > Repositories". When the Repositories window opens select from the "Download from:" pull-down menu "Other...". It will give you a list; however, click the "Select Best Server" button. It will take a while as Synaptic tests for the best server. Click on the "Select Server" button. When you click the "Close" button, it will tell you to click on the "Reload" button. Click "Close" button, then on the main Synaptic window, click on the "Reload" icon. You can close the windows and try to update again.

I hope this solves your problem.

---

