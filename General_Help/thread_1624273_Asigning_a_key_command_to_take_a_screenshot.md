---
title: "Asigning a key command to take a screenshot"
date: 2010-11-17
forum: General Help
---

### Post by rmcellig on 2010-11-17
Every time I take a screen shot using Select Area to Grab, I have to 

1. Select Take Screenshot 
2. Click on Select area to grab
3. Click on Take screenshot

Is there a way I can assign a key command that will do all of this for me? When I am using my Mac, I assigned option-F2 to do what I listed above. I would like to do something similar in Ubuntu.

---

### Post by sisco311 on 2010-11-18
System -> Preferences -> Keyboard Shortcuts -> Add... -> In the command field type:
```
gnome-screenshot -a
```

---

### Post by rmcellig on 2010-11-18
Thanks but when I invoke the keyboard shortcut it takes a screenshot of the entire screen. What I would like is to have the crosshairs come up so I can selct what I want to take the screenshot.

---

### Post by jpl888 on 2010-11-18
Use "--interactive" instead of -a.

May be an idea to assign it to a different key combo like shift + print screen to avoid changing the default ones.

---

### Post by rmcellig on 2010-11-18
Thanks! That worked but it brought up the Take screenshot window instead of the crosshair so that I don't have to see the tke screenshot window. I would like when I press the key board shortcut to have the crosshairs appear so that I can just select what screenshot I would like to take instead of having the Take screenshot window come up.

---

### Post by jpl888 on 2010-11-18
Actually the previous poster was right it is "-a". 

I think the problem was that there is a default shortcut for print screen that just does the whole screen.

My previous idea of assigning the command to shift + printscreen will get around that.

---

### Post by sisco311 on 2010-11-18
That's exactly what **gnome-screenshot -a** should do. Don't know why is not working. Try the long form:
```
gnome-screenshot --area
```

---

### Post by rmcellig on 2010-11-18
Now I have a stupid question :)

Where is the print screen key? I look at my keyboard and I don't seem to have one. I am using a Mac keyboard. I just compared it to a PC keyboard I am using on another computer and where the ptint screen button is, I have F14. Maybe I can just assign that key to the screenshot function and see if it works?

---

### Post by rmcellig on 2010-11-18
I tried that but here is what I get when I press shift-F14

---

### Post by rmcellig on 2010-11-18
When I run gnome-screenshot -a from the command line I get the crosshairs but not when I put the command in keyboard shortcuts.

---

### Post by sisco311 on 2010-11-18
Does the command work if you run it in a terminal?

EDIT: try running the command in a sub-shell:
```
sh -c "gnome-screenshot -a"
```

---

### Post by rmcellig on 2010-11-18
I just tried it on my other PC also using a Mac keyboard and it works fine just like you said, but on my iMac which I am running Ubuntu 10.10 in dual boot mode, it doesn't work.

---

### Post by rmcellig on 2010-11-18
Yes. Works fine from that command in the terminal.

---

### Post by jpl888 on 2010-11-18
It does the same to me as well. Must be a "feature" ;)

---

### Post by rmcellig on 2010-11-18
Hi jpl888,

So it doesn't work for you either when you set up a keyboard shortcut but it works from the terminal? I wonder why this is? I take a lot of screenshots and I would sure like to simplify the process using a keyboard shortcut.

---

### Post by jpl888 on 2010-11-18
Yep. Does work from terminal. Doesn't work from shortcut. 

And the funny thing is -w does work from the shortcut so you can do the current window.

---

### Post by rmcellig on 2010-11-18
That's weird. Sounds like a bug?

---

### Post by jpl888 on 2010-11-18
Yes that's what I meant when I said "feature" it's corporate speak for a bug :)

---

### Post by celldweller1591 on 2010-11-18
use [Shutter]("www.linoob.com/2010/09/shutter-feature-rich-screenshot-app-for-ubuntu/") to take screenshot of almost anything on your desktop in just 1 click

---

### Post by sisco311 on 2010-11-18
M'KAY, figured it out. You have to delay the command:
```
sh -c "sleep 1 && gnome-screenshot -a"
```

---

### Post by jpl888 on 2010-11-18
Nice one! Works a treat.

---

### Post by rmcellig on 2010-11-18
Yes sisco311!! That works!!

I will also try Shutter as well. I just wanted to make this work with the Gnome screenshot feature. I'm stubborn that way :)

Thanks again for all of your help and suggestions!!

---

### Post by sisco311 on 2010-11-18
You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" menu, then "Mark this thread as Solved".

Thanks.

---

### Post by rmcellig on 2010-11-18
I just got to try my new key shortcut and it works fine. Unfortunately, I cannot install Shutter from the Ubuntu Software Centre. I receive the following error. What can I do to fix this?

---

### Post by sisco311 on 2010-11-18
> **rmcellig said:**
> I just got to try my new key shortcut and it works fine. Unfortunately, I cannot install Shutter from the Ubuntu Software Centre. I receive the following error. What can I do to fix this?

Make sure that no other package manager (apt-get, Synaptic, Update Manager) runs. You can't use more than one package managers at the same time.

If no other package manager is running, then try:
```
sudo apt-get update
```

---

### Post by rmcellig on 2010-11-18
This is what I get when I type in sudo apt-get update:

randy@randy-ubuntu:~$ sudo apt-get update
[sudo] password for randy: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
randy@randy-ubuntu:~$

---

### Post by sisco311 on 2010-11-18
> **rmcellig said:**
> This is what I get when I type in sudo apt-get update:

randy@randy-ubuntu:~$ sudo apt-get update
[sudo] password for randy: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
randy@randy-ubuntu:~$

Check if apt-get is running:
```
pgrep -l apt
```

If the above command does not return anything, then run:
```
sudo rm /var/lib/apt/lists/lock
sudo apt-get update
```

and try to install the software via Software Center. 

Otherwise post any error messages you get.

---

### Post by rmcellig on 2010-11-18
This is what I got:

randy@randy-ubuntu:~$ pgrep -l apt
2274 apt
2723 apt-get
3570 update-apt-xapi
4808 aptd
randy@randy-ubuntu:~$

---

### Post by sisco311 on 2010-11-18
> **rmcellig said:**
> This is what I got:

randy@randy-ubuntu:~$ pgrep -l apt
2274 apt
2723 apt-get
3570 update-apt-xapi
4808 aptd
randy@randy-ubuntu:~$

I'm sorry it's late here (or early :) 4:07AM) and your issue is not related to your original question. So, I think you should start a new thread with an appropriate title in the appropriate sub-forum. I'm sure, you will get better answers.

---

### Post by rmcellig on 2010-11-18
I agree. Thanks for reminding me and for all of your help . Being a newbie I really appreciate it!!

---

