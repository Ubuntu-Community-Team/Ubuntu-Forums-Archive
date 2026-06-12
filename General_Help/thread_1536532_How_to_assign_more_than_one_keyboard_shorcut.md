---
title: "How to assign more than one keyboard shorcut"
date: 2010-07-22
forum: General Help
---

### Post by Myth123 on 2010-07-22
Hi,
    I'm running Ubuntu 10.04 on my Lenovo laptop. Sometimes I use USB KB which doesn't have the Multimedia keys. It would be great if I will be able to control my Volume etc using some Keyboard shortcut. I know that this can be done using Preferences->keyboard Shortcut. But the problem is it "replaces" old key (e.g. dedicated volume key on laptop ) with new one which I don't want to happen. I want to keep both keys for same operation.
Any help?

---

### Post by simosx on 2010-07-22
> **Myth123 said:**
> Hi,
    I'm running Ubuntu 10.04 on my Lenovo laptop. Sometimes I use USB KB which doesn't have the Multimedia keys. It would be great if I will be able to control my Volume etc using some Keyboard shortcut. I know that this can be done using Preferences->keyboard Shortcut. But the problem is it "replaces" old key (e.g. dedicated volume key on laptop ) with new one which I don't want to happen. I want to keep both keys for same operation.
Any help?

Indeed, the Keyboard Shortcuts do not allow to have, let's say, XF86AudioPlay assigned to an additional keyboard shortcut.

What you can do is somehow get to send yourself those keyboard events sends (like the XF86AudioPlay event) when you press your preferred keyboard shortcut. 

At least two tools can do this job,
1. keytouch, [http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/) (package: keytouch)
2. lineakd, [http://lineak.sourceforge.net/](http://lineak.sourceforge.net/)  (package: lineakd)

Did not try them myself, try them out and tell is if they work!

---

### Post by Myth123 on 2010-07-22
> **simosx said:**
> 
At least two tools can do this job,
1. keytouch, [http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/) (package: keytouch)
2. lineakd, [http://lineak.sourceforge.net/](http://lineak.sourceforge.net/)  (package: lineakd)

Did not try them myself, try them out and tell is if they work!

I just tried keytouch, but it doesn't take key combinations as its primary intension is to allow configuration of special keys and not to use some key combinations. :(

---

### Post by simosx on 2010-07-22
If you want to do this manually, you can 

1. Install lineakd (provides a utility 'xsendkeycode'),
sudo apt-get install lineakd

2. Find the keycode of the keyboard event you want to emulate,

xmodmap -pk

>     215    	0x1008ff14 (XF86AudioPlay)	0x0000 (NoSymbol)	0x1008ff14 (XF86AudioPlay)	


This means that '215' is the code for 'XF86AudioPlay'. If you have a music play one, you can send this to start/stop the music.

3. Write a script that sends this event,

$ gksudo gedit /usr/local/bin/myaudioplay

Now paste the following,
> 
#!/bin/sh

sleep 0.5
/usr/bin/xsendkeycode 215 1
/usr/bin/xsendkeycode 215 0
echo "Sent the XF86AudioPlay event" 1>&2


4. Make it executable,

sudo chmod 755 /usr/local/bin/myaudioplay

5. Test is (start your music player so that is makes sense to start/stop the audio)

/usr/local/bin/myaudioplay

(run the program again and again to start/stop.

6. Now you can go to the Keyboard Preferences and create a new entry. The command to run is /usr/local/bin/myaudioplay and select your favorite shortcut.

Note: 
The commands
/usr/bin/xsendkeycode 215 1
/usr/bin/xsendkeycode 215 0
you need to run them in a script, as a pair. The '1' means press the key, the '0' means release it. If you do not make a script, then your system will behave as if you keep pressed that key, messing things up. If you mess up, you can reboot and things will work again.

---

### Post by Myth123 on 2010-07-23
Thanks simosx. It worked really well!

---

### Post by 98cwitr on 2010-07-27
wrong thread :?

---

