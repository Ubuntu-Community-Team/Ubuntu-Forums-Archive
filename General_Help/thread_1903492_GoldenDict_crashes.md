---
title: "GoldenDict crashes"
date: 2012-01-02
forum: General Help
---

### Post by yoramdavid on 2012-01-02
Hello all,

I use GoldenDict a lot, on a daily basis and for the last week I was not able to use it as it crashes on loading with the following error:

```
GoldenDict has crashed with an unexpected exception

Exception: Config::exMalformedConfigFile
Message: The configuration file is malformed

Backtrace:
  /usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0xb9f26) [0x7ffda8bf4f26]
  /usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0xb9f53) [0x7ffda8bf4f53]
  /usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0xba04e) [0x7ffda8bf504e]
  goldendict(Config::load()+0x1385) [0x476ea5]
  goldendict(main+0x19b) [0x44d0bb]
  /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed) [0x7ffda832330d]
  goldendict() [0x44f5e1]

This information is located in file /tmp/qt_temp.J28896, which will be removed once you close this dialog.
```

I have completely removed GoldenDict from synaptic then reinstalled it, I reinstalled anything similar with "libstdc" but no luck.

How do I fix this?
Regards

---

### Post by Paddy Landau on 2012-01-03
Deinstalling and reinstalling will do nothing, because it won't change the settings. It just replaces the program with itself.

To reset the settings, you need to find where GoldenDict stores the settings -- probably a hidden file such as ~/.goldendict (note the leading dot) -- and delete it.

Of course, that will reset all your settings as if you'd never run it before.

This presumes that the configuration file has been corrupted. If that's not the case, resetting the settings probably won't help.

---

### Post by Frogs Hair on 2012-01-03
Installing the Gnome Desktop Utilities will include the dictionary that used to come with Ubuntu . You may find you may have most of the packages in the bundle installed . The dictionary will not include the ability add multiple dictionaries like Golden .

---

### Post by yoramdavid on 2012-01-03
> **Paddy Landau said:**
> Deinstalling and reinstalling will do nothing, because it won't change the settings. It just replaces the program with itself.

To reset the settings, you need to find where GoldenDict stores the settings -- probably a hidden file such as ~/.goldendict (note the leading dot) -- and delete it.

Of course, that will reset all your settings as if you'd never run it before.

This presumes that the configuration file has been corrupted. If that's not the case, resetting the settings probably won't help.

Thank you Paddy Landau,

That solved the problem.
I thought that uninstalling completely it would also remove the configuration files.
The config file was 0 bytes in size, now it is 13 kb. I have saved a backup od the .Goldendict folder this time.

Regards,
Yoram

---

### Post by Paddy Landau on 2012-01-03
> **yoramdavid said:**
> I thought that uninstalling completely it would also remove the configuration files.
Ex-Windows users often think that, because Windows uses the Registry. However, Linux's security model has a strict separation of users; if root (which installs, updates and deinstalls programs) were to fiddle with every user's configurations, that would violate the security model.

(Because Linux strictly separates users, two or more users can sign into a Linux machine and use it *at the same time* without affecting each other, except of course for performance.)

If you reinstall, you will at most affect the system-wide configuration files, if for some reason you had changed them. Normally, though, it won't, because (usually) a program would create a default configuration file only if it didn't already exist.

An example is Samba, whose configuration files are global and therefore modified by root. If you change Samba's configuration file, then deinstall and reinstall Samba, the configuration file will still be as you last left it.

---

### Post by yoramdavid on 2012-01-03
> **Frogs Hair said:**
> Installing the Gnome Desktop Utilities will include the dictionary that used to come with Ubuntu . You may find you may have most of the packages in the bundle installed . The dictionary will not include the ability add multiple dictionaries like Golden .

Thank you Frogs Hair,

Yes, I have that dictionary installed but I never understood how it worked, it opens, I type a word and nothing  happens. GoldenDict is my favourite. It is great.

Regards,

Yoram

---

### Post by yoramdavid on 2012-01-03
> **Paddy Landau said:**
> Ex-Windows users often think that, because Windows uses the Registry. However, Linux's security model has a strict separation of users; if root (which installs, updates and deinstalls programs) were to fiddle with every user's configurations, that would violate the security model.

(Because Linux strictly separates users, two or more users can sign into a Linux machine and use it *at the same time* without affecting each other, except of course for performance.)

If you reinstall, you will at most affect the system-wide configuration files, if for some reason you had changed them. Normally, though, it won't, because (usually) a program would create a default configuration file only if it didn't already exist.

An example is Samba, whose configuration files are global and therefore modified by root. If you change Samba's configuration file, then deinstall and reinstall Samba, the configuration file will still be as you last left it.

Thank you for explaining, Paddy Landau.

Regards,
Yoram

---

