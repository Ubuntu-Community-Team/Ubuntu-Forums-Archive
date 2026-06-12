---
title: "How Do You Upgrade to OpenOffice 3.3.1?"
date: 2009-08-29
forum: General Help
---

### Post by oldefoxx on 2009-08-29
I'm trying to upgrade Ubuntu 9.04 to have the latest free version of OpenOffice, which is version 3.1.1.  Only when I try to download it, I either get a shell script file (ends with .sh), a .deb.tar.gz file (a compressed tar file that needs to be extracted), and I can't find any instructions for working with these, at least not through the GUI (the user does not have sufficient rights).  I finally was able to use the sudo mode in a command terminal and the tar instruction to uncompress the .deb.tar.gz file into a new folder named Extract, and that created a DEBS subfolder and extracted the contained .deb file into it.  But neither apt-get install nor Synaptic Package Manager wants to work with the resulting .deb file.  And searches using key words are not helping.

I guess it is time to ask the essential question of, "Okay NOW What?"  Anybody care to help?

---

### Post by balaknair on 2009-08-30
The latest version of OOo is 3.1.1, and you can install it via the Launchpad PPA repositories(OOo 3.1.0 for Jaunty at present, will be updated to 3.1.1 soon)
[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)
Just add the repositories and the PGP key to Software Sources and then run update manager.
This way the packages will be updated automatically via the update manager(downloading and installing the debs, the packages won't be updated automatically).

Instructions on how to add repositories and PGP keys are available via a help link on the above page- 'Read about installing'

---

### Post by scouser73 on 2009-08-30
> **oldefoxx said:**
> I'm trying to upgrade Ubuntu 9.04 to have the latest free version of OpenOffice, which is version 3.3.1.  Only when I try to download it, I either get a shell script file (ends with .sh), a .deb.tar.gz file (a compressed tar file that needs to be extracted), and I can't find any instructions for working with these, at least not through the GUI (the user does not have sufficient rights).  I finally was able to use the sudo mode in a command terminal and the tar instruction to uncompress the .deb.tar.gz file into a new folder named Extract, and that created a DEBS subfolder and extracted the contained .deb file into it.  But neither apt-get install nor Synaptic Package Manager wants to work with the resulting .deb file.  And searches using key words are not helping.

I guess it is time to ask the essential question of, "Okay NOW What?"  Anybody care to help?

OpenOffice 3.1.1 is only at RC2 stage for the moment, and I'd love to know how you downloaded it as I can't seem to get my download manager to sort it.

Reading the OpenOffice Wiki, I've found that 3.1.1 is due to be released on [[COLOR="Red"]**Monday 31st August 2009**[/COLOR]]("http://wiki.services.openoffice.org/wiki/OOoRelease311").

---

### Post by oldefoxx on 2009-08-30
I had to follow different links, which took me to different downloads.  The deb version was found at Softpedia, but the first found page had variations That you could pick from, such as for Windows, Mac, 64-bit, English, and so on.  I guess I should have added it to my list of favorites.

This is a day with nothing going right.  My install of Windows 2000 Pro as a client under Ubuntu/VirtualBox is now getting the BSOD when I try to boot, and I can only get it up in safe mode.  It might have something to do with trying to enable the experimental version of Direct3D with Windows 2000 Pro, then being warned that it is only good for 16 bits, not 32 bits.  I found before that VirtualBox is not compatible with 16-bit windows or DOS, so what would be the point of including it?  Whatever is wrong, it looks like a complete reinstall of Windows 2000 Pro is in order.  

Sorry about indicating OpenOffice version 3.1.1 when I actually meant version 3.1.1.

---

### Post by mdurham on 2009-08-30
> **oldefoxx said:**
> Sorry about indicating OpenOffice version 3.1.1 when I actually meant version 3.1.1.

That's ok, which version do you prefer, 3.1.1 or 3.1.1? :)

---

### Post by Ian Ferguson on 2009-08-31
I've tried installing OpenOffice 3.1.1 using the method described in this link:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

The installation seemed to go fine, and I've got all the new OOo3-style icons in my Applications>Office menu, but when I try to open any Open Office application it crashes, and I get this:

[ATTACH]126944[/ATTACH]

Has anyone successfully installed 3.1.1 yet?

---

### Post by Copernicus1234 on 2009-08-31
> **mdurham said:**
> That's ok, which version do you prefer, 3.1.1 or 3.1.1? :)

This thread is getting better and better. :P

---

### Post by scouser73 on 2009-08-31
> That's ok, which version do you prefer, 3.1.1 or 3.1.1? 

I prefer 3.1.1 myself.

---

### Post by balaknair on 2009-08-31
> **Ian Ferguson said:**
> I've tried installing OpenOffice 3.1.1 using the method described in this link:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

The installation seemed to go fine, and I've got all the new OOo3-style icons in my Applications>Office menu, but when I try to open any Open Office application it crashes, and I get this:

[ATTACH]126944[/ATTACH]

Has anyone successfully installed 3.1.1 yet?

Using the downloaded version from Sun can cause major foulups with the currently installed version of Java and with Gnome integration(speaking from first hand experience).
I'd advise waiting a couple of days till they get OOo 3.1.1 uploaded to the PPA 
[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

---

### Post by scouser73 on 2009-08-31
> **Ian Ferguson said:**
> I've tried installing OpenOffice 3.1.1 using the method described in this link:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

The installation seemed to go fine, and I've got all the new OOo3-style icons in my Applications>Office menu, but when I try to open any Open Office application it crashes, and I get this:

[ATTACH]126944[/ATTACH]

Has anyone successfully installed 3.1.1 yet?

Hi Ian, I've installed the updated OpenOffice 3.1.1, please follow my instructions.

Firstly, go to the OpenOffice website: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and download the **Linux .deb** file.

Once you have done that, extract the .deb file, **OOo_3.1.1_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called [B]OOO310_m19_native_packed-1_en-US.9420
[/B]
You can remove the existing version of OpenOffice if you wish with this command: **sudo apt-get remove openoffice*.***

Copy and paste **OOO310_m19_native_packed-1_en-US.9420** onto the desktop then open Terminal and paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/*.deb**

Then paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9420_all.deb**

Once you've done that you'll find OpenOffice 3.1.1 in Office.

---

### Post by Ian Ferguson on 2009-09-01
Hi, Scouser.

That's more or less what I did, except for copying the OOO310......... folder to the desktop. I did the install from my home folder, where I'd extracted the .tar.gz archive. I think the problem may have been that, using Synaptic rather than **apt-get remove**, I hadn't completely removed all traces of the previously installed version.

I think the easiest way is to go with Balaknair and use the Launchpad PPA. That way, I've successfully upgraded from OOo 3.0.1, which came packaged with Jaunty when I installed it, to 3.1.0. The advantage of this, as Balaknair points out, is that  once you've got the PPA added to your software sources the Update Manager will take care of future updates.

According to the email I received yesterday from OpenOffice.org, 3.1.1 is just a minor update to 3.1.0, with a few bug fixes. The next major update, 3.2, is due in November 09, and will have significant added functionality.

---

### Post by vckeating on 2009-09-02
> **Ian Ferguson said:**
> I've tried installing OpenOffice 3.1.1 using the method described in this link:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

The installation seemed to go fine, and I've got all the new OOo3-style icons in my Applications>Office menu, but when I try to open any Open Office application it crashes, and I get this:

[ATTACH]126944[/ATTACH]

Has anyone successfully installed 3.1.1 yet?

I'm having exactly the same problem.  It installs fine, but you can't open a document without that error occurring.  Any ideas out there?

---

### Post by vckeating on 2009-09-02
Oh, and if it helps, here is the error report generated when the above happens:

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE errormail:errormail PUBLIC "-//OpenOffice.org//DTD ErrorMail 1.0//EN" "errormail.dtd">
<errormail:errormail xmlns:errormail="http://openoffice.org/2002/errormail" usertype="">
<reportmail:mail xmlns:reportmail="http://openoffice.org/2002/reportmail" version="1.1" feedback="false" email="">
<reportmail:title></reportmail:title>
<reportmail:attachment name="description.txt" media-type="text/plain" class="UserComment"/>
<reportmail:attachment name="stack.txt" media-type="text/plain" class="pstack output"/>
</reportmail:mail>
<officeinfo:officeinfo xmlns:officeinfo="http://openoffice.org/2002/officeinfo" build="310m19(Build:9420)" platform="unxlngi6.pro" language="" exceptiontype="6" product="OpenOffice.org 3.1" procpath="/opt/openoffice.org3/program/"/>
<systeminfo:systeminfo xmlns:systeminfo="http://openoffice.org/2002/systeminfo">
<systeminfo:System name="Linux" version="#49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009" build="2.6.28-15-generic" locale="en_CA.UTF-8"/>
<systeminfo:CPU type="i686"/>
</systeminfo:systeminfo>
<errormail:Stack type="Linux">
<errormail:StackInfo pos="0" ip="0xb7e53ed8" rel="0x1fed8" name="libuno_sal.so.3" path="/opt/openoffice.org/ure/lib/"/>
<errormail:StackInfo pos="1" ip="0xb7e547bc" rel="0x207bc" name="libuno_sal.so.3" path="/opt/openoffice.org/ure/lib/"/>
<errormail:StackInfo pos="2" ip="0xb7ff0400" rel="0x400" name="" ordinal="__kernel_sigreturn+0x0"/>
<errormail:StackInfo pos="3" ip="0xb7974098" rel="0x2d098" name="libc.so.6" path="/lib/tls/i686/cmov/" ordinal="abort+0x188"/>
<errormail:StackInfo pos="4" ip="0xb7b82ad1" rel="0xa8ad1" name="libstdc++.so.6" path="/opt/openoffice.org/ure/lib/" ordinal="_ZN9__gnu_cxx27__verbose_terminate_handlerEv+0x101"/>
<errormail:StackInfo pos="5" ip="0xb7b80505" rel="0xa6505" name="libstdc++.so.6" path="/opt/openoffice.org/ure/lib/"/>
<errormail:StackInfo pos="6" ip="0xb7b80542" rel="0xa6542" name="libstdc++.so.6" path="/opt/openoffice.org/ure/lib/"/>
<errormail:StackInfo pos="7" ip="0xb7b80739" rel="0xa6739" name="libstdc++.so.6" path="/opt/openoffice.org/ure/lib/" ordinal="__cxa_rethrow+0x59"/>
<errormail:StackInfo pos="8" ip="0xadb7ae86" rel="0x22e86" name="deploymentli.uno.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="9" ip="0xadb7e9a7" rel="0x269a7" name="deploymentli.uno.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="10" ip="0xb6620dc9" rel="0xb3dc9" name="libsbli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN5basic23ScriptExtensionIterator28implGetNextUserScriptPackageERb+0x1ed"/>
<errormail:StackInfo pos="11" ip="0xb66211a0" rel="0xb41a0" name="libsbli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN5basic23ScriptExtensionIterator24nextBasicOrDialogLibraryERb+0x5c"/>
<errormail:StackInfo pos="12" ip="0xb66214d2" rel="0xb44d2" name="libsbli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN5basic19SfxLibraryContainer18implScanExtensionsEv+0x27c"/>
<errormail:StackInfo pos="13" ip="0xb662cf93" rel="0xbff93" name="libsbli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN5basic19SfxLibraryContainer9init_ImplERKN3rtl8OUStringERKN3com3sun4star3uno9ReferenceINS7_5embed8XStorageEEE+0x25b7"/>
<errormail:StackInfo pos="14" ip="0xb6630200" rel="0xc3200" name="libsbli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN5basic19SfxLibraryContainer4initERKN3rtl8OUStringERKN3com3sun4star3uno9ReferenceINS7_5embed8XStorageEEE+0x2a"/>
<errormail:StackInfo pos="15" ip="0xb663525f" rel="0xc825f" name="libsbli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN5basic25SfxScriptLibraryContainerC1ERKN3com3sun4star3uno9ReferenceINS3_5embed8XStorageEEE+0x153"/>
<errormail:StackInfo pos="16" ip="0xb65e1ca9" rel="0x74ca9" name="libsbli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN5basic14ImplRepository34impl_createApplicationBasicManagerEv+0x6c1"/>
<errormail:StackInfo pos="17" ip="0xb65e217d" rel="0x7517d" name="libsbli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN5basic14ImplRepository26getApplicationBasicManagerEb+0x45"/>
<errormail:StackInfo pos="18" ip="0xb65e2ea7" rel="0x75ea7" name="libsbli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN5basic22BasicManagerRepository26getApplicationBasicManagerEb+0x1f"/>
<errormail:StackInfo pos="19" ip="0xb742207c" rel="0x9707c" name="libsfxli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN14SfxApplication15GetBasicManagerEv+0x2a"/>
<errormail:StackInfo pos="20" ip="0xb7422017" rel="0x97017" name="libsfxli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN14SfxApplication8GetBasicEv+0x19"/>
<errormail:StackInfo pos="21" ip="0xb742204c" rel="0x9704c" name="libsfxli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN14SfxApplication14EnterBasicCallEv+0x28"/>
<errormail:StackInfo pos="22" ip="0xb7422074" rel="0x97074" name="libsfxli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN14SfxApplication15GetBasicManagerEv+0x22"/>
<errormail:StackInfo pos="23" ip="0xb74cdf44" rel="0x142f44" name="libsfxli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN14SfxObjectShell19SetCurrentComponentERKN3com3sun4star3uno9ReferenceINS3_10XInterfaceEEE+0x8c"/>
<errormail:StackInfo pos="24" ip="0xb75700f2" rel="0x1e50f2" name="libsfxli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZNK12SfxViewShell18SetCurrentDocumentEv+0x30"/>
<errormail:StackInfo pos="25" ip="0xb7570783" rel="0x1e5783" name="libsfxli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN12SfxViewShell8ActivateEh+0x91"/>
<errormail:StackInfo pos="26" ip="0xaec0e17f" rel="0x7cb17f" name="libswli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN6SwView8ActivateEh+0x1cf"/>
<errormail:StackInfo pos="27" ip="0xb75bfdbd" rel="0x234dbd" name="libsfxli.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="28" ip="0xb75ade56" rel="0x222e56" name="libsfxli.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="29" ip="0xb758a50c" rel="0x1ff50c" name="libsfxli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN12SfxViewFrame10DoActivateEhPS_+0x32"/>
<errormail:StackInfo pos="30" ip="0xb7420f35" rel="0x95f35" name="libsfxli.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="31" ip="0xb758d7b3" rel="0x2027b3" name="libsfxli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN12SfxViewFrame12SetViewFrameEPS_+0x1d"/>
<errormail:StackInfo pos="32" ip="0xb7594cf8" rel="0x209cf8" name="libsfxli.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="33" ip="0xb759bf28" rel="0x210f28" name="libsfxli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN11SfxTopFrame14InsertDocumentEP14SfxObjectShell+0x862"/>
<errormail:StackInfo pos="34" ip="0xb7431371" rel="0xa6371" name="libsfxli.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="35" ip="0xb757a53a" rel="0x1ef53a" name="libsfxli.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="36" ip="0xb116ae06" rel="0x13be06" name="libfwkli.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="37" ip="0xb116bf91" rel="0x13cf91" name="libfwkli.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="38" ip="0xb11603df" rel="0x1313df" name="libfwkli.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="39" ip="0xb11606e8" rel="0x1316e8" name="libfwkli.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="40" ip="0xb78cc38c" rel="0xad38c" name="libcomphelp4gcc3.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN10comphelper19SynchronousDispatch8dispatchERKN3com3sun4star3uno9ReferenceINS4_10XInterfaceEEERKN3rtl8OUStringESD_lRKNS4_8SequenceINS3_5beans13PropertyValueEEE+0x4d8"/>
<errormail:StackInfo pos="41" ip="0xb7e00868" rel="0x30868" name="libsofficeapp.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="42" ip="0xb7e13375" rel="0x43375" name="libsofficeapp.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="43" ip="0xb7de6126" rel="0x16126" name="libsofficeapp.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="44" ip="0xb7def535" rel="0x1f535" name="libsofficeapp.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="45" ip="0xb7def64f" rel="0x1f64f" name="libsofficeapp.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="46" ip="0xb7def73e" rel="0x1f73e" name="libsofficeapp.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="47" ip="0xb69f8f6b" rel="0x265f6b" name="libvclli.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="48" ip="0xb47838ac" rel="0x508ac" name="libvclplug_genli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN10SalDisplay21DispatchInternalEventEv+0xb6"/>
<errormail:StackInfo pos="49" ip="0xb4d95d0f" rel="0x13d0f" name="libvclplug_gtkli.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="50" ip="0xb4d95e9d" rel="0x13e9d" name="libvclplug_gtkli.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="51" ip="0xb47e5c81" rel="0x37c81" name="libglib-2.0.so.0" path="/usr/lib/"/>
<errormail:StackInfo pos="52" ip="0xb47e7b88" rel="0x39b88" name="libglib-2.0.so.0" path="/usr/lib/" ordinal="g_main_context_dispatch+0x1e8"/>
<errormail:StackInfo pos="53" ip="0xb47eb0eb" rel="0x3d0eb" name="libglib-2.0.so.0" path="/usr/lib/"/>
<errormail:StackInfo pos="54" ip="0xb47eb268" rel="0x3d268" name="libglib-2.0.so.0" path="/usr/lib/" ordinal="g_main_context_iteration+0x68"/>
<errormail:StackInfo pos="55" ip="0xb4d95dce" rel="0x13dce" name="libvclplug_gtkli.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="56" ip="0xb478b408" rel="0x58408" name="libvclplug_genli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN14X11SalInstance5YieldEbb+0x2c"/>
<errormail:StackInfo pos="57" ip="0xb6822d4f" rel="0x8fd4f" name="libvclli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN11Application5YieldEb+0x5f"/>
<errormail:StackInfo pos="58" ip="0xb6822da1" rel="0x8fda1" name="libvclli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_ZN11Application7ExecuteEv+0x2f"/>
<errormail:StackInfo pos="59" ip="0xb7df2645" rel="0x22645" name="libsofficeapp.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="60" ip="0xb6828b2a" rel="0x95b2a" name="libvclli.so" path="/opt/openoffice.org/basis3.1/program/"/>
<errormail:StackInfo pos="61" ip="0xb6828cb5" rel="0x95cb5" name="libvclli.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="_Z6SVMainv+0x29"/>
<errormail:StackInfo pos="62" ip="0xb7e19e37" rel="0x49e37" name="libsofficeapp.so" path="/opt/openoffice.org/basis3.1/program/" ordinal="soffice_main+0xdb"/>
<errormail:StackInfo pos="63" ip="0x8048dea" rel="0xdea" name="soffice.bin" path="/opt/openoffice.org3/program/" ordinal="main+0x16"/>
<errormail:StackInfo pos="64" ip="0xb795d775" rel="0x16775" name="libc.so.6" path="/lib/tls/i686/cmov/" ordinal="__libc_start_main+0xe5"/>
<errormail:StackInfo pos="65" ip="0x8048d41" rel="0xd41" name="soffice.bin" path="/opt/openoffice.org3/program/" ordinal="__gxx_personality_v0+0x31"/>
</errormail:Stack>
<errormail:Checksums type="MD5">
<errormail:Checksum sum="0x5C505D5D95D60EB1AFDC48E83FDE59C7" bytes="1793952" file="libuno_sal.so.3"/>
<errormail:Checksum sum="0x5C505D5D95D60EB1AFDC48E83FDE59C7" bytes="1793952" file="libuno_sal.so.3"/>
<errormail:Checksum sum="0x6BECF70B7D244D7FF5A7D7E42BA04202" bytes="1442180" file="libc.so.6"/>
<errormail:Checksum sum="0xDC1A871C3322BC07916DE8345FC094D7" bytes="846672" file="libstdc++.so.6"/>
<errormail:Checksum sum="0xDC1A871C3322BC07916DE8345FC094D7" bytes="846672" file="libstdc++.so.6"/>
<errormail:Checksum sum="0xDC1A871C3322BC07916DE8345FC094D7" bytes="846672" file="libstdc++.so.6"/>
<errormail:Checksum sum="0xDC1A871C3322BC07916DE8345FC094D7" bytes="846672" file="libstdc++.so.6"/>
<errormail:Checksum sum="0x3642EBBD616CB59B6399EC83C6BAE3E8" bytes="548256" file="deploymentli.uno.so"/>
<errormail:Checksum sum="0x3642EBBD616CB59B6399EC83C6BAE3E8" bytes="548256" file="deploymentli.uno.so"/>
<errormail:Checksum sum="0xB4688A47821AF3234F24510CD86ED1D8" bytes="1354988" file="libsbli.so"/>
<errormail:Checksum sum="0xB4688A47821AF3234F24510CD86ED1D8" bytes="1354988" file="libsbli.so"/>
<errormail:Checksum sum="0xB4688A47821AF3234F24510CD86ED1D8" bytes="1354988" file="libsbli.so"/>
<errormail:Checksum sum="0xB4688A47821AF3234F24510CD86ED1D8" bytes="1354988" file="libsbli.so"/>
<errormail:Checksum sum="0xB4688A47821AF3234F24510CD86ED1D8" bytes="1354988" file="libsbli.so"/>
<errormail:Checksum sum="0xB4688A47821AF3234F24510CD86ED1D8" bytes="1354988" file="libsbli.so"/>
<errormail:Checksum sum="0xB4688A47821AF3234F24510CD86ED1D8" bytes="1354988" file="libsbli.so"/>
<errormail:Checksum sum="0xB4688A47821AF3234F24510CD86ED1D8" bytes="1354988" file="libsbli.so"/>
<errormail:Checksum sum="0xB4688A47821AF3234F24510CD86ED1D8" bytes="1354988" file="libsbli.so"/>
<errormail:Checksum sum="0xBF4AAB2751B36446699287EDAACDD2A8" bytes="3786540" file="libsfxli.so"/>
<errormail:Checksum sum="0xBF4AAB2751B36446699287EDAACDD2A8" bytes="3786540" file="libsfxli.so"/>
<errormail:Checksum sum="0xBF4AAB2751B36446699287EDAACDD2A8" bytes="3786540" file="libsfxli.so"/>
<errormail:Checksum sum="0xBF4AAB2751B36446699287EDAACDD2A8" bytes="3786540" file="libsfxli.so"/>
<errormail:Checksum sum="0xBF4AAB2751B36446699287EDAACDD2A8" bytes="3786540" file="libsfxli.so"/>
<errormail:Checksum sum="0xBF4AAB2751B36446699287EDAACDD2A8" bytes="3786540" file="libsfxli.so"/>
<errormail:Checksum sum="0xBF4AAB2751B36446699287EDAACDD2A8" bytes="3786540" file="libsfxli.so"/>
<errormail:Checksum sum="0x5A16C4F9036AB15B37E272511BC72B96" bytes="9920396" file="libswli.so"/>
<errormail:Checksum sum="0xBF4AAB2751B36446699287EDAACDD2A8" bytes="3786540" file="libsfxli.so"/>
<errormail:Checksum sum="0xBF4AAB2751B36446699287EDAACDD2A8" bytes="3786540" file="libsfxli.so"/>
<errormail:Checksum sum="0xBF4AAB2751B36446699287EDAACDD2A8" bytes="3786540" file="libsfxli.so"/>
<errormail:Checksum sum="0xBF4AAB2751B36446699287EDAACDD2A8" bytes="3786540" file="libsfxli.so"/>
<errormail:Checksum sum="0xBF4AAB2751B36446699287EDAACDD2A8" bytes="3786540" file="libsfxli.so"/>
<errormail:Checksum sum="0xBF4AAB2751B36446699287EDAACDD2A8" bytes="3786540" file="libsfxli.so"/>
<errormail:Checksum sum="0xBF4AAB2751B36446699287EDAACDD2A8" bytes="3786540" file="libsfxli.so"/>
<errormail:Checksum sum="0xBF4AAB2751B36446699287EDAACDD2A8" bytes="3786540" file="libsfxli.so"/>
<errormail:Checksum sum="0xBF4AAB2751B36446699287EDAACDD2A8" bytes="3786540" file="libsfxli.so"/>
<errormail:Checksum sum="0x561F24F12E6845A030488EA9EDFAEFB5" bytes="2927648" file="libfwkli.so"/>
<errormail:Checksum sum="0x561F24F12E6845A030488EA9EDFAEFB5" bytes="2927648" file="libfwkli.so"/>
<errormail:Checksum sum="0x561F24F12E6845A030488EA9EDFAEFB5" bytes="2927648" file="libfwkli.so"/>
<errormail:Checksum sum="0x561F24F12E6845A030488EA9EDFAEFB5" bytes="2927648" file="libfwkli.so"/>
<errormail:Checksum sum="0x9F31BAE146E4D9079C0C1C4DA9541732" bytes="1203708" file="libcomphelp4gcc3.so"/>
<errormail:Checksum sum="0xF18C054EB8DFC01E3A4B04C96F31CB2D" bytes="400384" file="libsofficeapp.so"/>
<errormail:Checksum sum="0xF18C054EB8DFC01E3A4B04C96F31CB2D" bytes="400384" file="libsofficeapp.so"/>
<errormail:Checksum sum="0xF18C054EB8DFC01E3A4B04C96F31CB2D" bytes="400384" file="libsofficeapp.so"/>
<errormail:Checksum sum="0xF18C054EB8DFC01E3A4B04C96F31CB2D" bytes="400384" file="libsofficeapp.so"/>
<errormail:Checksum sum="0xF18C054EB8DFC01E3A4B04C96F31CB2D" bytes="400384" file="libsofficeapp.so"/>
<errormail:Checksum sum="0xF18C054EB8DFC01E3A4B04C96F31CB2D" bytes="400384" file="libsofficeapp.so"/>
<errormail:Checksum sum="0x5B3E295EB81C8C0FF2D521E62588B052" bytes="3527116" file="libvclli.so"/>
<errormail:Checksum sum="0xB2BB757E6442D76EC970A56614DDA06D" bytes="500748" file="libvclplug_genli.so"/>
<errormail:Checksum sum="0x363ACC17772BA3E582231603EAAA32D7" bytes="310956" file="libvclplug_gtkli.so"/>
<errormail:Checksum sum="0x363ACC17772BA3E582231603EAAA32D7" bytes="310956" file="libvclplug_gtkli.so"/>
<errormail:Checksum sum="0x6D7033FDC22A6AB921B1288E371903C7" bytes="747948" file="libglib-2.0.so.0"/>
<errormail:Checksum sum="0x6D7033FDC22A6AB921B1288E371903C7" bytes="747948" file="libglib-2.0.so.0"/>
<errormail:Checksum sum="0x6D7033FDC22A6AB921B1288E371903C7" bytes="747948" file="libglib-2.0.so.0"/>
<errormail:Checksum sum="0x6D7033FDC22A6AB921B1288E371903C7" bytes="747948" file="libglib-2.0.so.0"/>
<errormail:Checksum sum="0x363ACC17772BA3E582231603EAAA32D7" bytes="310956" file="libvclplug_gtkli.so"/>
<errormail:Checksum sum="0xB2BB757E6442D76EC970A56614DDA06D" bytes="500748" file="libvclplug_genli.so"/>
<errormail:Checksum sum="0x5B3E295EB81C8C0FF2D521E62588B052" bytes="3527116" file="libvclli.so"/>
<errormail:Checksum sum="0x5B3E295EB81C8C0FF2D521E62588B052" bytes="3527116" file="libvclli.so"/>
<errormail:Checksum sum="0xF18C054EB8DFC01E3A4B04C96F31CB2D" bytes="400384" file="libsofficeapp.so"/>
<errormail:Checksum sum="0x5B3E295EB81C8C0FF2D521E62588B052" bytes="3527116" file="libvclli.so"/>
<errormail:Checksum sum="0x5B3E295EB81C8C0FF2D521E62588B052" bytes="3527116" file="libvclli.so"/>
<errormail:Checksum sum="0xF18C054EB8DFC01E3A4B04C96F31CB2D" bytes="400384" file="libsofficeapp.so"/>
<errormail:Checksum sum="0xA859C3086015510068BF381239B98EE0" bytes="7472" file="soffice.bin"/>
<errormail:Checksum sum="0x6BECF70B7D244D7FF5A7D7E42BA04202" bytes="1442180" file="libc.so.6"/>
<errormail:Checksum sum="0xA859C3086015510068BF381239B98EE0" bytes="7472" file="soffice.bin"/>
</errormail:Checksums>
</errormail:errormail>

```

---

### Post by stinger30au on 2009-09-02
> **vckeating said:**
> I'm having exactly the same problem.  It installs fine, but you can't open a document without that error occurring.  Any ideas out there?

uninstall it, and install it from the repos like someone said on the first page

the repos are at launchpad

try that and c how u go

---

### Post by Hagar Delest on 2009-09-03
After having installed the Sun version, try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

Personally, I advise the Sun version, less bugs than the Ubuntu/go-oo.org version. The ppa version has had many troubles last year.

Note that 3.1.1 is worth upgrading, especially if you export documents in containing tables in .doc format (even if that format should never been used but that's another story).

---

### Post by zmdmw52 on 2009-09-20
> **Ian Ferguson said:**
> I've tried installing OpenOffice 3.1.1 using the method described in this link:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

The installation seemed to go fine, and I've got all the new OOo3-style icons in my Applications>Office menu, but when I try to open any Open Office application it crashes, and I get this:

[ATTACH]126944[/ATTACH]

Has anyone successfully installed 3.1.1 yet?

[FONT=Arial]Have just upgraded to OpenOffice 3.1.1 in Ubuntu 9.04 [by enabling the extra software repo's in Ubuntu Tweak: (Applications > Third-Party Sources)], and was getting crashes on pasting HTML-formatted text from a webpage onto Writer. 
Changing the Java version helped in my case; changed from [/FONT][FONT=Arial][COLOR=Red]                     /usr/lib/jvm/java-6-openjdk/jre[/COLOR][/FONT][FONT=Arial] to[/FONT][FONT=Arial][COLOR=Green]/usr/lib/jvm/java-6-sun-1.6.0.16/jre[/COLOR][/FONT][FONT=Arial]. 
This option is available in Tools - Options - OpenOffice.org - Java (attached pict).[/FONT]

Above maybe worth trying before doing a User reset.

[[IMG]http://thumbnails22.imagebam.com/4944/39882e49439920.gif[/IMG]]("http://www.imagebam.com/image/39882e49439920")

---

### Post by oldefoxx on 2009-09-20
For a couple of years, I did the church Bulletin each week using Word 2000.  Worked pretty good, once you worked out some of the bugs, like creating text boxes for appearances sake.

Tried this with OpenOffice 3.0, and hit a real snag.  Some text is left justified, some right, and some centered in a proper appearing bulletin, but when I tried to set the alignment for just a part of the bulletin, the effect was for everything in the bulletin from top to bottom.  That was not good.  I hoped that an upgrade with OpenOffice would show that this had been addressed.  Right now I am jumping about between too many projects to get right back to it.  Or maybe someone will explain how to get this feature to work right.

---

### Post by geoffree on 2009-11-30
> **balaknair said:**
> The latest version of OOo is 3.1.1, and you can install it via the Launchpad PPA repositories(OOo 3.1.0 for Jaunty at present, will be updated to 3.1.1 soon)
[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)
Just add the repositories and the PGP key to Software Sources and then run update manager.
This way the packages will be updated automatically via the update manager(downloading and installing the debs, the packages won't be updated automatically).

Instructions on how to add repositories and PGP keys are available via a help link on the above page- 'Read about installing'
I want to upgrade to OO 3.1.. Went to Launchpad PPA page. Message there that it is only available by upgrading to 9.1 which I am loath to do.  So?  I tried entering the repos for OO in Karma but it was not available.  Is this simply another of the prissy responses by Ubu to requests that are a little radical?  Gee, maybe.  Same problem when trying to get Totem to work without the (dangerous) codecs.  Give us a break.  And some help?

Geoffrey

---

### Post by geoffree on 2009-11-30
I replied to another post re: upgrade to OO 3.1 or 3.2 but perhaps you could help. I am running Jaunty and was unable to get software sources to accept the PPA line. Suggestion was to upgrade to 9.1. (Stifled laugh).  Can you advise?

Geoffrey

---

### Post by wilee-nilee on 2009-11-30
Here is a OO deb link for 3.1.
[http://download.openoffice.org/other.html](http://download.openoffice.org/other.html)
I haven't used it giver a try and give the down low on it.

---

### Post by balaknair on 2009-11-30
> **geoffree said:**
> I replied to another post re: upgrade to OO 3.1 or 3.2 but perhaps you could help. I am running Jaunty and was unable to get software sources to accept the PPA line. Suggestion was to upgrade to 9.1. (Stifled laugh).  Can you advise?

Geoffrey
Hello Geoffrey

Seems the PPA I mentioned above has changed(as of Oct 30), the 3.1.1 packages having been removed to make way for OOo 3.2(in beta2 at present, RC on December 17 2009, final release in Jan 2010).
The current release Karmic(9.10) already has 3.1.1 by default, so I think that's what the suggestion to upgrade to 9.10 refers to.


Perhaps this will be of help if you want to install OOo 3.1.1 in Jaunty

[https://launchpad.net/~bugbear5/+archive/ooo-jaunty](https://launchpad.net/~bugbear5/+archive/ooo-jaunty)

---

### Post by Hagar Delest on 2009-11-30
Why don't you use the Sun version??? Better than the Ubuntu version IMHO. (See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68), same link as previously in the thread).

---

### Post by balaknair on 2009-11-30
> **Hagar de l'Est said:**
> Why don't you use the Sun version??? Better than the Ubuntu version IMHO. (See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68), same link as previously in the thread).

The problem with the Sun version is mainly that it doesn't offer a repository. Any security patches or bugfixes won't get installed automatically and one would have to manually download and install those. A bit of a hassle compared to Update Manager.

And as for the Sun version being better(Ubuntu uses GOOo, a modded version of OOo), well, that depends- the Sun version IMHO doesn't integrate that well with the Ubuntu desktop(even with the Desktop Integration deb included in the downloaded tar.gz), and tends to look terribly out of place. Besides, you have to remove all traces of the Ubuntu OOo before you can install Sun's OOo(which could also lead to dependency issues for other apps), or you end with a nigh unusable mess. Add to that Java Runtime hassles. I hope these issues have been fixed in the latest packages from Sun. With a repository, Synaptic can handle most of the dirty work for you. 
But then that's just *my* opinion :D YMMV.

---

### Post by Hagar Delest on 2009-11-30
It's true that in the past, OOo was linked to the ubuntu-desktop meta package but that's no longer the case now.

For the integration in Ubuntu, never had any issue (with xubuntu), using the Galaxy theme. Have never had any issue neither with JRE, it uses the one installed in the distro.

For the security updates, the new versions are usually not backported in the Ubuntu reps IIRC. Except major issues perhaps. And if you want to upgrade just OOo, it means that you can't you've to upgrade the whole distro.

But that's just my opinion too :lol:

---

### Post by balaknair on 2009-12-01
@Hagar:
Good to know that, maybe they've fixed some of these problems(which I went through when I installed OOo 3.0 in Intrepid). 
As for security updates, new versions may not be backported in the ubuntu main repos, but I believe patches are applied to fix security vulnerabilities, especially on the LTS versions.

Since I almost invariably upgrade to the latest Ubuntu edition by the time it hits late alphas or beta(I almost always prefer to do a clean install as well, leaving just the /home partition behind), I usually get the latest stable version of OOo anyway ;D

What I'd really like is for Sun to release an OOo PPA(either on their own servers or on Launchpad) for OOo, like Virtualbox has or Google or like the OOo-Scribblers or Banshee PPA perhaps.

---

### Post by oldefoxx on 2009-12-21
> **scouser73 said:**
> Hi Ian, I've installed the updated OpenOffice 3.1.1, please follow my instructions.

Firstly, go to the OpenOffice website: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and download the **Linux .deb** file.

Once you have done that, extract the .deb file, **OOo_3.1.1_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called [B]OOO310_m19_native_packed-1_en-US.9420
[/B]
You can remove the existing version of OpenOffice if you wish with this command: **sudo apt-get remove openoffice*.***

Copy and paste **OOO310_m19_native_packed-1_en-US.9420** onto the desktop then open Terminal and paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/*.deb**

Then paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9420_all.deb**

Once you've done that you'll find OpenOffice 3.1.1 in Office.

Well, whaddia know.  This actually worked for me on Ubuntu 9.04.  Other methods suggested only took me back to OpenOffice 3.0, and from what I read, somebody had decided that 9.04 stopped at 3.0.  This seemed confirmed with the other methods got OpenOffice 3.1.1 on to Ubuntu 9.10.  But actually, this download is for Linux 32-bit DEB, and that does include my PC and operating system.  That's great!

Ahhh, I messed up badly.  I installed OpenOffice 3.1.1 without first checking for JRE, and when I tried to use the Writer, it told me I had to install the Java Runtime Environment.  So I tried that using Sun's, but did not find the online instructions on how to install it.  The install process presents you with a License Statement, and it just says <OK> at the bottom.  What you have to do is press the space bar to go through the second page of that License thing next.  You don't do that, dpkg hangs, and though you are told how to clear that condition (dpkg --configure -a), it keeps hanging.  I could not find a way to get around that, and eventually ended up trashing my whole install, except for the user files.  Of course you can reinstall and recover those files, but I took more care in trying to find out what I must have done wrong.  That is one of the things I really like about Ubuntu, which has it all over Windows in this regard.  The hangup of dpkg effected both apt-get and the Synaptic Package Manager as well, so none of them worked.


Don't you really hate it when something bad happens, you research it against the next time, you find a related article which gives you a way to deal with it, you tell others to avoid your mistake, you then go forward with what you were told, but then it doesn't work for you and you are back in the same pickle again?  That's my experience with installing the Java Runtime Environment using apt-get install jre*.
I got to the point of the License Statement again, and the space key did nothing for me.  Nor the tab key, the esc key, the enter key, and nothing else worked either.

I could not just quit at that point, because it would have left dpkg in knots again.  The last time. I ended up having to pretty much wipe the partition and reinstalling Ubuntu on it.  I began by scrolling up and down the document, could not find anything in it to help, enlarged the windows, still no help, and randomly striking keys on the left side of the keyboad.  Finally, one or more of those keys worked, and I got to the second page, agreed to the terms, and I had jre installed.
That's all I can tell you.  Just don't close that window, because then you will really be in a mess.

I did not completely clean the partiton.  I had to run fscmk -t ext3 -a /dev/sda5 in order to fix any errors on it, then I mounted it witm mount -t ext3 /dev/sda5 /media/U910, because this is my Ubuntu 9.10 partition.  A dir /media/U910 showed all the folders still on partition, and what I first did was make note of two of significance at this point.  Lost&found is one I can leave alone, and home, which is where everything related to my users should be found.  All the others can safely be deleted, and need to be before you try another reinstall.  If not, somewhere in there is something that will make the partition appear unclean and the reinstall will fail.  You can even boot up the LiveCD in order to be doing all this.  You will also need to get administrator rights by entering this command first: sudo -s in a terminal window.  From the LiveCD, you don't even have to enter a password.


Of course for the mount command to work, there has to be a /media/U910 set up, which superuser can create with mkdir /media/U910.  I use U910 to signify that this is my Ubuntu 9.10 partition.  You can use a different folder name if you want.
Now some of the directories you see are going to be bin, boot, dev, home, all the way up to usr and var.  You begin with the following command:

rm -R /media/U910/bin

and that will get rid of the bin folder and all its contents.
 
You repeat  then for all the remaining folders EXCEPT home and lost&found.  That will leave your user accounts intact with their data.  That is one really great thing about Linux in general, is that the user accounts are set apart like that.

Done right, you will see a stream of commands like this as you proceed along:

rm -R /media/U910/bin
rm -R /media/U910/boot
rm -R /media/U910/cdrom0
rm -R /media.U910//debootstuff
rm -R /media/U910/dev
rm -R /nedia/U910/etc

The commands are so similar that you can use the up arrow to roll back to the previous one used and just delete back to the last / and type the next folder name.
Remember, you want to skip over home and losrfound.

For your install, you will have to use the manual partition method, which is the last choice listed.  You only have to designate the same partition(s) and file systems that were used previously, and you do not want to do a format or reformat, because that would overwrite everything. including the home folder and all user accounts and data.  Remember, we wanted a way that would allow us to keep those.

Certain changes in VirtualBox have meant that its critical information, including the VDI files, are stored in the user accounts.  Reinstall Ubuntu, Put VirtualBox back, and it should all fit into place again.

---

### Post by oldefoxx on 2009-12-29
I attempted the method given in Softpedia for putting Open Office 3.1.1 onto Ubuntu 9.04, after first removing OpenOffice 3.0 and adding back jre as described previously.  I got stuck with the License Statement towards the end of jre again, but using the keyboard more selectively, I finally realised that it was the Tab key that allowed me to move on, not the space key as advised elsewhere.

But after using its methods, I found I was back to OpenOffice 3.0, not 3.1.  So I just used apt-get remove OpenOffice,* again, and will now attempt the procedure given on this thread previously that did work, but lacked Java as required.  So I am about to take those steps again.

---

### Post by oldefoxx on 2009-12-31
Well, let's see what I have accomplished to date.  I remove OOo 3.0, install jre, follow two sets of instructions to try and install OOo 3.1.1, and either end up with OOo 3.0 again, which works, or end up with OOo 3.1, but it doesn't work.  I'm not gaining any ground here, and I've other things to attend to.  If you can do better, spell it out in clearer detail so that others can try to match your success.  Since I can't duplicate either result claimed, I have to conclude that some significant detail is missing.

---

### Post by fabianofcarlos on 2011-04-27
I successfully went from OOo 3.2.1 (default to Ubuntu 10.10) to version 3.3.0 following the instructions I found on this post and the other thread it refers to.
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=38224#p186602](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=38224#p186602)

Didn't took me more than 15 minutes to get it all set up and running fine.
Hope it works for other newbies like myself.

Cheers! :D

---

### Post by Objekt on 2011-05-11
Very nice!  I just followed the same steps specified above.  No problems at all, I didn't even have to reset my user profile.

Except for one thing: I'm using 3.3.0, not 3.3.1.  I can't find anywhere to download 3.3.1.  What's the deal?

---

### Post by Hagar Delest on 2011-05-11
Latest version is 3.3.0.

---

### Post by Objekt on 2011-05-11
Is what I thought, not sure where anyone got the idea of a version 3.3.1.

There may be one later, of course.

Libre Office is up to version 3.3.2 but I have no idea how it compares to OpenOffice.

---

### Post by Hagar Delest on 2011-05-11
3.3.0 was quite the same code for both (with some additions for LibO however). Now that the LibO releases seem to be more frequent, it will become more and more difficult to tell what is common.

---

### Post by Objekt on 2011-05-11
It looks like OO 3.3.0 has fixed a major problem I had in OO 3.2.1, where the Calc application would basically freeze up whenever I selected more than a few cells containing data.  This made cutting & pasting large amounts of data very frustrating.

---

