---
title: "no directory in terminal?"
date: 2010-11-22
forum: General Help
---

### Post by totallynew on 2010-11-22
in terminal no directorys exist!
whats happening?
specifically trying to navigate to my desktop

---

### Post by nothingspecial on 2010-11-22
What do you mean no directory exists?

```
cd ~/Desktop
```

Make sure you uae a capital D, linux is case sensitive.

---

### Post by TBABill on 2010-11-22
+1 and be cautious because some folders are lower case while others are capitals. You'll see it if you navigate through the file browser.

---

### Post by karthick87 on 2010-11-22
Type 
```
cd Desktop
```to move to Desktop and ls command will show you all the directory's and files which are in the Desktop
```

ls 
```

---

### Post by Joeb454 on 2010-11-22
> **karthick87 said:**
> Type 
```
cd Desktop
```to move to Desktop and ls command will show you all the directory's and files which are in the Desktop
```

ls 
```

That assumes you are in your home directory - which is opened by default, yes - but you can't guarantee this on a forum, so ```
cd ~/Desktop
``` as suggested above is the better choice in this case :)

---

### Post by karthick87 on 2010-11-22
Thanks for reminding me Joeb454 :)[[COLOR=#980101]****[/COLOR]]("http://ubuntuforums.org/member.php?u=373057")

---

### Post by totallynew on 2010-11-22
cd desktop = no file or directory exists

---

### Post by Bradj47 on 2010-11-22
> **totallynew said:**
> in terminal no directorys exist!
whats happening?
specifically trying to navigate to my desktop

This reminds me of when I was trying to use the Windows command line and nothing existed. 

> **Joeb454 said:**
> That assumes you are in your home directory - which is opened by default, yes - but you can't guarantee this on a forum, so ```
cd ~/Desktop
``` as suggested above is the better choice in this case :)

To see what directory you are in you can always use
```
pwd
```
if you are uncertain.

---

### Post by Bradj47 on 2010-11-22
> **totallynew said:**
> cd desktop = no file or directory exists

You need to capitalize 'Desktop'. Like mentioned above, file names are case sensitive.

---

### Post by totallynew on 2010-11-22
> **Bradj47 said:**
> You need to capitalize 'Desktop'. Like mentioned above, file names are case sensitive.
 
cd /Desktop = bash no such file or directory

---

### Post by Bradj47 on 2010-11-22
> **totallynew said:**
> cd /Desktop = bash no such file or directory

If you're putting a slash in front of it, there's your problem. If you want to use a slash, be sure to put the slash after. The slash before indicates the directory you want to change to is in root.

---

### Post by bonixavier on 2010-11-22
There is no /Desktop directory. People are telling you to go to ~/Desktop. The "~" is the same as /home/username. To show hidden files, type ls -a.

Are you sure what you are looking for is really in that directory? What are you looking for?

---

### Post by totallynew on 2010-11-22
looking for this [B][FONT=Helvetica-Bold][SIZE=3][FONT=Helvetica-Bold][SIZE=3]
$ cd /Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412
[/B][/SIZE][/FONT][/SIZE][/FONT]

---

### Post by DarthScape on 2010-11-22
cd ~/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412

---

### Post by bonixavier on 2010-11-22
> **totallynew said:**
> looking for this [B][FONT=Helvetica-Bold][SIZE=3][FONT=Helvetica-Bold][SIZE=3]
$ cd /Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412
[/SIZE][/FONT][/SIZE][/FONT][/B]
[SIZE=5]DON'T YELL!!![SIZE=3] [SIZE=2]It's rude.

You'll get nowhere looking for /Desktop. It just doesn't exist. Read my previous post again.

The desktop directory is in your home directory. Look for /home/totallynew/Desktop. Search your files there. Better yet, use Nautilus - it's more intuitive.
[/SIZE][/SIZE][/SIZE]

---

### Post by totallynew on 2010-11-22
tried that exactly^ bash: cd: /home/lee/Desktop/DPO blah blah

---

### Post by totallynew on 2010-11-22
> **bonixavier said:**
> [SIZE=5]DON'T YELL!!![SIZE=3] [SIZE=2]It's rude.[/SIZE]
 
[SIZE=5]You'll get nowhere looking for /Desktop. It just doesn't exist. Read my previous post again.[/SIZE]
 
[SIZE=5]The desktop directory is in your home directory. Look for /home/totallynew/Desktop. Search your files there. Better yet, use Nautilus - it's more intuitive.[/SIZE]
[/SIZE][/SIZE]
it was a copy/paste not yelling
nautilus?

---

### Post by nothingspecial on 2010-11-22
Copy and paste my first post

You need a ~

~ is shorthand for /home/$USER

There is no /Desktop directory.......

...... unless you have created one.
```

