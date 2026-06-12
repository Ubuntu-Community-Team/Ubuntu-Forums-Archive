---
title: "Power Iso equavalent in Ubuntu"
date: 2011-04-25
forum: General Help
---

### Post by cblnchat on 2011-04-25
Is there a power iso equavalent in Ubuntu?  A friend of mine gave me an .iso game that only works with power iso.  And i dont know of any in ubuntu.  

Thanks

---

### Post by TeoBigusGeekus on 2011-04-25
You can mount it via the command line.
First create a folder in which the image will be mounted
```
sudo mkdir /media/isofolder
```
and then mount the image
```
sudo mount -o loop /path/to/image/imagename.iso /media/isofolder
```
After you're done, you can unmount the image
```
sudo umount /media/isofolder
```
and delete the mount folder if you like
```
sudo rm -r /media/isofolder
```

---

### Post by bodhi.zazen on 2011-04-25
Or you can use /media/iso or /mnt as temp mount points (for those who are lazy enough not to want to make a directory and then remove it).

If you want a graphical interface, there are several.

gisomount =)

[https://launchpad.net/gisomount](https://launchpad.net/gisomount)

---

### Post by bluTaz on 2011-04-25
you can try out [cdemu]("http://cdemu.sourceforge.net/"). Its a panel applet and has worked well for me thus far. If your ok with using its ppa:

```
sudo add-apt-repository ppa:cdemu/ppa
```
```
sudo apt-get update && sudo apt-get install gcdemu cdemu-daemon
```
You will need to add it to one of your panels by right clicking it ---> Add to Panel..., look through the applets and double click gcdemu.

it didn't work for me until rebooting, guess the daemon needs to start up. not sure how to load it manually so... 
```
sudo reboot
```

---

### Post by cblnchat on 2011-05-28
> **bodhi.zazen said:**
> Or you can use /media/iso or /mnt as temp mount points (for those who are lazy enough not to want to make a directory and then remove it).

If you want a graphical interface, there are several.

gisomount =)

[https://launchpad.net/gisomount](https://launchpad.net/gisomount)

Yea i prefer graphical interfaces...its just easier for me.  I got it off of the software center...it got a bad review but ill give it a shot.

Thanks

> **bluTaz said:**
> you can try out [cdemu]("http://cdemu.sourceforge.net/"). Its a panel applet and has worked well for me thus far. If your ok with using its ppa:

```
sudo add-apt-repository ppa:cdemu/ppa
``````
sudo apt-get update && sudo apt-get install gcdemu cdemu-daemon
```You will need to add it to one of your panels by right clicking it ---> Add to Panel..., look through the applets and double click gcdemu.

it didn't work for me until rebooting, guess the daemon needs to start up. not sure how to load it manually so... 
```
sudo reboot
```

I did that and it didnt work...and ive figured out how to compile from source, but that wont work either...i use the configure command and it eventually get an error saying that i need pygtk past version 2.0. so i downloaded the thing for that and tried to compile THAT from source and it wont get past the configure either cause it says it cant find the Python headers..whats going on?

Thanks

---

