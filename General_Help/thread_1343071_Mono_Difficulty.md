---
title: "Mono Difficulty"
date: 2009-12-01
forum: General Help
---

### Post by j25451212 on 2009-12-01
Hello,

     I am migrating to Ubuntu completely from Windows and OS X. I have everything I need working except yWriter5, a free novel writing program written in VB8. I am trying to follow the steps here: [http://www.spacejock.com/yWriter5_Linux.html#InstallingMono](http://www.spacejock.com/yWriter5_Linux.html#InstallingMono), but I still cannot get it to work. I've narrowed it down to one of two problems.
1) When I try to run ./configure on the directory home/myname/mono-basic-2.4, I get the following message.
"mono-basic 2.4 module configure to use prefix=/usr/local"
When I try to run ./configure --prefix=/usr/local, I just get the same message.
2) When I try to run mono yWriter5.exe, I get the following error message:
"** (yWriter5.exe:10920): WARNING **: The following assembly referenced from /home/bedell/yWriter5/bin/yWriter5.exe could not be loaded:
     Assembly:   Microsoft.VisualBasic    (assemblyref_index=1)
     Version:    8.0.0.0
     Public Key: b03f5f7f11d50a3a
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/bedell/yWriter5/bin/).


** (yWriter5.exe:10920): WARNING **: Could not load file or assembly 'Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.
The entry point method could not be loaded"

I am trying to convert my entire school and all the libraries in the district to use strictly open-source software whenever possible. I do not want to run a VirtualBox containing one program, both because it is not open-source and it would use up most of my available RAM. I would greatly appreciate any help.

---

### Post by gradinaruvasile on 2009-12-01
First of all, Ubuntu has mono in the repositories and i think thr runtimes are installed by default.
Ubuntu Karmic has Mono in the repositories version, 2.4.2.

In a terminal:

sudo apt-get install mono

to install Mono.

---

### Post by j25451212 on 2009-12-01
I think that I already have mono installed, but when I try to type sudo apt-get install mono in terminal, I get the following error:
Package mono is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mono has no installation candidate

---

### Post by gradinaruvasile on 2009-12-01
Oh yes, mono is installed by default. I just tried it. Unfortunately i have the same error.

---

### Post by j25451212 on 2009-12-01
Thanks anyway. I appreciate it.

---

### Post by gradinaruvasile on 2009-12-01
Ok, i found the solution.

sudo apt-get install libmono-microsoft-visualbasic8.0-cil

It works for me.

Edit:

I have Ubuntu 9.10 installed.

---

### Post by j25451212 on 2009-12-01
That's exactly what I need. I got this message when I ru that command.
root@bedell-laptop:/home/bedell# sudo apt-get install libmono-microsoft-visualbasic8.0-cil
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libmono-microsoft-visualbasic8.0-cil is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

I still get this frustrating error when I try to run the program in mono:
root@bedell-laptop:/home/bedell/yWriter5/bin# mono yWriter5.exe

** (yWriter5.exe:11669): WARNING **: The following assembly referenced from /home/bedell/yWriter5/bin/yWriter5.exe could not be loaded:
     Assembly:   Microsoft.VisualBasic    (assemblyref_index=1)
     Version:    8.0.0.0
     Public Key: b03f5f7f11d50a3a
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/bedell/yWriter5/bin/).


** (yWriter5.exe:11669): WARNING **: Could not load file or assembly 'Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.
The entry point method could not be loaded
root@bedell-laptop:/home/bedell/yWriter5/bin#

---

### Post by gradinaruvasile on 2009-12-01
First of all...

Run the program as a normal user.

If doesnt work go further.

Hmm... It works for me.
Did you installed mono fron sources as explained on the site? Because that probably overwrites stuff.

Anyways, in my case these packages were installed:

The following NEW packages will be installed:
  libgdiplus libgluezilla libmono-accessibility2.0-cil libmono-data-tds2.0-cil
  libmono-microsoft-visualbasic8.0-cil libmono-posix2.0-cil
  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil
  libmono-system-web2.0-cil libmono-webbrowser0.5-cil libmono-winforms2.0-cil
  libmono2.0-cil libsqlite0
0 upgraded, 14 newly installed, 0 to remove and 0 not upgraded.

Check in synaptic if you have them all installed.

Remove the libmono package:

sudo apt-get purge libmono-microsoft-visualbasic8.0-cil

