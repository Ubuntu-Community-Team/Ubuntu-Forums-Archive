---
title: "can't log in"
date: 2010-10-15
forum: General Help
---

### Post by cam3roon on 2010-10-15
Hi. I have a really big problem. 

After installing the rgba transparency I had a bug that didn't show me the background. I tried to uninstall the rgba but seems that I managed to make it worst. Now I can't log in. The computer is starting normal but after I write the login password and press Enter the screens gets black for 2 seconds and after that it wants me to log in again and again.

Is there any way to solve this? Can I at least save my files and the configuration? I have the live cd so I can save my files on a usb I guess, but how do I save the configuration?

Thank you very much

---

### Post by ubudog on 2010-10-15
Well most of the configuration files for apps like Firefox are stored in files like .firefox .evolution, etc.  You can view them from a console with CTL>ALT>F1 using 

```
ls -a
```

and copy them (using .firefox as an example) (assuming you have the flash drive plugged in)

```
sudo cp .firefox /media/nameofdrive
```

---

### Post by ubudog on 2010-10-15
Oh, and what type of graphics card do you have?

You can find out with:

```
lspci
```

---

### Post by cam3roon on 2010-10-15
Thanks

I have a nvidia gforce 8600 GS

---

### Post by cam3roon on 2010-10-15
I saw on Internet some tutorials about copying the /home folder to a new partition and the root leave it on another. Is it posible that if I do that and after that install again ubuntu on the root partition to work?

I have these partitions: 

[IMG]http://img242.imageshack.us/img242/7825/screenshotsq.png[/IMG]

---

### Post by ubudog on 2010-10-15
Or just copy all the stuff you want to save using CTL>ALT>F1 to a flash drive, then try reinstalling.

---

### Post by cam3roon on 2010-10-15
With the liveCd I made a new /home partition and installed ubuntu again  in another one. It worked and saved all my files. The only downside of this is that the old /home folder was saved in /home/home. I still don't get it how this happened but at least I have my files and ubuntu is working correctly. 

Thanks for the advices

---

### Post by ubudog on 2010-10-15
Cool, glad you got it worked out. :):):)

---

