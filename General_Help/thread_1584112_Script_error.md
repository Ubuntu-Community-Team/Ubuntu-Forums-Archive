---
title: "Script error"
date: 2010-09-28
forum: General Help
---

### Post by viperwontbyte on 2010-09-28
Hi everyone.  I'm having a hard time with a script.  It's purpose is to install an Enigma1 image.  It chokes and i don't know what to do.  Can someone please take a look at this error and give me a hand?

[COLOR=#808000][COLOR=#808000][SIZE=2]( rm -rf  zlib-1.2.3 || /bin/true ) && bunzip2 -cd  Archive/zlib-1.2.3.tar.bz2 | tar -x && ( cd zlib-1.2.3; patch  -p1 < ../Patches/zlib.diff )
bunzip2: Archive/zlib-1.2.3.tar.bz2 is not a bzip2 file.
tar: This does not look like a tar archive
tar: Exiting with failure status due to previous errors
make: *** [.libz] Error 2
viperbyte ubuntu:~/tuxbox-cvs/cdk$ 

[/SIZE][SIZE=1]
[/SIZE][/COLOR][/COLOR]

---

### Post by DaithiF on 2010-09-29
[COLOR=#808000][COLOR=#808000][SIZE=2][COLOR=Black]Hi,
Its complaining that the [/COLOR][/SIZE][/COLOR][/COLOR][COLOR=#808000][COLOR=#808000][SIZE=2]Archive/zlib-1.2.3.tar.bz2 [COLOR=Black]file is not a valid bz2 file, and it cannot decompress it.  Perhaps a corruption to the file while downloading it, try re-downloading, and checking against a checksum (if provided)

[/COLOR][/SIZE][/COLOR][/COLOR]

---

