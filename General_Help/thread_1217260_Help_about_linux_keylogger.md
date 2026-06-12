---
title: "Help about linux keylogger"
date: 2009-07-19
forum: General Help
---

### Post by Kernl on 2009-07-19
I have downloaded linux keylogger from this[ site]("http://linux.softpedia.com/get/System/Logging/LKL-6347.shtml"). 
I had saved it in the desktop. Its name was lkl-0.1.1.tar.gz. I extracted it in the desktop.and all teh commands i used is here.

cd Desktop
cd lkl
./configure
make
make install

these were what written in read me file inside lkl folder. I installed it.. and i think it went okay..
then i used 
sudo lkl -l -k /usr/share/lkl/keymaps/us_km -o keylog1.file &

adn dont know what happened....... 
i dont know where the logs are created.. if they are being created or not....
could anyone please help me!!!!!!!!!!
really in trouble...

---

### Post by wojox on 2009-07-19
Look in /var/log

else try in terminal:

```
whereis lkl
```

---

### Post by 3rdalbum on 2009-07-19
> **Kernl said:**
> 
sudo lkl -l -k /usr/share/lkl/keymaps/us_km -o keylog1.file &

adn dont know what happened....... 
i dont know where the logs are created.. if they are being created or not....
could anyone please help me!!!!!!!!!!
really in trouble...

Change the command to:

```
sudo lkl -l -k /usr/share/lkl/keymaps/us_km -o /tmp/keylog1.file &
```

Yes, the -o flag specifies the destination of the output file; if you just put a filename and not a path it will dump the file into the current working directory.

---

### Post by juancarlospaco on 2009-07-19
BTW Its on the Repos :)

---

### Post by credobyte on 2009-07-19
> **Windows7FTW said:**
> Just use windows, easy .exe no fuss.

Shame on you :-&

---

### Post by Kernl on 2009-07-20
> **3rdalbum said:**
> Change the command to:

```
sudo lkl -l -k /usr/share/lkl/keymaps/us_km -o /tmp/keylog1.file &
```

Yes, the -o flag specifies the destination of the output file; if you just put a filename and not a path it will dump the file into the current working directory.


Ya may be that helped but when i saw in /tmp/ there was no file such as keylog1.file
adn everytime i give this command a no. is seen what is the importance of that... 
and ya how to see that keylog1.file....
thanx for you help....

---

### Post by theviscount on 2011-02-22
Hello Everyone I am pretty new to this whole ubuntu linux thing, i downlaoded it about two days ago, and I have been trying to install a the lkl keylogger. I have successful figured out how to install it, but i dont know how to make it work...can someone plz help me.

---

