---
title: "clingy wine install"
date: 2012-04-03
forum: General Help
---

### Post by bobman321123 on 2012-04-03
Hey all, I have wine 1.4 installed, and I'm finding that it WILL NOT uninstall no matter what I do. 
How would I go about uninstalling wine? 
I want it completely purged from my system, none left.

---

### Post by jerome1232 on 2012-04-03
```
sudo apt-get autoremove --purge wine
```

the --purge option will remove wines configuration options

autoremove will remove any packages that wine depends on, which nothing else depends on

---

### Post by bobman321123 on 2012-04-03
When I run "wine --version" it still shows up as installed.

---

### Post by jerome1232 on 2012-04-03
Well that comamnd would only remove it if you installed it via .deb or via repositories.

How did you install it then, via source? a binary?

If from source, you have to go into your source folder and run

```
sudo make uninstall
```

---

### Post by bobman321123 on 2012-04-03
I went into the source "Wine1.4" and ran ```
sudo make uninstall
``` but when I ran ```
wine --version
``` it still said wine 1.4 was installed. 

Could I just install a new version of wine overtop?

---

### Post by bobman321123 on 2012-04-03
Is there a way for me to manually uninstall it?

---

### Post by jerome1232 on 2012-04-03
> **bobman321123 said:**
> I went into the source "Wine1.4" and ran ```
sudo make uninstall
``` but when I ran ```
wine --version
``` it still said wine 1.4 was installed. 
Was there any output from that command? You should have had a ton of text, where there any errors?

> **bobman321123 said:**
> Could I just install a new version of wine overtop?

That depends on where your source put the binary.

What does this show, you can probably be safe just removing the binary, and then install a new version of wine.

```
whereis wine
```

---

### Post by bobman321123 on 2012-04-03
The output for make uninstall: 

