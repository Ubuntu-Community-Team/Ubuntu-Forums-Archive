---
title: "synaptiks will not auto start at login"
date: 2011-10-19
forum: General Help
---

### Post by Jaibo on 2011-10-19
Hi, I've trawled the forum, but couldn't find any help for this specific problem.


I'm using Ubuntu Lucid Lynx on a Dell Studio 1735 laptop. I prefer to use a mouse, and therefore I'd like to disable the touch-pad entirely. 

I installed Synaptiks, and it does what I need, but it will not save the settings, meaning every time I boot up, I have to run Synaptiks  manually, in order to turn the touch-pad off, which is getting rather irritating.
The settings are all ticked in Synaptiks, so I don't know why it won't run after login.

Whenever I try and run Synaptiks, I always have to click on it twice, in order for the program to start, plus the icon for the program is just a blank icon, not sure if that's right?

Any help, or alternative methods for disabling touch-pad, appreciated. Please bear in mind, I'm a Linux noob though!

---

### Post by fullerenedream on 2011-10-20
I'm having the same problem with Synaptiks - it won't save my settings and it won't start at login. It's also crashing several times a day! :P

---

### Post by Jaibo on 2011-10-22
Anyone please?

---

### Post by xapu69 on 2011-10-22
Hello!

I had exactly the same problem as you. I had to click twice and the changes dissapeared when I reboot.

I fixed it doing this:

1.- Open Synaptiks as you usually do (click twice)
2.- Change the settings the way you want and then click apply (and then yes)
3.- Close it
4.- Open a terminal and execute: syntaptikscfg save
5.- Go to System > Startup applications (or look for it in start menu)
6.- You will see Synaptikscfg init, well, BEFORE it, create a new row. In command, type this: synaptikscfg load
7.- Reboot
8.- ....
9.- Profit! :p

It works with me, I hope it helps!

---

### Post by Jaibo on 2011-10-24
Hi Xapu69, thanks for your help, but it's still not working for me.

I can only get to start up applications via control center, I don't know any other way, and when I add the 6th stage you posted, it still does not save for login after I reboot.

Is there another method of adding this command please?

---

### Post by samopn on 2012-03-23
Hi Jaibo
 
Did you ever get to the bottom of this? I have the same problem
 
Cheers
 
Sam

---

### Post by Jaibo on 2012-03-24
> **samopn said:**
> Hi Jaibo
 
Did you ever get to the bottom of this? I have the same problem
 
Cheers
 
Sam

Hi samopn, 

no I never got this working, I can still only turn off the touchpad by manually going into synaptiks, and I still have to click on synaptiks twice. I cannot get it to work at boot, to the point I **got so sick of it, that I gave up using Ubuntu and now boot into Windows.** If I could get this working I would use Ubuntu ...
I couldn't get xapu69's solution to work as I'm not adept anough at using Ubuntu in order to use "the terminal" - I need a "dummies" guide. :(

Please really need help on this!

---

### Post by DGINSD on 2012-11-30
> **Jaibo said:**
> Hi, I've trawled the forum, but couldn't find any help for this specific problem.


I'm using Ubuntu Lucid Lynx on a Dell Studio 1735 laptop. I prefer to use a mouse, and therefore I'd like to disable the touch-pad entirely. 

I installed Synaptiks, and it does what I need, but it will not save the settings, meaning every time I boot up, I have to run Synaptiks  manually, in order to turn the touch-pad off, which is getting rather irritating.
The settings are all ticked in Synaptiks, so I don't know why it won't run after login.

Whenever I try and run Synaptiks, I always have to click on it twice, in order for the program to start, plus the icon for the program is just a blank icon, not sure if that's right?

Any help, or alternative methods for disabling touch-pad, appreciated. Please bear in mind, I'm a Linux noob though!

Here's the solution I employed and my problem was exactly as you stated in your original post.

Open up Gedit and create a document, in this document place the following

```
#!/bin/bash
sleep 10
synaptiks
synaptikscfg init 
```

Save this document in your home folder as start_synaptiks.sh and exit gedit, then open a terminal (fear not the terminal it is your best friend, press <ctrl> <alt> <t> ) and execute this command which will make the document you created executable.

```
chmod +x start_synaptiks.sh
```

Next open up start up applications and click on the add button. In the pop up window name your start up application I named mine Synaptiks Start. 

In the command field enter the path to the script you wrote earlier in my case it reads /home/david/start_synaptiks.sh

The last field give a description of your start up, then click the save button. Make sure the check box next to your new start up is selected and click close.

Note if there is another synaptiks entry you may want to uncheck it as this should take care of everything.

Some visual aids. I also have another easy script for a key combo to turn off the touchpad, if your interested let me know.

[IMG]http://s19.postimage.org/s8g8gkqxf/synaptiks_start_up.png[/IMG]

---

### Post by ilmix on 2013-04-05
Script works perfectly for me, is there any specific reason you added ```
sleep 10 
``` ?

---

