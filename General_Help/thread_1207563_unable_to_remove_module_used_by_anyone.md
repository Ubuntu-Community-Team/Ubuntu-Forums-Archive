---
title: "unable to remove module used by anyone"
date: 2009-07-08
forum: General Help
---

### Post by edgarcgarzon on 2009-07-08
Hi my friends I have problems to removed a module used by anyone.

my lsmod is:

Module                  Size  Used by
provaSdo               11437  1 
rtai_sem               32168  1 provaSdo
rtai_fifos             33864  0 
rtai_sched            114624  3 provaSdo,rtai_sem,rtai_fifos
rtai_hal               78840  3 rtai_sem,rtai_fifos,rtai_sched
ec_8139too             23168  1 
ec_master             135868  2 provaSdo,ec_8139too
i915                   24320  2 
drm                    73876  3 i915
...

I tried to do 
rmmod provaSdo.ko
ERROR: Module provaSdo is in use

or 

rmmod -f provaSdo.ko
ERROR: Removing 'provaSdo': Device or resource busy

I know that is used by another one but which one???


when run the module is error: segmentation fault (or similar) and then I have to reboot my computer to begin the debbuger... is a very slow process...

someone can give me a tip....

---

