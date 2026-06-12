---
title: "Grub Fine- but Kernel Boots into Root Shell"
date: 2012-03-03
forum: General Help
---

### Post by packman123 on 2012-03-03
Been having many issues booting into the latest Kernel from Grub. I click on the 3.0.0-16 kernel and when I log in my password, it just goes into a root shell prompt that fills the whole screen with some kind of booting information. I have to restart with ctrl-alt-bspace because It wont take any kind of keyboard input. Here the boot.log text:

modem-manager[796]: <info>  ModemManager (version 0.5) starting... 
  
swapon: /dev/disk/by-uuid/25d45c0a-df30-49e5-a0b0-82156102395d: swapon failed: Device or resource busy 
mountall: swapon /dev/disk/by-uuid/25d45c0a-df30-49e5-a0b0-82156102395d [815] terminated with status 255 
mountall: Problem activating swap: /dev/disk/by-uuid/25d45c0a-df30-49e5-a0b0-82156102395d 
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
 * Starting AppArmor profiles       [80G  [74G[ OK ] 
Starting VMware services: 
   Virtual machine monitor[71G done 
   Virtual machine communication interface[71G done 
   VM communication interface socket family[71G done 
   Blocking file system[71G done 
   Virtual ethernetinitctl: Event failed


Can I fix this??  Thank You to anybody who can help!!

---

