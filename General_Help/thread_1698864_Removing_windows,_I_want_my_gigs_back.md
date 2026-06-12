---
title: "Removing windows, I want my gigs back"
date: 2011-03-02
forum: General Help
---

### Post by unbuntunewb on 2011-03-02
Hello,

I am so scared to attempt this but I want windows gone from dual boot and to reclaim the 100 gigs it is taking up.

here is what I see when I open gparted
[http://bayimg.com/kAejiaAdD](http://bayimg.com/kAejiaAdD)

where is windows and how do I get rid of it leaving everything else intact. I dont care if grub stays I just want windows out.

Thank you

---

### Post by mikewhatever on 2011-03-02
Windows is the ntfs partition, /dev/sda1. You might also want to remove the second swap partition, /dev/sda5. ;-)

---

### Post by unbuntunewb on 2011-03-02
I am not sure about these partitions and what to do with them and I really like how I have my system set up so I dont want to mess with it and possibly lose my ubuntu. Can you, or someone, walk me through it in super layman's terms? Just assume I know nothing because it is not far from the truth.

thank you!

---

### Post by MrRichard on 2011-03-02
[LIST=1]
[*]Go to System->Administration->Gparted
[*]After it's done scanning your hard drive(s) Select the NTFS partition (this is the partition to the very left). 
[*]Right click it and select delete. Now you should have this grey area in the deleted partition's place. 
WHOOPS: you must use your Live CD/USB to alter the largest partition on your computer. So please reboot into a Live Ubuntu CD/USB before you proceed.
[*]Move over to the largest partition. Right click and select "move/resize" and slide the rectangle so it fits as much space as possible. 
[*]Click okay and then the check mark above to start the process of getting your disk space back!
[/LIST]

By the way, as long as you are in Ubuntu and doing this process, it's impossible to delete Ubuntu's partition. Although, I do recommend backing up your most dear files whenever you alter your hard disk like in this case. You never know when there may be a power failure :)
Can you follow those steps?

---

### Post by unbuntunewb on 2011-03-02
I can follow that, what about the second swap partion though? Also thank you.

One more thing Im concerned about is that the windows partition has is flagged as "boot" is that wrapped up with ubuntu and its ability to boot from the HD?

---

### Post by MrRichard on 2011-03-02
Don't worry about the flagged Windows partition, once Ubuntu is installed, it overwrites Windows bootloader (the thing that chooses which operating system you're going to boot into).

To update the bootloader after resizing all of your partitions, open up a terminal by going to Acessories->Terminal and enter the following:
```
sudo update-grub
```
It will ask for a password, this is the same as your login password. If you see that there are no asterisks as you type (****), don't worry, this is perfectly normal. 

If your wondering, "sudo" gives you the privilege of changing important system files and "update-grub" is the command that, well, updates GRUB (Ubuntu's bootloader).

---

### Post by unbuntunewb on 2011-03-02
Should I do the same thing for the second swap, sda5? that is another few gigs I could free up

[http://bayimg.com/kAejiaAdD](http://bayimg.com/kAejiaAdD) this is my partitions

---

### Post by unbuntunewb on 2011-03-02
> **MrRichard said:**
> 
[LIST=1]
[*]Go to System->Administration->Gparted
[*]After it's done scanning your hard drive(s) Select the NTFS partition (this is the partition to the very left).
[*]Right click it and select delete. Now you should have this grey area in the deleted partition's place. 
WHOOPS: you must use your Live CD/USB to alter the largest partition on your computer. So please reboot into a Live Ubuntu CD/USB before you proceed.
[*]Move over to the largest partition. Right click and select "move/resize" and slide the rectangle so it fits as much space as possible.
[*]Click okay and then the check mark above to start the process of getting your disk space back!
[/LIST]


so do I do the whole thing from the live disc/usb?

---

### Post by jwcalla on 2011-03-02
I think it would be best to keep your /dev/sda5 as swap and then extend your /dev/sda6 all the way over to /dev/sda5 to pick up that extra space plus some unallocated megs.  However, it looks like your system is mounting /dev/sda7 for its swap space so you might have to adjust your /etc/fstab to use /dev/sda5 for swap instead of /dev/sda7.  But I don't know what else you have to do to change swaps around.

---

### Post by MrRichard on 2011-03-02
> **unbuntunewb said:**
> Should I do the same thing for the second swap, sda5? that is another few gigs I could free up

[http://bayimg.com/kAejiaAdD](http://bayimg.com/kAejiaAdD) this is my partitions

Yes you can,just make sure that you're using the live CD/usb to resize Ubuntu's ext4 partition (the largest one).
And yes, it would be best to do this all with the live CD.

---

### Post by unbuntunewb on 2011-03-02
what is the benefit of using the live cd?

---

### Post by jwcalla on 2011-03-02
> **unbuntunewb said:**
> what is the benefit of using the live cd?

I'd be surprised if you could modify that partition while the system is loaded (since it's on the same partition).  I don't think it can be resized while mounted.  In fact it should be locked in GParted.

---

