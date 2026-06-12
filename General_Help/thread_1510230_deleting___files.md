---
title: "deleting   files"
date: 2010-06-15
forum: General Help
---

### Post by choochoousmc on 2010-06-15
In Windows when you delete a file, it really isn't gone.
Have to have special software to actually wipe it.
what programs in Linux/Ubuntu are along same lines.
secure delete a file, secure empty trash, clean the hard drive unused areas (where files once were).
Are they in package manager, synaptics or on the web?


Update. I took the new Ubuntu system with me on road trip this weekend as a trial.
Wireless network connection is from across street. Connected just fine.
Hook Nikon camera in to D/L pics, "saw" camera immediately
Forgot cell phone charger at home. Used the USB cable. "saw" phone immediately and phone said charging.
So, so far all is well just some things are done a little differently than windows!

---

### Post by clhsharky on 2010-06-15
choochoousmc

BleachBit is a good one. Its in software center.

sharky

---

### Post by jerome1232 on 2010-06-15
there's shred.

Installed by default.

Type the following into a terminal for more info (Applications->Accessories->Terminal)

```
man shred 
```

---

### Post by choochoousmc on 2010-06-20
thanks guys. didn't see "shred" in the menus , will look again.
Also bleachbit

---

### Post by warfacegod on 2010-06-20
Your not going to find it in the menu, it's a Terminal command. To follow jerome1232's advice, go to: Applications> Accessories> Terminal> type man shred> hit Enter

---

### Post by HermanAB on 2010-06-20
Howdy, the better way to do it is to encrypt your home directory.  Trying to delete a file from magnetic memory is basically a waste of time.

---

### Post by Zip247 on 2010-06-20
[Here]("http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html")  is a good write up on how to use shred.  The page also tells you how to add shred to your right click menu in nautilus.

---

### Post by warfacegod on 2010-06-21
> **HermanAB said:**
> Howdy, the better way to do it is to encrypt your home directory.  Trying to delete a file from magnetic memory is basically a waste of time.

I beg to differ. An 8 lbs. sledge hammer is an highly effective way of deleting files. I have two. Named Logic And Reason.

---

### Post by mkvnmtr on 2010-06-21
The package secure-delete has four programs to wipe. It wipes a file, wipes memory. wipes swap space and wipes unused space. It is not a waste of time. It works well. Google secure-delete to learn to use it. The man pages are helpful also.

---

### Post by jerome1232 on 2010-06-21
> **mkvnmtr said:**
> The package secure-delete has four programs to wipe. It wipes a file, wipes memory. wipes swap space and wipes unused space. It is not a waste of time. It works well. Google secure-delete to learn to use it. The man pages are helpful also.

If someone really wants your files, sledge hammer option sometimes isn't even enough.

It's possible to disassemble a hard drive and use special equipment to recover files that were completely deleted, even sometimes from physically damaged hard drives. 

There is one company that specializes in recovering data from hard drives, they even claim to have success with fire damaged hard drives.

Is it  perfect? No, but if the fbi was knocking on your door and you wanted to erase data for sure you pretty much need specialized devices that physically destroy the hard drives in very destructive ways and have had the hard drives encrypted to begin with to boot.

If your just selling the computer at a yard sell and don't want the next owners getting a hold of your mypasswordsarehere.txt file or something then writing random data to the hard drive is enough.

---

### Post by Linux Lurker on 2010-07-06
> **jerome1232 said:**
> 
"It's possible to disassemble a hard drive and use special equipment...

"...you wanted to erase data for sure you pretty much need specialized devices that physically destroy the hard drives in very destructive ways..."


With all due respect. Your post seems to perpetuate what I believe is an over exaggerated sense of paranoia regarding this general issue.
Where and what is all this "specialized equipment"?

Again... WADR... but I tend to believe this article:
[http://www.nber.org/sys-admin/overwritten-data-guttman.html](http://www.nber.org/sys-admin/overwritten-data-guttman.html)

Now I wait patiently... for the black helicopters.

Lurker

---

### Post by warfacegod on 2010-07-06
I assure you Governments the world over are exactly that kind of paranoid when it comes to their secrets. I have no doubt that they possess such equipment for the sake of safeguarding such things as Nuclear Weapons designs or the deployment of their Armed Forces. Are there people out there that want those secrets? Certainly. Do those people want *our* secrets and are they willing to go to such extreme measures to get them? No. That's what Google is for.

---

