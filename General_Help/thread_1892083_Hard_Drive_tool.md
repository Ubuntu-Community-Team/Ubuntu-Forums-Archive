---
title: "Hard Drive tool"
date: 2011-12-07
forum: General Help
---

### Post by aaronmarsh632 on 2011-12-07
Hi,

Ageess ago on my old computer I used 2 run 10.04 (i think off top of ma head) and if I connected a hard drive which had bad sectors it popped up a notification in the top-right corner to notify me. I have recently installed 11.10 on ma new computer and I have connected a hdd which I know definitly has bad sectors but it hasnt notified me.

If I remember correctly It used to say something along the lines of... 'One of your HDD's is failing bla bla'

Does anyone know what this tool was and how I can get it again? or If its already there how can I run it manually?

Thanks

NOTE: I know the HDD has bad sectors 'cos I ran a FULL sector test with Ontracks Easy Recovery pro on windows

---

### Post by westie457 on 2011-12-07
Try in the Software Center for gsmartcontrol

---

### Post by aaronmarsh632 on 2011-12-07
Hi, thanks for the reply.

I dont think this was the software i'm thinking of but it looks pretty kwl, Got about 10 HDD's that i'll run full tests with - thanks for sharing.

I tried connecting a HDD via the USB tho and it 'grayed' out the option to run tests - is that because its on the usb? if so is there a way around this?

Thanks

---

### Post by josephmills on 2011-12-07
> **aaronmarsh632 said:**
> Hi, thanks for the reply.

I dont think this was the software i'm thinking of but it looks pretty kwl, Got about 10 HDD's that i'll run full tests with - thanks for sharing.

I tried connecting a HDD via the USB tho and it 'grayed' out the option to run tests - is that because its on the usb? if so is there a way around this?

Thanks

there is a command from the terminal 

```
sudo fdisk -l 
```

this will show your hardrives that are connected. now mount the hard drive that is for the usb 
```
sudo mount /dev/WHATEVER /mnt/
```

can you now run the benchmarks ?

---

### Post by BC59 on 2011-12-07
If you open the Disk Utility from the dash, and check the disk from there, you can see if there are bad sectors. 

Choose SMARTdata to make the disk test and check or uncheck the button down left to be warned or not if there are problems on the disk

---

