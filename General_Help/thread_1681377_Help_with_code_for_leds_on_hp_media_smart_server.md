---
title: "Help with code for leds on hp media smart server"
date: 2011-02-04
forum: General Help
---

### Post by yagodajm on 2011-02-04
Hello all,
   I wanted to ask for your help in getting this code figured out for my leds on my hp media smart server.  I finally got ubuntu server 10.10 installed, and i found this code to get the leds to work under fedora linux, i got it to work under fedora. but i would rather use ubuntu server.  i get all the way done to the last 3 lines of the install and get a permission error.  i was hope some one could help me figure this out. i am pretty new to linux. here is what i got. 

```
yum -y install gcc-c++ libudev-devel 
cd /tmp
wget http://bitbucket.org/adaptation/mediasmartserverd/get/5654cec4f4d1.zip] unzip 5654cec4f4d1.zip
cd mediasmartserverd/ && make
mv mediasmartserverd /opt
chmod 755 /opt/mediasmartserverd
echo "# start our led daemon" >> /etc/rc.local
echo "/opt/mediasmartserverd -D" >> /etc/rc.local
./opt/mediasmartserverd -D
```

thank you for help,
justin

---

