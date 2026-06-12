---
title: "Problem with user pref"
date: 2011-02-01
forum: General Help
---

### Post by Zwing on 2011-02-01
hello

i just installed ubuntu and truing too change settings for Conky but it says i have too have permission too change thing in the root folder.. i am the only user om this and i only know one password with i have set for this account.. and still it says i have no permission too change anything.. how do i activate so i can change thing in root and do what what i want in Ubuntu. is there some hidden root account that i don't know about?

---

### Post by stinkeye on 2011-02-01
If it's the **/etc/conky/conky.conf** you want to edit,enter in the terminal
```
cp /etc/conky/conky.conf ~/.conkyrc
```
Open your home folder and ctl+h to show hidden files and you'll see **.conkyrc**
which you can edit.


From man conky
> Default configuration file location is $HOME/.conkyrc or ${sysconfdir}/conky/conky.conf. On most systems, sysconfdir is /etc, and you can find the sample config file there (/etc/conky/conky.conf). 

You might want to copy it to $HOME/.conkyrc and then start modifying it. Other configs can be found at [http://conky.sf.net/](http://conky.sf.net/)

When running the command **conky** it looks for a config file at **~/.conkyrc**

If there is no such file it will load the default config at **/etc/conky/conky.conf**

You can start any config you like (can be any name you wish to give it) with...
```
conky -c /path/to/your/config
```


[**_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

---

