---
title: "Ubuntu 11.10 takes long time to load desktop after login"
date: 2011-12-06
forum: General Help
---

### Post by thomasmanalil on 2011-12-06
Hi All,
   I upgraded my Dell Inspiron 15R (2years old with no graphics card) to Ubuntu 11.10 from 11.04. 
Now machine takes a long time to load desktop after hitting login button. Login screen loads pretty fast but takes atleast 1-2 minutes to load desktop after that. I tried Ubuntu 3D/2D , but no success. 

Shut down also takes longer time than it used to take in Natty. 

please help.

---

### Post by phidia on 2011-12-06
Did you notice any error messages after the upgrade completed? Sometimes upgrading can cause problems, but it's hard to say without more info.
You might try in the terminal: > sudo apt-get update && sudo apt-get upgrade and see what that brings and and what effect it has. You say you have no graphics card-do you mean by that that it has onboard graphics? Obviously your expecting some video output so you have a gpu even if it isn't a separate add on card. If you think that could be the problem it would be good to know what type graphics are in the computer.

---

### Post by didinium on 2011-12-06
Or it could just be your computer itself is slow. You said it was old didnt youy.

---

### Post by oldtimer7777 on 2011-12-06
> **didinium said:**
> Or it could just be your computer itself is slow. You said it was old didnt youy.

Usually upgrading your entire system leaves a big mess in there.. Make sure to always clean out your system when you do one:

[https://debianhelp.wordpress.com/2011/08/02/how-to-maximize-system-performance-in-ubuntu/](https://debianhelp.wordpress.com/2011/08/02/how-to-maximize-system-performance-in-ubuntu/)

Try to do fresh installations when you can budget some time for the task.

---

### Post by thomasmanalil on 2011-12-07
I meant ,no separate card, i have an on board intel card. 
Installing the OS from scratch involves a lot of effort as i have to install lotsa softwares. I would prefer an upgrade.

---

### Post by thomasmanalil on 2012-01-23
Is there any way to enable verbose mode while login where i can see which all processes are loading and etc. hopefully i can figure out which one is taking more time.

---

### Post by xyzzyman on 2012-01-23
First step is to make sure ureadahead is working and have it rebuild its cache. First set your account to auto-login (System Settings->User Accounts) then at a prompt:

```
sudo rm /var/lib/ureadahead/*pack
```

Then reboot. Wait until it's been sitting on the desktop for a minute or two with no hard drive activity. Then very that it's recreated it's cache:

```
ls /var/lib/ureadahead
```

You should have multiple files ending in .pack

Now install bootchart [https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)

```
sudo apt-get install bootchart
```

Reboot, and wait 3-4 minutes after it's done finally booting and reading from the hard drive. (Running anything can make bootchart think it's still booting and not finish when it should.)

Then you'll have a nice .png image sitting in /var/log/bootchart. As it can be large in size, I'd recommend uploading to [http://www.imgur.com](http://www.imgur.com) or another free similiar site, and provide us the link so we can see it (The forums here like to resize it down automatically). This all will give us a nice graphical visualization of what's going on when and for how long.

As an example here is mine. I can get down to just 24 seconds (Which I love as it's a 3 year old core2duo 2.53Ghz and a basic 5400RPM hard drive) but it's close to doubled with everything I have auto-load:

[[IMG]http://i.imgur.com/b8tebl.png[/IMG]](http://imgur.com/b8teb)

---

