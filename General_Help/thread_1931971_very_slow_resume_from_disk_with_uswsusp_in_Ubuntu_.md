---
title: "very slow resume from disk with uswsusp in Ubuntu 10.04 LTS"
date: 2012-02-26
forum: General Help
---

### Post by Erwin123 on 2012-02-26
I'm using uswsusp for the hibernation of an Ubuntu 10.04 LTS (64 bit) desktop. Suspend to disk works fine within a few seconds. With the resume, I have 2 issues:

1) there is always a pause at the initial text screen with the image statistics and it requires my to press a key.

2) more annoying, after the resume is done, the machine starts to read tons of data from swap after each mouse click and it takes several minutes until I can work normally. I thought that all memory is compressed in the hibernation image to be read in in one chunk at the beginning?

Ubuntu 10.04 LTS ships with uswsusp 0.8, may an update to 1.0 address these issues? Is there a binary deb package available?

I have 4GB of RAM, use Kubuntu, and my uswsusp.conf is attached. Increasing "image size" and running "sudo update-initramfs -u" didn't help.

Best,
Erwin

---

### Post by Erwin123 on 2012-03-04
Anybody any idea? If this it the wrong forum, please guide me where to put my request.

Thanks,
Erwin

---

