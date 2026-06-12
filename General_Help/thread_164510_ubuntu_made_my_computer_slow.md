---
title: "ubuntu made my computer slow"
date: 2006-04-22
forum: General Help
---

### Post by greenwoodman on 2006-04-22
Im a total linux newb, but I was able to install ubuntu fine.  The problem is that it made my computer much slower than it was with windows.

the computer is a Compaq Evo D310 Microtower

I dont know anything else about the system because I dont know how to get system information with GNOME.

Is there a way that I can speed this up, like a defragmenter?  Also, I didn't really understand what the partition process did.  I copied all the files I needed from when I had windows, so if its still on the system, I could delete it to speed things up(?)

---

### Post by dermotti on 2006-04-22
You culd try try Xubuntu, its lighter and leaner.


[B]sudo apt-get install xubuntu-desktop
[/B]
when you are at the login screenm select XFCE instead of gnome.

---

### Post by Sef on 2006-04-22
> the computer is a Compaq Evo D310 Microtower

What is your GHz and ram?   If you don't have too much, then xubuntu would be better for you.  It's a lightweight window manager, so it doesn't use as many resources as Gnome.  From the terminal (Applications > Accessories > Terminal)

sudo apt-get update

sudo apt-get install xubuntu-desktop

> Is there a way that I can speed this up, like a defragmenter?

You don't need to defrag Linux.

> Also, I didn't really understand what the partition process did. I copied all the files I needed from when I had windows, so if its still on the system, I could delete it to speed things up(?)

Did you or the computer set up your patitions?

> I dont know anything else about the system because I dont know how to get system information with GNOME.

To find your ram, do this from the terminal:  'dmesg | grep -i ram' (without the quotes.)

For example mine says I have 524224 kilobytes of memory which is 524 megabytes

sef@jokat1:~$ dmesg | grep -i memory
[4294668.016000] Memory: 509108k/524224k available (1973k kernel code, 14592k reserved, 601k data, 288k init, 0k highmem)

---

### Post by IYY on 2006-04-22
Define "slow". This word can mean many things, and the solutions differ from one interpertation to the next. For example, if the interface is unresponsive, you might consider switching themes or just using a different window manager (or a different desktop enviorment). If you feel that moving and minimizing windows is not smooth enough, you could try installing Compiz (if you have a decent video card) and make it *much* smoother (and prettier). If your boot speed is slow, there is a nice thread on these forums that could do the trick.

---

### Post by dermotti on 2006-04-22
What if i'm slow? is there a way to slow the computer down to match my mental and physical capabilities?

---

### Post by greenwoodman on 2006-04-22
slow, meaning applications take a long time to work, I cant close applications (have to force quit), Web pages are impossible to use because the computer freezes whenever I scroll.

---

### Post by IYY on 2006-04-22
Which version of Windows were you running? How old is this machine? 

I have a PII from 98, and it's still much more usable with Ubuntu than what you describe...

---

### Post by greenwoodman on 2006-04-22
the computer is a celeron from 2002.

Can I upgrade to xubuntu using a CD of the iso image?

If I cant, could you describe more in depth how I do it on the computer?

---

### Post by dermotti on 2006-04-22
The easiest way is the way we described above. Do you you not have a fast internet connection?

---

### Post by greenwoodman on 2006-04-22
Its fast, but its wireless and I normally have to connect it using the networking manager.  It should work, but the connection is a little unreliable](*,)

---

### Post by dracule on 2006-04-22
I havd a 450mhz pIII processor and compared to windows 98 that looked like crap and ran slow, ubuntu runs quite nicely. I was really surprised because ubuntu is a lot more graphically intense than 98 so i was expecting it to get slower. but everything runs super fast (compared to 98) my only complaint is that moving the mouse across the screen makes the processor jump to 68%. but for a 450mhz machine, ubuntu is lightspeed.

---

### Post by z_diver on 2006-04-23
[QUOTE=greenwoodman]the computer is a celeron from 2002.

Can I upgrade to xubuntu using a CD of the iso image?

If I cant, could you describe more in depth how I do it on the computer?[/QUOTE]
I think the missing part of the equation was "Open a terminal" to run the commands given. In ubuntu this is usually gnome-terminal.  [COLOR="Red"]Applications > Accesories > Terminal.[/COLOR]

Here are the commands again.
```

you@somemachine:~$ [COLOR="Blue"]sudo apt-get update[/COLOR]

you@somemachine:~$ [COLOR="Blue"]sudo apt-get install xubuntu-desktop[/COLOR]
```
It's really that simple.  When you get to the login screen choose Options > sessions > xfce

Edit: I just looked up some specs for a D310 and it has a P4 2.4 ghz cpu with 640 mb or ram and a 80 gig drive.  If your system is like that, IT'S SOMETHING ELSE.  I don't think you need to run xfce.  Let's just figure out what the problem is.  Post back with more symptoms if you can.

---

