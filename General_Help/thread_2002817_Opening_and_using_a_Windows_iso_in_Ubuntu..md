---
title: "Opening and using a Windows iso in Ubuntu."
date: 2012-06-13
forum: General Help
---

### Post by Beatsleigher on 2012-06-13
Hey guys!

I need to create a Windows USB stick, using Ubuntu, to install it next to Ubuntu, but Ubuntu won't show the contents of the iso images.

Using Startupdisk Creator; I selected the ISO and nothing showed up, I thought this is an open-sourced OS, which has support for everything, I mean, if it can read Windows HDD, file formats and can create/modify the NTFS, why won't it open Windows ISOs?

I need Windows, because the virtual machines, won't accept 64x Windows images/DVDs, so I need to install it natively, but now, I can't and my Windows XP computer won't build Windows on USB sticks.

Before anyone comments stupidly, yes. I've tried burning using Brasero AND PowerISO, both won't take the ISO image...

---

### Post by Linux_junkie on 2012-06-13
Yes Ubuntu is open source but that does not mean it will support closed software like Windows. In fact I didn't even know Microsoft distributed iso's?  If it is distributed from Microsoft then I am sure there will be some block in it the file to prevent unauthorised copying.

---

### Post by pbrane on 2012-06-13
GNU/Linux distributions can read and write the ISO file format. I have no problems opening an ISO created on windows. And if done correctly, vice versa. If you are trying to create a live windows ISO on USB then that's another matter. I'm pretty sure that would be illegal. Can you be more specific about the ISO in question?

When you say you selected the ISO in startup disk creator and *nothing showed up*, what do you mean? The startup disk creator doesn't display the file contents.

---

### Post by Beatsleigher on 2012-06-13
> **Linux_junkie said:**
> Yes Ubuntu is open source but that does not mean it will support closed software like Windows. In fact I didn't even know Microsoft distributed iso's?  If it is distributed from Microsoft then I am sure there will be some block in it the file to prevent unauthorised copying.

If you don't believe, then check [http://go.microsoft.com/fwlink/?LinkId=251532](http://go.microsoft.com/fwlink/?LinkId=251532) .
That's just an example...

The Windows 7 ISOs were ripped from a DVD (I did that), there is no blockage...
Hm.. But never mind, then if Ubuntu doesn't like Windows (Which it should), then I'll do it otherwise...

---

### Post by Beatsleigher on 2012-06-13
> **pbrane said:**
> GNU/Linux distributions can read and write the ISO file format. I have no problems opening an ISO created on windows. And if done correctly, vice versa. If you are trying to create a live windows ISO on USB then that's another matter. I'm pretty sure that would be illegal. Can you be more specific about the ISO in question?

When you say you selected the ISO in startup disk creator and *nothing showed up*, what do you mean? The startup disk creator doesn't display the file contents.

Well, basically, I selected the Windows ISO, and upon me selecting *open*, it didn't show anything in the OS secion, that's what I ment. And no, it's not illegal, to burn Windows images. It is only illegal to crack then and create keygens. Windows is free, the key, to keep it working is licensed. Microsoft is also planning an open-sourced version of Windows, which just isn't compatible with Microsoft-distributed components, like Windows Live messenger, Office, etc. ...

But I've found a way :) I'm extracting the files and moving them to a USB stick, with the boot sectors, etc. ... Like I said, I'm a dev, just not familiar with PC-distributions of Linux :D

---

