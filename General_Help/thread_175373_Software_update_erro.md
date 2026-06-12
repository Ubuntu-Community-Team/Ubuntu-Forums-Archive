---
title: "Software update erro"
date: 2006-05-13
forum: General Help
---

### Post by beren on 2006-05-13
I just updated the software with all recent updates. This included a new Linux image.

During the update I got an error message:
E: /var/cache/apt/archives/linux-image-2.6.12-10-386_2.6.12-10.32_i386.deb: failed in buffer_write(fd) (10, ret=-1)

In the terminal, it also says 
/boot (.......)   no space left on device

At the moment, some software stopped running such as Thunderbird. I understand I have to increase the size of /boot, but how?

-> I can't unmount and increase size as "device is busy"

What is the best way out?

Thanks for any help!

---

### Post by Ramses de Norre on 2006-05-13
Boot up a live disc and delete unneeded kernels or enlarge the /boot partition.

---

