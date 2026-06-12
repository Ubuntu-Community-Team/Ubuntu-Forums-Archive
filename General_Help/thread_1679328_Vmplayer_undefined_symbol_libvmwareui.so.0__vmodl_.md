---
title: "Vmplayer undefined symbol libvmwareui.so.0 : vmodl_vmomi_key_any_value_get_type"
date: 2011-01-31
forum: General Help
---

### Post by ikus060 on 2011-01-31
I recently wanned to use my vmplayer installation and I got the following error :

/usr/lib/vmware/bin/vmplayer: symbol lookup error: /usr/lib/vmware/lib/libvmwareui.so.0/libvmwareui.so.0: undefined symbol: vmodl_vmomi_key_any_value_get_type

I try to reinstall vmplayer. It didn't help.

Any suggestion ?

---

### Post by masterdje on 2011-04-05
Same here, used to work like a charm, reboot, won't work anymore...

[ Linux ORDXXXX 2.6.32-32-server #55-Ubuntu SMP Mon Jan 10 23:57:16 UTC 2011 x86_64 GNU/Linux ]

---

### Post by ikus060 on 2011-04-05
I forgot to update the post.

I manage to solve the issue. VMWare player and VMWare Remote Console was conflicting. So solved it, I remove all the lib* related to vmware and then reinstall VMWare player.

I didn't reinstall VMWare Remote Console.

---

