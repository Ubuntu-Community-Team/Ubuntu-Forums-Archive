---
title: "retain the changes done to live usb"
date: 2010-11-29
forum: General Help
---

### Post by ydristi on 2010-11-29
some days ago i lost my hard disk ,so i installed ubuntu to a usb using usb startup disk creator ...
there was an option to specify memory to save the changes 
i specified a 4 gb memory and everything went fine .
i then booted with it .i installed some softwares & tweaked a bit.
but when i tried to install that into hard disk of my friend's computer it installed the default ubuntu .
any of the applications that were installed to the live usb was not present 
so is there a way to get that applications to the new install from the usb??
 thanks in advance

---

### Post by Hippytaff on 2010-11-29
You can use remastersys to make a liveCD from the modifiied ubuntu set-up on your usb pen (or startup disc creator I think). But I don't think you can just install the persistent live USB as is, you need to make a new iso out of it :-)

---

### Post by ydristi on 2010-11-29
thanks hippytaff 
but  i h've given half of the space (ie 4gb out of 8gb) 
so remastersys can't operate 
does any one know a tool to convert a live usb to live cd?

---

### Post by C.S.Cameron on 2010-11-29
I think remastersys is it, but you can mount casper-rw and resync stuff out of it.

---

### Post by dcstar on 2010-11-30
> **ydristi said:**
> 
...........
any of the applications that were installed to the live usb was not present 
so is there a way to get that applications to the new install from the usb??
 thanks in advance

Copy the files from the USB /var/cache/apt/archives folder into the same place on the new system, then they will not have to be downloaded when you install them.

---

