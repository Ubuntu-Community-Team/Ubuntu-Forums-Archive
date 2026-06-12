---
title: "Error loading operating system"
date: 2009-11-27
forum: General Help
---

### Post by traviezo on 2009-11-27
hello everybody!! I´m new in  linux and I really need the help  of you guys. I installed ubuntu 9.10 in an Acer Aspire 5610 and it was  working well, except that it didn´t recognize the 5-in-1 card reader(which accepts:MS,MS PRO,MMC,SD,xD)and I needed to do a recovery of pictures from a MSPRO card. I tried  test disk but as  I said it  doesn´t recognize the device. Then I remembered  that using windows  in this  computer I was able   to use the card´s reader so I decided to install XP on it in a partition  that I left for this purpose. I did google a bit, took some notes and I started  with  the installation. When It asked where to install xp I think  I selected the partition where I have linux (I´m no really sure about that), well the thing  is that it  was telling me to mark the partition as ¨inactive¨ to continue with the  installation and didn´t give me choice to get  back in the  process, I didn´t know what to do to cancel the installation, so I took the disc out and turned the  computer off manually. I thought it was not going to happen anything, but when I turned the computer on, it gave me this: ¨Error loading operating system¨, and thats all...I can´t do anything, I already tried to boot from the CD (I change the priority of the booting from the hard disk to the CD), but didn´t work neither with the XP or ubuntu live CD. Anybody..any ideas...what can I do  to get  my ubuntu back, thats all I want. Thanks a lot in advance. 

Another piece of information: I did not format  anything.

---

### Post by mdurham on 2009-11-27
Nothing that you have done will prevent booting from a CD, unless that's disabled in the bios somehow. Take a look in the bios.

---

### Post by traviezo on 2009-11-27
I already took a look at  the BIOS &set it up to boot from CD... The result was  exactly  the same.... Thanks any way for   the idea.

---

### Post by lisati on 2009-11-27
> **traviezo said:**
> hello everybody!! I´m new in  linux and I really need the help  of you guys. I installed ubuntu 9.10 in an Acer Aspire 5610 and it was  working well, except that it didn´t recognize the 5-in-1 card reader(which accepts:MS,MS PRO,MMC,SD,xD)and I needed to do a recovery of pictures from a MSPRO card. I tried  test disk but as  I said it  doesn´t recognize the device. Then I remembered  that using windows  in this  computer I was able   to use the card´s reader so I decided to install XP on it in a partition  that I left for this purpose. I did google a bit, took some notes and I started  with  the installation. [COLOR="Red"]**When It asked where to install xp I think  I selected the partition where I have linux **[/COLOR](I´m no really sure about that), well the thing  is that it  was telling me to mark the partition as ¨inactive¨ to continue with the  installation and didn´t give me choice to get  back in the  process, I didn´t know what to do to cancel the installation, so I took the disc out and turned the  computer off manually. I thought it was not going to happen anything, but when I turned the computer on, it gave me this: ¨Error loading operating system¨, and thats all...I can´t do anything, I already tried to boot from the CD (I change the priority of the booting from the hard disk to the CD), but didn´t work neither with the XP or ubuntu live CD. Anybody..any ideas...what can I do  to get  my ubuntu back, thats all I want. Thanks a lot in advance. 

Another piece of information: I did not format  anything.

Ah yes. I'm beginning to get a picture. I believe Windows can get "confused" when its installer is pointed towards a partition formatted for *nix. Others more knowledgable in this area might be able to advise you.

---

