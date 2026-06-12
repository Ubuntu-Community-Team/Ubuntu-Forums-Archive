---
title: "Can I change my Ubuntu OS harddrive to another computer?"
date: 2009-11-26
forum: General Help
---

### Post by Ubu4moi on 2009-11-26
I wanna upgrade my computer, can I just install my current harddrive on the new system? What do I have to do to move my OS to the new one? Anything I have to configure?

---

### Post by plucky on 2009-11-26
> **Ubu4moi said:**
> I wanna upgrade my computer, can I just install my current harddrive on the new system? What do I have to do to move my OS to the new one? Anything I have to configure?

What version are you running?

There would be issues with your graphics card on older versions,but I have just moved a karmic drive from a pentium machine with an intel card to an Amd cpu with an ATI card and every thing worked OOTB.


Good Luck

---

### Post by Ubu4moi on 2009-11-26
I'm running Ultimate Edition 2.0 64bit on an HP Pavilion. I'm just wondering if there are issues like when you try to move a Windows OS harddrive.

---

### Post by nwadams on 2009-11-26
it generally isn't as bad as a windows os partition. There may be some issues with the first boot, but they "should" resolve thsemselves. But remember worst comes to worst you can do a re-install with the same home partition so none of your files are lost. 

best of luck

nwadams

---

### Post by Cam42 on 2009-11-26
> ...you can do a re-install with the same home partition so none of your files are lost. 

But you have everything backed up, right? So that shouldn't be a problem...

;)

---

### Post by Cam42 on 2009-11-26
> **Ubu4moi said:**
> I wanna upgrade my computer, can I just install my current harddrive on the new system? What do I have to do to move my OS to the new one? Anything I have to configure?
Oh, and sorry if this is a stupid thing to say but....
What type of hard drive is it? IDE? SATA?
What type of hard drive does your new computer take? IDE? SATA?

---

### Post by Ubu4moi on 2009-11-26
OK. How do you install with the same home partition? Does that keep your programs too?

---

### Post by dcstar on 2009-11-26
> **Ubu4moi said:**
> Does that keep your programs too?

No, simply use the Synaptic "Save Markings" and "Read Markings" functions to have your new system install the same apps as the old one.

---

### Post by diesch on 2009-11-26
> **Ubu4moi said:**
> I wanna upgrade my computer, can I just install my current harddrive on the new system? What do I have to do to move my OS to the new one? Anything I have to configure?

Remove */etc/udev/rules.d/*persistent**, if you have a */etc/X11/xorg.conf* you may need to change a few things there. Anything else should work out of the box.

---

### Post by Ubu4moi on 2009-11-26
> **diesch said:**
> Remove */etc/udev/rules.d/*persistent**, if you have a */etc/X11/xorg.conf* you may need to change a few things there. Anything else should work out of the box.
Thanks. There are a few persistence files, persistence-input, persistence-storage, etc. Which do you mean and what should I edit?

---

### Post by ranch hand on 2009-11-26
I have a HDD that I keep a few OS' on that I loan to folks so that they can try out Linux at speed.  It is an external enclosure for one SATA HDD.

When you install your OS, it is best to do it on 2 partitions.  A 10 to 30Gb for / (root) and one 20Gbs up to what ever you want for /home (home).  If you are really screwed you can reinstall and choos to NOT format the /home partition.

A couple of things;
A> I have 8.10 installed on a 4Gb / and 5Gb /home on an old HP Pavilion xt993.
B> Reinstalling will loose you a lot of stuff as most programs are in /.  Your restricted extras and so forth are there too.  You will keep, barring disaster, all your documents and major settings.

Always backup your data.  It is a pain in the butt.  It is easier than trying to recover it.

---

### Post by diesch on 2009-11-26
> **Ubu4moi said:**
> Thanks. There are a few persistence files, persistence-input, persistence-storage, etc. Which do you mean and what should I edit?

Just remove all of them. They will be created again at the next boot.

---