then remove the remaining dependencies:

sudo apt-get autoremove --purge

then reinstall the package:

sudo apt-get install libmono-microsoft-visualbasic8.0-cil

Hope it helps...

PS I made the above screenshot on my computer to show that it really works...

---

### Post by j25451212 on 2009-12-01
I am very confused now. On my computer, I did follow the guides on the website, but I double-check in synaptic and all of the packages that you listed are installed. I even reinstalled all of them, the purged and reinstalled the other file. I keep getting the same error when I try to launch yWriter in terminal and nothing happens when I click on the .exe and click launch in mono.
I also tried this on a clean install of Ubuntu and am getting the exact same error, which seems odd to me, but I still am fairly new to Ubuntu. Thank you for your patience.

---

### Post by gradinaruvasile on 2009-12-01
[COLOR="Red"]root[/COLOR]@bedell-laptop means that you are logged in as root (administrator) user. Thats not good if you want to run normal programs. Never log in as root if you are beginner, run the programs that need administrative rights with "sudo" prefix from normal user.

At the command prompt where you are logged in as root type:

logout

and press enter.

then go to the /home/bedell/yWriter5/bin/ folder and launch yWriter:

cd /home/bedell/yWriter5/bin/

mono yWriter.exe

That should work.

---

### Post by j25451212 on 2009-12-01
I still get the same error even when I am not using root.
[U]
bedell@bedell-laptop[/U]:~/yWriter5/bin$ mono yWriter5.exe

** (yWriter5.exe:2392): WARNING **: The following assembly referenced from /home/bedell/yWriter5/bin/yWriter5.exe could not be loaded:
     Assembly:   Microsoft.VisualBasic    (assemblyref_index=1)
     Version:    8.0.0.0
     Public Key: b03f5f7f11d50a3a
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/bedell/yWriter5/bin/).


** (yWriter5.exe:2392): WARNING **: Could not load file or assembly 'Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.

---

### Post by gradinaruvasile on 2009-12-01
Ok. This means there is another problem somewhere.
What does

mono -V 

return (in terminal)?

---

### Post by gradinaruvasile on 2009-12-01
And

locate b03f5f7f11d50a3a

in a terminal?

---

### Post by gradinaruvasile on 2009-12-01
I have:

```
$ locate b03f5f7f11d50a3a
/usr/lib/mono/gac/CustomMarshalers/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/CustomMarshalers/2.0.0.0__b03f5f7f11d50a3a/CustomMarshalers.dll
/usr/lib/mono/gac/System.Configuration/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/System.Configuration/2.0.0.0__b03f5f7f11d50a3a/System.Configuration.dll
/usr/lib/mono/gac/System.Configuration.Install/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/System.Configuration.Install/2.0.0.0__b03f5f7f11d50a3a/System.Configuration.Install.dll
/usr/lib/mono/gac/System.Drawing/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/System.Drawing/2.0.0.0__b03f5f7f11d50a3a/System.Drawing.dll
/usr/lib/mono/gac/System.Drawing/2.0.0.0__b03f5f7f11d50a3a/System.Drawing.dll.config
/usr/lib/mono/gac/System.EnterpriseServices/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/System.EnterpriseServices/2.0.0.0__b03f5f7f11d50a3a/System.EnterpriseServices.dll
/usr/lib/mono/gac/System.Management/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/System.Management/2.0.0.0__b03f5f7f11d50a3a/System.Management.dll
/usr/lib/mono/gac/System.Security/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/System.Security/2.0.0.0__b03f5f7f11d50a3a/System.Security.dll
/usr/lib/mono/gac/System.ServiceProcess/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/System.ServiceProcess/2.0.0.0__b03f5f7f11d50a3a/System.ServiceProcess.dll
```

And:

```
$ mono -V
Mono JIT compiler version 2.4.2.3 (Debian 2.4.2.3+dfsg-2)
Copyright (C) 2002-2008 Novell, Inc and Contributors. www.mono-project.com
	TLS:           __thread
	GC:            Included Boehm (with typed GC)
	SIGSEGV:       altstack
	Notifications: epoll
	Architecture:  x86
	Disabled:      none

```

---

