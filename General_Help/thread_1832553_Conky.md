---
title: "Conky"
date: 2011-08-24
forum: General Help
---

### Post by trj021782 on 2011-08-24
I need a default conky.conf file Can anyone supply that to me?

I tried removing and re-installing conky in a variety of ways but it never replaced the conky.conf file.

---

### Post by Frogs Hair on 2011-08-24
I am having a little trouble understanding what you need . If you have installed Conky . ```
sudo apt-get install conky-all
``` You can then press Alt + F2 or open the terminal type and enter . ```
conky
``` The default conky configuration should appear in the top left corner of the monitor. To stop Conky use this command .```
killall conky
``` 

If you are looking for a conky configuration including a .conkrc file , use the link and search Conky . If you need help installing it post a thread with a link to the configuration you would like to use .[http://gnome-look.org/](http://gnome-look.org/)

---

### Post by stinkeye on 2011-08-25
> **trj021782 said:**
> I need a default conky.conf file Can anyone supply that to me?

I tried removing and re-installing conky in a variety of ways but it never replaced the conky.conf file.

If you run conky it will load the conf file @
**[B]~/.conkyrc**[/B] (hidden file in your home folder...ctrl+h to view)

If this file doesn't exist (which is the case unless you put one there)
it will load the default config @
**/etc/conky/conky.conf**


So if you want to edit your own config starting with the default config
as your base, copy the default to your home folder and rename to **.conkyrc**

ie in the terminal
```
cp /etc/conky/conky.conf ~/.conkyrc
```
Now you can easily edit the **.conkyrc** file.


Alternatively you can use anyone's config and save it as whatever you like
and run with 
```
conky -c /path/to/your/config
```

eg if I save someone's config as **conky1** in my home folder, I would run it with
```
conky -c ~/conky1
```


[**_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

---

