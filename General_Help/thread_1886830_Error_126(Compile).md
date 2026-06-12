---
title: "Error 126(Compile)"
date: 2011-11-25
forum: General Help
---

### Post by sasha19323 on 2011-11-25
```
/bin/bash: /media/A8B4E5A5B4E575EA/u-boot-2011.09/mkconfig: Permission denied
make: *** [SX1_config] Error 126

```SX1_config(Makefile):
```
SX1_config:        unconfig
    @mkdir -p $(obj)include
    @if [ "$(findstring _stdout_serial_, $@)" ] ; then \
        echo "#undef CONFIG_STDOUT_USBTTY" >> $(obj)include/config.h ; \
    else \
        echo "#define CONFIG_STDOUT_USBTTY" >> $(obj)include/config.h ; \
    fi;
    @$(MKCONFIG) -n $@ SX1 arm arm926ejs sx1

```What's wrong?:confused:

---

