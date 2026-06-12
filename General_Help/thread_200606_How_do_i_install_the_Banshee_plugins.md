---
title: "How do i install the Banshee plugins?"
date: 2006-06-20
forum: General Help
---

### Post by rekahsoft on 2006-06-20
I use banshee for my music and i would like to have podcast support and such (which is provided by the plugins). I have not been succesful in installing them. After checking out the banshee-officail-plugins from thier subversion server I run autogen.sh and get the following errors: ```
Checking for required M4 macros...
  libtool.m4 not found
  glib-gettext.m4 not found
  intltool.m4 not found
  pkg.m4 not found
Checking for forbidden M4 macros...
***Error***: some autoconf macros required to build banshee-official-plugins
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?
```

---

### Post by jkwarras on 2006-06-20
Yeah, I'm having the same problem here...

---

### Post by cskeide on 2006-06-21
[QUOTE=rekahsoft]I use banshee for my music and i would like to have podcast support and such (which is provided by the plugins). I have not been succesful in installing them. After checking out the banshee-officail-plugins from thier subversion server I run autogen.sh and get the following errors: ```
Checking for required M4 macros...
  libtool.m4 not found
  glib-gettext.m4 not found
  intltool.m4 not found
  pkg.m4 not found
Checking for forbidden M4 macros...
***Error***: some autoconf macros required to build banshee-official-plugins
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?
```[/QUOTE]

This should fix the error you are receiving:
```

sudo apt-get build-dep banshee
sudo apt-get install automake1.9
sudo update-alternatives --set automake /usr/bin/automake-1.9
sudo ldconfig

```

However, you need to compile [banshee from source]("http://patches.ximian.com/Banshee_Source") in order to use the podcast plugin and/or the smart playlists plugin. The following plugins work for the version of banshee in the repositories:
- MiniMode
- Radio
- Recommendation

This is what I did for those three plugins to work:
```

./autogen.sh --prefix=/usr --disable-smart-playlists --disable-podcast
make
sudo make install

```

---

### Post by rekahsoft on 2006-06-21
Thanks you so much :) i have one more question tho...I installed Banshee from source and now have 0.10.0 from cvs (i got mine from subversion). Anyway all the plugins installed great except the itunes plugin...i get this error:
```
collin@RekahSoft:~/source/banshee-itunes-plugin$ make
Making all in src
make[1]: Entering directory `/home/collin/source/banshee-itunes-plugin/src'
/usr/bin/mcs -debug -nowarn:0169 -out:iTunesMusicStore.dll -target:library -r:ICSharpCode.SharpZipLib -r:System.Web -r:/usr/lib/banshee/Banshee.Base.dll -r:/usr/lib/banshee/Banshee.Widgets.dll -r:/usr/lib/banshee/entagged-sharp.dll -r:/usr/lib/banshee/hal-sharp.dll -r:/usr/lib/banshee/MusicBrainz.dll -r:Mono.Posix -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/pango-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/atk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gdk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gtk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gconf-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gconf-sharp-peditors.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gnome-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/art-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gnome-vfs-sharp.dll   ./MusicStorePlugin.cs ./MusicStoreSource.cs ./MusicStoreConfigDialog.cs ./MusicStoreView.cs ./MusicStoreTrackInfo.cs ./MusicStorePurchaseTransaction.cs ./fairstore/FairStore.cs ./fairstore/iTMS.cs ./fairstore/Utility.cs ./fairstore/MP4.cs

