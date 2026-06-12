---
title: "can't boot except with noacpi flag"
date: 2010-12-18
forum: General Help
---

### Post by Ahmed Kotb on 2010-12-18
yesterday ubuntu 10.04 hanged so i restarted it and i wasnt able to boot again all what i get is a blank screen with a blinking cursor...
also windows7 dont boot (hangs during loading)
after some googling i was able to boot only in linux by setting the noacpi flag during booting in grub but there was no internet connection (wired connection) i guess that noacpi is the reason ??

what i have tried :
[LIST]
[*]livecd: doesnt boot except with the noacpi flag and no internet connection
[*]reinstalling grub : doesnt solve the problem
[*]replace the power supply : nothing differ
[/LIST]

thanks in advance ...

---

### Post by hoooootz82 on 2010-12-19
I'm not sure what is causing this problem, but possibly editing grub to always have noacpi would help.

To do this, edit the file /etc/default/grub (may be different, as i am away from my linux machine right now)
```
gksudo gedit /etc/default/grub
```

You should see a line of kernel boot options, just add noacpi to the end of it like you would in grub. 
Then run something like 
```
sudo update-grub
```

As for the root of your problem, I cannot say what is causing it. If you post the content of
```
sudo lshw
```
i may be able to help. It could be a flaky motherboard/hard drive, but hopefully its something else.

---

### Post by Ahmed Kotb on 2010-12-19
thanks for your consideration 
i guess it is a hardware problem ..
coz when trying the recovery kernel it hangs at the line
```
isapnp : no plug and play devices found

```
also windows hangs in safemode at loading ClassPNP.sys

as i have said i can boot with noacpi but i dont think this is a solution as my net connection become disabled ..

attached the output of sudo lshw

thanks ..

---

### Post by Yellow Pasque on 2010-12-19
Something went wrong with the BIOS. I would suggest clearing it using the jumper on your motherboard if it's so equipped. You also should see if there are any BIOS updates available for your motherboard.

---

### Post by Ahmed Kotb on 2010-12-20
i tried clearing the bios settings and flashing it to the latest version but that also didn't help...

---

