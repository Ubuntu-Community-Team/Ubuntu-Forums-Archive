---
title: "Shell script wont work at startup, but will work if clicked on in file manager"
date: 2009-07-23
forum: General Help
---

### Post by KinKiac on 2009-07-23
Hello all!  I was just wondering if someone could maybe help me out with a shell script.  Im a bit of a newb and recently I found a tutorial to create an embedded terminal in my desktop.  I think it used a program called wmctrl or something like that.  

Anyway, I managed to get the script to work, sort of, after reading through a tutorial on writing shell scripts, but it only works if I double click in my file manager and select 'run in terminal'.  It will not work by selecting just run and will not work if I place it in my startup.  

Any suggestions?

(sorry I dont have the actual script right now, Im not at home, but can get it later if needed)

Thanks

---

### Post by wojox on 2009-07-23
Right click and make it executable.
Then add it to System > Prefrences >Start Up Applications

---

### Post by michy99 on 2009-07-23
When you tried putting it i startup, did you use the full path to the script?

---

### Post by KinKiac on 2009-07-23
As far as I know it is executable, and I have added to my startup, thats not the problem.  I used the full path as well in my startup.  

If I click on it in file manager and select just run, it opens a terminal but does not place it properly.  If I select 'run in terminal' it opens the terminal and places it like it should.  I think what I need to know is how to make the script automatically 'run in terminal' rather then just run.  However, I may need to post the script when I get a chance.

---

### Post by KinKiac on 2009-07-24
Ok, so here is the actual script.  Could anyone help me out?  This is literally the first script Ive written and Im not sure if I did it right.  
Thanks

```
#!/bin/bash

# embedded terminal setup

xfce4-terminal --hide-menubar --hide-borders --hide-toolbars --title=descon && wmctrl -r descon -e 0,350,600,500,175 && wmctrl -r descon -b add,sticky,below && wmctrl -r descon -b add,skip_pager,skip_taskbar
```

---

### Post by dcstar on 2009-07-24
> **KinKiac said:**
> Ok, so here is the actual script.  Could anyone help me out?  This is literally the first script Ive written and Im not sure if I did it right.  
Thanks

```
#!/bin/bash

# embedded terminal setup

xfce4-terminal --hide-menubar --hide-borders --hide-toolbars --title=descon && wmctrl -r descon -e 0,350,600,500,175 && wmctrl -r descon -b add,sticky,below && wmctrl -r descon -b add,skip_pager,skip_taskbar
```

[LIST=1]
[*]Scripts tested in a user environment may not function in a system environment
[*]Anything that uses a X-screen requires specific settings when run from a non-graphics environment
[*]A lot of these things are already covered in things like cron job posts - do a search and you should get some hints
[/LIST]

---

### Post by KinKiac on 2009-07-24
> **dcstar said:**
> [LIST=1]
[*]Scripts tested in a user environment may not function in a system environment
[*]Anything that uses a X-screen requires specific settings when run from a non-graphics environment
[*]A lot of these things are already covered in things like cron job posts - do a search and you should get some hints
[/LIST]

Cool, thanks!  Ill try that.  Like I said though this is my first attempt at writing a script and applying it to my system so there could be a lot of things that I am missing or just dont know about.

---

### Post by mikey_likesit on 2009-07-25
I've got a similar problem with a script I wrote, though for some reason it doesn't seem to want to run even when put into the system>preferences>startup applications.

