---
title: "how to open a .bin file"
date: 2009-12-08
forum: General Help
---

### Post by savage123 on 2009-12-08
how do i open a .bin file?

---

### Post by fancypiper on 2009-12-08
.bin files are binaries and need to be run.

1. Make the file executable if it isn't already.
chmod 755 /path/to/<name>.bin
2. Execute the file
For user:
/path/to/<name>.bin
For system wide:
sudo /path/to/<name>.bin

[How To Install Software in Linux](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html)

[How to install ANYTHING in Ubuntu!](http://amitech.50webs.com/installing/index.php.html)

---

### Post by sanderj on 2009-12-08
Together with a .cue file, a .bin file is an image file. See [http://www.ubuntugeek.com/how-to-convert-bincue-files-to-iso-in-ubuntu.html](http://www.ubuntugeek.com/how-to-convert-bincue-files-to-iso-in-ubuntu.html) how to convert to iso.

---

### Post by kellemes on 2009-12-08
> **sanderj said:**
> Together with a .cue file, a .bin file is an image file. See [http://www.ubuntugeek.com/how-to-convert-bincue-files-to-iso-in-ubuntu.html](http://www.ubuntugeek.com/how-to-convert-bincue-files-to-iso-in-ubuntu.html) how to convert to iso.

Possible indeed.
But a .bin file in a unix environment can also be a compiled binary file.

---

### Post by shantiq on 2010-10-24
> **sanderj said:**
> Together with a .cue file, a .bin file is an image file. See [http://www.ubuntugeek.com/how-to-convert-bincue-files-to-iso-in-ubuntu.html](http://www.ubuntugeek.com/how-to-convert-bincue-files-to-iso-in-ubuntu.html) how to convert to iso.


to open them to wav

use  

```
sudo apt-get bchunk 

```




then
```
bchunk -w filename.bin filename.cue filename.wav

```

---

