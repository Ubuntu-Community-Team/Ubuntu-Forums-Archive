---
title: "I need help with the make command!"
date: 2010-05-26
forum: General Help
---

### Post by glopso on 2010-05-26
I have never successfully run a "make" command. They always can't find some library. Here is my most recent one, which I need to be working so I can jailbreak my ipod.

> leon@leon-desktop:~/posixninja-spirit-linux-37db2fe$ make
gcc -std=gnu99 -c -o spirit.o spirit.c
spirit.c:28:25: error: openssl/sha.h: No such file or directory
spirit.c:29:25: error: plist/plist.h: No such file or directory
spirit.c:30:34: error: libimobiledevice/afc.h: No such file or directory
spirit.c:31:39: error: libimobiledevice/lockdown.h: No such file or directory
spirit.c:32:43: error: libimobiledevice/mobilebackup.h: No such file or directory
spirit.c:33:47: error: libimobiledevice/libimobiledevice.h: No such file or directory
In file included from spirit.c:35:
afc.h:24: error: expected ‘)’ before ‘afc’
afc.h:25: error: expected ‘)’ before ‘afc’
afc.h:26: error: expected ‘)’ before ‘afc’
afc.h:27: error: expected ‘)’ before ‘afc’
afc.h:28: error: expected ‘)’ before ‘afc’
spirit.c:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘device’
spirit.c:47: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘lockdownd’
spirit.c:49: error: expected ‘)’ before ‘backup’
spirit.c: In function ‘sha1_of_data’:
spirit.c:59: error: ‘SHA_CTX’ undeclared (first use in this function)
spirit.c:59: error: (Each undeclared identifier is reported only once
spirit.c:59: error: for each function it appears in.)
spirit.c:59: error: expected ‘;’ before ‘ctx’
spirit.c:60: warning: implicit declaration of function ‘SHA1_Init’
spirit.c:60: error: ‘ctx’ undeclared (first use in this function)
spirit.c:61: warning: implicit declaration of function ‘SHA1_Update’
spirit.c:62: warning: implicit declaration of function ‘SHA1_Final’
spirit.c: At top level:
spirit.c:107: error: expected ‘)’ before ‘afc’
spirit.c: In function ‘send_files_thread’:
spirit.c:137: error: ‘lockdownd_error_t’ undeclared (first use in this function)
spirit.c:137: error: expected ‘;’ before ‘lockdownd_error’
spirit.c:139: error: ‘lockdownd_error’ undeclared (first use in this function)
spirit.c:139: warning: implicit declaration of function ‘lockdownd_client_new_with_handshake’
spirit.c:139: error: ‘device’ undeclared (first use in this function)
spirit.c:139: error: ‘lockdownd’ undeclared (first use in this function)
spirit.c:140: error: ‘LOCKDOWN_E_SUCCESS’ undeclared (first use in this function)
spirit.c:145: error: ‘afc_client_t’ undeclared (first use in this function)
spirit.c:145: error: expected ‘;’ before ‘afc’
spirit.c:148: error: expected ‘;’ before ‘lockdown_err’
spirit.c:149: error: ‘lockdown_err’ undeclared (first use in this function)
spirit.c:154: error: ‘afc_error_t’ undeclared (first use in this function)
spirit.c:154: error: expected ‘;’ before ‘afc_err’
spirit.c:155: error: ‘afc_err’ undeclared (first use in this function)
spirit.c:155: error: ‘AFC_E_SUCCESS’ undeclared (first use in this function)
spirit.c:161: error: ‘plist_t’ undeclared (first use in this function)
spirit.c:161: error: expected ‘;’ before ‘node’
spirit.c:164: warning: implicit declaration of function ‘lockdownd_get_value’
spirit.c:164: error: ‘node’ undeclared (first use in this function)
spirit.c:165: warning: implicit declaration of function ‘plist_get_string_val’
spirit.c:166: warning: implicit declaration of function ‘plist_free’
spirit.c:175: warning: implicit declaration of function ‘lockdownd_client_free’
spirit.c:188: warning: implicit declaration of function ‘afc_client_free’
spirit.c:188: error: ‘afc’ undeclared (first use in this function)
spirit.c:192: error: expected ‘;’ before ‘map’
spirit.c:193: warning: implicit declaration of function ‘plist_from_xml’
spirit.c:193: error: ‘map’ undeclared (first use in this function)
spirit.c:194: error: expected ‘;’ before ‘one_dylib_node’
spirit.c:195: error: ‘one_dylib_node’ undeclared (first use in this function)
spirit.c:204: warning: implicit declaration of function ‘afc_remove_all’
spirit.c:205: warning: implicit declaration of function ‘afc_create_directory’
spirit.c:208: warning: implicit declaration of function ‘send_over’
spirit.c: At top level:
spirit.c:223: error: expected ‘)’ before ‘backup’
spirit.c:256: error: expected ‘)’ before ‘files’
spirit.c:298: error: expected ‘)’ before ‘backup’
spirit.c: In function ‘restore_thread’:
spirit.c:326: error: ‘lockdownd_error_t’ undeclared (first use in this function)
spirit.c:326: error: expected ‘;’ before ‘lockdownd_error’
spirit.c:328: error: ‘lockdownd_error’ undeclared (first use in this function)
spirit.c:328: error: ‘device’ undeclared (first use in this function)
spirit.c:328: error: ‘lockdownd’ undeclared (first use in this function)
spirit.c:329: error: ‘LOCKDOWN_E_SUCCESS’ undeclared (first use in this function)
spirit.c:334: error: ‘mobilebackup_client_t’ undeclared (first use in this function)
spirit.c:334: error: expected ‘;’ before ‘backup’
spirit.c:337: error: expected ‘;’ before ‘lockdown_err’
spirit.c:338: error: ‘lockdown_err’ undeclared (first use in this function)
spirit.c:348: error: ‘mobilebackup_error_t’ undeclared (first use in this function)
spirit.c:348: error: expected ‘;’ before ‘backup_err’
spirit.c:349: error: ‘backup_err’ undeclared (first use in this function)
spirit.c:349: error: ‘MOBILEBACKUP_E_SUCCESS’ undeclared (first use in this function)
spirit.c:356: error: ‘plist_t’ undeclared (first use in this function)
spirit.c:356: error: expected ‘;’ before ‘files’
spirit.c:358: error: expected ‘;’ before ‘overrides’
spirit.c:359: error: expected ‘;’ before ‘use_gmalloc’
spirit.c:361: warning: implicit declaration of function ‘start_restore’
spirit.c:361: error: ‘backup’ undeclared (first use in this function)
spirit.c:361: error: ‘files’ undeclared (first use in this function)
spirit.c:363: warning: implicit declaration of function ‘send_file’
spirit.c:363: error: ‘overrides’ undeclared (first use in this function)
spirit.c:364: error: ‘use_gmalloc’ undeclared (first use in this function)
spirit.c:367: warning: implicit declaration of function ‘mobilebackup_client_free’
spirit.c: In function ‘main’:
spirit.c:375: error: ‘idevice_error_t’ undeclared (first use in this function)
spirit.c:375: error: expected ‘;’ before ‘device_error’
spirit.c:379: warning: implicit declaration of function ‘idevice_get_device_list’
spirit.c:386: warning: implicit declaration of function ‘idevice_device_list_free’
spirit.c:389: error: ‘device_error’ undeclared (first use in this function)
spirit.c:389: warning: implicit declaration of function ‘idevice_new’
spirit.c:389: error: ‘device’ undeclared (first use in this function)
spirit.c:390: error: ‘IDEVICE_E_SUCCESS’ undeclared (first use in this function)
spirit.c:391: error: ‘IDEVICE_E_NO_DEVICE’ undeclared (first use in this function)
spirit.c:404: warning: implicit declaration of function ‘idevice_free’
make: *** [spirit.o] Error 1
Popcorn for whoever helps me?:popcorn:

---

### Post by gadolinio on 2010-05-27
Did you find any error messages when running the ./configure command, if there's one?
Read this; it could help: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo).

---

### Post by glopso on 2010-05-27
> **gadolinio said:**
> Did you find any error messages when running the ./configure command, if there's one?
Read this; it could help: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo).

What ./configure? Oh you mean the one in the folder not related to this? Nah, it's fine. But I still need an interpretation on my errors.

---

### Post by mc4man on 2010-05-27
Your missing  an openssl header and libimobiledevice, plist headers - try this

```
sudo apt-get install libimobiledevice-dev libplist-dev libusbmuxd-dev libssl-dev
```

---

### Post by gadolinio on 2010-05-27
> **glopso said:**
> What ./configure? Oh you mean the one in the folder not related to this? Nah, it's fine. But I still need an interpretation on my errors.

Sorry, I don't understand what you say XD  No configure script for that application? :S

---

