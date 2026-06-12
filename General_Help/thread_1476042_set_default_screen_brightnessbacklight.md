---
title: "set default screen brightness/backlight"
date: 2010-05-07
forum: General Help
---

### Post by tflazio on 2010-05-07
hi anyone know how to set the brightness/backlight on ubuntu 10.04?? i can adjust using fn key on my laptop but i want to set it dimmed everytime i reboot. thanks

---

### Post by DeXeS on 2010-05-27
I want to know the same... in 9 it's possible due a command line script but in 10 it doesn't work...

---

### Post by DeXeS on 2010-05-29
So, after some days of searching I found out the solution myself though it&#8217;s a dirty solution.
Here it is

What is [COLOR="Red"]red[/COLOR], depends on your configuration.
the configuration it works on is Ubuntu 10.04 with all the updates to may 29 2010.

Find out how to control the brightness from the command line.
The brightness you can control by doing so in the file /proc/acpi/video/[COLOR="Red"]M86[/COLOR]/LCD/brightness.
Where M86 is, you probably have something else so replace the folder name you have on your system with my folder name.

To find out how to control that file, type in

```
cat /proc/acpi/video/[COLOR="Red"]M86[/COLOR]/LCD/brightness
``` or
```
more /proc/acpi/video/[COLOR="Red"]M86[/COLOR]/LCD/brightness
```

I got this as output but you can have something different
```
levels:  [COLOR="Red"]1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16[/COLOR]
current: [COLOR="Red"]16[/COLOR]
```

test out what the values are by typing in
```
sudo echo -n [COLOR="Red"]1[/COLOR] > /proc/acpi/video/[COLOR="Red"]M86[/COLOR]/LCD/brightness
```

where 1 is, place your particular value

More about brightness control via command line see these threads
[http://ubuntuforums.org/showthread.php?t=858368]("http://ubuntuforums.org/showthread.php?t=858368")
[http://ubuntuforums.org/showthread.php?t=999497]("http://ubuntuforums.org/showthread.php?t=999497")
[http://www.linuxscrew.com/2007/10/25/ajust-lcd-brightness-from-command-line-works-at-dell-1501/]("http://www.linuxscrew.com/2007/10/25/ajust-lcd-brightness-from-command-line-works-at-dell-1501/")
use search

Now we know how to control the brightness from the command line, make a new file called brightness.sh somewhere on the disk. I put it in my home folder

```
gedit brightness.sh
```

put in the following text

```
#!/bin/bash
sudo echo -n [COLOR="Red"]1[/COLOR] > /proc/acpi/video/[COLOR="Red"]M86[/COLOR]/LCD/brightness
exit 0
```

make it executable

```
sudo chmod +x brightness.sh
```

make the file startup when Gnome has started. Go to System > Preferences > Startup Applications and click add and set the command to

```
sudo [COLOR="Red"]/home/dexes/[/COLOR]./brightness.sh
```

where of course /home/dexes/ is, put your own path to the script.

When in Gnome you need to enter a password when you enter the sudo command. Since it is a automatic startup script, Gnome will not let you enter the password so the whole script gets ignored.

So here is the dirty part. 
Edit sudoers so the script and the path inside the script does not need a password when using sudo.
You do that by entering 

Sudo visudo

And put this at the end of the file

```
[COLOR="Red"]dexes[/COLOR] ALL=NOPASSWD:/proc/acpi/video/[COLOR="Red"]M86[/COLOR]/LCD/brightness
[COLOR="Red"]dexes[/COLOR] ALL=NOPASSWD:/[COLOR="Red"]home/dexes[/COLOR]/brightness.sh
```

press ctrl+X and save the file.
Reboot and see if it worked for you. It did work for me

---

### Post by webmoly on 2010-11-17
Hi

there is no name as VIDEO in acpi folder..

I have install ubuntu 10.10 on Samsung N148
I have problem adjusting the backlight brightness.

what can I do ?

---

### Post by chrisauk0 on 2011-01-30
I am thanking you for posting this question in the most appropriate place being a reply in another thread.

One way to control brightness being a method using acpi is to be using the module for the kernel that is found here de.google.com/p/easy-slow-down-manage

for ubuntu there are some other repositories which you can be finding here [http://ubuntuforums.org/showthread.php?t=1502384](http://ubuntuforums.org/showthread.php?t=1502384)

> **webmoly said:**
> Hi

there is no name as VIDEO in acpi folder..

I have install ubuntu 10.10 on Samsung N148
I have problem adjusting the backlight brightness.

what can I do ?

---

