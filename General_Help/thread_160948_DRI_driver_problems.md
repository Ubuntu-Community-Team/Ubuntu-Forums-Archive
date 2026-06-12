---
title: "DRI driver problems"
date: 2006-04-16
forum: General Help
---

### Post by pjbgravely on 2006-04-16
While trying to get 3D acceleration working I have gone through 3 video cards. on the last I think I have found the problem.

~$ sudo modprobe r128
FATAL: Error inserting r128 (/lib/modules/2.6.12-10-686/kernel/drivers/char/drm/r128.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
$ dmesg set 2, code 0xaa on isa0060/serio0).
[ 5834.852976] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 5834.990076] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 5834.990097] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 5835.129587] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 5835.129610] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 5835.637230] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 5835.637252] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 5835.757279] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 5835.757302] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 5836.409289] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 5836.409312] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 5836.526897] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 5836.526920] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 5836.690489] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 5836.690508] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 5836.837305] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 5836.837328] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 5837.145254] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 5837.145275] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 5837.270171] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 5837.270193] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 5837.380832] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 5837.380852] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 5837.532510] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 5837.532533] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 5838.146030] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 5838.146052] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 5838.256344] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 5838.256367] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 8853.709802] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 8853.709825] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 8853.922314] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 8853.922336] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 8854.191816] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 8854.191838] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 8854.333777] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 8854.333800] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 8855.243723] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 8855.243746] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 8855.366247] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 8855.366269] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 8856.234909] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 8856.234931] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 8856.352532] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 8856.352554] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 8856.677366] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 8856.677387] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 8856.797420] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 8856.797442] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 8876.521448] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 8876.521471] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 8876.648793] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 8876.648815] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 8946.789516] r128: disagrees about version of symbol drm_open
[ 8946.789537] r128: Unknown symbol drm_open
[ 8946.789838] r128: disagrees about version of symbol drm_fasync
[ 8946.789850] r128: Unknown symbol drm_fasync
[ 8946.790129] r128: disagrees about version of symbol drm_poll
[ 8946.790141] r128: Unknown symbol drm_poll
[ 8946.790524] r128: disagrees about version of symbol drm_core_get_reg_ofs
[ 8946.790536] r128: Unknown symbol drm_core_get_reg_ofs
[ 8946.790934] r128: disagrees about version of symbol drm_irq_uninstall
[ 8946.790947] r128: Unknown symbol drm_irq_uninstall
[ 8946.791302] r128: disagrees about version of symbol drm_ioctl
[ 8946.791313] r128: Unknown symbol drm_ioctl
[ 8946.791590] r128: disagrees about version of symbol drm_exit
[ 8946.791616] r128: Unknown symbol drm_exit
[ 8946.792165] r128: disagrees about version of symbol drm_core_get_map_ofs
[ 8946.792177] r128: Unknown symbol drm_core_get_map_ofs
[ 8946.792458] r128: disagrees about version of symbol drm_init
[ 8946.792470] r128: Unknown symbol drm_init
[ 8946.792911] r128: disagrees about version of symbol drm_vbl_send_signals
[ 8946.792924] r128: Unknown symbol drm_vbl_send_signals
[ 8946.793232] r128: disagrees about version of symbol drm_ati_pcigart_init
[ 8946.793244] r128: Unknown symbol drm_ati_pcigart_init
[ 8946.793557] r128: disagrees about version of symbol drm_mmap
[ 8946.793585] r128: Unknown symbol drm_mmap
[ 8946.794129] r128: disagrees about version of symbol drm_ati_pcigart_cleanup
[ 8946.794141] r128: Unknown symbol drm_ati_pcigart_cleanup
[ 8946.794585] r128: disagrees about version of symbol drm_core_reclaim_buffers
[ 8946.794613] r128: Unknown symbol drm_core_reclaim_buffers
[ 8946.794888] r128: disagrees about version of symbol drm_release
[ 8946.794900] r128: Unknown symbol drm_release
[ 8994.943348] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 8994.943372] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 8995.073247] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 8995.073270] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 9213.277187] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 9213.277210] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 9214.291817] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 9214.291840] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 9972.064428] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 9972.064452] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 9972.167443] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 9972.167465] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 9975.759685] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 9975.759707] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 9976.647653] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 9976.647675] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 9992.073585] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 9992.073608] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 9992.169297] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 9992.169320] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 9992.626431] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 9992.626453] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 9993.246422] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 9993.246444] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 9993.478446] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 9993.478466] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 9993.576598] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 9993.576620] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 9993.680044] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 9993.680064] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 9993.802521] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 9993.802543] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 9995.128783] radeon: disagrees about version of symbol drm_open
[ 9995.128828] radeon: Unknown symbol drm_open
[ 9995.129109] radeon: disagrees about version of symbol drm_fasync
[ 9995.129121] radeon: Unknown symbol drm_fasync
[ 9995.129401] radeon: disagrees about version of symbol drm_poll
[ 9995.129426] radeon: Unknown symbol drm_poll
[ 9995.129810] radeon: disagrees about version of symbol drm_core_get_reg_ofs
[ 9995.129823] radeon: Unknown symbol drm_core_get_reg_ofs
[ 9995.130205] radeon: disagrees about version of symbol drm_irq_uninstall
[ 9995.130217] radeon: Unknown symbol drm_irq_uninstall
[ 9995.130601] radeon: disagrees about version of symbol drm_ioctl
[ 9995.130613] radeon: Unknown symbol drm_ioctl
[ 9995.130890] radeon: disagrees about version of symbol drm_exit
[ 9995.130901] radeon: Unknown symbol drm_exit
[ 9995.131450] radeon: disagrees about version of symbol drm_core_get_map_ofs
[ 9995.131477] radeon: Unknown symbol drm_core_get_map_ofs
[ 9995.131759] radeon: disagrees about version of symbol drm_init
[ 9995.131771] radeon: Unknown symbol drm_init
[ 9995.132197] radeon: disagrees about version of symbol drm_vbl_send_signals
[ 9995.132210] radeon: Unknown symbol drm_vbl_send_signals
[ 9995.132517] radeon: disagrees about version of symbol drm_ati_pcigart_init
[ 9995.132547] radeon: Unknown symbol drm_ati_pcigart_init
[ 9995.132862] radeon: disagrees about version of symbol drm_mmap
[ 9995.132874] radeon: Unknown symbol drm_mmap
[ 9995.133417] radeon: disagrees about version of symbol drm_ati_pcigart_cleanup[ 9995.133445] radeon: Unknown symbol drm_ati_pcigart_cleanup
[ 9995.133889] radeon: disagrees about version of symbol drm_core_reclaim_buffers
[ 9995.133902] radeon: Unknown symbol drm_core_reclaim_buffers
[ 9995.134177] radeon: disagrees about version of symbol drm_release
[ 9995.134189] radeon: Unknown symbol drm_release
[11794.021769] r128: disagrees about version of symbol drm_open
[11794.021791] r128: Unknown symbol drm_open
[11794.022071] r128: disagrees about version of symbol drm_fasync
[11794.022107] r128: Unknown symbol drm_fasync
[11794.022388] r128: disagrees about version of symbol drm_poll
[11794.022399] r128: Unknown symbol drm_poll
[11794.022782] r128: disagrees about version of symbol drm_core_get_reg_ofs
[11794.022795] r128: Unknown symbol drm_core_get_reg_ofs
[11794.023192] r128: disagrees about version of symbol drm_irq_uninstall
[11794.023205] r128: Unknown symbol drm_irq_uninstall
[11794.023560] r128: disagrees about version of symbol drm_ioctl
[11794.023571] r128: Unknown symbol drm_ioctl
[11794.023847] r128: disagrees about version of symbol drm_exit
[11794.023858] r128: Unknown symbol drm_exit
[11794.024421] r128: disagrees about version of symbol drm_core_get_map_ofs
[11794.024434] r128: Unknown symbol drm_core_get_map_ofs
[11794.024714] r128: disagrees about version of symbol drm_init
[11794.024725] r128: Unknown symbol drm_init
[11794.025151] r128: disagrees about version of symbol drm_vbl_send_signals
[11794.025177] r128: Unknown symbol drm_vbl_send_signals
[11794.025485] r128: disagrees about version of symbol drm_ati_pcigart_init
[11794.025498] r128: Unknown symbol drm_ati_pcigart_init
[11794.025811] r128: disagrees about version of symbol drm_mmap
[11794.025822] r128: Unknown symbol drm_mmap
[11794.026390] r128: disagrees about version of symbol drm_ati_pcigart_cleanup
[11794.026404] r128: Unknown symbol drm_ati_pcigart_cleanup
[11794.026847] r128: disagrees about version of symbol drm_core_reclaim_buffers
[11794.026860] r128: Unknown symbol drm_core_reclaim_buffers
[11794.027134] r128: disagrees about version of symbol drm_release
[11794.027161] r128: Unknown symbol drm_release
[11818.823011] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[11818.823035] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[11818.945591] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[11818.945614] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[11819.489505] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[11819.489528] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[11819.626685] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[11819.626709] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[11871.499276] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[11871.499299] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[11871.614479] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[11871.614502] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[11872.249819] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[11872.249843] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[11872.340700] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[11872.340723] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[11873.762968] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[11873.762991] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[11873.887911] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[11873.887934] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[11875.074330] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[11875.074353] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[11875.189531] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[11875.189554] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[11877.649016] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[11877.649039] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[11877.759349] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[11877.759371] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[11878.358572] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[11878.358595] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[11878.451878] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[11878.451901] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[11878.646801] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[11878.646824] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[11878.786341] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[11878.786364] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
dawn@peter:~$