### Post by j25451212 on 2009-12-01
bedell@bedell-laptop:~$ mono -V
Mono JIT compiler version 2.4 (tarball Tue Dec  1 11:19:03 CST 2009)
Copyright (C) 2002-2008 Novell, Inc and Contributors. [www.mono-project.com](www.mono-project.com)
    TLS:           __thread
    GC:            Included Boehm (with typed GC)
    SIGSEGV:       altstack
    Notifications: epoll
    Architecture:  x86
    Disabled:      none

and (I think mine is longer than yours because I also installed Windows Mono on 1 machine under Wine thinking I might be able to run yWriter through mono through wine.)

/home/bedell/.wine/drive_c/windows/assembly/GAC_32/System.EnterpriseServices/2.0.0.0__b03f5f7f11d50a3a
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/Accessibility/2.0.0.0__b03f5f7f11d50a3a
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/Accessibility/2.0.0.0__b03f5f7f11d50a3a/Accessibility.dll
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/AspNetMMCExt/2.0.0.0__b03f5f7f11d50a3a
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/AspNetMMCExt/2.0.0.0__b03f5f7f11d50a3a/AspNetMMCExt.dll
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/Microsoft.Build.Engine/2.0.0.0__b03f5f7f11d50a3a
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/Microsoft.Build.Engine/2.0.0.0__b03f5f7f11d50a3a/Microsoft.Build.Engine.dll
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/Microsoft.Build.Framework/2.0.0.0__b03f5f7f11d50a3a
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/Microsoft.Build.Framework/2.0.0.0__b03f5f7f11d50a3a/Microsoft.Build.Framework.dll
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/Microsoft.Build.Tasks/2.0.0.0__b03f5f7f11d50a3a
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/Microsoft.Build.Tasks/2.0.0.0__b03f5f7f11d50a3a/Microsoft.Build.Tasks.dll
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/Microsoft.Build.Utilities/2.0.0.0__b03f5f7f11d50a3a
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/Microsoft.Build.Utilities/2.0.0.0__b03f5f7f11d50a3a/Microsoft.Build.Utilities.dll
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/Microsoft.JScript/8.0.0.0__b03f5f7f11d50a3a
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/Microsoft.JScript/8.0.0.0__b03f5f7f11d50a3a/Microsoft.JScript.dll
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/Microsoft.VisualBasic.Vsa/8.0.0.0__b03f5f7f11d50a3a
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/Microsoft.VisualBasic.Vsa/8.0.0.0__b03f5f7f11d50a3a/Microsoft.VisualBasic.Vsa.dll
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/Microsoft.Vsa/8.0.0.0__b03f5f7f11d50a3a
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/Microsoft.Vsa/8.0.0.0__b03f5f7f11d50a3a/Microsoft.Vsa.dll
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/Microsoft.Vsa.Vb.CodeDOMProcessor/8.0.0.0__b03f5f7f11d50a3a
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/Microsoft.Vsa.Vb.CodeDOMProcessor/8.0.0.0__b03f5f7f11d50a3a/Microsoft.Vsa.Vb.CodeDOMProcessor.dll
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/Microsoft_VsaVb/8.0.0.0__b03f5f7f11d50a3a
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/Microsoft_VsaVb/8.0.0.0__b03f5f7f11d50a3a/Microsoft_VsaVb.dll
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/System.Deployment/2.0.0.0__b03f5f7f11d50a3a
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/System.Deployment/2.0.0.0__b03f5f7f11d50a3a/System.Deployment.dll
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/cscompmgd/8.0.0.0__b03f5f7f11d50a3a
/home/bedell/.wine/drive_c/windows/assembly/GAC_MSIL/cscompmgd/8.0.0.0__b03f5f7f11d50a3a/cscompmgd.dll
/home/bedell/.wine/drive_c/windows/winsxs/x86_System.EnterpriseServices_b03f5f7f11d50a3a_2.0.0.0_x-ww_7d5f3790
/home/bedell/.wine/drive_c/windows/winsxs/manifests/x86_System.EnterpriseServices_b03f5f7f11d50a3a_2.0.0.0_x-ww_7d5f3790.manifest
/home/bedell/.wine/drive_c/windows/winsxs/x86_System.EnterpriseServices_b03f5f7f11d50a3a_2.0.0.0_x-ww_7d5f3790/System.EnterpriseServices.Wrapper.dll
/home/bedell/.wine/drive_c/windows/winsxs/x86_System.EnterpriseServices_b03f5f7f11d50a3a_2.0.0.0_x-ww_7d5f3790/System.EnterpriseServices.dll
/usr/lib/mono/gac/Accessibility/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/Accessibility/2.0.0.0__b03f5f7f11d50a3a/Accessibility.dll
/usr/lib/mono/gac/CustomMarshalers/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/CustomMarshalers/2.0.0.0__b03f5f7f11d50a3a/CustomMarshalers.dll
/usr/lib/mono/gac/Microsoft.VisualBasic/8.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/Microsoft.VisualBasic/8.0.0.0__b03f5f7f11d50a3a/Microsoft.VisualBasic.dll
/usr/lib/mono/gac/System.Configuration/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/System.Configuration/2.0.0.0__b03f5f7f11d50a3a/System.Configuration.dll
/usr/lib/mono/gac/System.Configuration.Install/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/System.Configuration.Install/2.0.0.0__b03f5f7f11d50a3a/System.Configuration.Install.dll
/usr/lib/mono/gac/System.Design/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/System.Design/2.0.0.0__b03f5f7f11d50a3a/System.Design.dll
/usr/lib/mono/gac/System.Drawing/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/System.Drawing/2.0.0.0__b03f5f7f11d50a3a/System.Drawing.dll
/usr/lib/mono/gac/System.Drawing/2.0.0.0__b03f5f7f11d50a3a/System.Drawing.dll.config
/usr/lib/mono/gac/System.Drawing.Design/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/System.Drawing.Design/2.0.0.0__b03f5f7f11d50a3a/System.Drawing.Design.dll
/usr/lib/mono/gac/System.EnterpriseServices/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/System.EnterpriseServices/2.0.0.0__b03f5f7f11d50a3a/System.EnterpriseServices.dll
/usr/lib/mono/gac/System.Management/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/System.Management/2.0.0.0__b03f5f7f11d50a3a/System.Management.dll
/usr/lib/mono/gac/System.Security/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/System.Security/2.0.0.0__b03f5f7f11d50a3a/System.Security.dll
/usr/lib/mono/gac/System.ServiceProcess/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/System.ServiceProcess/2.0.0.0__b03f5f7f11d50a3a/System.ServiceProcess.dll
/usr/lib/mono/gac/System.Web/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/System.Web/2.0.0.0__b03f5f7f11d50a3a/System.Web.dll
/usr/lib/mono/gac/System.Web.Services/2.0.0.0__b03f5f7f11d50a3a
/usr/lib/mono/gac/System.Web.Services/2.0.0.0__b03f5f7f11d50a3a/System.Web.Services.dll
/usr/local/lib/mono/gac/Accessibility/1.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/Accessibility/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/Accessibility/1.0.5000.0__b03f5f7f11d50a3a/Accessibility.dll
/usr/local/lib/mono/gac/Accessibility/1.0.5000.0__b03f5f7f11d50a3a/Accessibility.dll.mdb
/usr/local/lib/mono/gac/Accessibility/2.0.0.0__b03f5f7f11d50a3a/Accessibility.dll
/usr/local/lib/mono/gac/Accessibility/2.0.0.0__b03f5f7f11d50a3a/Accessibility.dll.mdb
/usr/local/lib/mono/gac/CustomMarshalers/1.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/CustomMarshalers/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/CustomMarshalers/1.0.5000.0__b03f5f7f11d50a3a/CustomMarshalers.dll
/usr/local/lib/mono/gac/CustomMarshalers/1.0.5000.0__b03f5f7f11d50a3a/CustomMarshalers.dll.mdb
/usr/local/lib/mono/gac/CustomMarshalers/2.0.0.0__b03f5f7f11d50a3a/CustomMarshalers.dll
/usr/local/lib/mono/gac/CustomMarshalers/2.0.0.0__b03f5f7f11d50a3a/CustomMarshalers.dll.mdb
/usr/local/lib/mono/gac/Microsoft.Build.Engine/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/Microsoft.Build.Engine/2.0.0.0__b03f5f7f11d50a3a/Microsoft.Build.Engine.dll
/usr/local/lib/mono/gac/Microsoft.Build.Engine/2.0.0.0__b03f5f7f11d50a3a/Microsoft.Build.Engine.dll.mdb
/usr/local/lib/mono/gac/Microsoft.Build.Framework/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/Microsoft.Build.Framework/2.0.0.0__b03f5f7f11d50a3a/Microsoft.Build.Framework.dll
/usr/local/lib/mono/gac/Microsoft.Build.Framework/2.0.0.0__b03f5f7f11d50a3a/Microsoft.Build.Framework.dll.mdb
/usr/local/lib/mono/gac/Microsoft.Build.Tasks/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/Microsoft.Build.Tasks/2.0.0.0__b03f5f7f11d50a3a/Microsoft.Build.Tasks.dll
/usr/local/lib/mono/gac/Microsoft.Build.Tasks/2.0.0.0__b03f5f7f11d50a3a/Microsoft.Build.Tasks.dll.mdb
/usr/local/lib/mono/gac/Microsoft.Build.Utilities/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/Microsoft.Build.Utilities/2.0.0.0__b03f5f7f11d50a3a/Microsoft.Build.Utilities.dll
/usr/local/lib/mono/gac/Microsoft.Build.Utilities/2.0.0.0__b03f5f7f11d50a3a/Microsoft.Build.Utilities.dll.mdb
/usr/local/lib/mono/gac/Microsoft.JScript/7.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/Microsoft.JScript/8.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/Microsoft.JScript/7.0.5000.0__b03f5f7f11d50a3a/Microsoft.JScript.dll
/usr/local/lib/mono/gac/Microsoft.JScript/7.0.5000.0__b03f5f7f11d50a3a/Microsoft.JScript.dll.mdb
/usr/local/lib/mono/gac/Microsoft.JScript/8.0.0.0__b03f5f7f11d50a3a/Microsoft.JScript.dll
/usr/local/lib/mono/gac/Microsoft.JScript/8.0.0.0__b03f5f7f11d50a3a/Microsoft.JScript.dll.mdb
/usr/local/lib/mono/gac/Microsoft.VisualC/7.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/Microsoft.VisualC/8.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/Microsoft.VisualC/7.0.5000.0__b03f5f7f11d50a3a/Microsoft.VisualC.dll
/usr/local/lib/mono/gac/Microsoft.VisualC/7.0.5000.0__b03f5f7f11d50a3a/Microsoft.VisualC.dll.mdb
/usr/local/lib/mono/gac/Microsoft.VisualC/8.0.0.0__b03f5f7f11d50a3a/Microsoft.VisualC.dll
/usr/local/lib/mono/gac/Microsoft.VisualC/8.0.0.0__b03f5f7f11d50a3a/Microsoft.VisualC.dll.mdb
/usr/local/lib/mono/gac/Microsoft.Vsa/7.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/Microsoft.Vsa/8.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/Microsoft.Vsa/7.0.5000.0__b03f5f7f11d50a3a/Microsoft.Vsa.dll
/usr/local/lib/mono/gac/Microsoft.Vsa/7.0.5000.0__b03f5f7f11d50a3a/Microsoft.Vsa.dll.mdb
/usr/local/lib/mono/gac/Microsoft.Vsa/8.0.0.0__b03f5f7f11d50a3a/Microsoft.Vsa.dll
/usr/local/lib/mono/gac/Microsoft.Vsa/8.0.0.0__b03f5f7f11d50a3a/Microsoft.Vsa.dll.mdb
/usr/local/lib/mono/gac/Mono.Messaging/1.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/Mono.Messaging/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/Mono.Messaging/1.0.5000.0__b03f5f7f11d50a3a/Mono.Messaging.dll
/usr/local/lib/mono/gac/Mono.Messaging/1.0.5000.0__b03f5f7f11d50a3a/Mono.Messaging.dll.mdb
/usr/local/lib/mono/gac/Mono.Messaging/2.0.0.0__b03f5f7f11d50a3a/Mono.Messaging.dll
/usr/local/lib/mono/gac/Mono.Messaging/2.0.0.0__b03f5f7f11d50a3a/Mono.Messaging.dll.mdb
/usr/local/lib/mono/gac/Mono.Messaging.RabbitMQ/1.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/Mono.Messaging.RabbitMQ/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/Mono.Messaging.RabbitMQ/1.0.5000.0__b03f5f7f11d50a3a/Mono.Messaging.RabbitMQ.dll
/usr/local/lib/mono/gac/Mono.Messaging.RabbitMQ/1.0.5000.0__b03f5f7f11d50a3a/Mono.Messaging.RabbitMQ.dll.mdb
/usr/local/lib/mono/gac/Mono.Messaging.RabbitMQ/2.0.0.0__b03f5f7f11d50a3a/Mono.Messaging.RabbitMQ.dll
/usr/local/lib/mono/gac/Mono.Messaging.RabbitMQ/2.0.0.0__b03f5f7f11d50a3a/Mono.Messaging.RabbitMQ.dll.mdb
/usr/local/lib/mono/gac/RabbitMQ.Client/1.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/RabbitMQ.Client/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/RabbitMQ.Client/1.0.5000.0__b03f5f7f11d50a3a/RabbitMQ.Client.dll
/usr/local/lib/mono/gac/RabbitMQ.Client/1.0.5000.0__b03f5f7f11d50a3a/RabbitMQ.Client.dll.mdb
/usr/local/lib/mono/gac/RabbitMQ.Client/2.0.0.0__b03f5f7f11d50a3a/RabbitMQ.Client.dll
/usr/local/lib/mono/gac/RabbitMQ.Client/2.0.0.0__b03f5f7f11d50a3a/RabbitMQ.Client.dll.mdb
/usr/local/lib/mono/gac/System.Configuration/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Configuration/2.0.0.0__b03f5f7f11d50a3a/System.Configuration.dll
/usr/local/lib/mono/gac/System.Configuration/2.0.0.0__b03f5f7f11d50a3a/System.Configuration.dll.mdb
/usr/local/lib/mono/gac/System.Configuration.Install/1.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Configuration.Install/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Configuration.Install/1.0.5000.0__b03f5f7f11d50a3a/System.Configuration.Install.dll
/usr/local/lib/mono/gac/System.Configuration.Install/1.0.5000.0__b03f5f7f11d50a3a/System.Configuration.Install.dll.mdb
/usr/local/lib/mono/gac/System.Configuration.Install/2.0.0.0__b03f5f7f11d50a3a/System.Configuration.Install.dll
/usr/local/lib/mono/gac/System.Configuration.Install/2.0.0.0__b03f5f7f11d50a3a/System.Configuration.Install.dll.mdb
/usr/local/lib/mono/gac/System.Design/1.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Design/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Design/1.0.5000.0__b03f5f7f11d50a3a/System.Design.dll
/usr/local/lib/mono/gac/System.Design/1.0.5000.0__b03f5f7f11d50a3a/System.Design.dll.mdb
/usr/local/lib/mono/gac/System.Design/2.0.0.0__b03f5f7f11d50a3a/System.Design.dll
/usr/local/lib/mono/gac/System.Design/2.0.0.0__b03f5f7f11d50a3a/System.Design.dll.mdb
/usr/local/lib/mono/gac/System.DirectoryServices/1.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.DirectoryServices/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.DirectoryServices/1.0.5000.0__b03f5f7f11d50a3a/System.DirectoryServices.dll
/usr/local/lib/mono/gac/System.DirectoryServices/1.0.5000.0__b03f5f7f11d50a3a/System.DirectoryServices.dll.mdb
/usr/local/lib/mono/gac/System.DirectoryServices/2.0.0.0__b03f5f7f11d50a3a/System.DirectoryServices.dll
/usr/local/lib/mono/gac/System.DirectoryServices/2.0.0.0__b03f5f7f11d50a3a/System.DirectoryServices.dll.mdb
/usr/local/lib/mono/gac/System.Drawing/1.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Drawing/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Drawing/1.0.5000.0__b03f5f7f11d50a3a/System.Drawing.dll
/usr/local/lib/mono/gac/System.Drawing/1.0.5000.0__b03f5f7f11d50a3a/System.Drawing.dll.mdb
/usr/local/lib/mono/gac/System.Drawing/2.0.0.0__b03f5f7f11d50a3a/System.Drawing.dll
/usr/local/lib/mono/gac/System.Drawing/2.0.0.0__b03f5f7f11d50a3a/System.Drawing.dll.mdb
/usr/local/lib/mono/gac/System.Drawing.Design/1.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Drawing.Design/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Drawing.Design/1.0.5000.0__b03f5f7f11d50a3a/System.Drawing.Design.dll
/usr/local/lib/mono/gac/System.Drawing.Design/1.0.5000.0__b03f5f7f11d50a3a/System.Drawing.Design.dll.mdb
/usr/local/lib/mono/gac/System.Drawing.Design/2.0.0.0__b03f5f7f11d50a3a/System.Drawing.Design.dll
/usr/local/lib/mono/gac/System.Drawing.Design/2.0.0.0__b03f5f7f11d50a3a/System.Drawing.Design.dll.mdb
/usr/local/lib/mono/gac/System.EnterpriseServices/1.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.EnterpriseServices/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.EnterpriseServices/1.0.5000.0__b03f5f7f11d50a3a/System.EnterpriseServices.dll
/usr/local/lib/mono/gac/System.EnterpriseServices/1.0.5000.0__b03f5f7f11d50a3a/System.EnterpriseServices.dll.mdb
/usr/local/lib/mono/gac/System.EnterpriseServices/2.0.0.0__b03f5f7f11d50a3a/System.EnterpriseServices.dll
/usr/local/lib/mono/gac/System.EnterpriseServices/2.0.0.0__b03f5f7f11d50a3a/System.EnterpriseServices.dll.mdb
/usr/local/lib/mono/gac/System.Management/1.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Management/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Management/1.0.5000.0__b03f5f7f11d50a3a/System.Management.dll
/usr/local/lib/mono/gac/System.Management/1.0.5000.0__b03f5f7f11d50a3a/System.Management.dll.mdb
/usr/local/lib/mono/gac/System.Management/2.0.0.0__b03f5f7f11d50a3a/System.Management.dll
/usr/local/lib/mono/gac/System.Management/2.0.0.0__b03f5f7f11d50a3a/System.Management.dll.mdb
/usr/local/lib/mono/gac/System.Messaging/1.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Messaging/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Messaging/1.0.5000.0__b03f5f7f11d50a3a/System.Messaging.dll
/usr/local/lib/mono/gac/System.Messaging/1.0.5000.0__b03f5f7f11d50a3a/System.Messaging.dll.mdb
/usr/local/lib/mono/gac/System.Messaging/2.0.0.0__b03f5f7f11d50a3a/System.Messaging.dll
/usr/local/lib/mono/gac/System.Messaging/2.0.0.0__b03f5f7f11d50a3a/System.Messaging.dll.mdb
/usr/local/lib/mono/gac/System.Runtime.Serialization.Formatters.Soap/1.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Runtime.Serialization.Formatters.Soap/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Runtime.Serialization.Formatters.Soap/1.0.5000.0__b03f5f7f11d50a3a/System.Runtime.Serialization.Formatters.Soap.dll
/usr/local/lib/mono/gac/System.Runtime.Serialization.Formatters.Soap/1.0.5000.0__b03f5f7f11d50a3a/System.Runtime.Serialization.Formatters.Soap.dll.mdb
/usr/local/lib/mono/gac/System.Runtime.Serialization.Formatters.Soap/2.0.0.0__b03f5f7f11d50a3a/System.Runtime.Serialization.Formatters.Soap.dll
/usr/local/lib/mono/gac/System.Runtime.Serialization.Formatters.Soap/2.0.0.0__b03f5f7f11d50a3a/System.Runtime.Serialization.Formatters.Soap.dll.mdb
/usr/local/lib/mono/gac/System.Security/1.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Security/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Security/1.0.5000.0__b03f5f7f11d50a3a/System.Security.dll
/usr/local/lib/mono/gac/System.Security/1.0.5000.0__b03f5f7f11d50a3a/System.Security.dll.mdb
/usr/local/lib/mono/gac/System.Security/2.0.0.0__b03f5f7f11d50a3a/System.Security.dll
/usr/local/lib/mono/gac/System.Security/2.0.0.0__b03f5f7f11d50a3a/System.Security.dll.mdb
/usr/local/lib/mono/gac/System.ServiceProcess/1.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.ServiceProcess/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.ServiceProcess/1.0.5000.0__b03f5f7f11d50a3a/System.ServiceProcess.dll
/usr/local/lib/mono/gac/System.ServiceProcess/1.0.5000.0__b03f5f7f11d50a3a/System.ServiceProcess.dll.mdb
/usr/local/lib/mono/gac/System.ServiceProcess/2.0.0.0__b03f5f7f11d50a3a/System.ServiceProcess.dll
/usr/local/lib/mono/gac/System.ServiceProcess/2.0.0.0__b03f5f7f11d50a3a/System.ServiceProcess.dll.mdb
/usr/local/lib/mono/gac/System.Web/1.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Web/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Web/1.0.5000.0__b03f5f7f11d50a3a/System.Web.dll
/usr/local/lib/mono/gac/System.Web/1.0.5000.0__b03f5f7f11d50a3a/System.Web.dll.mdb
/usr/local/lib/mono/gac/System.Web/2.0.0.0__b03f5f7f11d50a3a/System.Web.dll
/usr/local/lib/mono/gac/System.Web/2.0.0.0__b03f5f7f11d50a3a/System.Web.dll.mdb
/usr/local/lib/mono/gac/System.Web.Services/1.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Web.Services/2.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/System.Web.Services/1.0.5000.0__b03f5f7f11d50a3a/System.Web.Services.dll
/usr/local/lib/mono/gac/System.Web.Services/1.0.5000.0__b03f5f7f11d50a3a/System.Web.Services.dll.mdb
/usr/local/lib/mono/gac/System.Web.Services/2.0.0.0__b03f5f7f11d50a3a/System.Web.Services.dll
/usr/local/lib/mono/gac/System.Web.Services/2.0.0.0__b03f5f7f11d50a3a/System.Web.Services.dll.mdb
/usr/local/lib/mono/gac/cscompmgd/7.0.5000.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/cscompmgd/8.0.0.0__b03f5f7f11d50a3a
/usr/local/lib/mono/gac/cscompmgd/7.0.5000.0__b03f5f7f11d50a3a/cscompmgd.dll
/usr/local/lib/mono/gac/cscompmgd/7.0.5000.0__b03f5f7f11d50a3a/cscompmgd.dll.mdb
/usr/local/lib/mono/gac/cscompmgd/8.0.0.0__b03f5f7f11d50a3a/cscompmgd.dll
/usr/local/lib/mono/gac/cscompmgd/8.0.0.0__b03f5f7f11d50a3a/cscompmgd.dll.mdb

