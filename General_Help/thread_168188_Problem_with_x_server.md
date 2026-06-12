---
title: "Problem with x server"
date: 2006-04-30
forum: General Help
---

### Post by emkay84 on 2006-04-30
Hi guys
I encoutered a problem as after I'm finishing installing the ubuntu on my dell inspiron 6400 laptop,this massage come out:

>  Failed to start the X server (your graphical interface) It is likely that it is not set up correctly. Would you like to view the x server outputto diagnose the problem

and 

> Fatal service error: no screen found

and

> The x server is now disabled. Restart the GDM when it is configured correctly

I have tried this solution that i take from somewhere in this forum but  the problem still occured:

> dpkg -reconfigure -phigh xserver-xorg

the graphic card is ati radeon x1400 256mb, and i've download the driver software from ati website but i dont know how to install it .

hope someone can help
thanks you.:???:

---

### Post by cilynx on 2006-04-30
Check out the ATI bin drivers wiki:

[https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI]("https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI")

---

### Post by r4ik on 2006-04-30
Try,

sudo dpkg-reconfigure xserver-xorg

Hit enter and follow instructions.
Under section "Device" change "ati" to "vesa"

After that,

sudo /etc/init.d/gdm stop     =>enter
sudo /etc/init.d/gdm start     =>enter

Good luck !

---

### Post by tringger on 2006-05-02
That fix worked like a charm. Thank you r4ik. Now it's time to learn what exactly I did...Can't wait!

---

### Post by cilynx on 2006-05-02
Just to be clear:

This fix switches away from using drivers that allow use of any neat things about the ATI card.  The VESA driver is a good productivity system driver as well as a good fallback.  If you want to do Cool Graphic Stuff (tm), you need the binary drivers.

---

