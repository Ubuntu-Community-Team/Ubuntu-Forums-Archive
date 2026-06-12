---
title: "gconf-tool doesn't work on start-up"
date: 2010-09-03
forum: General Help
---

### Post by hakermania on 2010-09-03
I want to change my desktop background on my every boot. So, I made a script that reads images from a file which contains their path (the 1st path is on the 1st line, the 2nd path is on the 2nd line etc)
So, I The script (located at /home/background_change) is
```
b=`cat /home/previous_image`
c=`expr $b + 1`
show_now=`image=$(sed -n "${c}p;${c}q" /home/images_list)`
echo "The image that will be shown now will be $show_now"
gconftool-2 --type string --set /desktop/gnome/background/picture_filename "$show_now"
echo $c > /home/previous_image`
sleep 5;
```
This could be at the programming talk as well, but I don't think that has to do with programming. I have add this string to /home/$USER/.gnomerc :
[B]gnome-terminal -e /home/background_change&
[/B]This means that the script will run once at start-up. the mad thing is that the $show_now path exists and if I start another gnome-terminal and I give by hand
*gconftool-2 --type string --set /desktop/gnome/background/picture_filename "$show_now"*
the wallpaper will change and this drives me crazy!!! :(

---

### Post by Miragej on 2010-10-04
Posted in the wrong place somehow, sorry guys.

---

### Post by Crazedpsyc on 2010-10-04
try instead adding the script to /bin or /usr/bin and putting the name of it for the command in System>Preferences>Startup Applications

---

### Post by thexnightmare on 2011-05-08
Hello guys,
I am facing same problem.
{
gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/xxx/script/picture.png"
}
If I run the entire script directly it runs very well, but this portion of the script dont run from startup.
I tried to make 2 scripts where 1 call 2, and this part of the script is in 2, both 1 & 2 works perfectly, just this portion dont work.
Any idea?

---

