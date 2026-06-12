---
title: "UT2K4 MOD: Killing Floor Issues"
date: 2010-01-30
forum: General Help
---

### Post by OwnLife on 2010-01-30
Hello! I've just recently liberated myself from the clutches of *****soft and am excited to dig in and learn. Huzzah to the open-source community, I never thought it was possible to install an operating system that's self-sufficient and works out of the box(disc). 

Ubuntu 9.04 GNOME
Wine 1.1.31

[http://ubuntuforums.org/showthread.php?t=1159780](http://ubuntuforums.org/showthread.php?t=1159780)

I want to reference this post because of the well played solution, and hopefully with another well played solution they can be together for others. The mouse problem is resolved in my case but I have a new problem that I wouldn't know where to start with. After loading I switch over to the internet tab and no servers populate. When I close the application I get a Critical Error:

 Build UT2004_Build_[2004-11-11_10.48]

OS: Windows XP 5.1 (Build: 2600)
CPU: GenuineIntel PentiumPro-class processor @ 2196 MHz with 2047MB RAM
Video: NVIDIA GeForce 8600 GT (8618)

General protection fault!

History: ResourceList <- UD3D9RenderDevice::Flush <- DeleteRenDev <- UViewport::Destroy <- (WindowsViewport Package.WindowsClient.WindowsViewport) <- UWindowsViewport::Destroy <- UObject::ConditionalDestroy <- (WindowsViewport Package.WindowsClient.WindowsViewport) <- UWindowsClient::Destroy <- UObject::ConditionalDestroy <- (WindowsClient Package.WindowsClient) <- DispatchDestroy <- (15860: WindowsClient Package.WindowsClient Class WinDrv.WindowsClient) <- DispatchDestroys <- UObject::PurgeGarbage <- UObject::StaticExit <- appPreExit <- FMallocWindows::Free <- FMallocWindows::Free

Some of this looks reasonable, but my speculations will get me nowhere.

1 2 3 Go!

EDIT:
Tinkering around I noticed here that Steam is being kind of buggy with the menus and what not. Also, I tried a different app(CS) and it also did not populate a server list. Forgot to mention that Wine was installed from SPM.

---

