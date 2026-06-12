---
title: "SD reader does not work. Help!"
date: 2010-11-04
forum: General Help
---

### Post by imtired111 on 2010-11-04
I have installed ubuntu 10.10 netbook edition on my hp mini 1010nr. i went to upload some photos on my sd reader and nothing happened. is there some way to make ubuntu recognize the reader as a usb port. if so can someone tell me how?:confused:

---

### Post by fragos on 2010-11-04
USB is the standard interface on Desktops for SD readers but some laptops use a proprietary approach which requires a driver be installed. Running lspci in a terminal window may be helpful. If the proprietary SD interface was used this should give you information on the driver chip used. Search for the driver chip by name and number in this forum.

---

