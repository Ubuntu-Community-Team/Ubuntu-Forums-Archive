---
title: "Broke my grub - I need help!"
date: 2012-10-08
forum: General Help
---

### Post by BBB3000 on 2012-10-08
First post..go easy :)

I just installed Ubuntu 12.04 as a dual boot with my Windows 7. I was using the Grub Customizer to mess with the Grub menu. I changed the resolution of the grub menu using Grub Customizer from 1900x1080x8 (or 16) to 1900x1080x24. Upon reboot I can no longer see my Grub menu. I can hit up/down arrow and select the OS by guessing. Windows 7 loads fine but Ubuntu does not load. It gives some error and never boots.

Can anyone help?

---

### Post by BBB3000 on 2012-10-08
I was able to get the grub menu back by using a LiveCD and changing the resolution in /etc/default/grub back to 1900x1080x24.

However, Ubuntu gives shows me a "broken pipe cannot write bytes" error upon booting. I will investigate further, but if anyone has suggestion..I am all ears!

---

