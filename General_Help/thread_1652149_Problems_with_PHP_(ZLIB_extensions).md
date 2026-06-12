---
title: "Problems with PHP (ZLIB extensions)"
date: 2010-12-24
forum: General Help
---

### Post by kleyber on 2010-12-24
Hi to all,

I know this is Christmas Eve and everybody is getting ready to the Christmas, but I am here, this is my first post and I have a problem that I don't know how to solve.

I have installed Ubuntu Server 10.10 on my computer and LAMP which comes with PHP 5.3. The problem is I have a software that runs just with PHP 5.2 and I had to downgrade it. After downgrading, when I try to make upload of a file in my project, I see the message: "Abort pclzip.lib.php : Missing zlib extensions". How to solve this? I have seen many articles on Google, but nothing about Ubuntu 10.10 server. Any clues?

TIA and Merry Christmas to all

Kleyber

---

### Post by IamNot on 2010-12-24
zlib extension is not enabled by default. Check if that's the problem using phpinfo().

---

### Post by kleyber on 2010-12-24
> **IamNot said:**
> zlib extension is not enabled by default. Check if that's the problem using phpinfo().

The PHPINFO() gives me that:

**[SIZE=2]zlib[/SIZE]**

  [SIZE=2]ZLib Support [/SIZE][SIZE=2]enabled [/SIZE] [SIZE=2]Stream Wrapper support [/SIZE][SIZE=2]compress.zlib:// [/SIZE] [SIZE=2]Stream Filter support [/SIZE][SIZE=2]zlib.inflate, zlib.deflate [/SIZE] [SIZE=2]Compiled Version [/SIZE][SIZE=2]1.2.3 [/SIZE] [SIZE=2]Linked Version [/SIZE][SIZE=2]1.2.3 [/SIZE] [SIZE=2]
[/SIZE]  [SIZE=2]Directive[/SIZE][SIZE=2]Local Value[/SIZE][SIZE=2]Master Value[/SIZE] [SIZE=2]zlib.output_compression[/SIZE][SIZE=2]Off[/SIZE][SIZE=2]Off[/SIZE] [SIZE=2]zlib.output_compression_level[/SIZE][SIZE=2]-1[/SIZE][SIZE=2]-1[/SIZE] [SIZE=2]zlib.output_handler[/SIZE][SIZE=2]*no value*[/SIZE][SIZE=2]*no value*[/SIZE][SIZE=2]
[/SIZE]
But even with this info, when i try to upload a file, the error "Abort pclzip.lib.php : Missing zlib extensions" still appears.

---

### Post by kleyber on 2010-12-24
Any other clues?

---

