---
title: "How do i copy a cd that only works in windows to a blank cd that works in ubuntu?"
date: 2010-08-29
forum: General Help
---

### Post by miko611 on 2010-08-29
I just want to be able to copy the files from a cd that is only compatible with windows to and new cd that is compatible with ubuntu

PLEASE HELP!

---

### Post by lisati on 2010-08-29
Your question doesn't belong in "Forum Feedback and Help" - I've moved it.

---

### Post by sikander3786 on 2010-08-29
> **miko611 said:**
> I just want to be able to copy the files from a cd that is only compatible with windows to and new cd that is compatible with ubuntu

PLEASE HELP!

Will you please elaborate. Which type of windows cd and which type of Ubuntu CD? Never seen a CD that isn't cross OS compatible.

---

### Post by lisati on 2010-08-29
Is the CD for a Windows program? If so, you'll have to see if it works with [WINE]("https://help.ubuntu.com/community/Wine"), look for a version that works natively with Ubuntu, or look for an equivalent.

---

### Post by carl4926 on 2010-08-29
> **miko611 said:**
> I just want to be able to copy the files from a cd that is only compatible with windows to and new cd that is compatible with ubuntu

PLEASE HELP!
This isn't making much sense
Do you mean Ubuntu can't read the CD:o

---

### Post by miko611 on 2010-08-29
> Is the CD for a Windows program? If so, you'll have to see if it works with [WINE]("https://help.ubuntu.com/community/Wine"), look for a version that works natively with Ubuntu, or look for an equivalent.

I have already checked if it works with wine and it doesn't

---

### Post by miko611 on 2010-08-29
> This isn't making much sense
Do you mean Ubuntu can't read the CD:eek:

yes i do

---

### Post by SoFl W on 2010-08-29
Okay, we all give up.... "What CD is it?"

---

### Post by miko611 on 2010-08-29
> **sikander3786 said:**
> Will you please elaborate. Which type of windows cd and which type of Ubuntu CD? Never seen a CD that isn't cross OS compatible.

I am trying to get the files from the windows cd and burn them onto a blank cd that can work in ubuntu.

---

### Post by miko611 on 2010-08-29
> **SoFl W said:**
> Okay, we all give up.... "What CD is it?"

its like a program that saves videos from a camera and edits them, it is made by canon, and called "digital video solution disk ver.31.0"

---

### Post by Sub101 on 2010-08-29
> **miko611 said:**
> its like a program that saves videos from a camera and edits them, it is made by canon, and called "digital video solution disk ver.31.0"

Can you "see" the files on the disk when in Ubuntu?

---

### Post by fiyer on 2010-08-29
> **miko611 said:**
> its like a program that saves videos from a camera and edits them, it is made by canon, and called "digital video solution disk ver.31.0"

I think you may need to tell Wine to look at the CD when you put it into your computer.

Other people will know the terminal instructions. I just know the GUI so far:
Check in Applications, Wine, Configure Wine, Drives, if you don't see the cd recognized, go to Add, Go to Show Advanced, set the path for where the CD drive

That should enable Wine to recognize the Windows Canon CD.

If not, you probably should be able to download the .exe for the Canon disc online somewhere, and run that within Wine.

Edit:
I have the same software with a previous edition, so I just tried it out.  You may need to copy the entire CD to your harddrive in order to set the setup.exe to to allow it to be run as an executable.  I had trouble changing the permissions for it on the CD, but once on the harddrive, I could change the permissions and install. Right click the file, go to Properties, Permissions, check the box for "Allow executing file as program"

---

### Post by miko611 on 2010-08-29
> **Sub101 said:**
> Can you "see" the files on the disk when in Ubuntu?
  yea you can

---

### Post by miko611 on 2010-08-29
> **fiyer said:**
> I think you may need to tell Wine to look at the CD when you put it into your computer.

Other people will know the terminal instructions. I just know the GUI so far:
Check in Applications, Wine, Configure Wine, Drives, if you don't see the cd recognized, go to Add, Go to Show Advanced, set the path for where the CD drive

