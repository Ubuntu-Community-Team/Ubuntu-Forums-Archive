---
title: "Partition Issues"
date: 2010-10-17
forum: General Help
---

### Post by CosmicDream on 2010-10-17
I'm visitng a friend and helping her with her computer. It is an old box, and it has 2 partitions installed on it, 1 windows, 1 ubuntu.  She is older and has no knowledge of computers, someone did this for her. 

It is booting to Ubuntu on default. She wants it to boot to windows. I am trying to do this for her, I am good with computers but new to Ubuntu.

At boot screen, an option is given to boot from the partitions, however I am unable to use the keyboard to navigate to the other partition. The arrow keys won't work. I do not believe this is an error with the keyboard, because I can access the BIOS (can't access partitions in BIOS either). Probably a hardware issue. It is an OLD computer.

I downloaded a few partition manager programs on the Ubuntu install, and I tried setting the other partition to boot. This changed nothing, it still auto-boots to Ubuntu. I tried to make a live gparted cd boot but i only had one blank Cd available and I jacked it up trying to burn the ISO file. Whoops. Leaving town tomorrow so trying to do this soon.

Any suggestions? I realize this isn't entirely an unbuntu issue but I am trying to do this from an unbuntu operating system which is why I am here. Keep in mind I'm good with computers but new to Ubuntu. 

Thank you.

---

### Post by entropy1 on 2010-10-17
Have you tried booting into Ubuntu and using synaptic to install startupmanager?  Then go to System > Administration > StartUp-Manager and you can use that to select the default OS to boot.

---

### Post by oldfred on 2010-10-17
Some BIOS require a setting for USB keyboard & mouse. Windows & Ubuntu used to ignore the setting in BIOS and work, but now grub seems to follow the setting in BIOS.

---

### Post by CosmicDream on 2010-10-18
> **entropy1 said:**
> Have you tried booting into Ubuntu and using synaptic to install startupmanager? Then go to System > Administration > StartUp-Manager and you can use that to select the default OS to boot.
 
This worked very well, I thank you. Unfortunately I've just screwed myself. The windows partition is now the one that auto-loads, and it turns out that windows partition has a boot problem... No one told me this. infinite blinking dash syndrome, nothing loads. 
 
So now I can't switch back to Linux due to GRUB Partition keyboard issue mentioned in original post, and the box is useless unless someone can help me fix the GRUB interface issue with the keyboard not working to select other partitions.
 
Time to reformat! Unless anyone knows of something I could do... Ahaha.

---

### Post by entropy1 on 2010-10-18
If I recall correctly, and maybe someone else can confirm, if you have a windows Reinstallation CD or DVD that came with the system, then by booting with it in the drive, you may be able access an option to "repair windows".  I think this option just rewrites the master boot record so that the system automatically boots into windows (assuming there are no other serious problems with your Windows OS).  If you don't need Ubuntu anymore, this would fix your problem.  If you ever want to use Ubuntu again, there is a way to fix grub that you could find out about; of course, in your case, you might then end up automatically booting into Ubuntu if you still can't use the keyboard to tell grub to select Windows as the alternative OS to boot.

---

