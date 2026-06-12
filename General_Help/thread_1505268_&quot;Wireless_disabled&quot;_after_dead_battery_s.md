---
title: "&quot;Wireless disabled&quot; after dead battery shutoff"
date: 2010-06-08
forum: General Help
---

### Post by Helios747 on 2010-06-08
Hello,

I have 2 batteries for my laptop. The one I use at home only has about 15 minutes or so on it. If I leave it unplugged for too long, naturally it dies.

If this happens, half of the time when I reboot it, it says "wireless disabled" and I can't seem to find any way to re-enable it. So I bite the bullet and do an OS reinstall. (This isn't TOO big of an issue as my data is on my /home partition)

It's still annoying. Anybody know what could cause this?

Also, this doesn't happen when I shutdown properly or hard reset.


I have a Macbook Aluminum (5.1)

---

### Post by dcstar on 2010-06-09
> **Helios747 said:**
> Hello,

I have 2 batteries for my laptop. The one I use at home only has about 15 minutes or so on it. If I leave it unplugged for too long, naturally it dies.

If this happens, half of the time when I reboot it, it says "wireless disabled" and I can't seem to find any way to re-enable it.
........

So what happens after you reboot?

---

### Post by Helios747 on 2010-06-09
Nothing. A proper restart still keeps the network manager applet at "wireless disabled"

---

### Post by dcstar on 2010-06-10
> **Helios747 said:**
> Nothing. A proper restart still keeps the network manager applet at "wireless disabled"

Laptops usually have FN keys to turn on and off the wireless hardware, is it actually on?

---

### Post by Helios747 on 2010-06-10
My MacBook has no method of enabling the wifi from keyboard.


The interesting thing, however, is that when I remember using OS X, there WAS a way to flip off wifi from the menubar to save juice. Maybe Ubuntu is doing something that is triggering that little switch?

---

### Post by dcstar on 2010-06-10
> **Helios747 said:**
> My MacBook has no method of enabling the wifi from keyboard.


The interesting thing, however, is that when I remember using OS X, there WAS a way to flip off wifi from the menubar to save juice. Maybe Ubuntu is doing something that is triggering that little switch?

Possible, because a dead battery would not have shutdown Ubuntu properly then it is possible there is some sort of lock file/corruption preventing the hardware being re-enabled (or Ubuntu "assumes" it is already enabled).

Where that may be I don't know.

---

### Post by something_clever on 2010-10-19
this just happened to me not 15 minutes ago. i have no idea whats going on. this is kind of ridiculous to be honest.

my battery died before i could grab my power cable and when i turned it back on wireless was disabled. if i hit the wireless key (to turn wireless on and off) there is no response. if i right click the wireless icon in the tray i can click the "enable networking" option but it doesn't show any networks (there are usually between 4 and 5 networks that show up here in my apartment). I've tried to restarted my computer several times, and disabled and re-enabled my networking several times to no avail. I'm currently posting this from my old as dirt desktop which is hardwired and i would really prefer to get back on my shiny new laptop so does any one have any idea how to fix this?

---

### Post by BevS97 on 2010-10-27
This is happening to me,  you need to edit the file

var/lib/NetworkManager/NetworkManager.state

and change them all back to True.

What I want to know, is how do I stop it happening.    it's my DD's laptop and she frequently leaves it to go flat,  or closes it without powering it down.  This was never an issue until I upgraded to 10.04,   but I am now having to fix her network everytime she wants to use it.

---

