---
title: "Using KDE. What file ending does a KWrite file have?"
date: 2011-10-16
forum: General Help
---

### Post by hashes on 2011-10-16
I did a dmesg and got many pages of text. I am looking for something particular in this file. I think I have found it, but only by using dmesg with a usb device and dmesg without a usb device. (Long story). And then I went through the two files line by line until I found the difference maaaaany hours later. So there has got to be a faster way. I copyed and pasted this dmesg output to a KWrite file.
 
Question: I was wondering if I now could use some kind of command on this file, now that I know what I am looking for ( and know the answer).
 
I thought grep usb0 nameoffile.ending
But there is no ending on the KWrite file. It only states Plain Text File.
So what would I use as an ending?

---

### Post by zealibib slaughter on 2011-10-16
You could just use a wildcard * for the file type.  Like grep (device) filename.*

---

