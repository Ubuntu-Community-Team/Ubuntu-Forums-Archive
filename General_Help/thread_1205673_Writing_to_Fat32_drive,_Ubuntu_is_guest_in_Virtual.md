---
title: "Writing to Fat32 drive, Ubuntu is guest in VirtualBox"
date: 2009-07-06
forum: General Help
---

### Post by somethingkindawierd on 2009-07-06
I have Ubuntu 9.04 installed as a guest in VirtualBox, running on OSX. I have an external Fat32 drive with photos on it. For whatever reason, I cannot get this drive to share via the USB feature of VirtualBox.

So, I symlinked it to my user folder in OS X and Ubuntu can read that symlink just fine. Here is my problem.

When I open a file, ex: 22mb tiff, from the Fat32 drive, edit it with Gimp, and save it, it saves a 200-500kb file. It's a broken, incomplete tiff. I can "Save as..." and save to the Linux Desktop and it will be the full 22mb tiff, which I can then move to the Fat32 drive. But saving it directly from Gimp to the Fat32 drive fails every time.

Any ideas?

---

### Post by carml on 2009-07-06
Maybe you need to install the Guest Additions on your Jaunty machine.

---

### Post by somethingkindawierd on 2009-07-06
Guest additions are on and sharing of other drives works great, including a Fat32 thumb drive.

It's just this one drive, and the only time writing to it has failed is when Gimp is saving large tiffs.

---

