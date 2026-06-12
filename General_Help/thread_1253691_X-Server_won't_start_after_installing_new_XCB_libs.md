---
title: "X-Server won't start after installing new XCB libs"
date: 2009-08-30
forum: General Help
---

### Post by zolero on 2009-08-30
Hi everybody.

I am on Ubuntu Hardy Heron, and got a big problem with X-Server and GDM. Few days ago I was compiling the latest XCB libraries, the XCB-PROTO, and some other necessary stuffs (intltool, dbus-glib-1-2) from latest sources (pulled from Karmic). The builds weren't performed traditionally with dh_build, but manually, and packages obtained from checkinstall were also manually arranged to follow the Ubuntu packaging guidance. The point in doing this is to build and install at the final point the latest GDM package (from Karmic too), because of an annoying error on system restart/shutdown in Hardy version:

```
gdm[6282]: GLIB-CRITICAL: g_hash_table_lookup_extended: assertion 'hash_table != NULL' failed
gdm[6282]: WARNING: Request for invalid configuration key xdmcp/Enable=false
```which is also described in [this bugreport]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/249039"), where it's claimed to be solved in version 2.20.8 and higher. The XCB libraries mentioned before are build depends for GDM.

All OK till here. My problem went after I've installed the XCB libraries (libs and libdevels) and restarting to try out how it works in live mode. The X-Server won't start at all. Its error message was (see the screenshot):

[http://img18.imageshack.us/img18/2152/xserverisrunningerror.jpg](http://img18.imageshack.us/img18/2152/xserverisrunningerror.jpg)

I've also tried to install GDM from Intrepid and Jaunty (after I've tricked the package dependencies to fit) but result was the same. Moreover, I've tried to install my selfbuilt 2.27.4 version (backported from Karmic) without the XCB libs suite, in which case GDM won't start at all, but I was able to login into console, and start X manually.

As a side note I mention that XCB libs breaks libxcb-xlib which I have purged when used those libs.

Had anyone this problem? Is here anyone who can help me to solve this? Any tips will come in handy, and I thank you for them in advance.

---

