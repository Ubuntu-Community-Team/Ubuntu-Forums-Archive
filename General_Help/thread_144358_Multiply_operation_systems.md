---
title: "Multiply operation systems???"
date: 2006-03-14
forum: General Help
---

### Post by baysl on 2006-03-14
First I installed winXP and then I installed ubuntu.
When I turn on the PC it boots ubuntu avtomatic.
I cant choose between operating systems.

How do I make this right, so I can choose between operating systems
on startup?

---

### Post by Jason_25 on 2006-03-14
You'll need to edit grub
```

sudo nano /boot/grub/menu.lst

```
There are some examples in there.

---

### Post by baysl on 2006-03-14
I am a begginer with this operating system,
so can you please tell me where to write this code, please...

---

### Post by Jason_25 on 2006-03-14
Applications > accessories > terminal

I've long wondered why the developers chose it to be hidden away.  It's not like you can get away without it.  Paste the line in the terminal and it will start nano, a text editor.

Append something like this to the end of the file
```

title           Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```
You may need to change the root section to reflect your setup.  Then ctrl-o, then enter to save.  Then ctrl-z to quit.

---

### Post by AndyCooll on 2006-03-14
Or if your prefer a text file to work with, at the command line type:
```
sudo gedit /boot/grub/menu.lst
```

In that file are a number of options for configuring the boot-up process. One of them might be to alter the time you have before the selection menu disappears and a default option is made.

As Jason has just indicated, if at the bottom of this list an entry doesn't appear like the one he has displayed then you'll need to add it. Save it and reboot.

On reboot there should then be a delay while you choose which OS you want to boot into. If no selection is made after 10 seconds (or whatever you've altered it to) then it will default to Ubuntu

:cool:

---

