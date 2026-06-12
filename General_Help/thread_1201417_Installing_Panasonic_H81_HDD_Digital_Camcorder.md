---
title: "Installing Panasonic H81 HDD Digital Camcorder"
date: 2009-07-01
forum: General Help
---

### Post by rmhodv on 2009-07-01
Hi I have just bought the above and it only come with Windoze drivers. How should I go about installing it in Ubuntu 8.10

---

### Post by thespirit3 on 2009-07-01
Plug it in - it may well get detected and 'just work'.   I'm not familiar with camcorders but I'd hope it would either act as a USB storage device or do something using video4linux (or whatever they're called) drivers.

Open a terminal, then run 'tail -f /var/log/messages' - then plug the camera in via USB/Firewire.   This will then show you what the kernel has identified - and may well give you a clue on how to proceed.   If you're lucky, gnome may simply spring to life and do the required magic.

Give it a go.  Meanwhile someone else that knows more will probably respond with something much more helpful :)


Steve

---

### Post by rmhodv on 2009-07-02
Thank you for your help. Does anyone else have any suggestions?

---

