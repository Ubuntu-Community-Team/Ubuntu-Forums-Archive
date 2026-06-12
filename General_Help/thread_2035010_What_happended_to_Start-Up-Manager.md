---
title: "What happended to Start-Up-Manager?"
date: 2012-07-29
forum: General Help
---

### Post by derekpock on 2012-07-29
I loved that program so much. I used it all the time to adjust the GRUB setup. Is there a place I can re-download it or another program that would do the same things? Also, where is the file that grub uses to read which OS is default and how much time to wait before automatically starting.

---

### Post by OM55 on 2012-07-29
Hello derekpock,

You can try the Grub Customizer.

To install the graphical 'grub-customizer' tool:

sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer

Be careful when playing around with the Grub too much, or might corrupt your MBR and will need to reinstall it.

Enjoy.

---

