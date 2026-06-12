---
title: "No package 'gtk+-2.0' found"
date: 2009-12-12
forum: General Help
---

### Post by ThirdKind on 2009-12-12
Hello,
Installed Ubuntu on PC yesterday for purpose of using 'xoscope'...when I ./configure the program I get an error such as;

.....
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.2) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


I have looked in the usr/bin directory and the synaptic package manager for gtk-2.0 and it seems they have been installed..

I am new to ubuntu with only previous experience in windows.

Any help would be great. Thanks in Advance

---

### Post by Physical Hook on 2009-12-12
```
sudo apt-get install libgtk2.0-dev

```

You haven't installed development libraries.

---

### Post by ThirdKind on 2009-12-12
Thnaks for they reply,

Ran the code and presented with this;

0 upgraded, 59 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.3MB of archives.
After this operation, 75.2MB of additional disk space will be used
Do you want to continue [Y/n]?

-I gather I say yes??

In future when I get packages from 'synaptic package manager' do I need to run install code like you demonstrated before??

---

### Post by Physical Hook on 2009-12-12
> **ThirdKind said:**
> 
-I gather I say yes??
Yes.

> **ThirdKind said:**
> In future when I get packages from 'synaptic package manager' do I need to run install code like you demonstrated before??
Haven't used Synaptic for a while now - not really sure whether it shows libraries or not.

---

### Post by ThirdKind on 2009-12-12
Magical - Very Nicccce....Thanks alot,  it passed config -YAY

I have a couple questions about ubuntu;

-is there a book you could recommend that would explain linux.unix commands and ubuntu operating sys
-Do I need motherboard drivers (everything seems to be working fine)
-Do I have a firewall and virus protector already installed or do I need to get these as packages..

Sorry for the novice Q's

And  Again

Thanks alot

---

