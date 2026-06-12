---
title: "Intermittent copy failure."
date: 2011-02-15
forum: General Help
---

### Post by lucifer369 on 2011-02-15
Hello.  This is my first post here.  Please be gentle...

I have a system that has an intermittent issue with copying files.  Below is the error that occurs.[INDENT]Error while copying "<filename>"
There was an error coping the file into network:///
Operation not support by backend

[/INDENT]The user has Ubuntu 8.04.  They are using the Nautilus window to copy files (drag and drop) from a CD/DVD or USB device.  The directory they are copying onto is a RAID0 device with approximately 2T of space, and more than enough space to take the files.  The permissions for the drive and folders are set to the user.

This occurs randomly and is very frustrating.  We cannot duplicate it and when it does occur, it will happen once, then work fine.  Very odd behavior.

I've been checking forums and help files all over, but find nothing similar.  The only stuff I find is if it's a new install and the permissions haven't been set correctly.

Any suggestions or help would be greatly appreciated.  Even a confirmation that someone else has seen this before.  I don't have a lot of hair left, but I'm starting to pull at it...
Richard

---

### Post by Eggbertx on 2011-02-15
Did they try copying it from the usb/cd drive to the hard drive, then to the network drive? I think I've had issues like this before.

---

### Post by [S|G] on 2011-02-15
Hello!

First, you seem to be using a pretty old version of Ubuntu, and I'd avise you to update if possible. As for the problem itself, it seems to be a known bug on Hardy's nautilus that is marked fixed on intrepid:

[https://bugs.launchpad.net/nautilus/+bug/205773](https://bugs.launchpad.net/nautilus/+bug/205773)

I think the fix was never released on Hardy, as it was mentioned that "the change is not trivial and not likely to be backported to hardy".

Hope this helps!

---

### Post by lucifer369 on 2011-02-15
Thank you both for your responses.  

Yes, it is an older version, but it's on a number of systems in the field and there is no way to update them without major costs.  

I appreciate the link and can now move forward and start to prove that we really need to move to the newest version for the next release.

I took some time and proved out that if the drag runs over a non-active network drive, it will fail every time.  Now, I just have a work around ("Don't do that") to write and can move on to the next issue.

Thanks again.

---

