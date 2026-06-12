---
title: "Win4Lin enabled kernel not detected"
date: 2005-02-07
forum: General Help
---

### Post by h4n9m4n on 2005-02-07
I have tried compiling my own win4lin kernels, they run, but then, Win4Lin installer doesnt detect them! It just says that i am running a kernel not directly supported with win4lin. I also tried a kernel that i got from sgbeamer, but it was all the same. Is there anyway to force the installer to work? Or get past that message? Do you have to modprobe anything? 
plz help  :-(

---

### Post by h4n9m4n on 2005-02-08
i dont know if this helps or not, but heres my win4lin logfile
```
Feb 08 16:32:19 win4lin-i..ll-main.c:363   

### starting up Win4Lin Installer Version  5.1.7-a1 ###


Feb 08 16:32:19          accessors.c:2072  state mgr: stateMgrStruct.fromMini set to FALSE
Feb 08 16:32:19 win4lin-i..ll-main.c:432   Unsupported locale: 'en_US' - default to 'C'
Feb 08 16:32:19          accessors.c:1424  state mgr: stateMgrStruct.CLAcd set to FALSE
Feb 08 16:32:19          accessors.c:1460  state mgr: stateMgrStruct.CLAdir set to FALSE
Feb 08 16:32:19          accessors.c:1496  state mgr: stateMgrStruct.CLAweb set to FALSE
Feb 08 16:32:19          accessors.c:1532  state mgr: stateMgrStruct.CLAranmyself set to FALSE
Feb 08 16:32:19          accessors.c:1568  state mgr: stateMgrStruct.CLAqa set to FALSE
Feb 08 16:32:19          accessors.c:1604  state mgr: stateMgrStruct.CLAdevel set to FALSE
Feb 08 16:32:19          accessors.c:1964  state mgr: stateMgrStruct.ethernetSupportPresent set to TRUE
Feb 08 16:32:19          accessors.c:524   state mgr: stateMgrStruct.licenseFileExists set to TRUE
Feb 08 16:32:19      check_license.c:140   License code provided is OK(): 2 - No such file or directory
Feb 08 16:32:19          accessors.c:560   state mgr: stateMgrStruct.licenseCodeGood set to TRUE
Feb 08 16:32:19          accessors.c:632   state mgr: stateMgrStruct.licenseRegistered set to TRUE
Feb 08 16:32:19          accessors.c:416   state mgr: stateMgrStruct.installerNewsFound set to FALSE
Feb 08 16:32:19          accessors.c:884   state mgr: stateMgrStruct.productNewsFound set to FALSE
Feb 08 16:32:19             panels.c:1417  cur_installer is /usr/bin/win4lin-install
Feb 08 16:32:20       rpminterface.c:337   rpm -q Win4Lin
Feb 08 16:32:20       rpminterface.c:352   RPM operation failed
Feb 08 16:32:20       rpminterface.c:353   pclose(): 0 - Success
Feb 08 16:32:20          accessors.c:56    state mgr: stateMgrStruct.win4linIsInstalled set to FALSE
Feb 08 16:32:20          accessors.c:92    state mgr: stateMgrStruct.windowsIsInstalled set to FALSE
Feb 08 16:32:20        panel_intro.c:568   The user is running as root.
Feb 08 16:32:20          accessors.c:20    state mgr: stateMgrStruct.runningAsRoot set to TRUE
Feb 08 16:32:20        panel_intro.c:571   the current installer: 
Feb 08 16:32:20        panel_intro.c:572   /usr/bin/win4lin-install
Feb 08 16:32:20        panel_intro.c:709   No Win4Lin installation present.  Preparing to install Win4Lin.
Feb 08 16:32:20          accessors.c:344   state mgr: stateMgrStruct.checkNewInstaller set to FALSE
Feb 08 16:32:20          accessors.c:344   state mgr: stateMgrStruct.checkNewInstaller set to TRUE
Feb 08 16:32:20          accessors.c:344   state mgr: stateMgrStruct.checkNewInstaller set to TRUE
Feb 08 16:32:20          accessors.c:488   state mgr: stateMgrStruct.userAgreedToEULA set to TRUE
Feb 08 16:32:20        panel_intro.c:727   No Win4Lin installation present.  Preparing to install Win4Lin.
Feb 08 16:32:21          accessors.c:344   state mgr: stateMgrStruct.checkNewInstaller set to TRUE
Feb 08 16:32:21          accessors.c:344   state mgr: stateMgrStruct.checkNewInstaller set to FALSE
Feb 08 16:32:22           stateMgr.c:323   State Manager: performing stage 1 package installation.
Feb 08 16:32:22        panel_intro.c:314   reset the current stage to 0 
Feb 08 16:32:22           stateMgr.c:253   stateMgr Error: stateMgrStruct.postinstall_Register was accessed before it was set
Feb 08 16:32:22           stateMgr.c:253   stateMgr Error: stateMgrStruct.removeSelected was accessed before it was set
Feb 08 16:32:22           stateMgr.c:253   stateMgr Error: stateMgrStruct.postinstall_Bump was accessed before it was set
Feb 08 16:32:22           stateMgr.c:253   stateMgr Error: stateMgrStruct.unloadSelected was accessed before it was set
Feb 08 16:32:22           stateMgr.c:253   stateMgr Error: stateMgrStruct.reloadSelected was accessed before it was set
Feb 08 16:32:22           stateMgr.c:253   stateMgr Error: stateMgrStruct.miniSelected was accessed before it was set
Feb 08 16:32:22               util.c:432   The cdrom mount dir is 
Feb 08 16:32:22               util.c:433   /media/cdrom
Feb 08 16:32:22             panels.c:574   try to mount cdrom at 
Feb 08 16:32:22             panels.c:575   /media/cdrom
Feb 08 16:32:22             panels.c:897   try to mount /dev/cdrom at /media/cdrom
Feb 08 16:32:22             panels.c:585   Check if following file (Win4Lin Installer) is exists: 
Feb 08 16:32:22             panels.c:589   /media/cdrom/win4lin-install
Feb 08 16:32:22          accessors.c:164   state mgr: stateMgrStruct.win4linCDIsInDrive set to FALSE
Feb 08 16:32:22               util.c:432   The cdrom mount dir is 
Feb 08 16:32:22               util.c:433   /media/cdrom
Feb 08 16:32:22               util.c:432   The cdrom mount dir is 
Feb 08 16:32:22               util.c:433   /media/cdrom
Feb 08 16:32:22               util.c:490   product_xref file not found
Feb 08 16:32:22               util.c:491   access(): 2 - No such file or directory
Feb 08 16:32:22          accessors.c:920   state mgr: stateMgrStruct.supportedKernel set to FALSE
Feb 08 16:32:22          accessors.c:1064  state mgr: stateMgrStruct.kernelPatch set to FALSE
Feb 08 16:32:22          accessors.c:992   state mgr: stateMgrStruct.kernelSymbolsMatch set to FALSE
Feb 08 16:32:22           stateMgr.c:253   stateMgr Error: stateMgrStruct.gotLocalSystemInfo was accessed before it was set
Feb 08 16:32:22          accessors.c:668   state mgr: stateMgrStruct.checkNewPackages set to TRUE
Feb 08 16:32:22           notebook.c:886   

###Panel change###

setting panel to 9 (PANEL_SYSTEM_ANALYSIS) 
Feb 08 16:32:22           stateMgr.c:253   stateMgr Error: stateMgrStruct.gotRemoteSystemInfo was accessed before it was set
Feb 08 16:32:22             panels.c:1010  running getOnlineXrefAndNews
Feb 08 16:32:22           stateMgr.c:323   State Manager: performing stage 1 package installation.
Feb 08 16:32:22         licenseMgr.c:478   fopen(): 2 - No such file or directory
Feb 08 16:32:22         licenseMgr.c:479   get_name_value_from_file(): unable to open /var/win4lin/install/nvinst-settings
Feb 08 16:32:22               util.c:1043  get_nvinst_setting(): USE_PROXY=???
Feb 08 16:32:22   libinetxfer_http.c:184   using 6 for protocol number
Feb 08 16:32:23 libinetxf.._common.c:258   IXCheckConnect(): connectivity available
Feb 08 16:32:23         licenseMgr.c:478   fopen(): 2 - No such file or directory
Feb 08 16:32:23         licenseMgr.c:479   get_name_value_from_file(): unable to open /var/win4lin/install/nvinst-settings
Feb 08 16:32:23               util.c:1043  get_nvinst_setting(): USE_PROXY=???
Feb 08 16:32:23   libinetxfer_http.c:184   using 6 for protocol number
Feb 08 16:32:24             panels.c:1057  Okay, I got the online xref file
Feb 08 16:32:24    lnx_system_info.c:762   getNewMKIVersion(): bad license level: 053
Feb 08 16:32:24    lnx_system_info.c:789   did not find mki_version_3\|mkia_ver_1 in /proc/ksyms
Feb 08 16:32:24    lnx_system_info.c:804   getSystemInfoMKIMatch: rtn(0)
Feb 08 16:32:24    lnx_system_info.c:189   Try to parsing baseVersion, installerVersion and defaultPkg
Feb 08 16:32:24    lnx_system_info.c:189   Try to parsing baseVersion, installerVersion and defaultPkg
Feb 08 16:32:24    lnx_system_info.c:218   Trying to parse baseMiniVersion, installerMiniVersion, and MKI_version
Feb 08 16:32:24    lnx_system_info.c:219   minimum_installer_version 3 = 6.6
Feb 08 16:32:24    lnx_system_info.c:218   Trying to parse baseMiniVersion, installerMiniVersion, and MKI_version
Feb 08 16:32:24    lnx_system_info.c:219   mki_symbol  [mki_version_3_0_0\|mki_version_3_0_1\|mkia_ver_1_0_6\|mkia_ver_1_0_7\|mkia_ver_1_0_8\|mkia_ver_1_0_10]
Feb 08 16:32:25    lnx_system_info.c:379   procVersionGeneric(): uname -r: 2.6.8.1
Feb 08 16:32:25    lnx_system_info.c:405   procVersionGeneric(): 2.6 kernel, but bad license.
Feb 08 16:32:25    lnx_system_info.c:408   procVersionGeneric(): licenseLevel=053
Feb 08 16:32:25    lnx_system_info.c:615   procVersion saya: <Linux version 2.6.8.1 (root@monarch) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Tue Jan 18 20:15:58 CST 2005
>
Feb 08 16:32:25    lnx_system_info.c:617   after do_kernel_fix, procVersion says: <Linux version 2.6.8.1 (root@monarch) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Tue Jan 18 20:15:58 CST 2005
>
Feb 08 16:32:25    lnx_system_info.c:673   Win4Lin/RPMS/i386/Win4Lin-5.3.25b-d.i386.rpm
Feb 08 16:32:25    lnx_system_info.c:762   getNewMKIVersion(): bad license level: 053
Feb 08 16:32:25    lnx_system_info.c:789   did not find mki_version_3_0_0\|mki_version_3_0_1\|mkia_ver_1_0_6\|mkia_ver_1_0_7\|mkia_ver_1_0_8\|mkia_ver_1_0_10 in /proc/ksyms
Feb 08 16:32:25    lnx_system_info.c:804   getSystemInfoMKIMatch: rtn(0)
Feb 08 16:32:25          accessors.c:236   state mgr: stateMgrStruct.gotRemoteSystemInfo set to TRUE
Feb 08 16:32:25             panels.c:1081  printing remote sys info...
Feb 08 16:32:25    lnx_system_info.c:812   >>> BEGIN logSystemInfo():
distroName((null))
distroVer(0.0)
kernelVer(0.0.0)
smpSupport(0)
baseVersion(3),installerVersion(8.7)
baseMiniVersion(3),installerMiniVersion(6.6)
mkiVersion(mki_version_3_0_0\|mki_version_3_0_1\|mkia_ver_1_0_6\|mkia_ver_1_0_7\|mkia_ver_1_0_8\|mkia_ver_1_0_10)defaultPkg(Win4Lin/RPMS/i386/Win4Lin-5.3.25b-d.i386.rpm)supportLevel(0)
Feb 08 16:32:25    lnx_system_info.c:822   <<< END logSystemInfo()
Feb 08 16:32:25             panels.c:1797  Product version from online product_xref: 4.0.25
Feb 08 16:32:25             panels.c:1812  Installer version from online product_xref: 5.1.4
Feb 08 16:32:25             panels.c:1827  release_notes_link version from online product_xref: http://www.netraverse.com/support/docs/win4lin-30-relnote.html
Feb 08 16:32:25             panels.c:1842  kernel_release_notes_link version from online product_xref: http://www.netraverse.com/support/kernel_release_notes/
Feb 08 16:32:25             panels.c:1857  installer_release_notes_link version from online product_xref: http://www.netraverse.com/support/docs/win4lin_installer_release_notes.html
Feb 08 16:32:25          accessors.c:956   state mgr: stateMgrStruct.supportedKernelOnline set to FALSE
Feb 08 16:32:25          accessors.c:1100  state mgr: stateMgrStruct.kernelPatchOnline set to FALSE
Feb 08 16:32:25          accessors.c:1028  state mgr: stateMgrStruct.kernelSymbolsMatchOnline set to FALSE
Feb 08 16:32:25         licenseMgr.c:478   fopen(): 2 - No such file or directory
Feb 08 16:32:25         licenseMgr.c:479   get_name_value_from_file(): unable to open /var/win4lin/install/nvinst-settings
Feb 08 16:32:25               util.c:1043  get_nvinst_setting(): USE_PROXY=???
Feb 08 16:32:25   libinetxfer_http.c:184   using 6 for protocol number
Feb 08 16:32:25         licenseMgr.c:478   fopen(): 2 - No such file or directory
Feb 08 16:32:25         licenseMgr.c:479   get_name_value_from_file(): unable to open /var/win4lin/install/nvinst-settings
Feb 08 16:32:25               util.c:1043  get_nvinst_setting(): USE_PROXY=???
Feb 08 16:32:25   libinetxfer_http.c:184   using 6 for protocol number
Feb 08 16:32:26    lnx_system_info.c:812   >>> BEGIN logSystemInfo():
distroName((null))
distroVer(0.0)
kernelVer(0.0.0)
smpSupport(0)
baseVersion(3),installerVersion(8.7)
baseMiniVersion(3),installerMiniVersion(6.6)
mkiVersion(mki_version_3_0_0\|mki_version_3_0_1\|mkia_ver_1_0_6\|mkia_ver_1_0_7\|mkia_ver_1_0_8\|mkia_ver_1_0_10)defaultPkg(Win4Lin/RPMS/i386/Win4Lin-5.3.25b-d.i386.rpm)supportLevel(0)
Feb 08 16:32:26    lnx_system_info.c:822   <<< END logSystemInfo()
Feb 08 16:32:26               util.c:944   fopen(): 2 - No such file or directory
Feb 08 16:32:26               util.c:945   unable to open /proc/ksyms
Feb 08 16:32:26           stateMgr.c:253   stateMgr Error: stateMgrStruct.gotLocalSystemInfo was accessed before it was set
Feb 08 16:32:26           stateMgr.c:253   stateMgr Error: stateMgrStruct.genericKernel was accessed before it was set
Feb 08 16:32:26     panel_sys_info.c:435   Unfortunately, your system is not running a kernel directly supported by Win4Lin. Click Help for details.
Feb 08 16:32:26               util.c:944   fopen(): 2 - No such file or directory
Feb 08 16:32:26               util.c:945   unable to open /proc/ksyms
Feb 08 16:32:26     panel_sys_info.c:548   Unfortunately, your system is not running a kernel directly supported by Win4Lin. Click Help for details.
Feb 08 16:32:28           guiutils.c:376   trying to find a help brower: 
Feb 08 16:32:28           guiutils.c:382   trying gnome-help-browser
Feb 08 16:32:28           guiutils.c:395   trying kdehelp
Feb 08 16:32:28           guiutils.c:408   trying konqueror
Feb 08 16:32:28           guiutils.c:421   trying netscape
Feb 08 16:32:28           guiutils.c:434   trying lynx
Feb 08 16:32:28           guiutils.c:78    guiutils.c:335 errorDialog -3333 = 'No help system available!
'
Feb 08 16:32:33           guiutils.c:271   prepare question dialog
Feb 08 16:32:33           guiutils.c:272   Do you really want to quit?
You may restart later.
Feb 08 16:32:34           stateMgr.c:253   stateMgr Error: stateMgrStruct.installedKernelFromOnline was accessed before it was set
Feb 08 16:32:34           stateMgr.c:253   stateMgr Error: stateMgrStruct.installedKernelFromLocal was accessed before it was set
Feb 08 16:32:34           stateMgr.c:253   stateMgr Error: stateMgrStruct.installedWin4linFromOnline was accessed before it was set
Feb 08 16:32:34           stateMgr.c:253   stateMgr Error: stateMgrStruct.installedWin4linFromLocal was accessed before it was set
```

---