---

### Post by gradinaruvasile on 2009-12-01
Hmm.. U have 2 mono installations: the ubuntu one in /usr/lib/mono and the other one you installed from sources in /usr/local/lib/mono. Probably there is some path or another configuration problem. U should uninstall the mono installed from sources.

Also, the mono executable is launched from the version installed from source.
What does

ls -al /usr/bin/mono

and

ls -al /usr/local/bin/mono

return?


Also, try this:

/usr/bin/mono yWriter.exe

Also, i dont think the wine mono idea is that great. Wine is unstable software.

---

### Post by j25451212 on 2009-12-01
Sorry for the delay. I was commuting home. I will return soon if you are able to check on the thread again tonight or tomorrow. I have to take my daughter for Christmas pictures.
/usr/bin/mono yWriter5.exe almost worked. It brought up the program, but none of the text was displayed. 
[IMG]http://litteacher.com/Screenshot.png[/IMG]

bedell@bedell-laptop:~$ ls -al /usr/bin/mono
-rwxr-xr-x 1 root root 2528612 2009-09-23 10:15 /usr/bin/mono
bedell@bedell-laptop:~$ ls -al /usr/local/bin/mono
-rwxr-xr-x 1 root root 7224794 2009-12-01 11:43 /usr/local/bin/mono

---

### Post by j25451212 on 2009-12-01
> **gradinaruvasile said:**
> Hmm.. U have 2 mono installations: the ubuntu one in /usr/lib/mono and the other one you installed from sources in /usr/local/lib/mono. Probably there is some path or another configuration problem. U should uninstall the mono installed from sources.
How do I do this without deleting the mono that came installed with Ubuntu?

---

### Post by gradinaruvasile on 2009-12-04
Go to the sources folder from where you installed (make etc) the mono from sources. 
In a terminal:

sudo make uninstall 

If you dont have the folder anymore, unpack it again, do the whole installation routine again then uninstall it.
Then try running yWriter. Else you could purge and reinstall those packages we talked before.

---

### Post by pinokkio on 2009-12-11
Hi,

I had the same problem but found out that I had to install:

   mono

and 

   libmono-microsoft-visualbasic8.0-cil

using the synaptic package manager from the menu.
This did the trick for me and I'm a happy yWriter now.

And if you then rightclick the yWriter5.exe and:
- choose: Open with another application
- choose: Use a custom command
- type: mono
then the next time you rightclick the yWriter5.exe icon you can choose:

Open with mono

That made me an even happier yWriter.
:popcorn:

---

