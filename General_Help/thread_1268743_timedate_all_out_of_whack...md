---
title: "time/date all out of whack.."
date: 2009-09-17
forum: General Help
---

### Post by ROY.G.BIV on 2009-09-17
Okay... need some help here...

I was trying to install a new DVD writer. I reset my BIOS during the process so I could start the config fresh. However, upon trying to boot, I could not get a BIOS screen, and I quickly found out that for whatever reason my comp doesn't like the drive. So I removed it and put the old back in.

So I reboot, and make it into linux. My time/date is all messed up, so I fix it. But now, Google apparently thinks the date is february and I cannot check my email.  The security certificate is invalid. Also, at the top, I get a bar that says "Your browser has been updated and needs to be restarted". Letting it do so accomplishes nothing. Tells me the same thing after it restarts. 

I've trying updating and restarting, but this is not going away.

Screenshot on one error:



[IMG]http://i40.photobucket.com/albums/e242/Chromos1048/Screenshot-Alert.png[/IMG]


Help??

---

### Post by schmidtbag on 2009-09-17
when you reset bios, you reset the system clock too (no, i don't mean the fsb).  for whatever reason you can't change the date in linux's gui, try changing the date in bios

---

### Post by hwttdz on 2009-09-17
Couple thoughts, make sure you've updated everything.  That might magically fix it. 

Check your time zone, run "sudo dpkg-reconfigure tzdata".
Update the time "sudo ntpdate ntp.ubuntu.com" (you might have to install ntpdate).  

Let us know if any of that helps.

---

