---
title: "Trouble Installing Flash"
date: 2009-10-15
forum: General Help
---

### Post by jakekimpton on 2009-10-15
Hi there! I've already looked around for a solution to this problem but everyone else seems to have a slightly different issue with this. Every time i try to install flash i get a error complaining about "libnspr4-dev" which was unable to be installed. 

So i went out and got libnspr4-dev and installed it using:

```
sudo dpkg -i ~/Desktop/libnspr4-dev.deb
```Which the returned the following error: 

```
libnspr4-dev: Depends: libnspr4-0d (<= 4.7.3-0ubuntu2.1~) but 4.7.5-0ubuntu0.9.04.1
```Thanks in advance :D

---

### Post by justleen on 2009-10-15
how about ```

sudo apt-get install flashplugin-installer 
```
Doesn't that work?

---

### Post by philinux on 2009-10-15
Whats wrong with using synaptic. 

If its a 64 bit plugin you need then get it here.
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Extract the libflashplayer.so file and copy or move to /home/youruser/.mozilla/plugins

You will need to create the plugins folder.

---

### Post by jakekimpton on 2009-10-15
> **philinux said:**
> Whats wrong with using synaptic. 

If its a 64 bit plugin you need then get it here.
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Extract the libflashplayer.so file and copy or move to /home/youruser/.mozilla/plugins

You will need to create the plugins folder.


Permission Denied on the folder :/

---

### Post by justleen on 2009-10-15
did you copy and paste that??

Since its you home folder, you have full access on it.

---

### Post by jakekimpton on 2009-10-15
> **justleen said:**
> did you copy and paste that??

Since its you home folder, you have full access on it.
Oh ok it seems to have pasted in now. I restarted FF but flash still isn't working...I test it with Youtube

---

### Post by justleen on 2009-10-15
You should change the path, to fit your username..

Why dont you use the package manager?

---

### Post by philinux on 2009-10-15
> **jakekimpton said:**
> Oh ok it seems to have pasted in now. I restarted FF but flash still isn't working...I test it with Youtube

Ok,

In a terminal,
```

sudo updatedb

then

locate libflashplayer.so
```

Post back the results. The first command takes a bit to do and has no output it just updates the locate database.

---

### Post by jakekimpton on 2009-10-15
Ok:

```
/home/jkimpton/Desktop/libflashplayer.so
/home/jkimpton/firefox/plugins/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
jkimpton@jakepad:~$ 
```

---

### Post by philinux on 2009-10-15
> **jakekimpton said:**
> Ok:

```
/home/jkimpton/Desktop/libflashplayer.so
/home/jkimpton/firefox/plugins/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
jkimpton@jakepad:~$ 
```

Use copy and paste into the terminal

```
sudo apt-get remove flashplugin-installer flashplugin-nonfree

then

mkdir /home/jkimpton/.mozilla/plugins

cp ~/Desktop/libflashplayer.so  ~/.mozilla/plugins

```

restart firefox

---

### Post by jakekimpton on 2009-10-15
Ok done all of that. Restarted and Tested on Youtube, still nothing...However, Youtube has stopped asking me to install Flash now... :S

---

### Post by philinux on 2009-10-15
What version ubuntu and firefox you running.

---

### Post by jakekimpton on 2009-10-15
Ubuntu 9.04 Jaunty
Firefox 3.0.8

---

### Post by philinux on 2009-10-15
> **jakekimpton said:**
> Ubuntu 9.04 Jaunty
Firefox 3.0.8

I noticed you had a firefox directory in your user folder, how come?

In firefox address bar type this and press enter.

```
about:config
```
type in the filter box, full. Now double click the last entry plugin.expose_full_path, it should change it's value to true.

Then in ff address bar
```
about:plugins
```

See if it's picking up the flash plugin. Post back what it says about flash.
I'm using 64 bit and mine looks like this.
> Shockwave Flash

    File name: /home/philinux/.mozilla/plugins/libflashplayer.so
    Shockwave Flash 10.0 r32

---

### Post by Niko Johnson on 2009-10-15
you can also try ```
 sudo flashplugin-nonfree 
```
but keep in mind that flash is also in the add/remove and synaptic package manager i believe

---

### Post by jakekimpton on 2009-10-15
Right ok here you go:

File name:  /usr/lib/swfdec-mozilla/libswfdecmozilla.so
Shockwave Flash 9.0 r999

I see i have only got 9...?

Also i'm not sure what that ff dir in my home dir is...Lol

---

### Post by Niko Johnson on 2009-10-15
i had that same problem in firefox 3... as much as i love firefox i have to say i think its just a browser issue. i tryed using a different browser (opera) and everything worked just fine. maybe you should try using a different browser?

---

### Post by jakekimpton on 2009-10-15
Right ok it seems to be working now. :D 

Thanks for your help [philinux]("http://ubuntuforums.org/member.php?u=353083")

---

### Post by philinux on 2009-10-15
> **jakekimpton said:**
> Right ok it seems to be working now. :D 

Thanks for your help [philinux]("http://ubuntuforums.org/member.php?u=353083")

You must have uninstalled swfdec-mozilla then. Good job.

---

