---
title: "gnome-panel crashes"
date: 2004-10-19
forum: General Help
---

### Post by tanari on 2004-10-19
```

Backtrace was generated from '/usr/bin/gnome-panel'

&#40;no debugging symbols found&#41;...Using host libthread_db library &quot;/lib/tls/i686/cmov/libthread_db.so.1&quot;.
&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#91;Thread debugging using libthread_db enabled&#93;
&#91;New Thread 1087412160 &#40;LWP 3784&#41;&#93;
&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...&#40;no debugging symbols found&#41;...0xffffe410 in __kernel_vsyscall &#40;&#41;
#0  0xffffe410 in __kernel_vsyscall &#40;&#41;
#1  0x40a62403 in __waitpid_nocancel &#40;&#41;
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x4009b3dd in libgnomeui_module_info_get &#40;&#41;
   from /usr/lib/libgnomeui-2.so.0
#3  &lt;signal handler called&gt;
#4  0x40b7a26a in wcsxfrm &#40;&#41; from /lib/tls/i686/cmov/libc.so.6
#5  0x40aaae11 in g_utf8_collate_key &#40;&#41; from /usr/lib/libglib-2.0.so.0
#6  0x0808372c in fr_compare &#40;&#41;
#7  0x40a9e361 in g_slist_insert_sorted &#40;&#41; from /usr/lib/libglib-2.0.so.0
#8  0x40a9e406 in g_slist_insert_sorted &#40;&#41; from /usr/lib/libglib-2.0.so.0
#9  0x40a9e3c6 in g_slist_insert_sorted &#40;&#41; from /usr/lib/libglib-2.0.so.0
#10 0x40a9e3c6 in g_slist_insert_sorted &#40;&#41; from /usr/lib/libglib-2.0.so.0
#11 0x40a9e435 in g_slist_sort &#40;&#41; from /usr/lib/libglib-2.0.so.0
#12 0x08082a84 in get_mfiles_from_menudir &#40;&#41;
#13 0x08082e38 in fr_read_dir &#40;&#41;
#14 0x08082ad8 in get_mfiles_from_menudir &#40;&#41;
#15 0x08082e38 in fr_read_dir &#40;&#41;
#16 0x0807ae7a in init_menus &#40;&#41;
#17 0x08063535 in main &#40;&#41;

Thread 1 &#40;Thread 1087412160 &#40;LWP 3784&#41;&#41;&#58;
#0  0xffffe410 in __kernel_vsyscall &#40;&#41;
No symbol table info available.
#1  0x40a62403 in __waitpid_nocancel &#40;&#41;
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0x4009b3dd in libgnomeui_module_info_get &#40;&#41;
   from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  &lt;signal handler called&gt;
No symbol table info available.
#4  0x40b7a26a in wcsxfrm &#40;&#41; from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#5  0x40aaae11 in g_utf8_collate_key &#40;&#41; from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0x0808372c in fr_compare &#40;&#41;
No symbol table info available.
#7  0x40a9e361 in g_slist_insert_sorted &#40;&#41; from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0x40a9e406 in g_slist_insert_sorted &#40;&#41; from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0x40a9e3c6 in g_slist_insert_sorted &#40;&#41; from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0x40a9e3c6 in g_slist_insert_sorted &#40;&#41; from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#11 0x40a9e435 in g_slist_sort &#40;&#41; from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#12 0x08082a84 in get_mfiles_from_menudir &#40;&#41;
No symbol table info available.
#13 0x08082e38 in fr_read_dir &#40;&#41;
No symbol table info available.
#14 0x08082ad8 in get_mfiles_from_menudir &#40;&#41;
No symbol table info available.
#15 0x08082e38 in fr_read_dir &#40;&#41;
No symbol table info available.
#16 0x0807ae7a in init_menus &#40;&#41;
No symbol table info available.
#17 0x08063535 in main &#40;&#41;
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall &#40;&#41;

```

i can't see gnome panels :(
i just updated something through synaptic

---

