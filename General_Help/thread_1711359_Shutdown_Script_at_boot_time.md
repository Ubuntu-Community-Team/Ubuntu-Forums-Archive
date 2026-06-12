---
title: "Shutdown Script at boot time"
date: 2011-03-21
forum: General Help
---

### Post by nikhillife11 on 2011-03-21
Hey all

I have made a Shutdown script which i want to run at boot time.Can anyone help. The script is a below

#!\bin\sh

echo "When do u want the machine to shutdown itself"
read num
shutdown -h $num good bye

Now as you can see,I am trying to read an input i.e. the time from the user and then shutdown the machine when that time is reached..So anyone can help me to get it connected to boot file..
So that as soon as i m logged in i can give it the shutdown time and then work with ease..
Thanks

Also i m using UBUNTU 10.10

---

### Post by btindie on 2011-03-21
You'd be better of with creating a script that is run by the desktop when the user logs in instead of as a system startup script as I don't believe that interactive.

Create a script similar to the below
```
#!/bin/sh

time=$(zenity --entry --title="Shutdown" --text="Time to shutdown?")
if [ $? -eq 0 ]; then
  sudo shutdown -h $time "Good bye"
fi

```If you run that script by its self it should open up a GTK+ dialog prompting for when you want to shut it down. Just click on Cancel and it won't do anything...

To activate it when a user logs in create a new entry under Startup Applications which can be found under gnome-control-center. This should be fine if it's just the one user account you want it applied to but if you want it to be run for all then you might have to define that entry somewhere else so it gets applied on a global basis.

---

### Post by nikhillife11 on 2011-03-21
Hii mate,

Thanks for the idea..But if we save it as .sh files and double click on it...It open in GTK already..

But as you know programmers are lazy people,i want to go one step ahead. i would like it to run on its own after boot time. 
So that i just need to add the time and it works after that...

So anymore idea...any suggestion plz help

and thanks to all of you here to help us...

Thanks to you too Mr. btinedie

---

### Post by btindie on 2011-03-22
If you follow the instructions in my previous post you can get it to run automatically when a user logs in. You did set the eXecutable bit on it didn't you? ( chmod +x filename )

I suggested running it on it's own just to test that it works for you, once confirmed you can then add it to the list of Startup jobs run and it'll appear automatically at boot when the gnome session begins.

---

### Post by Krytarik on 2011-03-22
You either need to use "gksudo" instead "sudo" to query the needed password graphically, or disable the password query by following this thread:
[http://ubuntuforums.org/showthread.php?t=1677548](http://ubuntuforums.org/showthread.php?t=1677548)

---

