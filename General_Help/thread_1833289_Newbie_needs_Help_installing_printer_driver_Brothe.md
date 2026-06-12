---
title: "Newbie needs Help installing printer driver Brother MFC5890CN"
date: 2011-08-25
forum: General Help
---

### Post by Rolyh on 2011-08-25
Hi All,
I have just installed natty 11.04 and am really pleased with it so far.
I managed to install graphics card driver using terminal commands.
However I am having real difficulties trying to install a printer driver for my Brother MFC5480cn.
It is a networked printer and is recognised as being on the network by searching system administration printer.
I have found a site that has drivers for my printer

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html)

but I am not sure which to use or how to install it. I tried using the instructions on the website where the driver is but kept getting errors stating directories couldn't be created?

There are two different drivers listed one being lpr driver and the other cupswrapper driver. 

Can someone please advise me which one I should use and how to install it.

A step by step list of instructions would be greatly appreciated.

Many thanks in advance,
Roly

---

### Post by wojox on 2011-08-25
Start around [Step 6]("http://ubuntuforums.org/showthread.php?t=590793&highlight=mfc420cn")

---

### Post by fdrake on 2011-08-25
,,,,

---

### Post by dave01945 on 2011-08-25
did you run the install instructions with sudo also the website appears to say install both drivers

it also says to run this command before follwing install instructions

```
mkdir /var/spool/lpd
```

if i give you the step by step instructions i will be repeating what the other site says did you read through the pre required procedure

---

### Post by Rolyh on 2011-08-25
Thanks guys,
I'll give it a go.
I think my problem was not creating the directory.
I'll report back and let you know how it goes.
regards,
Roly

---

### Post by Rolyh on 2011-08-25
Thanks Wojox
I followed the link and it worked perfectly.
All up and running.
Regards,
Roly

---

### Post by wojox on 2011-08-25
> **Rolyh said:**
> Thanks Wojox
I followed the link and it worked perfectly.
All up and running.
Regards,
Roly

Cool, your welcome. :P

---

