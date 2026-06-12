---
title: "VMware WS and Player - not working"
date: 2006-06-02
forum: General Help
---

### Post by kbudurka on 2006-06-02
I had a running 5.10, but last night I did a dist-upgrade.
I had a couple of notifications stating my install was a little different with things like:
/etc/gdm/Init/default
/etc/mplayer/mplayer.conf
/etc/esound/esd.conf
and
/etc/firefox/firefoxrc

In each instance, I said go ahead and replace with the distros version (figured my little tweaks may or may not be fixed in 6.06.

Once I rebooted, I could no longer run VMware. Unstandable, I usually have to complile after a kernel update, but this time my kernel-source files seem to be missing (anything current at least). So It tells me it can't find my C header files. I tried doing a sudo apt-get kernel-source but this wanted to bring down 2.4 files, not 2.6.15

Ok, I just need to get my Windows XP image back up for work (darn Lotus Notes), so I figure I'll get vmware-player. This started to configure, then bombs out with I think a signal 1.
So I tried to just run it as: /usr/lib/vmware-player/bin$ ./vmplayer

But I get:
./vmplayer: error while loading shared libraries: libglibmm-2.4.so.1: cannot open shared object file: No such file or directory

any suggestions?

---

### Post by mannheim on 2006-06-02
[QUOTE=kbudurka] So It tells me it can't find my C header files. I tried doing a sudo apt-get kernel-source but this wanted to bring down 2.4 files, not 2.6.15
[/QUOTE]

I can help with that part. You need to apt-get install **linux-headers-386** (or 686 or k7 etc as appropriate).

Edit: And if you want the whole source you need linux-source, not kernel-source, for the 2.6 ubuntu linux kernel. (The headers are all you need though.)

---

### Post by kbudurka on 2006-06-02
Got 'er fixed now!
Your help put me on the right track. I did have to get the headers, but I still kept getting problmes relating to VMplayer.

So, I totally uninstalled that, but still had some grief, so I totally uninstalled VMware too and rebooted, then reinstalled VMware, and it automatically detected my headers that time.

I'm back in business - THANKS for the VERY FAST response and quality answer!

---

