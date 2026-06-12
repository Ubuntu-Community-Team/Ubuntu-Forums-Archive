---
title: "Microsoft Office 2007 SP2 won't install under Wine"
date: 2009-08-27
forum: General Help
---

### Post by nbtrap on 2009-08-27
Has anyone had success installing service pack 2 under Wine? I'm getting a "Installation of this package failed." message. I'm running the newest the newest developmental version of Wine (1.1.28) and Ubuntu 9.04.

---

### Post by ZettaGeek on 2009-08-27
Do you have a terminal output I can review? Run the install using the terminal and post your output.

---

### Post by nbtrap on 2009-08-27
Here you go:

```

nathan@Nathan-Linux:~$ cd Downloads
nathan@Nathan-Linux:~/Downloads$ wine office2007sp2-kb953195-fullfile-en-us.exe
fixme:reg:GetNativeSystemInfo (0x32fa1c) using GetSystemInfo()
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1652a8 0x32e4b8 0x169418 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x173f00 0x32e4b8 0x179840 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1924c0 0x32e4b8 0x192528 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1ad1d8 0x32e4b8 0x1c3e68 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1c6f68 0x32e4b8 0x1ce8c90 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1d02460 0x32e4b8 0x1cfc670 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1d1a350 0x32e4b8 0x1d21b80 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1d6b828 0x32e4b8 0x1d6b2b8 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1d3d1d0 0x32e4b8 0x1d3fa10 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1d622d8 0x32e4b8 0x1d620b0 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1d65728 0x32e4b8 0x1d6b068 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1da3c68 0x32e4b8 0x1d96e68 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1dea008 0x32e4b8 0x1de9b38 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1ded038 0x32e4b8 0x1df2978 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1e360e8 0x32e4b8 0x1e3b2a8 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1e4de10 0x32e4b8 0x1e54028 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1e69ce8 0x32e4b8 0x1e6ee28 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1e87da8 0x32e4b8 0x1e8d4f8 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1eaee50 0x32ddec 0x1eb2fc0 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1ebc210 0x32ddec 0x1ec9ea0 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x37e15b0 0x32ddec 0x37e1040 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1f19518 0x32ddec 0x1f117f8 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x37c23b8 0x32ddec 0x37b55b8 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x37f0410 0x32ddec 0x37f0478 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x3809ee0 0x32ddec 0x3809cb8 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x3832918 0x32ddec 0x380d918 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x384e660 0x32ddec 0x3850ea0 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x3878d18 0x32ddec 0x38726a8 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x3891120 0x32ddec 0x387aef0 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x38a5410 0x32ddec 0x38a94f8 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x38cfd78 0x32ddec 0x38cf8a8 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x38d7880 0x32ddec 0x38d29d8 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x39224f8 0x32ddec 0x39265e0 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x3939388 0x32ddec 0x393db38 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x39533e8 0x32ddec 0x3958528 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x39704d8 0x32ddec 0x3975c28 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x3292f8 (nil) 0x3292fc 0x3292f0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x398ec20 0x3292f8 0x3992d90 0x3292fc 0x3292f0 - stub
fixme:msi:MsiSourceListGetInfoW Unhandled context 4
fixme:msi:MsiSourceListGetInfoW Unhandled context 4
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
fixme:msxml:DllCanUnloadNow 
fixme:msxml:DllCanUnloadNow 
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
err:msi:ACTION_CallDllFunction GetProcAddress(L"DoNiceRegistry") failed
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 72 ignored L"Upgrade" table values
fixme:mscoree:LoadLibraryShim (0x7dddea4c L"fusion.dll", (nil), (nil), 0x329550): semi-stub
fixme:msi:MsiSourceListGetInfoW Unhandled context 4
err:msi:source_matches_volume Failed to get volume information
err:msi:ready_media Cabinet not found: L"C:\\windows\\Installer\\EnterWW.CAB"
err:msi:ACTION_MsiPublishAssemblies Failed to ready media
err:msi:ITERATE_Actions Execution halted, action L"InstallExecute" returned 1603
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x3292f8 (nil) 0x3292fc 0x3292f0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x4c5b2f0 0x3292f8 0x4c5e350 0x3292fc 0x3292f0 - stub
fixme:msi:MsiSourceListGetInfoW Unhandled context 4
fixme:msi:MsiSourceListGetInfoW Unhandled context 4
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
fixme:msxml:DllCanUnloadNow 
fixme:msxml:DllCanUnloadNow 
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msidb:JOIN_get_row (0x4a88148, 4, 0x9decb28): stub!
fixme:mscoree:LoadLibraryShim (0x7dddea4c L"fusion.dll", (nil), (nil), 0x329550): semi-stub
fixme:msi:MsiSourceListGetInfoW Unhandled context 4
err:msi:source_matches_volume Failed to get volume information
err:msi:ready_media Cabinet not found: L"C:\\windows\\Installer\\InfLR.CAB"
err:msi:ACTION_MsiPublishAssemblies Failed to ready media
err:msi:ITERATE_Actions Execution halted, action L"InstallExecute" returned 1603
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:imm:ImmDisableIME (-1): stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:imm:ImmDisableIME (-1): stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
err:ole:CoUninitialize Mismatched CoUninitialize
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:reg:GetNativeSystemInfo (0x33fc5c) using GetSystemInfo()
fixme:netapi32:NetGetJoinInformation Stub (null) 0x33fc84 0x33fc78
fixme:advapi:CheckTokenMembership ((nil) 0x159330 0x33fc60) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x159330 0x33fc60) stub!
err:ole:CoUninitialize Mismatched CoUninitialize
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:reg:GetNativeSystemInfo (0x33fc5c) using GetSystemInfo()
fixme:netapi32:NetGetJoinInformation Stub (null) 0x33fc84 0x33fc78
fixme:advapi:CheckTokenMembership ((nil) 0x159330 0x33fc60) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x159330 0x33fc60) stub!

```