the file is owned by root but i've done chmod 777 hoping that would get it to work, but no dice. I'm thinking it may be because of the use of sudo in the script, could that be right? When I run it from terminal (doesn't work with regular run) I get asked for my password, then everything works fine.

Basically the script, included below, is a workaround to me trying to get my 2 network drives to automount at startup. I've tried editing /etc/fstab but maybe I just don't know the right commands...

```

#!/bin/bash

sudo ifconfig eth0 169.254.9.9
sudo smbmount //169.254.157.241/disk /mnt/networkdisk
sudo smbmount //169.254.157.241/usbdisk2 /mnt/networkdisk2
```

---

### Post by Tomatz on 2009-07-25
> **mikey_likesit said:**
> I've got a similar problem with a script I wrote, though for some reason it doesn't seem to want to run even when put into the system>preferences>startup applications.

the file is owned by root but i've done chmod 777 hoping that would get it to work, but no dice. I'm thinking it may be because of the use of sudo in the script, could that be right? When I run it from terminal (doesn't work with regular run) I get asked for my password, then everything works fine.

Basically the script, included below, is a workaround to me trying to get my 2 network drives to automount at startup. I've tried editing /etc/fstab but maybe I just don't know the right commands...

```

#!/bin/bash

sudo ifconfig eth0 169.254.9.9
sudo smbmount //169.254.157.241/disk /mnt/networkdisk
sudo smbmount //169.254.157.241/usbdisk2 /mnt/networkdisk2
```     


This should work (its a bit dirty though):

```
gksudo ifconfig eth0 169.254.9.9
gksudo smbmount //169.254.157.241/disk /mnt/networkdisk
gksudo smbmount //169.254.157.241/usbdisk2 /mnt/networkdisk2
```  

:)

---

### Post by wojox on 2009-07-25
?

---

### Post by mikey_likesit on 2009-07-25
thanks Tomatz, that did the trick! Now though, I get a password prompt after login. Any way to stop that happening?

I read another thread ([http://ubuntuforums.org/showthread.php?t=1219165](http://ubuntuforums.org/showthread.php?t=1219165)) where it was suggested that the poster (who wanted to run a script to load his mousepad) do so at startup rather than login by linking the script into /etc/rc3.d

I've never played with this stuff, but it sounds promising. Do scripts get executed as root? (ie could I leave out the sudo stuff altogether?) Also, I'm not sure what level to put the script in but am I right in assuming that rc6.d is the last one to get run?

---

### Post by mikey_likesit on 2009-07-25
so I tried moving my script to /etc/init.d and making a link to /etc/rc6.d, renamed S99networkmount. nothing happened.

am I wrong thinking I can assign an IP to eth0 and mount the 2 drives at startup rather than login? I have a partition that automounts at login through a line in /etc/fstab, can I do something similar for my network drives?

---

### Post by Tomatz on 2009-07-25
There is a GUI for configuring fstab called **mountmanager**.

To install it:

```
sudo apt-get install mountmanager
```

Though i havent used it, there is a plugin included in mountmanager to configure samba shares (smb).


Hope that helps ;)

---

### Post by KinKiac on 2009-07-25
Hmmmm....   Looks like my thread's been hijacked, lol, oh well. 
 
So.. I tried searching cron jobs as was recommended, and while I appreciate any help at all, I dont see how cron jobs apply to what I am trying to do(I did not know even what a cron job was before now).  I also dont quite understand what was said about user environments being different than system environments.  It is in the user environment I thought I was executing the script(via startup manager) when I log in.  Is this not correct?  

All I am trying to do is figure out how to get my script to automatically run in a terminal window rather than just trying to execute, which for some reason doesnt work.  

Is there anything I can add to the script or any place I can put it to tell it to just run in terminal?  Ive seriously spent hours reading up on shell scripts(nothing but the basics seem to apply to this particular script) and also searching google and these forums and have not made any progress.  

Thanks!
(oh and I just wanted to add that my total working experience with linux and Ubuntu amounts to about 3 weeks at this point)

---

### Post by lswb on 2009-07-25
For Kinkiac:

I am not familiar with the xfce terminal so I can't help with the options there, but have you tried putting the xfce-terminal... line directly in the command field of the startup app dialog box?

For Mikey:

Take a look at the file /etc/rc.local

This is a script that is called at the end of the boot process. It runs and must be edited as root so "sudo" is not necessary and should not be used in it. In a default installation the contents of this file will only be some comments and a single "exit" statement. You can put your commands directly in the rc.local file, before the "exit" line, or call your script from the rc.local file if you prefer. If calling a script from rc.local, make root the script owner and provide the full path give the script permissions of 755. The traditional location for scripts of this nature is /usr/local/bin or /usr/local/sbin. Another advantage of using your script here is that it doesn't require logging in to the desktop before it runs.

Using /etc/rc.local for these kinds of commands is generally preferable to creating scripts in /etc/init.d and linking to them from the /etc/rcx.d directories. BTW, in ubuntu, the default runlevel is 2 and the links to init scripts are in /etc/rc2.d  The links in /etc/rc6.d only run for runlevel 6, which is for rebooting.

---

### Post by KinKiac on 2009-07-26
> **lswb said:**
> For Kinkiac:

I am not familiar with the xfce terminal so I can't help with the options there, but have you tried putting the xfce-terminal... line directly in the command field of the startup app dialog box?



Hmmmm.... interesting, now that's something Ill have to try.  Thanks!

---

### Post by mikey_likesit on 2009-07-26
sorry KinKiac, didn't mean to get in your way, it just seemed like our issues may be somewhat related...

Iswb, thanks for the explanation of rc.local. I did as you said, tried a few variations on referencing my script (though I wasn't entirely sure how to do it) and even pasting it directly into the file (minus the sudo). When referencing the script, I included the line:
```

./usr/local/bin/networkmount.sh
```
but that didn't seem to do anything. Also tried it without the leading dot, no change. Should I be doing something different?

---

### Post by lswb on 2009-07-26
> **mikey_likesit said:**
> sorry KinKiac, didn't mean to get in your way, it just seemed like our issues may be somewhat related...

Iswb, thanks for the explanation of rc.local. I did as you said, tried a few variations on referencing my script (though I wasn't entirely sure how to do it) and even pasting it directly into the file (minus the sudo). When referencing the script, I included the line:
```

./usr/local/bin/networkmount.sh
```
but that didn't seem to do anything. Also tried it without the leading dot, no change. Should I be doing something different?

Not sure where the problem is, but here are a few things to check:

Is your script actually in the /usr/local/bin directory with the proper owner and permissions? (confirm with ls -l /usr/local/bin/networkmount.sh)

Do not use "sudo" in the networkmount script as it is now being run as root.

The correct line to call it from /etc/rc.local is "/usr/local/bin/networkmount.sh" (without the quotes)

Make sure this line is put in /etc/rc.local *before* the "exit" line.

---

### Post by KinKiac on 2009-07-29
> **mikey_likesit said:**
> sorry KinKiac, didn't mean to get in your way, it just seemed like our issues may be somewhat related...


Oh no dont worry about it, I was mostly joking anyway.  I just checked on my thread one day to find that I had a bunch of responses but, most of the new responses were to your issue and I was just thought to my self "hey, this is my thread, :P"  lol.  Its all good though.  Im kinda giving up on running an embedded terminal in this way.  There are many other tutorials out there and I cant seem to find the one I got it from so I can find a different way to do it when I get time.  Until then I just have to navigate to my script and and tell it to run in terminal manually and it works for that session.  

Ive also been working on some conky stuff too, sort of, and may not end up keeping an embedded terminal anyway.

Cheers

---

