---
title: "Failed to compile &quot;obfsproxy&quot;"
date: 2012-06-01
forum: General Help
---

### Post by sempak on 2012-06-01
Need help.....!!!

I have ubuntu maverick on my Desktop, i try to compile "obfsproxy" on it but failed.
I just following the instruction: [http://tor.loritsu.com/projects/obfsproxy-instructions.html.en#instructions](http://tor.loritsu.com/projects/obfsproxy-instructions.html.en#instructions)

but failed to compile with this warning in the last compilation:
```

checking for libevent... yes
checking for libcrypto... no
configure: error: Package requirements (libcrypto >= 0.9.7) were not met:

No package 'libcrypto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables libcrypto_CFLAGS
and libcrypto_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by Cheesemill on 2012-06-01
Install the missing [libcrypto++-dev]("apt://libcrypto++-dev") package and try again :)

---

### Post by sempak on 2012-06-01
> **Cheesemill said:**
> Install the missing [libcrypto++-dev]("apt://libcrypto++-dev") package and try again :)


still can't...!!!

any more advice.....

---