That should enable Wine to recognize the Windows Canon CD.

If not, you probably should be able to download the .exe for the Canon disc online somewhere, and run that within Wine.

Edit:
I have the same software with a previous edition, so I just tried it out.  You may need to copy the entire CD to your harddrive in order to set the setup.exe to to allow it to be run as an executable.  I had trouble changing the permissions for it on the CD, but once on the harddrive, I could change the permissions and install. Right click the file, go to Properties, Permissions, check the box for "Allow executing file as program"

thanks

---

### Post by oldfred on 2010-08-29
We have a Canon camera and even in Windows I do not run any Canon software. 

I just pop the memory card out of the camera and using a multicard reader that connects to a USB port copy all the files onto my Ubuntu (or before window) folders.

---

### Post by miko611 on 2010-08-29
> **oldfred said:**
> We have a Canon camera and even in Windows I do not run any Canon software. 

I just pop the memory card out of the camera and using a multicard reader that connects to a USB port copy all the files onto my Ubuntu (or before window) folders.

I might try that but i still want the software on the cd

---

### Post by fiyer on 2010-08-29
There is at least one open source RAW converter for the DSLRs that you can install through the Ubuntu Software Center. Let us know if you get the Canon CD working, but also play around with the things that run natively in Ubuntu to see which features you get in both.

---

### Post by blazemore on 2010-08-29
You're in a "Windows Mindset"

In Windows you have to use special software that is secret only to the manufacturer and you are restricted in how you use it.
So in your case it will "import pictures from a Canon camera".

But in Ubuntu there is common software to "import pictures from digital cameras". You don't need specialist software to do it, you don't need to install any drivers.

You can plug the camera in via USB, or slot in the memory card (if you have a card reader).

The software included in Ubuntu will do the rest, and, if you'd prefer something different you can find a load of awesome free software in the Software Centre.

---

### Post by miko611 on 2010-08-29
> **fiyer said:**
> There is at least one open source RAW converter for the DSLRs that you can install through the Ubuntu Software Center. Let us know if you get the Canon CD working, but also play around with the things that run natively in Ubuntu to see which features you get in both.

thanks ill let you guys know if it works

---

### Post by miko611 on 2010-08-29
> **blazemore said:**
> You're in a "Windows Mindset"

In Windows you have to use special software that is secret only to the manufacturer and you are restricted in how you use it.
So in your case it will "import pictures from a Canon camera".

But in Ubuntu there is common software to "import pictures from digital cameras". You don't need specialist software to do it, you don't need to install any drivers.

You can plug the camera in via USB, or slot in the memory card (if you have a card reader).

The software included in Ubuntu will do the rest, and, if you'd prefer something different you can find a load of awesome free software in the Software Centre.

thanks

---

### Post by miko611 on 2010-08-29
I'm trying to import videos as well as pictures

---

### Post by Sub101 on 2010-08-30
> **miko611 said:**
> I'm trying to import videos as well as pictures

As someone said earlier, you can either remove the memory card from the camera and plug that directly into your computer if you have a memory hard reader.

Or you can plug the camera directly into your computer, assuming it has a USB connection.

Once connected go to Places -> Computer and your camera/memory card should appear.

---

### Post by miko611 on 2010-08-30
> **Sub101 said:**
> As someone said earlier, you can either remove the memory card from the camera and plug that directly into your computer if you have a memory hard reader.

Or you can plug the camera directly into your computer, assuming it has a USB connection.

Once connected go to Places -> Computer and your camera/memory card should appear.

thanks

---

### Post by sydbat on 2010-08-30
Kind of off topic, but...

For support, this is possibly the best forum I have ever been a part of. With an absolute minimum of information from the OP, and the subsequent patience of the forum community, the OP's problem was solved in under 10 posts. Amazing!

Imagine if the OP (and all other people with problems/questions) were to give much more specific information in their initial posts, how quickly things could be resolved.

A major **+ INFINITY** to the Ubuntu Forums support community!!!

---

