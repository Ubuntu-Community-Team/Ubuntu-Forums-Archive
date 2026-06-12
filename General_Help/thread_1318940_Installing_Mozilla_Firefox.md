---
title: "Installing Mozilla Firefox"
date: 2009-11-08
forum: General Help
---

### Post by jon80 on 2009-11-08
I'm trying to install Mozilla FF by 

1. extracting the file downloaded (firefox-3.5.3.tar.bz2) using Ark.  The file is extracted to /Home/Documents.

2. I move the files using the command line to /usr/mozilla_firefox

administrator@elsueno:~/Documents/firefox$ sudo mv * /usr/mozilla_firefox
administrator@elsueno:~/Documents/firefox$ ls -latr                      
total 8                                                                  
-rw-r--r-- 1 administrator administrator    0 2009-08-24 17:33 .autoreg  
drwxr-xr-x 3 administrator administrator 4096 2009-11-08 06:15 ..        
drwxr-xr-x 2 administrator administrator 4096 2009-11-08 06:19 .         
administrator@elsueno:~/Documents/firefox$ cd /usr/mozilla_firefox
administrator@elsueno:/usr/mozilla_firefox$ ls -latr              
total 17900  

3. I try to run a few commands (random).

> administrator@elsueno:/usr/mozilla_firefox$ sudo run-mozilla.sh                                      
rwxr-xr-x  2 administrator administrator     4096 2009-08-24 17:                                        
> sudo: run-mozilla.sh: command not found                                                               
drwxr-xr-x 14 root          root              4096 2009-11-08 0                                         
> administrator@elsueno:/usr/mozilla_firefox$ sudo ./run-mozilla.sh                                     
drwxr-xr-x 13 root          root              4096 2009-11-08 06:                                       
>                                                                                                       

> run-mozilla.sh: Cannot execute .

(firefox-bin:4456): Gtk-WARNING> 
                                 
> administrator@elsueno:/usr/mozilla_firefox$ ls -latr

:lolflag:

Any ideas??

Also, I am installing Mozilla FF because Konqueror browser (comes packaged with Kubuntu) does not seem to support java on the website, or maybe I did.  Has anyone encountered similar problems with websites that used java?  Does Mozilla have similar problems?  Have you resolved them?

(see [https://answers.launchpad.net/ubuntu/+source/kdebase/+question/89088](https://answers.launchpad.net/ubuntu/+source/kdebase/+question/89088)).

---

### Post by thegreenblob on 2009-11-08
Have you tried changing the permisions so it can be executed?

```
sudo chmod +x run-mozilla.sh
```

and then just run it with,

```
./run-mozilla.sh
```

---

### Post by halj32 on 2009-11-08
when online why dont you just use
sudo apt-get install firefox
it's easyer than building
open bash cd to files
./config...
make
sudo make install

---

### Post by Lekensteyn on 2009-11-08
Ubuntuzilla is a great installer for Firefox:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