```

I found this same [modprobe error on an old DIR Wiki]("http://72.14.203.104/search?q=cache:H6Wn0ZCIG94J:dri.freedesktop.org/wiki/Building++Error+inserting+r128+Unknown+symbol+in+module,+or+unknown+parameter&hl=en&gl=us&ct=clnk&cd=2")



> 2.1. I cannot load my new DRM module on Linux Kernel 2.6.1

FATAL: Error inserting via (/lib/modules/2.6.1/kernel/
drivers/char/drm/<module name>.ko): Unknown symbol in module,
or unknown parameter (see dmesg)

This error occurs because there are some missing symbols in the 2.6.1 kernel source. One way to get around this problem is to upgrade your kernel to a newer version... (You *might* be able to patch the DRM code to avoid this... Not sure about this, though!)


$ uname -a
Linux peter 2.6.12-10-686 #1 Sat Mar 11 16:22:51 UTC 2006 i686 GNU/Linux

Obvious I am not using that kernel, but I am wondering what I could possibly have going on here. So far I have not found this problem mentioned anywhere I have searched. Has anyone else run into this situation? All I can think to do is try different kernels for a fix.


Paul

---

### Post by pjbgravely on 2006-04-22
Fixed,
The drivers I got from the DRI site came in 2 zip files, unzipped the files both had directories with the same name. I unzipped the first with the GUI, then ran the install script in a terminal. I then deleted the first file and unzipped the second with the GUI. When I ran the second install script in the terminal, that had the same name as the first one, I was actually rerunning the first which the terminal was still holding, even though I had deleted it with the GUI. If I had done everything in the terminal or GUI this wouldn't have happened. Oh well, we learn from our mistakes.

Paul

---

### Post by MrRoboto on 2006-07-31
hey i got the same error...
could you be so kind to tell me how you fixed it excatly?

thanks

---

### Post by pjbgravely on 2006-07-31
As stated in my above post but in brief, when you are done with the first folder, delete it and make sure you change the dir you are in  so that it is really deleted.

---