```
josh@Nero:~/Desktop/Wines/wine-1.4$ sudo make uninstall
[sudo] password for josh: 
rm -f /usr/local/bin/wine-1.4/lib64/wine/acledit.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/acledit.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/aclui.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/aclui.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libaclui.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/activeds.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/activeds.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libactiveds.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/actxprxy.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/actxprxy.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libadsiid.a
rm -f /usr/local/bin/wine-1.4/lib64/wine/advapi32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/advapi32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libadvapi32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/advpack.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/advpack.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libadvpack.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/amstream.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/amstream.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/apphelp.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/apphelp.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/appwiz.cpl.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/appwiz.cpl
rm -f /usr/local/bin/wine-1.4/lib64/wine/atl.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/atl.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libatl.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/authz.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/authz.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/avicap32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/avicap32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libavicap32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/avifil32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/avifil32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libavifil32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/avrt.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/avrt.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libavrt.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/bcrypt.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/bcrypt.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/browseui.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/browseui.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/cabinet.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/cabinet.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libcabinet.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/capi2032.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/capi2032.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libcapi2032.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/cards.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/cards.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libcards.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/cfgmgr32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/cfgmgr32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libcfgmgr32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/clusapi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/clusapi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libclusapi.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/comcat.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/comcat.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/comctl32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/comctl32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libcomctl32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/comdlg32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/comdlg32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libcomdlg32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/compstui.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/compstui.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libcompstui.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/credui.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/credui.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libcredui.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/crtdll.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/crtdll.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libcrtdll.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/crypt32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/crypt32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libcrypt32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/cryptdlg.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/cryptdlg.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/cryptdll.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/cryptdll.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libcryptdll.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/cryptnet.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/cryptnet.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libcryptnet.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/cryptui.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/cryptui.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libcryptui.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/ctapi32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/ctapi32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/ctl3d32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/ctl3d32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libctl3d32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3d10.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3d10.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libd3d10.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3d10core.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3d10core.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libd3d10core.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3d8.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3d8.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libd3d8.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3d9.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3d9.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libd3d9.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dcompiler_33.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dcompiler_33.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dcompiler_34.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dcompiler_34.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dcompiler_35.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dcompiler_35.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dcompiler_36.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dcompiler_36.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dcompiler_37.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dcompiler_37.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dcompiler_38.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dcompiler_38.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dcompiler_39.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dcompiler_39.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dcompiler_40.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dcompiler_40.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dcompiler_41.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dcompiler_41.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dcompiler_42.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dcompiler_42.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dcompiler_43.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dcompiler_43.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libd3dcompiler.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dim.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dim.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libd3dim.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3drm.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3drm.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libd3drm.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx10_33.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx10_33.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx10_34.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx10_34.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx10_35.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx10_35.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx10_36.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx10_36.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx10_37.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx10_37.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx10_38.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx10_38.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx10_39.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx10_39.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx10_40.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx10_40.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx10_41.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx10_41.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx10_42.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx10_42.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx10_43.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx10_43.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx9_24.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx9_24.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx9_25.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx9_25.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx9_26.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx9_26.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx9_27.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx9_27.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx9_28.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx9_28.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx9_29.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx9_29.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx9_30.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx9_30.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx9_31.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx9_31.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx9_32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx9_32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx9_33.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx9_33.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx9_34.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx9_34.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx9_35.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx9_35.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx9_36.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx9_36.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libd3dx9.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx9_37.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx9_37.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx9_38.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx9_38.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx9_39.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx9_39.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx9_40.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx9_40.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx9_41.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx9_41.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx9_42.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx9_42.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dx9_43.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dx9_43.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/d3dxof.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/d3dxof.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libd3dxof.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/dbgeng.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dbgeng.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libdbgeng.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/dbghelp.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dbghelp.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libdbghelp.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/dciman32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dciman32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libdciman32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/ddraw.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/ddraw.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libddraw.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/ddrawex.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/ddrawex.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/devenum.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/devenum.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/dhcpcsvc.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dhcpcsvc.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/dinput.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dinput.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libdinput.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/libdinput.def.a
rm -f /usr/local/bin/wine-1.4/lib64/wine/dinput8.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dinput8.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libdinput8.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/dispex.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dispex.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/dmband.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dmband.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/dmcompos.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dmcompos.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/dmime.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dmime.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/dmloader.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dmloader.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/dmscript.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dmscript.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/dmstyle.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dmstyle.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/dmsynth.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dmsynth.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/dmusic.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dmusic.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/dmusic32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dmusic32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libdmusic32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/dnsapi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dnsapi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libdnsapi.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/dplay.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dplay.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libdplay.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/dplayx.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dplayx.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libdplayx.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/dpnaddr.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dpnaddr.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/dpnet.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dpnet.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libdpnet.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/dpnhpast.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dpnhpast.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/dpnlobby.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dpnlobby.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/dpwsockx.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dpwsockx.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/drmclien.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/drmclien.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/dsound.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dsound.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libdsound.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/dssenh.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dssenh.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/dswave.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dswave.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/dwmapi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dwmapi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libdwmapi.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/dxdiagn.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dxdiagn.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libdxerr8.a
rm -f /usr/local/bin/wine-1.4/lib64/wine/libdxerr9.a
rm -f /usr/local/bin/wine-1.4/lib64/wine/dxgi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dxgi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libdxgi.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/libdxguid.a
rm -f /usr/local/bin/wine-1.4/lib64/wine/explorerframe.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/explorerframe.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/faultrep.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/faultrep.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libfaultrep.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/fltlib.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/fltlib.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/fusion.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/fusion.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/fwpuclnt.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/fwpuclnt.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/gameux.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/gameux.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/gdi32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/gdi32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libgdi32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/gdiplus.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/gdiplus.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libgdiplus.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/glu32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/glu32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libglu32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/gphoto2.ds.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/gphoto2.ds
rm -f /usr/local/bin/wine-1.4/lib64/wine/gpkcsp.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/gpkcsp.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/hal.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/hal.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/hhctrl.ocx.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/hhctrl.ocx
rm -f /usr/local/bin/wine-1.4/lib64/wine/hid.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/hid.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libhid.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/hlink.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/hlink.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libhlink.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/hnetcfg.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/hnetcfg.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/httpapi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/httpapi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/iccvid.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/iccvid.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/icmp.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/icmp.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/ieframe.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/ieframe.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libieframe.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/imaadp32.acm.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/imaadp32.acm
rm -f /usr/local/bin/wine-1.4/lib64/wine/imagehlp.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/imagehlp.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libimagehlp.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/imm32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/imm32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libimm32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/inetcomm.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/inetcomm.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libinetcomm.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/inetcpl.cpl.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/inetcpl.cpl
rm -f /usr/local/bin/wine-1.4/lib64/wine/inetmib1.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/inetmib1.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/infosoft.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/infosoft.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/initpki.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/initpki.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/inkobj.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/inkobj.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/inseng.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/inseng.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/iphlpapi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/iphlpapi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libiphlpapi.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/itircl.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/itircl.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/itss.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/itss.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/jscript.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/jscript.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/kernel32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/kernel32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libkernel32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/ktmw32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/ktmw32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/loadperf.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/loadperf.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libloadperf.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/localspl.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/localspl.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/localui.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/localui.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/lz32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/lz32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/liblz32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/mapi32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mapi32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libmapi32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/mapistub.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mapistub.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/mciavi32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mciavi32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/mcicda.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mcicda.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/mciqtz32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mciqtz32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/mciseq.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mciseq.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/mciwave.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mciwave.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/midimap.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/midimap.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/mlang.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mlang.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libmlang.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/mmcndmgr.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mmcndmgr.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/mmdevapi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mmdevapi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/mountmgr.sys.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mountmgr.sys
rm -f /usr/local/bin/wine-1.4/lib64/wine/mpr.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mpr.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libmpr.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/mprapi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mprapi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libmprapi.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/msacm32.drv.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msacm32.drv
rm -f /usr/local/bin/wine-1.4/lib64/wine/msacm32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msacm32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libmsacm32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/msadp32.acm.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msadp32.acm
rm -f /usr/local/bin/wine-1.4/lib64/wine/mscat32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mscat32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/mscms.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mscms.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libmscms.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/mscoree.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mscoree.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msctf.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msctf.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msdaps.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msdaps.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msdmo.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msdmo.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libmsdmo.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/msftedit.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msftedit.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msg711.acm.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msg711.acm
rm -f /usr/local/bin/wine-1.4/lib64/wine/msgsm32.acm.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msgsm32.acm
rm -f /usr/local/bin/wine-1.4/lib64/wine/mshtml.tlb.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mshtml.tlb
rm -f /usr/local/bin/wine-1.4/lib64/wine/mshtml.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mshtml.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libmshtml.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/msi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libmsi.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/msimg32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msimg32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libmsimg32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/msimsg.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msimsg.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msimtf.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msimtf.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msisip.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msisip.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msisys.ocx.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msisys.ocx
rm -f /usr/local/bin/wine-1.4/lib64/wine/msnet32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msnet32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/mspatcha.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mspatcha.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msrle32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msrle32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/mssign32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mssign32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/mssip32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mssip32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/mstask.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mstask.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msvcirt.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msvcirt.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msvcp100.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msvcp100.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msvcp60.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msvcp60.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msvcp70.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msvcp70.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msvcp71.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msvcp71.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msvcp80.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msvcp80.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msvcp90.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msvcp90.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msvcr100.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msvcr100.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msvcr70.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msvcr70.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libmsvcr70.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/msvcr71.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msvcr71.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libmsvcr71.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/msvcr80.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msvcr80.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msvcr90.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msvcr90.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msvcrt.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msvcrt.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libmsvcrt.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/msvcrt20.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msvcrt20.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libmsvcrt20.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/msvcrt40.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msvcrt40.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libmsvcrt40.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/msvcrtd.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msvcrtd.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libmsvcrtd.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/msvfw32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msvfw32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libmsvfw32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/msvidc32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msvidc32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/mswsock.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mswsock.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libmswsock.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/msxml.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msxml.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msxml2.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msxml2.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msxml3.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msxml3.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msxml4.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msxml4.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/msxml6.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msxml6.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/nddeapi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/nddeapi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libnddeapi.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/netapi32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/netapi32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libnetapi32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/newdev.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/newdev.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libnewdev.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/normaliz.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/normaliz.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libnormaliz.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/npmshtml.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/npmshtml.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/ntdll.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/ntdll.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libntdll.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/ntdsapi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/ntdsapi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libntdsapi.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/ntoskrnl.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/ntoskrnl.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/libntoskrnl.exe.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/ntprint.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/ntprint.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/objsel.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/objsel.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/odbc32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/odbc32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libodbc32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/odbccp32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/odbccp32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libodbccp32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/ole32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/ole32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libole32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/oleacc.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/oleacc.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/liboleacc.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/oleaut32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/oleaut32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/liboleaut32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/olecli32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/olecli32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libolecli32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/oledb32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/oledb32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/oledlg.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/oledlg.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/liboledlg.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/olepro32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/olepro32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libolepro32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/olesvr32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/olesvr32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libolesvr32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/olethk32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/olethk32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/openal32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/openal32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/opencl.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/opencl.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/opengl32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/opengl32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libopengl32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/pdh.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/pdh.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libpdh.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/photometadatahandler.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/photometadatahandler.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/pidgen.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/pidgen.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/powrprof.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/powrprof.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libpowrprof.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/printui.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/printui.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/propsys.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/propsys.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libpropsys.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/psapi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/psapi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libpsapi.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/pstorec.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/pstorec.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/qcap.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/qcap.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/qedit.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/qedit.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/qmgr.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/qmgr.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/qmgrprxy.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/qmgrprxy.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/quartz.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/quartz.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libquartz.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/query.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/query.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/rasapi32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/rasapi32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/librasapi32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/rasdlg.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/rasdlg.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/librasdlg.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/regapi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/regapi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/resutils.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/resutils.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libresutils.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/riched20.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/riched20.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libriched20.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/riched32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/riched32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/rpcrt4.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/rpcrt4.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/librpcrt4.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/rsabase.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/rsabase.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/rsaenh.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/rsaenh.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/librsaenh.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/rstrtmgr.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/rstrtmgr.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/rtutils.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/rtutils.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/librtutils.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/samlib.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/samlib.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/sane.ds.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/sane.ds
rm -f /usr/local/bin/wine-1.4/lib64/wine/scarddlg.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/scarddlg.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/sccbase.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/sccbase.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/schannel.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/schannel.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/scrrun.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/scrrun.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/secur32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/secur32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libsecur32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/security.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/security.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/sensapi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/sensapi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libsensapi.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/serialui.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/serialui.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libserialui.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/setupapi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/setupapi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libsetupapi.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/sfc.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/sfc.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libsfc.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/sfc_os.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/sfc_os.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libsfc_os.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/shdoclc.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/shdoclc.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/shdocvw.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/shdocvw.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libshdocvw.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/shell32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/shell32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libshell32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/shfolder.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/shfolder.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libshfolder.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/shlwapi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/shlwapi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libshlwapi.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/slbcsp.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/slbcsp.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/slc.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/slc.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libslc.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/snmpapi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/snmpapi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libsnmpapi.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/softpub.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/softpub.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/spoolss.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/spoolss.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libspoolss.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/stdole2.tlb.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/stdole2.tlb
rm -f /usr/local/bin/wine-1.4/lib64/wine/stdole32.tlb.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/stdole32.tlb
rm -f /usr/local/bin/wine-1.4/lib64/wine/sti.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/sti.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libsti.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/libstrmbase.a
rm -f /usr/local/bin/wine-1.4/lib64/wine/libstrmiids.a
rm -f /usr/local/bin/wine-1.4/lib64/wine/svrapi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/svrapi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/sxs.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/sxs.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/t2embed.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/t2embed.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/tapi32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/tapi32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libtapi32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/traffic.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/traffic.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/twain_32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/twain_32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/unicows.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/unicows.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libunicows.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/updspapi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/updspapi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/url.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/url.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/liburl.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/urlmon.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/urlmon.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/liburlmon.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/usbd.sys.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/usbd.sys
rm -f /usr/local/bin/wine-1.4/lib64/wine/libusbd.sys.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/user32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/user32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libuser32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/userenv.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/userenv.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libuserenv.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/usp10.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/usp10.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libusp10.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/libuuid.a
rm -f /usr/local/bin/wine-1.4/lib64/wine/uxtheme.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/uxtheme.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libuxtheme.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/vbscript.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/vbscript.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/vcomp.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/vcomp.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/vdmdbg.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/vdmdbg.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libvdmdbg.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/version.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/version.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libversion.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/wbemprox.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wbemprox.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/wer.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wer.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libwer.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/wiaservc.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wiaservc.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/windowscodecs.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/windowscodecs.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libwindowscodecs.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/winealsa.drv.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winealsa.drv
rm -f /usr/local/bin/wine-1.4/lib64/wine/libwinecrt0.a
rm -f /usr/local/bin/wine-1.4/lib64/wine/wined3d.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wined3d.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libwined3d.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/winegstreamer.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winegstreamer.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/winejoystick.drv.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winejoystick.drv
rm -f /usr/local/bin/wine-1.4/lib64/wine/winemapi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winemapi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/winemp3.acm.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winemp3.acm
rm -f /usr/local/bin/wine-1.4/lib64/wine/wineoss.drv.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wineoss.drv
make[1]: Entering directory `/home/josh/Desktop/Wines/wine-1.4/tools'
make[1]: `makedep' is up to date.
make[1]: Leaving directory `/home/josh/Desktop/Wines/wine-1.4/tools'
make[1]: Entering directory `/home/josh/Desktop/Wines/wine-1.4/dlls/wineps.drv'
rm -f /usr/local/bin/wine-1.4/lib64/wine/wineps.drv.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wineps.drv
rm -f /usr/local/bin/wine-1.4/share/wine/generic.ppd
make[1]: Leaving directory `/home/josh/Desktop/Wines/wine-1.4/dlls/wineps.drv'
rm -f /usr/local/bin/wine-1.4/lib64/wine/winex11.drv.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winex11.drv
rm -f /usr/local/bin/wine-1.4/lib64/wine/wing32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wing32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/winhttp.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winhttp.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libwinhttp.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/wininet.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wininet.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libwininet.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/winmm.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winmm.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libwinmm.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/winnls32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winnls32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libwinnls32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/winscard.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winscard.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libwinscard.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/winspool.drv.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winspool.drv
rm -f /usr/local/bin/wine-1.4/lib64/wine/libwinspool.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/winsta.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winsta.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/wintab32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wintab32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libwintab32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/wintrust.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wintrust.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libwintrust.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/wlanapi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wlanapi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/wldap32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wldap32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libwldap32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/wmi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wmi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/wmiutils.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wmiutils.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/wnaspi32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wnaspi32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libwnaspi32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/ws2_32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/ws2_32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libws2_32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/wshom.ocx.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wshom.ocx
rm -f /usr/local/bin/wine-1.4/lib64/wine/wsock32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wsock32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libwsock32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/wtsapi32.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wtsapi32.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libwtsapi32.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/wuapi.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wuapi.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/wuaueng.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wuaueng.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/xapofx1_1.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/xapofx1_1.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/xinput1_1.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/xinput1_1.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/xinput1_2.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/xinput1_2.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/xinput1_3.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/xinput1_3.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/libxinput.def
rm -f /usr/local/bin/wine-1.4/lib64/wine/xinput9_1_0.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/xinput9_1_0.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/xmllite.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/xmllite.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/xolehlp.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/xolehlp.dll
rm -f /usr/local/bin/wine-1.4/lib64/wine/xpsprint.dll.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/xpsprint.dll
make[1]: Entering directory `/home/josh/Desktop/Wines/wine-1.4/fonts'
cd /usr/local/bin/wine-1.4/share/wine/fonts && rm -f coue1255.fon coue1256.fon coue1257.fon coure.fon couree.fon coureg.fon courer.fon couret.fon cvgasys.fon hvgasys.fon jsmalle.fon jvgasys.fon smalle.fon smallee.fon smalleg.fon smaller.fon smallet.fon smae1255.fon smae1256.fon smae1257.fon sserife.fon sserifee.fon sserifeg.fon sserifer.fon sserifet.fon ssee1255.fon ssee1256.fon ssee1257.fon ssee874.fon svgasys.fon vgasys.fon vgasyse.fon vgasysg.fon vgasysr.fon vgasyst.fon vgas1255.fon vgas1256.fon vgas1257.fon vgas874.fon marlett.ttf symbol.ttf tahoma.ttf tahomabd.ttf
/bin/sh: 1: cd: can't cd to /usr/local/bin/wine-1.4/share/wine/fonts
make[1]: [uninstall] Error 2 (ignored)
rmdir /usr/local/bin/wine-1.4/share/wine/fonts
rmdir: failed to remove `/usr/local/bin/wine-1.4/share/wine/fonts': No such file or directory
make[1]: [uninstall] Error 1 (ignored)
make[1]: Leaving directory `/home/josh/Desktop/Wines/wine-1.4/fonts'
make[1]: Entering directory `/home/josh/Desktop/Wines/wine-1.4/include'
for f in stdole2.idl activaut.idl activdbg.idl activscp.idl amstream.idl amvideo.idl asptlb.idl atliface.idl audioclient.idl audiopolicy.idl austream.idl bits.idl bits1_5.idl comcat.idl commoncontrols.idl control.idl cor.idl cordebug.idl ctfutb.idl ctxtcall.idl d3d10.idl d3d10_1.idl d3d11.idl d3dcommon.idl ddstream.idl devicetopology.idl dimm.idl dispex.idl docobj.idl docobjectservice.idl downloadmgr.idl dxgi.idl endpointvolume.idl exdisp.idl fusion.idl gameux.idl hlink.idl htiface.idl htiframe.idl httprequest.idl iads.idl icftypes.idl iextag.idl imnact.idl imnxport.idl indexsrv.idl mediaobj.idl metahost.idl mimeinfo.idl mimeole.idl mlang.idl mmc.idl mmdeviceapi.idl mmstream.idl mscoree.idl msctf.idl msdadc.idl mshtmhst.idl mshtml.idl msinkaut.idl mstask.idl msxml.idl msxml2.idl msxml6.idl netcon.idl netfw.idl oaidl.idl objectarray.idl objidl.idl objsafe.idl ocidl.idl ocmm.idl oleacc.idl oledb.idl oleidl.idl optary.idl perhist.idl propidl.idl propsys.idl pstore.idl qedit.idl richole.idl sensevts.idl servprov.idl shdeprecated.idl shldisp.idl shobjidl.idl shtypes.idl strmif.idl structuredquerycondition.idl textstor.idl tlogstg.idl tom.idl unknwn.idl urlhist.idl urlmon.idl vmr9.idl wbemcli.idl wia_lh.idl wia_xp.idl wincodec.idl wincodecsdk.idl wine/itss.idl wine/svcctl.idl winsxs.idl wpcapi.idl wtypes.idl wuapi.idl xmllite.idl rmxftmpl.x accctrl.h access.idl aclapi.h aclui.h adshlp.h advpub.h af_irda.h amaudio.h appmgmt.h asynot.idl asysta.idl audevcod.h audiosessiontypes.h aviriff.h avrt.h axcore.idl axextend.idl basetsd.h basetyps.h bcrypt.h binres.idl bitsmsg.h cderr.h cfgmgr32.h cguid.h cierror.h clusapi.h cmdbas.idl cmdtxt.idl commctrl.h commctrl.rh commdlg.h compobj.h corerror.h corhdr.h cpl.h crtrow.idl cryptdlg.h cryptuiapi.h custcntl.h cvconst.h d3d.h d3d10_1shader.h d3d10effect.h d3d10misc.h d3d10shader.h d3d11shader.h d3d8.h d3d8caps.h d3d8types.h d3d9.h d3d9caps.h d3d9types.h d3dcaps.h d3dcompiler.h d3dhal.h d3drm.h d3drmdef.h d3drmobj.h d3drmwin.h d3dtypes.h d3dvec.inl d3dx9.h d3dx9anim.h d3dx9core.h d3dx9effect.h d3dx9math.h d3dx9math.inl d3dx9mesh.h d3dx9shader.h d3dx9shape.h d3dx9tex.h d3dx9xof.h dbccmd.idl dbcses.idl dbdsad.idl dbghelp.h dbinit.idl dbprop.idl dbs.idl dbt.h dciddi.h dciman.h dde.h dde.rh ddeml.h ddk/compstui.h ddk/hidsdi.h ddk/imm.h ddk/mountmgr.h ddk/ntddcdvd.h ddk/ntddk.h ddk/ntddser.h ddk/ntddtape.h ddk/usb.h ddk/usb100.h ddk/usb200.h ddk/usbdlib.h ddk/wdm.h ddk/winddiui.h ddk/winsplp.h ddraw.h ddrawgdi.h ddrawi.h devenum.idl devguid.h devpkey.h devpropdef.h digitalv.h dinput.h dinputd.h dispdib.h dlgs.h dls1.h dls2.h dmdls.h dmerror.h dmo.h dmoreg.h dmort.h dmplugin.h dmusbuff.h dmusicc.h dmusicf.h dmusici.h dmusics.h dpaddr.h dplay.h dplay8.h dplobby.h dplobby8.h dpnathlp.h dsconf.h dsgetdc.h dshow.h dsound.h dsrole.h dvdmedia.h dwmapi.h dxdiag.h dxerr8.h dxerr9.h dxfile.h dxgiformat.h dxgitype.h dyngraph.idl errorrep.h errors.h evcode.h evntprov.h evntrace.h excpt.h exdispid.h fci.h fdi.h fltdefs.h gdiplus.h gdipluscolor.h gdipluscolormatrix.h gdiplusenums.h gdiplusflat.h gdiplusgpstubs.h gdiplusimaging.h gdiplusinit.h gdiplusmem.h gdiplusmetaheader.h gdipluspixelformats.h gdiplustypes.h guiddef.h hlguids.h htmlhelp.h http.h httprequestid.h i_cryptasn1tls.h icm.h icmpapi.h idispids.h ifdef.h ifmib.h imagehlp.h imm.h in6addr.h inaddr.h initguid.h intshcut.h ipexport.h iphlpapi.h ipifcons.h ipmib.h iprtrmib.h iptypes.h isguids.h knownfolders.h ks.h ksguid.h ksmedia.h lm.h lmaccess.h lmapibuf.h lmat.h lmbrowsr.h lmcons.h lmerr.h lmjoin.h lmmsg.h lmserver.h lmshare.h lmstats.h lmuse.h lmuseflg.h lmwksta.h loadperf.h lzexpand.h mapi.h mapicode.h mapidefs.h mapiform.h mapiguid.h mapitags.h mapiutil.h mapival.h mapix.h mciavi.h mcx.h mediaerr.h midles.h minmax.h mmddk.h mmreg.h mmsystem.h mprapi.h mprerror.h msacm.h msacmdlg.h msacmdrv.h mscat.h msdaguid.h mshtmcid.h mshtmdid.h msi.h msidefs.h msiquery.h mssip.h mstcpip.h msvcrt/assert.h msvcrt/conio.h msvcrt/crtdbg.h msvcrt/crtdefs.h msvcrt/ctype.h msvcrt/direct.h msvcrt/dirent.h msvcrt/dos.h msvcrt/eh.h msvcrt/errno.h msvcrt/fcntl.h msvcrt/float.h msvcrt/io.h msvcrt/limits.h msvcrt/locale.h msvcrt/malloc.h msvcrt/math.h msvcrt/mbctype.h msvcrt/mbstring.h msvcrt/memory.h msvcrt/process.h msvcrt/search.h msvcrt/setjmp.h msvcrt/share.h msvcrt/signal.h msvcrt/stddef.h msvcrt/stdio.h msvcrt/stdlib.h msvcrt/string.h msvcrt/sys/locking.h msvcrt/sys/stat.h msvcrt/sys/timeb.h msvcrt/sys/types.h msvcrt/sys/unistd.h msvcrt/sys/utime.h msvcrt/time.h msvcrt/unistd.h msvcrt/wchar.h msvcrt/wctype.h mswsock.h msxml2did.h msxml6did.h msxmldid.h nb30.h ndrtypes.h nldef.h npapi.h nspapi.h ntddcdrm.h ntddndis.h ntddscsi.h ntddstor.h ntdsapi.h ntquery.h ntsecapi.h ntsecpkg.h ntstatus.h objbase.h objsel.h odbcinst.h ole2.h ole2ver.h oleauto.h olectl.h oledberr.h oledlg.h opnrst.idl patchapi.h pdh.h pdhmsg.h pktdef.h poppack.h powrprof.h profinfo.h propkey.h propkeydef.h propvarutil.h prsht.h psapi.h pshpack1.h pshpack2.h pshpack4.h pshpack8.h ras.h rasdlg.h raserror.h reason.h regstr.h restartmanager.h richedit.h rmxfguid.h row.idl rowchg.idl rpc.h rpcasync.h rpcdce.h rpcdcep.h rpcndr.h rpcnterr.h rpcproxy.h rpcsal.h rstbas.idl rstinf.idl rstloc.idl rtutils.h scarderr.h schannel.h schemadef.h schnlsp.h sddl.h secext.h security.h sensapi.h sesprp.idl setupapi.h sfc.h shdispid.h shellapi.h shlguid.h shlobj.h shlwapi.h sipbase.h slerror.h slpublic.h snmp.h softpub.h sql.h sqlext.h sqltypes.h srrestoreptapi.h sspi.h sti.h storage.h strsafe.h svrapi.h t2embapi.h tapi.h tchar.h tcpmib.h textserv.h tlhelp32.h tmschema.h traffic.h twain.h udpmib.h userenv.h usp10.h uuids.h uxtheme.h vdmdbg.h ver.h verrsrc.h vfw.h vfwmsgs.h vmrender.idl vsstyle.h vssym32.h werapi.h wfext.h wia.h winbase.h wincon.h wincred.h wincrypt.h windef.h windns.h windows.h windowsx.h wine/debug.h wine/exception.h wine/library.h wine/unicode.h winerror.h wingdi.h winhttp.h wininet.h winineti.h winioctl.h winldap.h winnetwk.h winnls.h winnls32.h winnt.h winnt.rh winperf.h winreg.h winresrc.h winsafer.h winscard.h winsmcrd.h winsock.h winsock2.h winspool.h winsvc.h wintab.h wintabx.h winternl.h wintrust.h winuser.h winuser.rh winver.h wmistr.h wnaspi32.h wownt32.h ws2def.h ws2ipdef.h ws2spi.h ws2tcpip.h wshisotp.h wsipx.h wsnwlink.h wtsapi32.h xcmc.h xinput.h xmldom.h xmldom.idl xmldomdid.h xmldso.idl xmldsodid.h zmouse.h activaut.h activdbg.h activscp.h amstream.h amvideo.h asptlb.h atliface.h audioclient.h audiopolicy.h austream.h bits.h bits1_5.h comcat.h commoncontrols.h control.h cor.h cordebug.h ctfutb.h ctxtcall.h d3d10.h d3d10_1.h d3d11.h d3dcommon.h ddstream.h devicetopology.h dimm.h dispex.h docobj.h docobjectservice.h downloadmgr.h dxgi.h endpointvolume.h exdisp.h fusion.h gameux.h hlink.h htiface.h htiframe.h httprequest.h iads.h icftypes.h iextag.h imnact.h imnxport.h indexsrv.h mediaobj.h metahost.h mimeinfo.h mimeole.h mlang.h mmc.h mmdeviceapi.h mmstream.h mscoree.h msctf.h msdadc.h mshtmhst.h mshtml.h msinkaut.h mstask.h msxml.h msxml2.h msxml6.h netcon.h netfw.h oaidl.h objectarray.h objidl.h objsafe.h ocidl.h ocmm.h oleacc.h oledb.h oleidl.h optary.h perhist.h propidl.h propsys.h pstore.h qedit.h richole.h sensevts.h servprov.h shdeprecated.h shldisp.h shobjidl.h shtypes.h strmif.h structuredquerycondition.h textstor.h tlogstg.h tom.h unknwn.h urlhist.h urlmon.h vmr9.h wbemcli.h wia_lh.h wia_xp.h wincodec.h wincodecsdk.h wine/itss.h wine/svcctl.h winsxs.h wpcapi.h wtypes.h wuapi.h xmllite.h rmxftmpl.h; do case $f in \
	  wine/*)   rm -f /usr/local/bin/wine-1.4/include/wine/`expr $f : 'wine/\(.*\)'` ;; \
	  msvcrt/*) rm -f /usr/local/bin/wine-1.4/include/wine/$f ;; \
	  *)        rm -f /usr/local/bin/wine-1.4/include/wine/windows/$f ;; \
	esac; done
rmdir /usr/local/bin/wine-1.4/include/wine/windows/ddk /usr/local/bin/wine-1.4/include/wine/windows /usr/local/bin/wine-1.4/include/wine/msvcrt/sys /usr/local/bin/wine-1.4/include/wine/msvcrt /usr/local/bin/wine-1.4/include/wine
rmdir: failed to remove `/usr/local/bin/wine-1.4/include/wine/windows/ddk': No such file or directory
rmdir: failed to remove `/usr/local/bin/wine-1.4/include/wine/windows': No such file or directory
rmdir: failed to remove `/usr/local/bin/wine-1.4/include/wine/msvcrt/sys': No such file or directory
rmdir: failed to remove `/usr/local/bin/wine-1.4/include/wine/msvcrt': No such file or directory
rmdir: failed to remove `/usr/local/bin/wine-1.4/include/wine': No such file or directory
make[1]: [uninstall] Error 1 (ignored)
make[1]: Leaving directory `/home/josh/Desktop/Wines/wine-1.4/include'
make[1]: Entering directory `/home/josh/Desktop/Wines/wine-1.4/libs/wine'
cd /usr/local/bin/wine-1.4/lib64 && rm -f libwine.a libwine.dll libwine.so libwine.so.1.0 \
		libwine.so.1 libwine.dylib libwine.1.0.dylib libwine.1.dylib
make[1]: Leaving directory `/home/josh/Desktop/Wines/wine-1.4/libs/wine'
make[1]: Entering directory `/home/josh/Desktop/Wines/wine-1.4/loader'
rm -f /usr/local/bin/wine-1.4/share/man/man1/wine.1
cd /usr/local/bin/wine-1.4/bin && rm -f wine64 wine64-preloader
rm -f /usr/local/bin/wine-1.4/share/man/de.UTF-8/man1/wine.1
rm -f /usr/local/bin/wine-1.4/share/man/fr.UTF-8/man1/wine.1
rm -f /usr/local/bin/wine-1.4/share/man/pl.UTF-8/man1/wine.1
make[1]: Leaving directory `/home/josh/Desktop/Wines/wine-1.4/loader'
rm -f /usr/local/bin/wine-1.4/lib64/wine/aspnet_regiis.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/aspnet_regiis.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/attrib.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/attrib.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/cabarc.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/cabarc.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/cacls.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/cacls.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/clock.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/clock.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/cmd.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/cmd.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/control.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/control.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/cscript.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/cscript.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/dxdiag.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/dxdiag.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/eject.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/eject.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/expand.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/expand.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/explorer.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/explorer.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/extrac32.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/extrac32.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/hh.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/hh.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/hostname.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/hostname.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/icinfo.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/icinfo.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/iexplore.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/iexplore.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/ipconfig.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/ipconfig.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/lodctr.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/lodctr.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/mofcomp.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mofcomp.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/mshta.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/mshta.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/msiexec.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/msiexec.exe
rm -f /usr/local/bin/wine-1.4/bin/msiexec
rm -f /usr/local/bin/wine-1.4/share/man/man1/msiexec.1
rm -f /usr/local/bin/wine-1.4/lib64/wine/net.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/net.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/netsh.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/netsh.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/ngen.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/ngen.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/notepad.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/notepad.exe
rm -f /usr/local/bin/wine-1.4/bin/notepad
rm -f /usr/local/bin/wine-1.4/share/man/man1/notepad.1
rm -f /usr/local/bin/wine-1.4/lib64/wine/oleview.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/oleview.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/ping.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/ping.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/plugplay.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/plugplay.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/presentationfontcache.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/presentationfontcache.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/progman.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/progman.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/reg.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/reg.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/regasm.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/regasm.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/regedit.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/regedit.exe
rm -f /usr/local/bin/wine-1.4/bin/regedit
rm -f /usr/local/bin/wine-1.4/share/man/man1/regedit.1
rm -f /usr/local/bin/wine-1.4/lib64/wine/regsvcs.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/regsvcs.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/regsvr32.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/regsvr32.exe
rm -f /usr/local/bin/wine-1.4/bin/regsvr32
rm -f /usr/local/bin/wine-1.4/share/man/man1/regsvr32.1
rm -f /usr/local/bin/wine-1.4/lib64/wine/rpcss.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/rpcss.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/rundll32.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/rundll32.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/sc.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/sc.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/secedit.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/secedit.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/servicemodelreg.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/servicemodelreg.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/services.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/services.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/spoolsv.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/spoolsv.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/start.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/start.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/svchost.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/svchost.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/taskkill.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/taskkill.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/taskmgr.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/taskmgr.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/termsv.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/termsv.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/uninstaller.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/uninstaller.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/unlodctr.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/unlodctr.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/view.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/view.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/wineboot.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wineboot.exe
rm -f /usr/local/bin/wine-1.4/bin/wineboot
rm -f /usr/local/bin/wine-1.4/share/man/man1/wineboot.1
rm -f /usr/local/bin/wine-1.4/lib64/wine/winebrowser.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winebrowser.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/winecfg.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winecfg.exe
rm -f /usr/local/bin/wine-1.4/bin/winecfg
rm -f /usr/local/bin/wine-1.4/share/man/man1/winecfg.1
rm -f /usr/local/bin/wine-1.4/lib64/wine/wineconsole.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wineconsole.exe
rm -f /usr/local/bin/wine-1.4/bin/wineconsole
rm -f /usr/local/bin/wine-1.4/share/man/man1/wineconsole.1
rm -f /usr/local/bin/wine-1.4/lib64/wine/winedbg.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winedbg.exe
rm -f /usr/local/bin/wine-1.4/bin/winedbg
rm -f /usr/local/bin/wine-1.4/share/man/man1/winedbg.1
rm -f /usr/local/bin/wine-1.4/lib64/wine/winedevice.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winedevice.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/winefile.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winefile.exe
rm -f /usr/local/bin/wine-1.4/bin/winefile
rm -f /usr/local/bin/wine-1.4/share/man/man1/winefile.1
rm -f /usr/local/bin/wine-1.4/lib64/wine/winemenubuilder.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winemenubuilder.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/winemine.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winemine.exe
rm -f /usr/local/bin/wine-1.4/bin/winemine
rm -f /usr/local/bin/wine-1.4/share/man/man1/winemine.1
rm -f /usr/local/bin/wine-1.4/lib64/wine/winemsibuilder.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winemsibuilder.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/winepath.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winepath.exe
rm -f /usr/local/bin/wine-1.4/bin/winepath
rm -f /usr/local/bin/wine-1.4/share/man/man1/winepath.1
rm -f /usr/local/bin/wine-1.4/lib64/wine/winhlp32.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winhlp32.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/winver.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/winver.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/wmic.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wmic.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/wordpad.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wordpad.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/write.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/write.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/wscript.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/wscript.exe
rm -f /usr/local/bin/wine-1.4/lib64/wine/xcopy.exe.so /usr/local/bin/wine-1.4/lib64/wine/fakedlls/xcopy.exe
make[1]: Entering directory `/home/josh/Desktop/Wines/wine-1.4/server'
rm -f /usr/local/bin/wine-1.4/share/man/man1/wineserver.1
rm -f /usr/local/bin/wine-1.4/bin/wineserver
rm -f /usr/local/bin/wine-1.4/share/man/de.UTF-8/man1/wineserver.1
rm -f /usr/local/bin/wine-1.4/share/man/fr.UTF-8/man1/wineserver.1
make[1]: Leaving directory `/home/josh/Desktop/Wines/wine-1.4/server'
make[1]: Entering directory `/home/josh/Desktop/Wines/wine-1.4/tools'
rm -f /usr/local/bin/wine-1.4/share/man/man1/winemaker.1
rm -f /usr/local/bin/wine-1.4/share/wine/wine.inf \
		/usr/local/bin/wine-1.4/share/wine/l_intl.nls \
		/usr/local/bin/wine-1.4/share/applications/wine.desktop \
		/usr/local/bin/wine-1.4/bin/winemaker \
		/usr/local/bin/wine-1.4/share/man/de.UTF-8/man1/winemaker.1 \
		/usr/local/bin/wine-1.4/share/man/fr.UTF-8/man1/winemaker.1
update-desktop-database
make[1]: Leaving directory `/home/josh/Desktop/Wines/wine-1.4/tools'
make[1]: Entering directory `/home/josh/Desktop/Wines/wine-1.4/tools/widl'
rm -f /usr/local/bin/wine-1.4/share/man/man1/widl.1
rm -f /usr/local/bin/wine-1.4/bin/widl
make[1]: Leaving directory `/home/josh/Desktop/Wines/wine-1.4/tools/widl'
make[1]: Entering directory `/home/josh/Desktop/Wines/wine-1.4/tools/winebuild'
rm -f /usr/local/bin/wine-1.4/share/man/man1/winebuild.1
rm -f /usr/local/bin/wine-1.4/bin/winebuild
make[1]: Leaving directory `/home/josh/Desktop/Wines/wine-1.4/tools/winebuild'
make[1]: Entering directory `/home/josh/Desktop/Wines/wine-1.4/tools/winedump'
rm -f /usr/local/bin/wine-1.4/share/man/man1/winedump.1
rm -f /usr/local/bin/wine-1.4/bin/function_grep.pl /usr/local/bin/wine-1.4/bin/winedump
make[1]: Leaving directory `/home/josh/Desktop/Wines/wine-1.4/tools/winedump'
make[1]: Entering directory `/home/josh/Desktop/Wines/wine-1.4/tools/winegcc'
rm -f /usr/local/bin/wine-1.4/share/man/man1/winegcc.1
rm -f /usr/local/bin/wine-1.4/bin/winegcc /usr/local/bin/wine-1.4/bin/wineg++ /usr/local/bin/wine-1.4/bin/winecpp
rm -f /usr/local/bin/wine-1.4/share/man/man1/wineg++.1 /usr/local/bin/wine-1.4/share/man/man1/winecpp.1
make[1]: Leaving directory `/home/josh/Desktop/Wines/wine-1.4/tools/winegcc'
make[1]: Entering directory `/home/josh/Desktop/Wines/wine-1.4/tools/wmc'
rm -f /usr/local/bin/wine-1.4/share/man/man1/wmc.1
rm -f /usr/local/bin/wine-1.4/bin/wmc
make[1]: Leaving directory `/home/josh/Desktop/Wines/wine-1.4/tools/wmc'
make[1]: Entering directory `/home/josh/Desktop/Wines/wine-1.4/tools/wrc'
rm -f /usr/local/bin/wine-1.4/share/man/man1/wrc.1
rm -f /usr/local/bin/wine-1.4/bin/wrc
make[1]: Leaving directory `/home/josh/Desktop/Wines/wine-1.4/tools/wrc'
rmdir /usr/local/bin/wine-1.4/share/wine /usr/local/bin/wine-1.4/lib64/wine/fakedlls /usr/local/bin/wine-1.4/lib64/wine
rmdir: failed to remove `/usr/local/bin/wine-1.4/share/wine': No such file or directory
rmdir: failed to remove `/usr/local/bin/wine-1.4/lib64/wine/fakedlls': No such file or directory
rmdir: failed to remove `/usr/local/bin/wine-1.4/lib64/wine': No such file or directory
make: [uninstall] Error 1 (ignored)

```

---

### Post by bobman321123 on 2012-04-03
```
whereis wine
```
posts

```
wine: /usr/bin/wine /usr/bin/X11/wine /usr/share/wine /usr/share/man/man1/wine.1.gz

```
Am I ok to just delete all folders that hold wine?

---

### Post by jerome1232 on 2012-04-03
--snip--

It looks like you installed it another way than via that source code, since your source was removing it from /usr/local/bin and you still have a copy in /usr/bin.

Did you install wine any other way than that source code? I'm hesitant to say yes, just delete the files since it may leave residual files that may conflict with future installs of wine.

---

### Post by bobman321123 on 2012-04-03
Aside from installing from source, and installing from deb, not that I know of. My first several attempts at compiling somewhat failed though, so could that be the problem?

---

### Post by jerome1232 on 2012-04-03
perhaps, I just want to check to make sure that there is nothing "wine" installed by .deb (maybe you have a specific version installed and that's why the command I gave failed to remove it)

```
dpkg-query -l "wine"
```

---

### Post by bobman321123 on 2012-04-03
```
josh@Nero:~$ dpkg-query -l "wine"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                 Version              Description
+++-====================-====================-========================================================
un  wine                 <none>               (no description available)

```

---

### Post by jerome1232 on 2012-04-03
Sounds like your just going to have to manually delete the files, 

I would delete the files you found with whereis wine, in addition to what's listed here

[http://wiki.winehq.org/FAQ#head-2e99ab665e3b15d1880eff2bcbb640b2d5839586](http://wiki.winehq.org/FAQ#head-2e99ab665e3b15d1880eff2bcbb640b2d5839586)

Then try installing wine from apt-get and cross your fingers. I can't guarantee it'll work.

---

### Post by bobman321123 on 2012-04-03
Well "wine --version" no longer runs, so that's a good sign I guess.
What if I want to install old versions of wine?
Just install from source?

---

### Post by jerome1232 on 2012-04-03
Depends on what version you want you can get down to 1.2 easily enough

```
sudo apt-get install wine1.2
########### or ###################
sudo apt-get install wine1.3
```

Then lock it to that version, so it won't be upgraded (based on the man page I believe this is correct syntax)

```
sudo apt-mark hold wine1.2
############o or ###############
sudo apt-mark hold wine1.3
```

---

### Post by bobman321123 on 2012-04-03
Whenever I install wine1.3, it adds 1.4 to the list and sets it as the default.
Whenever I remove 1.4, it takes 1.3 with it.
GAH

---

### Post by jerome1232 on 2012-04-03
Strange, do you have a wine ppa enabled? I just noticed wine1.3 is the latest on my system (11.10) If so, disable that ppa.

If I install wine1.2 it explicitly removes all other versions of wine. Wine 1.3 I can't really play with since it's the latest on my system.

---

### Post by bobman321123 on 2012-04-03
Gah, it turns out that 12.04's default is 1.4, and the PPA enables getting 1.5.1. 
So, I can't install from source because 12.04 is multiarch which makes compiling 32bit wine very very complicated. 
*sigh* Ah well.

---

### Post by jerome1232 on 2012-04-03
ah, your using the beta, the dependencies are *probably* just not setup correctly and that's why installing 1.3 get's you 1.4 as well. You should root around in the precise section of the forums, you will probably get better answers there for it.

---

### Post by bobman321123 on 2012-04-03
Yeah, ok. Thanks. :)
The reason I posted here is because it seemed like a wine problem, and not a 12.04 problem.

---