** (/usr/lib/mono/1.0/mcs.exe:27919): WARNING **: The class System.Collections.Generic.IEnumerable`1 could not be loaded, used in mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries
used by your application.
=================================================================

Stacktrace:

in (wrapper managed-to-native) System.Reflection.MonoMethodInfo:get_method_info (intptr,System.Reflection.MonoMethodInfo&) <0x4>
in (wrapper managed-to-native) System.Reflection.MonoMethodInfo:get_method_info (intptr,System.Reflection.MonoMethodInfo&) <0xffffffe5>
in System.Reflection.MonoMethod:get_Attributes () <0x25>
in System.Reflection.MethodBase:get_IsVirtual () <0xc>
in Mono.CSharp.MemberCache:AddMethods (System.Reflection.BindingFlags,System.Type) <0x188>
in Mono.CSharp.MemberCache:AddMethods (System.Type) <0x13>
in Mono.CSharp.MemberCache:.ctor (Mono.CSharp.IMemberContainer) <0x149>
in Mono.CSharp.TypeHandle:.ctor (System.Type) <0xbc>
in Mono.CSharp.TypeHandle:GetTypeHandle (System.Type) <0x4e>
in Mono.CSharp.TypeHandle:GetMemberCache (System.Type) <0xb>
in Mono.CSharp.TypeManager:MemberLookup_FindMembers (System.Type,System.Reflection.MemberTypes,System.Reflection.BindingFlags,string,bool&) <0x14e>
in Mono.CSharp.TypeManager:RealMemberLookup (System.Type,System.Type,System.Type,System.Reflection.MemberTypes,System.Reflection.BindingFlags,string,System.Collections.IList) <0x1ad>
in Mono.CSharp.TypeManager:MemberLookup (System.Type,System.Type,System.Type,System.Reflection.MemberTypes,System.Reflection.BindingFlags,string,System.Collections.IList) <0x1f>
in Mono.CSharp.Expression:MemberLookup (Mono.CSharp.EmitContext,System.Type,System.Type,System.Type,string,System.Reflection.MemberTypes,System.Reflection.BindingFlags,Mono.CSharp.Location) <0x38>
in Mono.CSharp.Expression:MemberLookupFinal (Mono.CSharp.EmitContext,System.Type,System.Type,string,System.Reflection.MemberTypes,System.Reflection.BindingFlags,Mono.CSharp.Location) <0x2f>
in Mono.CSharp.Expression:MemberLookupFinal (Mono.CSharp.EmitContext,System.Type,System.Type,string,Mono.CSharp.Location) <0x1d>
in Mono.CSharp.MemberAccess:DoResolve (Mono.CSharp.EmitContext,Mono.CSharp.Expression) <0x217>
in Mono.CSharp.MemberAccess:DoResolve (Mono.CSharp.EmitContext) <0xf>
in Mono.CSharp.Expression:Resolve (Mono.CSharp.EmitContext,Mono.CSharp.ResolveFlags) <0xe3>
in Mono.CSharp.Expression:Resolve (Mono.CSharp.EmitContext) <0x12>
in Mono.CSharp.Assign:DoResolve (Mono.CSharp.EmitContext) <0xd0>
in Mono.CSharp.Expression:Resolve (Mono.CSharp.EmitContext,Mono.CSharp.ResolveFlags) <0xe3>
in Mono.CSharp.Expression:Resolve (Mono.CSharp.EmitContext) <0x12>
in Mono.CSharp.ExpressionStatement:ResolveStatement (Mono.CSharp.EmitContext) <0x13>
in Mono.CSharp.StatementExpression:Resolve (Mono.CSharp.EmitContext) <0x1f>
in Mono.CSharp.Block:Resolve (Mono.CSharp.EmitContext) <0x1d9>
in Mono.CSharp.EmitContext:ResolveTopBlock (Mono.CSharp.EmitContext,Mono.CSharp.ToplevelBlock,Mono.CSharp.Parameters,Mono.CSharp.IMethodData,bool&) <0x122>
in Mono.CSharp.EmitContext:EmitTopBlock (Mono.CSharp.IMethodData,Mono.CSharp.ToplevelBlock) <0x4b>
in Mono.CSharp.MethodData:Emit (Mono.CSharp.TypeContainer,Mono.CSharp.Attributable) <0x1ab>
in Mono.CSharp.Method:Emit () <0x30>
in Mono.CSharp.TypeContainer:EmitType () <0x64d>
in Mono.CSharp.RootContext:EmitCode () <0x226>
in Mono.CSharp.Driver:MainDriver (string[]) <0xae4>
in Mono.CSharp.Driver:Main (string[]) <0x41>
in (wrapper runtime-invoke) System.Object:runtime_invoke_int_string[] (object,intptr,intptr,intptr) <0x6c1684f>

Native stacktrace:

        /usr/lib/libmono.so.0(mono_handle_native_sigsegv+0xe3) [0x4756309f]
        /usr/lib/libmono.so.0 [0x47524c9e]
        [0xffffe440]
        /usr/lib/libmono.so.0 [0x475f4b05]
        /usr/lib/libmono.so.0(mono_type_create_from_typespec_full+0x13f) [0x475f77df]
        /usr/lib/libmono.so.0 [0x47609783]
        /usr/lib/libmono.so.0 [0x4760993c]
        /usr/lib/libmono.so.0(mono_class_get_full+0x24) [0x47609acc]
        /usr/lib/libmono.so.0(mono_metadata_interfaces_from_typedef_full+0x132) [0x475f60bf]
        /usr/lib/libmono.so.0 [0x4760a336]
        /usr/lib/libmono.so.0(mono_class_init+0x7a8) [0x47606bb4]
        /usr/lib/libmono.so.0(mono_type_get_object+0x8b) [0x47595561]
        /usr/lib/libmono.so.0 [0x475ace10]
        [0x40c23590]
        [0x40c2354e]
        [0x40fa967d]
        [0x40fa9059]
        [0x40fa8e7c]
        [0x40fa8dba]
        [0x40fa8c5d]
        [0x40fa8b5f]
        [0x40fa8a1c]
        [0x40fc0be7]
        [0x40fc0576]
        [0x40fc03a8]
        [0x40fc02a9]
        [0x40fce450]
        [0x40fce406]
        [0x40fce078]
        [0x40fcde48]
        [0x40fc8f14]
        [0x40fc8dc3]
        [0x40fc9369]
        [0x40fc8f14]
        [0x40fc8dc3]
        [0x40fc924c]
        [0x40fcba50]
        [0x40fc6372]
        [0x40fc5d2b]
        [0x40fc5b94]
        [0x40fcb5cc]
        [0x40fcb1f9]
        [0x40fbc6d6]
        [0x40fbbc17]
        [0x409321e5]
        [0x40930c1a]
        [0x4092b874]
        /usr/lib/libmono.so.0 [0x47542098]
        /usr/lib/libmono.so.0(mono_runtime_invoke+0x33) [0x475a4b4d]
        /usr/lib/libmono.so.0(mono_runtime_exec_main+0xa8) [0x475a7729]
        /usr/lib/libmono.so.0(mono_runtime_run_main+0x188) [0x475aa850]
        /usr/lib/libmono.so.0(mono_jit_exec+0x90) [0x475547be]
        /usr/lib/libmono.so.0(mono_main+0x962) [0x475551af]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0x47cadea2]
        /usr/bin/mono [0x8048459]
make[1]: *** [iTunesMusicStore.dll] Aborted
make[1]: Leaving directory `/home/collin/source/banshee-itunes-plugin/src'
make: *** [all-recursive] Error 1

```Why is this happening? When i run autogen.sh this is its output:
```
collin@RekahSoft:~/source/banshee-itunes-plugin$ ./autogen.sh --prefix=/usr
Running aclocal -I .  ...
Running automake --gnu  ...
Running autoconf ...
Running ./configure --prefix=/usr ...
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/collin/source/banshee-itunes-plugin/missing: Unknown `--run' option
Try `/home/collin/source/banshee-itunes-plugin/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for mono... /usr/bin/mono
checking for mcs... /usr/bin/mcs
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for BANSHEE... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile

Plugin will be installed in /usr/lib/banshee/Banshee.Plugins
You should now run `make'
```

Also on a side not why is there gray around the banshee tray icon? There never was before...(see the screen shot)

---

