---
title: "help !!"
date: 2011-05-23
forum: General Help
---

### Post by neomaniac on 2011-05-23
i'm working on the symbian qemu after i set the environment  .. 
i should now load a rom image of the system core to be booted  .. 
the build process of the qemu generates a memory dump of an ARM processor which i think is used to load the image  ..

i'm using this command to boot  

./qemu-system-arm -M versatilepb -kernel $/home/m3ssaf/symbian/gcc/epoc32/rom/syborg/syborg.dtb -hda $/home/m3ssaf/symbian/gcc/epoc32/rom/syborg_tshell_ARMV5_udeb.img -d out_asm,in_asm,op,op_opt,int,exec,cpu  

with that command it  produces an error 
"qemu: could not open disk image $/home/m3ssaf/symbian/gcc/epoc32/rom/syborg_tshell_ARMV5_udeb.img"

i don't understand that  ?? ... the img file has full access  ...., 

regards ...

---

