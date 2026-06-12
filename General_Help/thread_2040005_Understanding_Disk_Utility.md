---
title: "Understanding Disk Utility"
date: 2012-08-10
forum: General Help
---

### Post by Shadius on 2012-08-10
Hey everybody! :)

I have a 1 TB HDD and I was using Disk Utility to view the S.M.A.R.T test results to basically check the health of the drive. Some things are puzzling me though. It's a SATA HDD, but Disk Utility is showing the connection type as ATA? Shouldn't it be showing it as SATA? Also, the location shows PATA? These readouts are confusing to me. Please help me understand. 

I've attached the screenshot. 

Thanks in advance.

---

### Post by dcstar on 2012-08-10
> **Shadius said:**
> Hey everybody! :)

I have a 1 TB HDD and I was using Disk Utility to view the S.M.A.R.T test results to basically check the health of the drive. Some things are puzzling me though. It's a SATA HDD, but Disk Utility is showing the connection type as ATA? Shouldn't it be showing it as SATA? Also, the location shows PATA? These readouts are confusing to me. Please help me understand. 

I've attached the screenshot. 

Thanks in advance.

ATA
Serial ATA
Parallel ATA

Look up the terms on the Internet.

---

### Post by oldfred on 2012-08-10
Do you have BIOS set to legacy IDE mode not AHCI?

---

### Post by Shadius on 2012-08-10
> **oldfred said:**
> Do you have BIOS set to legacy IDE mode not AHCI?

Could you point me to where exactly in the BIOS that would be found?

---

### Post by oldfred on 2012-08-10
Everyone's BIOS is different. Attached is when I was still running XP which was from before AHCI and is difficult to change. But my new SSD needs AHCI, so finally I stopped booting XP. :) 
Mine now says AHCI where is shows IDE in attached.

---

### Post by Shadius on 2012-08-10
> **oldfred said:**
> Everyone's BIOS is different. Attached is when I was still running XP which was from before AHCI and is difficult to change. But my new SSD needs AHCI, so finally I stopped booting XP. :) 
Mine now says AHCI where is shows IDE in attached.

Thank you very much! This helps tremendously!

---

### Post by Shadius on 2012-08-13
Okay, so I went into the BIOS and couldn't find anything like your screenshot. The only thing that I can see that might be related is "IDE Configuration". It gave me options to set it to "P-ATA", P-ATA+S+ATA", and I think another option. I can post pictures of the BIOS if it'll help you assist me better. I tried the option "P-ATA+S+ATA", but it didn't seem to like that because when I tried booting into Ubuntu the screen would redraw and I'd get a system error message. I've reset it back to it's original setting, "P-ATA".

---

### Post by oldfred on 2012-08-13
Is this an older Dell? Some posted that they had one PATA & one early version SATA, but could only boot from the PATA or IDE drive. 

I think the settings you have are IDE or PATA. There also should be a setting for the drive that is LBA, large or something similar. 

[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick.

---

### Post by Shadius on 2012-08-17
> **oldfred said:**
> Is this an older Dell? Some posted that they had one PATA & one early version SATA, but could only boot from the PATA or IDE drive. 

I think the settings you have are IDE or PATA. There also should be a setting for the drive that is LBA, large or something similar. 

[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick.

No, it's not a Dell. It's an ASUS P5P800 motherboard.

---

### Post by oldfred on 2012-08-17
I have a Gigabyte 775 motherboard that should be somewhat equivalent to  yours. Are you sure you do not have some settings related to IDE channel or hard drive settings? Some may show it as a sub menu under something related to hard drives?

See this in your manual:
4.3.5
Primary and Secondary Master/Slave;
Third and Fourth IDE Master

Some have reported that change from auto to LBA to force LBA helps, not sure with your system. 

If you have quick boot on, turn it off also.

---

