---
title: "Can Anyone Make Heads Or Tails Of This?"
date: 2010-01-17
forum: General Help
---

### Post by Mark76 on 2010-01-17
> ~/kazehakase-0.5.8$ make
Making all in po
Making all in libegg
Making all in pixbufthumbnail
  CC    egg-pixbuf-thumbnail.o
egg-pixbuf-thumbnail.c:36:18: error: glib.h: No such file or directory
egg-pixbuf-thumbnail.c:37:24: error: glib/gi18n.h: No such file or directory
egg-pixbuf-thumbnail.c:38:25: error: glib/gstdio.h: No such file or directory
egg-pixbuf-thumbnail.c:40:38: error: gdk-pixbuf/gdk-pixbuf-io.h: No such file or directory
In file included from egg-pixbuf-thumbnail.c:42:
egg-pixbuf-thumbnail.h:25:35: error: gdk-pixbuf/gdk-pixbuf.h: No such file or directory
In file included from egg-pixbuf-thumbnail.c:42:
egg-pixbuf-thumbnail.h:30: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘typedef’
egg-pixbuf-thumbnail.h:39: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
egg-pixbuf-thumbnail.h:42: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
egg-pixbuf-thumbnail.h:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
egg-pixbuf-thumbnail.h:51: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
egg-pixbuf-thumbnail.h:54: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
egg-pixbuf-thumbnail.h:58: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘egg_pixbuf_save_thumbnail’
egg-pixbuf-thumbnail.h:61: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘egg_pixbuf_save_thumbnailv’
egg-pixbuf-thumbnail.h:66: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘egg_pixbuf_has_failed_thumbnail’
egg-pixbuf-thumbnail.h:69: warning: type defaults to ‘int’ in declaration of ‘gchar’
egg-pixbuf-thumbnail.h:69: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.h:73: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘egg_pixbuf_is_thumbnail’
egg-pixbuf-thumbnail.h:78: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘egg_pixbuf_get_thumbnail_size’
egg-pixbuf-thumbnail.h:79: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.h:82: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gchar’
egg-pixbuf-thumbnail.h:83: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.h:85: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gchar’
egg-pixbuf-thumbnail.h:86: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.h:88: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gchar’
egg-pixbuf-thumbnail.h:89: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.h:91: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.h:92: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.h:94: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘egg_pixbuf_get_thumbnail_filesize’
egg-pixbuf-thumbnail.h:95: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.h:97: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘egg_pixbuf_get_thumbnail_image_width’
egg-pixbuf-thumbnail.h:98: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.h:100: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘egg_pixbuf_get_thumbnail_image_height’
egg-pixbuf-thumbnail.h:101: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.h:103: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘egg_pixbuf_get_thumbnail_document_pages’
egg-pixbuf-thumbnail.h:104: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.h:106: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.h:107: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.h:110: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gchar’
egg-pixbuf-thumbnail.h:112: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
egg-pixbuf-thumbnail.c:97: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘typedef’
egg-pixbuf-thumbnail.c:124: error: expected specifier-qualifier-list before ‘gint’
egg-pixbuf-thumbnail.c:136: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘thumbnail_data_get_quark’
egg-pixbuf-thumbnail.c: In function ‘thumbnail_data_free’:
egg-pixbuf-thumbnail.c:152: warning: implicit declaration of function ‘g_free’
egg-pixbuf-thumbnail.c:152: error: ‘ThumbnailData’ has no member named ‘uri’
egg-pixbuf-thumbnail.c:153: error: ‘ThumbnailData’ has no member named ‘mime_type’
egg-pixbuf-thumbnail.c:154: error: ‘ThumbnailData’ has no member named ‘description’
egg-pixbuf-thumbnail.c:155: error: ‘ThumbnailData’ has no member named ‘software’
egg-pixbuf-thumbnail.c: At top level:
egg-pixbuf-thumbnail.c:160: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.c:166: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.c:195: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘parse_thumbnail_data’
egg-pixbuf-thumbnail.c:325: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ensure_one_dir’
egg-pixbuf-thumbnail.c:344: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ensure_thumbnail_dirs’
egg-pixbuf-thumbnail.c:405: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.c:429: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
egg-pixbuf-thumbnail.c:572: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
egg-pixbuf-thumbnail.c:695: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
egg-pixbuf-thumbnail.c:737: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
egg-pixbuf-thumbnail.c:790: error: expected ‘)’ before ‘opts’
egg-pixbuf-thumbnail.c:842: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘egg_pixbuf_save_thumbnail’
egg-pixbuf-thumbnail.c:868: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
egg-pixbuf-thumbnail.c:882: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.c:1013: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘egg_pixbuf_save_thumbnailv’
egg-pixbuf-thumbnail.c:1114: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘egg_pixbuf_has_failed_thumbnail’
egg-pixbuf-thumbnail.c:1166: warning: type defaults to ‘int’ in declaration of ‘gchar’
egg-pixbuf-thumbnail.c:1166: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.c:1273: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
egg-pixbuf-thumbnail.c:1339: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘egg_pixbuf_is_thumbnail’
egg-pixbuf-thumbnail.c:1391: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘egg_pixbuf_get_thumbnail_size’
egg-pixbuf-thumbnail.c:1414: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.c:1437: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gchar’
egg-pixbuf-thumbnail.c:1460: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.c:1483: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gchar’
egg-pixbuf-thumbnail.c:1506: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.c:1531: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gchar’
egg-pixbuf-thumbnail.c:1554: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.c:1580: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.c:1602: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.c:1625: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘egg_pixbuf_get_thumbnail_filesize’
egg-pixbuf-thumbnail.c:1647: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.c:1671: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘egg_pixbuf_get_thumbnail_image_width’
egg-pixbuf-thumbnail.c:1693: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.c:1717: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘egg_pixbuf_get_thumbnail_image_height’
egg-pixbuf-thumbnail.c:1739: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.c:1763: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘egg_pixbuf_get_thumbnail_document_pages’
egg-pixbuf-thumbnail.c:1786: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.c:1810: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.c:1832: error: expected ‘)’ before ‘*’ token
egg-pixbuf-thumbnail.c:1855: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gchar’
egg-pixbuf-thumbnail.c:1885: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make[4]: *** [libeggpixbufthumbnail_la-egg-pixbuf-thumbnail.lo] Error 1
make[3]: *** [all] Error 2
make[2]: *** [all-recursive] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2


:?

---

### Post by lisati on 2010-01-17
OK, going with the first rule of interpreting error messages ("fix the reason for the first error message and many other error messages will go away"), I'd say that it's  related to glib files not being available.

---

### Post by Mark76 on 2010-01-17
But they are available.

Look!

[ATTACH]143953[/ATTACH]

---

### Post by falconindy on 2010-01-17
You haven't shown us what you did before the make (or what your end goal is). The configure step becomes extremely important when debugging this kind of stuff.

---

