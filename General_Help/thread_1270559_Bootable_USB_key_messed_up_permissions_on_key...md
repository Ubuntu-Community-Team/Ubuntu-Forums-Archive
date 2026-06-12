---
title: "Bootable USB key messed up permissions on key.."
date: 2009-09-19
forum: General Help
---

### Post by VipX1 on 2009-09-19
I made a bootable USB key using the Ubuntu DELL iso. The key worked and I had look at the DELL iso. Now I have a problem though, I can't use my key to write an image to with Clonezilla.

I set the key up as the /home directory on Clonezilla, selected my only other drive in the laptop sda1 as the drive to be imaged and Clonezilla didn't even start it just returned an error straight away and then rebooted the laptop so I could not read the log file. I am fairly sure that it is the permissions on the USB key /home directory causing the problem. All directories on the key are drwx------. I can change the permissions when operating as root on the USB key OS. When I veiw the USB key diectories from another OS they have not changed. 
From another OS chmod seems to work, there's no output but the permissions don't change, chown doesn't work "operation not permitted"...
The USB key is 32GB and nearly full so I don't have space to copy all the files onto my laptop and the files are old back-ups so they're important. Re-fromat is not possible at present because of that. I know it wasn't very clever to use that key to test the DELL.iso

---

