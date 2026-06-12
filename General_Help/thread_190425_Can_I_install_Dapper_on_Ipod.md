---
title: "Can I install Dapper on Ipod??"
date: 2006-06-06
forum: General Help
---

### Post by muzaki on 2006-06-06
Ok, straight to the point, I have 60 G Ipod.I think it will be very cool to be able to install dapper on it and still able to use it to play music(as usual ipod)....
Is there anyone here succeed it?Please tell me your way...
I dont mind to try it myself if anyone here can confirm that its reversible.
I mean, if the installation cause the ipod not function ,can i uninstall dapper, and some how(by going to the ipod maker place??) reinstall my ipod....

Thanks

---

### Post by dueyfinster on 2006-06-06
It would certainly be possible to install it (thats if its a windows vfat iPod), but to use it, without serious modification, no I don't think so. See [http://www.ipodlinux.org/]("http://www.ipodlinux.org/") for a better version! 

Also check out RockBox, I use it opn my Nano:
[http://www.rockbox.org/](http://www.rockbox.org/)

---

### Post by Ramses de Norre on 2006-06-06
I'm pretty sure dapper wont work, an ipod is pretty special hardware. But the ipodlinux project has succesfully ported a linux kernel to run on it.
You can try if you want though, you can always reinstall the firmware with a tool from the apple website [here]("http://www.apple.com/ipod/download/") and repartition the harddrive with any normal partitioning tool.

---

### Post by mlind on 2006-06-06
Rockbox is great, just try it out!

---

### Post by onesojourner on 2006-06-06
I cant imagine you could just run dapper on there. like stated above Ipodlinux is for you.

---

### Post by kb3hkg on 2006-06-06
You could probably get dapper running but you would have to use a different kernel at the least

---

### Post by Lunar_Lamp on 2006-06-06
Wait a second, I think you mean something completely different to what people here are suggesting.

Do you mean that you want to use your ipod as a USB hard drive with ubuntu OS on it - so that you can run ubuntu on a pc that boots from usb, off your ipod?  If so, I haven't a clue (as I don't have an ipod I dont know how it works) - but to my knowledge ipods aren't able to be used as portable usb hard drives very easily - which may throw a spanner in the works.

---

### Post by muzaki on 2006-06-06
> I think you mean something completely different to what people here are suggestin

yes completely...

I googled about Rockbox
> Rockbox is an open source replacement firmware for mp3 players
or ipodlinux...
I dont want to replace the firmware..What i want is that I can run ubuntu on a pc that boots from usb, off my ipod...
Its because i read an article about the succes of installing ubuntu onto usb.So as i use my ipod as HDD very often,I want to know if i install dapper,will i still be able to use my ipod as normal ipod?
> but to my knowledge ipods aren't able to be used as portable usb hard drives very easily
Its very easy indeed because when its mounted,then you can save data on it(as long as you dont rewrite the file system)

---

### Post by Ramses de Norre on 2006-06-06
Hmm the other pc needs to boot from the usb interface and it has to recognize your ipod as a bootable partition.. meaning you'll have to create an mbr in the first 512kB of your hard drive. And I think that's were the firmware is right now.
Maybe it's easier through a grub floppy image or something which can let you boot from a normal partition on your ipod with a bootable flag.

---