---

### Post by ZettaGeek on 2009-08-27
*"fixme:mscoree:LoadLibraryShim (0x7dddea4c L"fusion.dll", (nil), (nil), 0x329550): semi-stub"*

Try adding this DLL to your Wine Windows folder:
[http://www.dlldump.com/download-dll-files_new.php/dllfiles/F/fusion.dll/1.0.3705.60186/download.html]("http://www.dlldump.com/download-dll-files_new.php/dllfiles/F/fusion.dll/1.0.3705.60186/download.html")

Also, **_make sure_** your WINE is set to emulate **_Windows XP_**.

---

### Post by ZettaGeek on 2009-08-27
> **ZettaGeek said:**
> *"fixme:mscoree:LoadLibraryShim (0x7dddea4c L"fusion.dll", (nil), (nil), 0x329550): semi-stub"*

Try adding this DLL to your Wine Windows folder:
[http://www.dlldump.com/download-dll-files_new.php/dllfiles/F/fusion.dll/1.0.3705.60186/download.html]("http://www.dlldump.com/download-dll-files_new.php/dllfiles/F/fusion.dll/1.0.3705.60186/download.html")

Also, **_make sure_** your WINE is set to emulate **_Windows XP_**.


After that, run the install again and post the output.

---

### Post by nbtrap on 2009-08-27
I'm now getting an error message in Wine. Here's the terminal output:

```

nathan@Nathan-Linux:~$ cd Downloads
nathan@Nathan-Linux:~/Downloads$ wine office2007sp2-kb953195-fullfile-en-us.exe
fixme:reg:GetNativeSystemInfo (0x32fa1c) using GetSystemInfo()
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:msxml:domcomment_QueryInterface Unsupported interface {2933bf86-7b36-11d2-b20e-00c04f983e60}
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x165038 0x32e4b8 0x1691a8 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x173c58 0x32e4b8 0x179598 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x192268 0x32e4b8 0x1922d0 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1acf80 0x32e4b8 0x1c3c10 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1c6d10 0x32e4b8 0x1ce8cd0 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1d024a0 0x32e4b8 0x1cfc6b0 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1d1a390 0x32e4b8 0x1d21bc0 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1d6b868 0x32e4b8 0x1d6b2f8 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1d3d210 0x32e4b8 0x1d3fa50 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1d62318 0x32e4b8 0x1d620f0 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1d65768 0x32e4b8 0x1d6b0a8 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1da3ca8 0x32e4b8 0x1d96ea8 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1dea048 0x32e4b8 0x1de9b78 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1ded078 0x32e4b8 0x1df29b8 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1e36130 0x32e4b8 0x1e3b2f0 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1e4de18 0x32e4b8 0x1e54030 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1e69c98 0x32e4b8 0x1e6edd8 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32e4b8 (nil) 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1e87d58 0x32e4b8 0x1e8d4a8 0x32e4bc 0x32e4b0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1eaecc8 0x32ddec 0x1eb2e38 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1ebced8 0x32ddec 0x1ed3b68 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x37e1488 0x32ddec 0x37e0f18 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x1f1acc0 0x32ddec 0x1f12fa0 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x37c2290 0x32ddec 0x37b5490 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x37f02e8 0x32ddec 0x37f0350 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x3809db8 0x32ddec 0x3809b90 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x38327f0 0x32ddec 0x380d7f0 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x384e538 0x32ddec 0x3850d78 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x3878bf0 0x32ddec 0x3872580 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x3890ff8 0x32ddec 0x387adc8 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x38a52e8 0x32ddec 0x38a93d0 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x38cfc50 0x32ddec 0x38cf780 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x38d7758 0x32ddec 0x38d28b0 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x39223e8 0x32ddec 0x39264d0 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x3939278 0x32ddec 0x393da28 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x39532d8 0x32ddec 0x3958418 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x32ddec (nil) 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x39703d8 0x32ddec 0x3975b28 0x32ddf0 0x32dde4 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" (nil) 0x3292f8 (nil) 0x3292fc 0x3292f0 - stub
fixme:advapi:LookupAccountNameW (null) L"nathan" 0x398eb50 0x3292f8 0x3992cc0 0x3292fc 0x3292f0 - stub
fixme:msi:MsiSourceListGetInfoW Unhandled context 4
fixme:msi:MsiSourceListGetInfoW Unhandled context 4
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform no matching row to transform
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
err:msidb:msi_table_load_transform insert row failed
fixme:msxml:DllCanUnloadNow 
fixme:msxml:DllCanUnloadNow 
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
err:msi:ACTION_CallDllFunction GetProcAddress(L"DoNiceRegistry") failed
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 72 ignored L"Upgrade" table values
fixme:mscoree:LoadLibraryShim (0x7df09a4c L"fusion.dll", (nil), (nil), 0x329550): semi-stub
fixme:msi:install_assembly Manifest unhandled
fixme:mscoree:CoInitializeCor (0x00000000): stub
fixme:mscoree:GetAssemblyMDImport (0x4bd6210 L"C:\\windows\\temp\\Microsoft.Office.Interop.Graph.dll", 0x79047e28, (nil)): stub
wine: Unhandled page fault on read access to 0x00000000 at address 0x7904a0ed (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7904a0ed).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7904a0ed ESP:003283c4 EBP:0032862c EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:00000000 ECX:00000000 EDX:003285e8
 ESI:04bd61e8 EDI:00328618
Stack dump:
0x003283c4:  00000078 04bd61e8 04bd5192 00000001
0x003283d4:  7de6c140 f7e32ff4 f7d42584 00328404
0x003283e4:  f7d43a3f f7e32ff4 7bcb0127 00328414
0x003283f4:  f7d43a3f 00328438 f7d42584 7bcb0127
0x00328404:  f7d13b0b 00000000 00000000 00328434
0x00328414:  f7d43a3f 00328458 f7e146ca 7bcb0127
Backtrace:
=>0 0x7904a0ed in fusion (+0xa0ed) (0x0032862c)
  1 0x79049f87 in fusion (+0x9f87) (0x00328644)
  2 0x79049f54 in fusion (+0x9f54) (0x00328650)
  3 0x79049ede in fusion (+0x9ede) (0x00328674)
  4 0x7905e046 in fusion (+0x1e046) (0x00328ee4)
  5 0x7de99b82 in msi (+0x19b82) (0x00328f24)

```

---

### Post by nbtrap on 2009-08-28
Bump.

---

### Post by scouser73 on 2009-08-28
See if this is any good for you: [[COLOR="Red"]**Microsoft Office 2007 using WINE**[/COLOR]]("http://www.quicktweaks.com/2008/04/09/install-ms-office-2007-in-linux/")

---

### Post by nbtrap on 2009-08-28
> **scouser73 said:**
> See if this is any good for you: [[COLOR="Red"]**Microsoft Office 2007 using WINE**[/COLOR]]("http://www.quicktweaks.com/2008/04/09/install-ms-office-2007-in-linux/")

This link is for installing Office 2007 on an older version of Wine that didn't support it out of the box. I need to install _Service Pack 2_.

---

### Post by nbtrap on 2009-08-28
Bump.

---

### Post by nbtrap on 2009-08-28
Bump.

---

### Post by uylug on 2009-08-28
Seriously, why would one want to emulate Microsoft Office?

---

### Post by nbtrap on 2009-08-29
Bump.

---

### Post by nbtrap on 2009-08-30
Bump.

---

### Post by spinstartshere on 2009-09-06
A bug report already exists for this issue at [http://bugs.winehq.org/show_bug.cgi?id=18376](http://bugs.winehq.org/show_bug.cgi?id=18376).  I would also like to be able to install Microsoft Office 2007 Service Pack 2 but I can't because of the errors.

---

### Post by the8thstar on 2009-10-03
BUMP too! Crossover will only let you install Office 2007 but no Service Packs (1 and 2 at this time). I wish Wine would allow this.

---

### Post by akakingess on 2009-10-03
As it is already submitted as a known bug, I would go to launchpad (the ubuntu bug tracker) and submit your support for getting that solved. Maybe the more of you that have the problem and submit support for finding a solution (no work on your half, just sign up and "vote" for the bug), then maybe the priority will be raised. Or, maybe it is already addressed in Karmic Koala(9.10) and that is what the developers are waiting for.

---

### Post by the8thstar on 2009-10-05
I believe this is a Wine related bug, not Ubuntu. Wine has its own bug reporting tool.

---

