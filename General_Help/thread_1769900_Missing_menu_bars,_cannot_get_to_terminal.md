---
title: "Missing menu bars, cannot get to terminal"
date: 2011-05-28
forum: General Help
---

### Post by mistergoomba on 2011-05-28
I just upgraded to Natty and I cannot access any of my menu bars. My mouse does not move any higher than the screen boundaries and I'm sure they're not set to auto hide. After doing some searching I found the following commands which I ran in a terminal on my Mac, controlling my Ubuntu machine through SSH.

```
martin@martin-desktop:~$ gnome-panel

(gnome-panel:2366): Gtk-WARNING **: cannot open display: 
martin@martin-desktop:~$ metacity --replace
Window manager error: Unable to open X display 

```

This is very frustrating and nothing I've been able to do through searching has worked. Any help would be greatly appreciated!

Thanks!

---

### Post by rocket0634 on 2011-05-31
I received a similar issue, after upgrading to Natty. I can get to the screen with a background- but other than that, all I get is a dropbox notice, and then.... nothing.
I can access the terminal with ctrl+alt+f1, and I was able to get firefox open through a link on the dropbox notice. However, what I don't understand is why the menu bars and everything are missing...

I've also notice that I have a "pae" version of the Natty image on Grub. Does that have any influence on how Ubuntu works? The generic image is also in "Previous Linux Images" and both versions give me a blank screen.

Also- just as a note, I'd like to say that this is my first post on the forums, and I just registered for the site today. However, I've been using Ubuntu for quite a while now, and haven't had trouble until the 11.04 update. Speaking of which, I lost a really tricky file in the installation- Bcm43-fwcutter. So this cuts my access to the internet. (Of course, I could plug it in- but my router is upstairs, and my broken laptop screen connected to a desktop display is downstairs, which is rather inconvenient for me.) Is it possible that this error was caused by me losing the bcm43xx firmware? Or maybe I shut down after it gave me the update error for bcm43-fwcutter?
I was just wondering if it was okay for me to post here, as it isn't my topic, but I'm having the same problem. I'll continue to try and troubleshoot and will update if I find a solution, but if anyone out there finds a solution first, I'd be grateful if you posted. Thanks, and sorry for any inconvenience of this post.

Edit- Well, this problem is basically solved, and I figured out that unity and gnome-panel weren't running. The only problem I have left is the bcm43xx driver, which this isn't the post to be asking for that anyway.

---

### Post by mistergoomba on 2011-05-31
I was able to get to the terminal finally by right clicking the desktop, selecting "Create Launcher" and using the command "gnome-terminal"

That got me into the terminal where I was able to use other solutions found throughout the site. Using the command "gnome-panel" restores your menu bars :}

---

### Post by garvinrick4 on 2011-05-31
> I've also notice that I have a "pae" version of the Natty image on Grub.  Does that have any influence on how Ubuntu works? The generic image is  also in "Previous Linux Images" and both versions give me a blank  screen.32 bit with 4 or more gig of Ram uses pae kernel: Do not worry.
> The only problem I have left is the bcm43xx driver, which this isn't the post to be asking for that anyway.     Just use Synaptics to install what your broadcom card is: OPen Synaptics and type in bcm:
  install what your driver is.
```
sudo lshw -C network 
```**Above to find your cards and drivers: *Below is Synaptics views just a few samples: Click on screenshots.
So b43-fwcutter and your driver should do it.

---

### Post by wildmanne39 on 2011-05-31
> **mistergoomba said:**
> I was able to get to the terminal finally by right clicking the desktop, selecting "Create Launcher" and using the command "gnome-terminal"

That got me into the terminal where I was able to use other solutions found throughout the site. Using the command "gnome-panel" restores your menu bars :}
Hi, so you are able to get into ubuntu classic now? Can you get into ubuntu that is the unity interface. If not run
```
lspci
```in a terminal and post the results here.

---

### Post by rocket0634 on 2011-06-01
> 32 bit with 4 or more gig of Ram uses pae kernel: Do not worry.

Actually, I have a 64bit computer. The problem is that the Ubuntu version I have is 32bit. I kinda want to switch it so it's more compatible with my computer, but I'm afraid that It'll take a bunch of installing, reinstalling, uninstalling, and downloading. (Mostly the downloading) /off topic

> Just use Synaptics to install what your broadcom card is: OPen Synaptics and type in bcm:
install what your driver is.
Code:
sudo lshw -C network
**Above to find your cards and drivers: *Below is Synaptics views just a few samples: Click on screenshots.
So b43-fwcutter and your driver should do it.

Yeah, thanks, but I solved that problem already. I had to uninstall the current files I had and reinstall them, and then go into jockey to activate them. (I had to drag my modem down here to do it, but it worked nonetheless) /off topic again

Thanks for the help, in any case.

---

