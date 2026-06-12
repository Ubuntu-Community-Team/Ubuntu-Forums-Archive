---
title: "HELP! Loading of OS stopped, showing tiny white terminal in top corner...."
date: 2009-11-24
forum: General Help
---

### Post by Dooms_day on 2009-11-24
so basically i tried to boot up ubuntu netbook remix and BAM! the loading icon keeps spinning but nothing is happening, and there is a tiny (640x480) terminal in the top left corner, just chilling......


HOW THE HECK DO I GET MY DESKTOP BACK! some kidna restore feature i dont know about? thanks a lot i cant do anything on my netbook with this nonsense!

---

### Post by Dooms_day on 2009-11-24
UPDATE, if i type exit in the terminal, it brings me to the login screen, and when i log in, same thing happens, another terminal....WTH!

i'm pretty sure it has something to do with the default startup programs since thats what i last messed with, so does anyone know where a file with these programs are kept? i need to edit that file NOW! lol

---

### Post by cta16 on 2009-11-24
Try typing in 
```
gdm
```
in the terminal.

---

### Post by Dooms_day on 2009-11-24
```
** (gdm-binary:1692): WARNING **: Failed to acquire org.gnome.DisplayManager
** (gdm-binary:1692): WARNING **: Could not acquire name; bailing out
```
ran it as root

---

### Post by Dooms_day on 2009-11-24
alright i stop the gdm service, but when i try to start it, SAME THING HAPPENS

so i know its gdm now, i looked at all the defaults and files but cant find anything that will fix it

---

### Post by cta16 on 2009-11-24
Sorry, I pasted the wrong command. You should type in 
```
sudo /etc/init.d/gdm start
```
before you log in. Does that make any difference?

---

### Post by Dooms_day on 2009-11-24
no it makes no difference, but do you know where the default programs that start when it starts are saved? i might be able to fix it with that file

---

### Post by Greenwidth on 2009-11-24
Some have had trouble with graphics driver after recently upgrading to the new kernel from the repo: - mostly laptops/netbooks:
[http://ubuntuforums.org/showthread.php?t=1305459&page=23](http://ubuntuforums.org/showthread.php?t=1305459&page=23)

A quick read seems to suggest reinstalling the driver fixes the problem.

---

### Post by Dooms_day on 2009-11-24
that isn't my problem, the best way i can describe it is, you know all that loading text when linux is starting? it converted itself to a tiny window in the top left corner while the desktop was loading, and just stopped...all i see is a black gnome desktop, with the loading icon going infinitely and the white terminal taking up a forth of the screen, it hangs there and when i type exit in the terminal, i get a text only login, and from there running gdm just brings me back to the same spot, its gota be something with the default programs i run or something, is there anyway to reinstall UNR without loosing any installed programs? i could reset the default applications if those reset too, but i have a LOT of stuff installed that i want to keep

didnt update any drivers or anything before this happened, just messed with my desktop's settings

also i did try reinstalling gdm and nothing improves, so the problem isnt in that folder, if that helps

---

### Post by t0p on 2009-11-24
I don't know how to solve your problem.  Sorry.

*If* you decide to reinstall, you can save your files by booting from a live cd/live usb and moving files from the disk drive to a flash stick or similar.

---

### Post by Dooms_day on 2009-11-25
bump

i am kinda thinking about reinstalling, but daaamn i had so many programs installed

---

### Post by topraamen on 2009-11-26
Hey i just encountered the same problem and stumbled across this forum. Here is what i did as a work around... Log in using root and the gdm configuration for root is hopefully in still good. You should see the full functional gnome desktop, make a new user and give him admin rights. Then log in to new user, copy your stuff from the old user to the new user. 

Hope that helps!

---

### Post by JoelJohnson on 2010-01-05
Hey, I started having this same problem and ran into this while looking for a solution. I'm able to get into my desktop by typing "gnome-session" into the little white terminal. I created a new user to see if that works, and that user has the same problem. I've uninstalled my nvidia drivers (which didn't help), and I'm about to install the latest update from nvidia's website. Hopefully this helps.

Such a strange problem, and I can't seem to find a solution. I'll let you know if the new NVIDIA drivers work for me.

I'm using Ubuntu 9.10 64 bit on a Lenovo T61p.

update:
no luck with nvidia drivers for me :( uninstalled, tried 3 different versions (170, 180, 190) all to no avail.
Hopefully i'll figure this out.

---

### Post by sithlordkyle on 2010-01-26
I have this same problem right now!  Haha.  Can't find any help on the forums nor google.  Tis a shame.  Had this same issue with the desktop version of Karmic and netbook remix version.  I think Karmic is just broken.

---

### Post by JoshOrndorff on 2010-05-08
[SIZE=3]I've Solved This Problem!
[/SIZE] 
I also had the small white terminal in the top left after trying to add the notification area to my gnome panel and get my skype icon to display correctly down there.

I took several steps to solve the problem, and I'm not sure how many of them were or were not necessary so I'll tell the whole story and let someone more experienced sort out which details are necessary

1.  Remove gdm and the config files: ```
sudo apt-get purge gdm
```2.  Reinstall gdm: ```
sudo apt-get install gdm
```At this point I was prompted to put my install CD in the drive, and if I had one that probably would have worked fine, but I didn't have one.
3.  Ctrl+c to abort the install
4.  Edit software sources: ```
sudo gedit /etc/apt/sources.list
```Comment out any lines that refer to a cdrom.  For me there was only one line like that
5.  Reinstall gdm:  ```
sudo apt-get install gdm
```6.  Start Gnome:  ```
gnome-session
```This got my desktop background and desktop icons to display, but no panel.
7.  Ctrl+C to kill gnome-session
8.  Try the gnome panel: ```
gnome-panel
```I got an error that gnome-panel was not installed.  I guess I must have removed it along with gdm earlier.
9.  Reinstall the panel: ```
sudo apt-get install gnome-panel
```10.  start the panel: ```
gnome-panel &
```that amersand is important to be sure that you get your prompt back after the panel is started
11.  Start gnome: ```
gnome-session &
```at this point it looks like everything is working okay.
12.  Restart the computer: ```
sudo shutdown -r now
```

That did it for *me.*  I don't know what steps were and were not necessary.  Maybe I could have used synaptic to remove and reinstall packages to make it easier, but apt-get works out okay too&#12290; I couldn't find any solution in the forums so I figured I'd post this to get everyone started.

Good Luck.

-Joshy

---

### Post by searchfgold6789 on 2010-06-07
This works:
```

sudo apt-get remove gnome-panel gnome-session
sudo apt-get install gnome-panel gnome-session
gnome-panel &
gnome-session &
```

---

### Post by Vuk Matic on 2010-07-29
Hey o ve got a similar problem! BUT it cannot find gnome session on my computer and cannot install it either it says something to do with the E: drive? i have the live ubuntu cd so can i use that to fix this problem?

sorry for the late reply

---

### Post by Dooms_day on 2010-11-10
UPDATE: I disabled the default email client and that screwed everything up, heres a hint, DONT DO THAT on a distro like this

---

