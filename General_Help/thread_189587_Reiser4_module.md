---
title: "Reiser4 module"
date: 2006-06-05
forum: General Help
---

### Post by nightw on 2006-06-05
Hello!

I've some reiser4 partitions from my last distro. I would like to access them with my newly installed ubuntu. I think the best way would be a new reiser4 modul additionally to the other one's, which are supported by default. I've installed the proper linux-sources which has the same version as my binary kernel package. I've unpacked, patched and compiled it. So i have a reiser4 module now. I've put it to /lib/modules/2.6.15-23-386/kernel/fs/reiser4/reiser4.ko (i had to make the reiser4 dir). Then made a depmod -a. After that i copied the new zlib_deflate.ko module(maybe it's been patched) to the proper directory, because reiser4 has a dependency on it. Then i typed modprobe reiser4 and got this error message:

```

[4295427.104000] reiser4: no version for "struct_module" found: kernel tainted.
[4295427.108000] reiser4: Unknown symbol page_cache_readahead
[4295427.108000] reiser4: Unknown symbol __remove_from_page_cache
[4295427.108000] reiser4: Unknown symbol radix_tree_preload
[4295427.109000] reiser4: Unknown symbol generic_sync_sb_inodes
[4295427.109000] reiser4: Unknown symbol handle_ra_miss
[4295427.109000] reiser4: Unknown symbol find_get_pages_tag
[4295427.110000] reiser4: Unknown symbol add_to_page_cache_lru
[4295427.110000] reiser4: Unknown symbol truncate_inode_pages_range
[4295427.111000] reiser4: Unknown symbol find_get_pages
[4295427.111000] reiser4: Unknown symbol remove_from_page_cache
[4295674.950000] reiser4: Unknown symbol page_cache_readahead
[4295674.950000] reiser4: Unknown symbol __remove_from_page_cache
[4295674.950000] reiser4: Unknown symbol radix_tree_preload
[4295674.950000] reiser4: Unknown symbol generic_sync_sb_inodes
[4295674.950000] reiser4: Unknown symbol handle_ra_miss
[4295674.951000] reiser4: Unknown symbol find_get_pages_tag
[4295674.951000] reiser4: Unknown symbol add_to_page_cache_lru
[4295674.951000] reiser4: Unknown symbol truncate_inode_pages_range
[4295674.951000] reiser4: Unknown symbol find_get_pages
[4295674.951000] reiser4: Unknown symbol remove_from_page_cache
[4296767.198000] reiser4: Unknown symbol page_cache_readahead
[4296767.198000] reiser4: Unknown symbol __remove_from_page_cache
[4296767.198000] reiser4: Unknown symbol radix_tree_preload
[4296767.198000] reiser4: Unknown symbol generic_sync_sb_inodes
[4296767.198000] reiser4: Unknown symbol handle_ra_miss
[4296767.199000] reiser4: Unknown symbol find_get_pages_tag
[4296767.199000] reiser4: Unknown symbol add_to_page_cache_lru
[4296767.199000] reiser4: Unknown symbol truncate_inode_pages_range
[4296767.200000] reiser4: Unknown symbol find_get_pages
[4296767.200000] reiser4: Unknown symbol remove_from_page_cache

```

And i noticed that, _every_ kernel module, which i've compiled has different size, that the default ones in /lib/modules. I've read a howto and i could do a make-kpkg, but i don't want a new kernel if it's not necessary. I'd like to have just an additional reiser4 module.

Can anybody has any ideas?

Thank you, bye: nightw

---

### Post by JoWilly on 2006-06-05
What you need to do if you want so stay with your actual kernel is:

1. install linux-source from synaptic.
2. patch it with reiser4
3. copy .config over from /boot
4. "make oldconfig " in  the  patched kernel source dir to add reiser 4 to your config.
5. "make menuconfig" and select reiser4 fs
6. go on with the howto
7. you will then need to boot this newly compiled kernel (but  it is the same as the original, only that it has the added reiser4).

Best wishes.

---