cd ~/Desktop
```


Use the ~

---

### Post by nothingspecial on 2010-11-22
If your directory has spaces in it, you have to escape them
```

cd /home/lee/Desktop/DPO\ blah\ blah 	
```

Notice the \

---

### Post by totallynew on 2010-11-22
> **nothingspecial said:**
> Copy and paste my first post
 
You need a ~
 
~ is shorthand for /home/$USER
 
There is no /Desktop directory.......
 
...... unless you have created one.
```

cd ~/Desktop
```
 
 
Use the ~
 i did

---

### Post by totallynew on 2010-11-22
> **nothingspecial said:**
> If your directory has spaces in it, you have to escape them
```

cd /home/lee/Desktop/DPO\ blah\ blah     
```
 
Notice the \
yes noticed all the spaces and caps etc

---

### Post by nothingspecial on 2010-11-22
> **totallynew said:**
> looking for this [B][FONT=Helvetica-Bold][SIZE=3][FONT=Helvetica-Bold][SIZE=3]
$ cd /Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412
[/SIZE][/FONT][/SIZE][/FONT][/B]

No you didn`t

**[FONT=Helvetica-Bold][SIZE=3][FONT=Helvetica-Bold][SIZE=3]$ cd [COLOR=Red]~[/COLOR]/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412[/SIZE][/FONT][/SIZE][/FONT]**

---

### Post by totallynew on 2010-11-22
> **totallynew said:**
> i did
 opps now it works
desktop$
so what is the cd for the DPO folder?

---

### Post by totallynew on 2010-11-22
> **nothingspecial said:**
> No you didn`t
 
**[FONT=Helvetica-Bold][SIZE=3][FONT=Helvetica-Bold][SIZE=3]$ cd [COLOR=red]~[/COLOR]/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412[/SIZE][/FONT][/SIZE][/FONT]**
oh bugger.

---

### Post by totallynew on 2010-11-22
wow that shouldn't of been hard at all.
right stuck here
[FONT=Helvetica-Bold][SIZE=3][COLOR=#33339a][FONT=Helvetica-Bold][SIZE=3][COLOR=#33339a][FONT=Helvetica-Bold][SIZE=3][COLOR=#33339a][LEFT][SIZE=1]Step 5: Copy the RT2870STA.dat to RT3070STA.dat, and then copy the[/SIZE][/LEFT]
[SIZE=1]RT3070STA.dat into the driver folder on the Desktop[/SIZE]
 
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by Bradj47 on 2010-11-22
> **nothingspecial said:**
> If your directory has spaces in it, you have to escape them
```

cd /home/lee/Desktop/DPO\ blah\ blah 	
```

Notice the \

Or just use quotes, which I find easier:

```
cd "/home/lee/Desktop/DPO blah blah
```

Or you can just type the first part then use the TAB key to complete the filename with escape chars.

---

### Post by totallynew on 2010-11-22
got these errors help me fix them please
 
/home/lee/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/../../common/cmm_mac_usb.c:83: error: implicit declaration of function ‘usb_buffer_alloc’
/home/lee/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/../../common/cmm_mac_usb.c:83: warning: assignment makes pointer from integer without a cast
/home/lee/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/../../common/cmm_mac_usb.c:112: error: implicit declaration of function ‘usb_buffer_free’
make[2]: *** [/home/lee/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/lee/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2
[EMAIL="lee@lee-VirtualBox:~/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412$"]lee@lee-VirtualBox:~/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412$[/EMAIL]

---

### Post by nothingspecial on 2010-11-22
I think you need to make a new thread with what you are actually trying to do in the title.

:D

---

