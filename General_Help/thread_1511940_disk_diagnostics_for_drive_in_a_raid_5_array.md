---
title: "disk diagnostics for drive in a raid 5 array"
date: 2010-06-17
forum: General Help
---

### Post by Jeffa on 2010-06-17
Hello Community. 

So I'm rebuilding a raid 5 to expand its capacity. I have an areca 1220 hardware raid controller. I have four brand new samsung hard drives. While building the storage volume in the raid controller bios, I was getting dozens of errors saying, "IDE Channel 3: reading error". And I mean DOZENS of those errors. So I got a little nervous, pulled the drive that was attached to channel 3, popped it into my windows machine so I could try to use samsung's disk diagnostics on it, but windows wouldn't recognize the drive. Makes sense, it wasn't partitioned or formatted in any way windows would recognize it. So I decided to put the drive back into the raid controller on my ubuntu machine. Now I get an error saying the raid volume is incomplete. I'm assuming this is because windows installed drivers onto the drive and the raid controller can't see the drive. 

Now for the questions:

Are there disk diagnostics in ubuntu that will allow me to scan an individual drive in a raid 5?

Not really sure where to go from here. The raid volume actually completed despite all the errors, and it appears as though I could format and mount the drive normally. But all those errors make me very nervous, especially because this drive will be used as a file server and drive (and data) integrity are paramount. 

Any advice the community might have would be greatly appreciated! 

-Jeff

---

