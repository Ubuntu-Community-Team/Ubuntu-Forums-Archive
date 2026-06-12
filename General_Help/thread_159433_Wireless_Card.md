---
title: "Wireless Card"
date: 2006-04-12
forum: General Help
---

### Post by Ignite_nz on 2006-04-12
I just installed a wireless card into my Ubuntu machine, I use command line becuase my Ubuntu machine is my DHCP/FTP server, and I have no idea how to install the drivers for a new card. The details are as follows:

New Card: Gigabyte GN-WP01GS (uses a RaLink Chipset I believe)

When I type lspci, the one that sticks out is the following: 

```
0000:0c.0 Network Controller: RaLink: Unknown Device 0301
```

If someone could tell me what to do that would be great, then I would know maybe how to instlall other hardware next time too :)

---

### Post by truNWA on 2006-04-12
I would get Automatrix if you havent already. It can install and app. that allows you to use the windows drivers for your card. If you don't want to do that, i'm sure one of these fine fellows could provide you with the terminal wayv(if you're not afraid of the terminal).

Automatrix- [http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)

---

### Post by Ignite_nz on 2006-04-12
You didn't read my post properly - I use command line Ubuntu (aka server install). I need to know how to do it through command line please. I will only install GNOME as a last resort.

---

### Post by Ignite_nz on 2006-04-13
*bump*

---

### Post by MrMojoRising on 2006-04-13
ndiswrapper?

---

### Post by carlos_silva on 2006-04-13
i think your card uses the Ralink rt61 chipset. try this: [http://elonen.iki.fi/code/misc-notes/debian-rt61/](http://elonen.iki.fi/code/misc-notes/debian-rt61/)

---

### Post by Stone123 on 2006-04-13
There is howto on ubuntu. 
So no need to google about it and get some other howtos. 

[http://ubuntuforums.org/showthread.php?t=132980&highlight=rt61](http://ubuntuforums.org/showthread.php?t=132980&highlight=rt61)

And when your done all you need to do is to link it to run level you wish , or just read my post about it in the thread.

---

### Post by Ignite_nz on 2006-04-13
[QUOTE=Stone123]There is howto on ubuntu. 
So no need to google about it and get some other howtos. 

[http://ubuntuforums.org/showthread.php?t=132980&highlight=rt61](http://ubuntuforums.org/showthread.php?t=132980&highlight=rt61)

And when your done all you need to do is to link it to run level you wish , or just read my post about it in the thread.[/QUOTE]

I tried that but when it came to the ```
sudo make all
``` it said that the command make was not found? What do I do here.....

---

### Post by taurus on 2006-04-13
I guess you have to install build-essential first before you can run make then...  Click on Applications -> Accessories -> Terminal and type
```

sudo apt-get install build-essential

```

---

### Post by Stone123 on 2006-04-13
since you are on the server there is a answer in the thread :

[http://ubuntuforums.org/showpost.php?p=857082&postcount=13](http://ubuntuforums.org/showpost.php?p=857082&postcount=13)

There you go ,all from terminal mode.

And then link it to run level as i posted or ln it you self.

And next time just read the thread.

I hope this helps

---

