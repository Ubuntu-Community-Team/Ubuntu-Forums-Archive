---
title: "Smartfoxserver install help?"
date: 2011-05-23
forum: General Help
---

### Post by Skybucks100 on 2011-05-23
Okay so I bought a brand new Linux ubuntu VPS from Hostgator and I connected just fine and logged in just fine and then when I went to go and install Smartfoxserver and I typed in:
```
wget http://www.smartfoxserver.com/download/SFSPRO_linux_1.6.6.tar.gz
```
and it installed just fine and then I went to go see how Smartfox says to install it and they say:
```

1. open a terminal window and move to the folder where you have downloaded the file.
2. type "gzip -d filename.tar.gz" to extract the .tar file (where "filename" is the name of the downloaded file) 
3. type "tar xf filename.tar" to extract the files.
4. move inside the uncompressed folder and type ./install 

```
then I typed in 
```
 gzip -d SFSPRO_1.6.6.tar.gz 
```
and then it said:
```
gzip: SFSPRO_linux_1.6.6.tar.gz: No such file or directory
```
Am I doing something wrong? Or whats wrong :confused:

Any help would be awesome!
Thanks

---

### Post by ashekarema@gmail.com on 2011-05-23
You don't really need to do all that in the terminal.  Just right click the file "SFSPRO_linux_1.6.6.tar.gz" and select "Extract Here".  Then open the extracted folder and double click "install" and select "Run in Terminal"

----------------
[http://www.dotdeb.com](http://www.dotdeb.com) is a great place to find deb packages

---

