---
title: "installing curlftpfs get glib error"
date: 2010-12-02
forum: General Help
---

### Post by conradin on 2010-12-02
Hi All 
Im trying to install cUrlFtpFs.  I get an error when  run the configure file though, it says:
***************************************************
checking for GLIB... configure: error: Package requirements (glib-2.0) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
***********************************************

echo $PKG_CONFIG_PATH
echo $GLIB_LIBS
echo $GLIB_CFLAGS

shows nothing. what should I do here?

---

### Post by conradin on 2010-12-02
Ok, I used a different package & it works!

---

