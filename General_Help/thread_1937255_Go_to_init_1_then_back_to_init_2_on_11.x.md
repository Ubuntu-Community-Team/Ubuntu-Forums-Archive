---
title: "Go to init 1 then back to init 2 on 11.x"
date: 2012-03-07
forum: General Help
---

### Post by CaseyC on 2012-03-07
I am having trouble at the bash... im a noobie by the way. What I am doing at this point might not make sense, but I am learning by experimenting. 

If i sudo init 1, the TUI comes up. But if i want to return to the GUI i type in sudo init 2... and the screen goes black and never returns to the GUI.. 

I have ran startx although from what I understand this isnt the same. 

Any thoughts?

---

### Post by raja.genupula on 2012-03-07
i think its runlevel  5 for Ubuntu
[http://en.wikipedia.org/wiki/Runlevel#Ubuntu](http://en.wikipedia.org/wiki/Runlevel#Ubuntu)

---

### Post by CaseyC on 2012-03-07
When I first open up bash this is what I typed. 

```
casey@ubuntu:~$ su
Password: 
root@ubuntu:/home/casey# runlevel
N 2
root@ubuntu:/home/casey# init 1
```

Then I press Enter, which it then enters single user TUI mode. Once I enter there he is what I typed and what I am presented with. 

```
root@ubuntu:~# runlevel
1 S
root@ubuntu:~# init 5
```

Now in the VMWare machine the screen goes black and never returns.. Also using 11.10.



Edit: 

My main reason for this is because I want to set my default runlevel to 1 and simply boot into a shell, and if I want I can change over to a GUI. Trying to force myself to delve deeper into the bash and leave the GUI alone unless needed.

---

### Post by CaseyC on 2012-03-08
Bump. 

Anyone else have anything to through in the thinking pot today :) would love to see this one solved. Anything is more than welcome.

---

### Post by Habitual on 2012-03-08
I usually type "exit" after an init 1 session to return to a normal boot.

Let us know...

---

### Post by CaseyC on 2012-03-08
Attached is a screenshot while I am in init 1. Here are the steps I took that got me there.  

1. Boot the machine into GUI, typed in su in the term, gave it the password. Then entered init 1. 

2. It then asked for the root password for maintenance, so I typed the root password in. 

3. As root I then typed in exit, which it hangs on either checking battery state, or the next step behind that (it says checking battery state, although it returns the OK code). 


I didn't boot straight into init 1, but into the GUI then entered init 1 and trying to return back to the GUI. 

Before it would go black and do nothing when typing init 2-5, but when typing exit, it hangs after trying to do something... 


Please see attached image.

---

### Post by jerome1232 on 2012-03-08
Wouldn't removing gdm work? It should just boot you into a commandline without gdm, from which you can startx if you ever find yourself in need of a gui.

---

### Post by CaseyC on 2012-03-08
I dont think that I have gdm installed, although I am new to Linux I might be mistaken lol. 

See attachment for bash info.

---

### Post by jerome1232 on 2012-03-08
Unless you removed it, it's there. It's the graphical login screen for Gnome.

---

### Post by CaseyC on 2012-03-08
I never removed it, I'm on 11.10 idk if it comes with that or something else.

Although I was able to apt-get install gdm and get the package, rebooted, and the login screen changed. 

But then tried to init 1 then return back to init 2 and/or gdm and didn't work. startx does return me to a GUI, but logged in as root and under runlevel 1 still.

---

### Post by jerome1232 on 2012-03-08
O.o, I must be behind the times, are they really using a different one now? I'm not sure why you installed gdm if it wasn't already installed though, you just need to figure out what display manager you are using and remove it.

I'm really surprised if they aren't using gdm as the default, you are using Gnome(Unity or Gnome-shell) right?

---

### Post by CaseyC on 2012-03-08
Unity desktop. Although I am fond of the past desktop environment, I might as well give this one a two week trial run before going back :) ..

My theory is that when i launch into the GUI from initial boot (init 2 from what the runlevel states), is that when I transition to init 1, it either doesn't completely kill all processes that are not suppose to run in runlevel 1 when coming from runlevel 2, or when launching init 2 it hangs trying to start a certain process. 

Is there an error log I can view to see what is going on perhaps?

---

### Post by CaseyC on 2012-03-09
I also wanted to point out I was using this in VMWare Workstation, although I don't have any evidence that it could be related, but does anything think this might be a virtual machine issue?

---

