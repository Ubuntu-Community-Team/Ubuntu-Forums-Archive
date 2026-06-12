---
title: "Moving old home to new pc"
date: 2010-08-05
forum: General Help
---

### Post by Razmear on 2010-08-05
Just finished building a new Ubuntu box and have been getting things setup. 
I have a new SATA 500 gig drive in the new system. My old IDE drive from the previous system is in and mounted. 
I can currently boot to either by flipping the BIOS info. Not sure if I can mount the SATA while booted to the old IDE tho, get mount errors at startup.

So, my plan is to move the essential bits of my /home into a storage area, and take ownership of them, so I can import my old mail and other essential stuff. When I try to copy from the SATA drives new install I get permission errors, and all the files are owned by #1002. 
Seeing how my brain is toast due to heat and working on this build for about the past 8 hours, can anyone give me a simple way to copy over the info from the IDE drive (which will be going away) to the SATA drive and have the data usable for import into my home folder. 

Thanks,
eb

---

### Post by dcstar on 2010-08-05
> **Razmear said:**
> Just finished building a new Ubuntu box and have been getting things setup. 
I have a new SATA 500 gig drive in the new system. My old IDE drive from the previous system is in and mounted. 
I can currently boot to either by flipping the BIOS info. Not sure if I can mount the SATA while booted to the old IDE tho, get mount errors at startup.

So, my plan is to move the essential bits of my /home into a storage area, and take ownership of them, so I can import my old mail and other essential stuff. When I try to copy from the SATA drives new install I get permission errors, and all the files are owned by #1002. 
Seeing how my brain is toast due to heat and working on this build for about the past 8 hours, can anyone give me a simple way to copy over the info from the IDE drive (which will be going away) to the SATA drive and have the data usable for import into my home folder. 

Thanks,
eb
Try this then see if you can copy:
```
sudo chown -r {your-user-name} /mount-path-to-old-drive/home/{your-user-name}
```

---

### Post by Razmear on 2010-08-05
Thanks man, 
brain is about fried, and that looks like it's doing the trick. Had to -R but you got me pointed in the right direction...

```

eb@eb-desktop:/media/04cb8be4-010d-48e1-a4e7-a164358b5fb2/home$ ls
eb  eb235  kebu

eb@eb-desktop:/media/04cb8be4-010d-48e1-a4e7-a164358b5fb2/home$ sudo chown -R eb ./eb235

```

btw,
Nice to finally see what Compiz can do, my last PC was an old P3 with 512mg ram. New one is an Athelon dual core with 2gig and a Nvidia 8200 graphics card. 

Copy finished while I was typing, looks like I'm good to go. 
:D

eb

---

