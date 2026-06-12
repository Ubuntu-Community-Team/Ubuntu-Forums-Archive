---
title: "openvrml"
date: 2010-06-18
forum: General Help
---

### Post by wattana on 2010-06-18
Hi all!!

Sorry about my english... I know is quite bad...

I'm trying to compile the [openvrml ]("http://openvrml.org/") library, and I'm going nuts...

I follow the steps in the INSTALL archive, and the "configure" command returns me error after error...

Digging the web, I've found some missing libraries I need to install, and the correct way to call configure:

```
./configure --disable-script-node-java --disable-mozilla-plugin
```

Now "make" fails with this error:
```

../../src/libopenvrml/openvrml/local/parse_vrml.cpp:182:   instantiated from here
../../src/libopenvrml/openvrml/x3d_vrml_grammar.h:708: error: ‘const struct openvrml::local::x3d_vrml_parse_actions’ has no member named ‘on_mfdouble’
make[4]: *** [libopenvrml/openvrml/local/libopenvrml_libopenvrml_la-parse_vrml.lo] Error 1
make[4]: Leaving directory `/ddf/personal/luria/openvrml/build/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/ddf/personal/luria/openvrml/build/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/ddf/personal/luria/openvrml/build/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/ddf/personal/luria/openvrml/build'
make: *** [all] Error 2


```

Any help will be highly apreciated.

The openvrml library, in any case, has never been in the repositories?? 

Thanks!

---

### Post by Mugiwara no Tapir on 2010-07-27
hi

try with "openvrml-0.18.6" and install this dependences:

  libboost-iostreams-dev
  libmozjsOd-dbg

I hope help you....

---

