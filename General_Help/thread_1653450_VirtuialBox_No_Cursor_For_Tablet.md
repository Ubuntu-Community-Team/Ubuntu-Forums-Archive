---
title: "VirtuialBox: No Cursor For Tablet"
date: 2010-12-26
forum: General Help
---

### Post by physic.dude on 2010-12-26
Since my my Wacom tablet and Photoshop don't work well in Ubuntu I was forced to use them both through VirtuialBox and Windows XP. However, even though I have everything installed properly on the Windows guest I can not see my courser when using the tablet. 

Also, enabling an absolute pointing device in the VirtuialBox settings doesn't help.

What can I do?

---

### Post by physic.dude on 2010-12-27
bump

Would it help if I upload a quick youtube video?

---

### Post by physic.dude on 2010-12-28
bump

---

### Post by Favux on 2010-12-28
Hi physic.dude,

Sorry don't know anything about VirtualBox.

But I'm not aware of any Wacom tablet currently that can't be gotten to work in Ubuntu Maverick.  What model do you have?

Also for the Photoshop gurus you need to identify your Photoshop version.  There are some threads on how to do that.  I think they have Photoshop 3 & 4 working in Wine anyway.  If I'm remembering the version numbers correctly, which I might not be.

---

### Post by coldraven on 2010-12-28
Which version of Vbox are you using?
I think that for proper USB support you need to download directly from VBox instead of the version from the Ubuntu repository.
Get  the new version 4  from here:  [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by physic.dude on 2010-12-28
Sorry, 
The VBox I use is the closed sourced version, version 4
For the Wacom tablet I have the Intuos4 wireless 
And I use Photoshop CS5

The main reason I am using Windows in VBox with my Wacom is because in Ubuntu you cant use the displays or function buttons on the side of the tablet. I did manage to get Photoshop CS5 to run on Ubuntu through Wine, but it doesn't know that there is a tablet connected so I can't use its full capabilities.

---

### Post by Favux on 2010-12-28
Hi physic.dude,

My understanding is you can get the Intuos4 wireless working in Maverick by using its usb charging cable.  It'll work over usb.

However the bluetooth doesn't work.  You need to patch the Bluez package to turn on high speed blue tooth for the tablet.  The only patch to do that is for the Graphire bluetooth and I think only goes up to Lucid.  We posted on their thread with the details of the Intuos4 but mesilliac, who's been fixing/patching the bluetooth stack for the Graphire, hasn't been around lately and updated it for the Graphire in Maverick much less add the Intuous4.  We looked at the code but there has been a major code reorganization and we couldn't figure out where to plug the changes into.  See:  [http://ubuntuforums.org/showthread.php?t=674738&page=15](http://ubuntuforums.org/showthread.php?t=674738&page=15)

An updated xf86-input-wacom X driver would get the pad (tablet buttons) working.  See the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1"), part II or the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") section 2.

Thanks to Christoph Karg & Sanette there is a working userland app. to display images on the OLED's.  See the Intuos4 OLED thread:  [http://ubuntuforums.org/showpost.php?p=10173761&postcount=111](http://ubuntuforums.org/showpost.php?p=10173761&postcount=111)

---

### Post by physic.dude on 2010-12-28
I went through your instructions on the other threads and bookmarked them for future reference along with others I came across before. However I would like to use the tablet's full original features without all of the compatibility issues. I'm fine using the tablet through VirtualBox but the **only** problem with that is the fact that I cant see a cursor. 

Well, there is a cursor that stays with the mouse but the tablet's cursor is never seen. Would a quick youtube video help?

---

### Post by physic.dude on 2010-12-29
bump

---

### Post by AtomZeppelin on 2010-12-29
Hey!  I had the same problem and just fixed it :)  Beware, I don't use Ubunut (anymore), I'm on ArchLinux. VBox: 3.2.10 (Closed Source version) Tablet: Wacom Intous 4 M, not tested with my old Aiptek  Get your tablet installed correctly on linux first, make sure you see all events with evtest in the event-Device when you move the pen around. Minimum are X,Y (absolute) and Pressure. In the config of your XP VM you have to disable the absolute pointing device and add a filter for your usb tablet. Boot up and disable the cursor integration.  The cursor is shown for my tablet as soon as I disable the integration. Digging abit on the net gave me a thread in the vmware forum which states that the integrated cursors behave like absolute pointing devices (like tables) and that there can't be two at once in Windows.  Hope eveything makes sense, I'm abit in rush :) I'll come back later

---

### Post by physic.dude on 2010-12-29
> **AtomZeppelin said:**
> Hey!  I had the same problem and just fixed it :)  Beware, I don't use Ubunut (anymore), I'm on ArchLinux. VBox: 3.2.10 (Closed Source version) Tablet: Wacom Intous 4 M, not tested with my old Aiptek  Get your tablet installed correctly on linux first, make sure you see all events with evtest in the event-Device when you move the pen around. Minimum are X,Y (absolute) and Pressure. In the config of your XP VM you have to disable the absolute pointing device and add a filter for your usb tablet. Boot up and disable the cursor integration.  The cursor is shown for my tablet as soon as I disable the integration. Digging abit on the net gave me a thread in the vmware forum which states that the integrated cursors behave like absolute pointing devices (like tables) and that there can't be two at once in Windows.  Hope eveything makes sense, I'm abit in rush :) I'll come back later


Thanks, it works now.:D

---

### Post by AtomZeppelin on 2010-12-30
Glad I could help. Someone, who is also a native speaker, should put that info in the big ubuntu wiki about everything. :)

---

