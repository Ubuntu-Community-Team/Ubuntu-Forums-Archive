---
title: "software installation CONFUSION."
date: 2011-06-30
forum: General Help
---

### Post by jfbooth on 2011-06-30
Running Xubuntu 11.04.

Some time ago, I installed TEAMVIEWER 5 on my Xubuntu machine.  This would be the LINUX version.  I can't remember if I got it with Package Manager or directly from the TV website (deb package), but suffice to say it worked great.  No problems at all.  I think I got it from Package Manager.

I ran it today to link up with a remote PC.  It said "The remote machine is running a newer version.  Do you want to upgrade IN ORDER TO CONNECT?"  I said YES.  The only choices were YES or NO.  If No, then it closed.  Apparently 5 will not connect to 6.  It went through an automatic routine and then TV 6 opened.  Great.

Then, to my surprise, my APPLICATIONS list showed ACCESSORIES, GAMES etc as usual but there was a new item ... WINE.  Under WINE is PROGRAMS/TEAMVIEWER 6/TEAMVIEWER 6 (and LICENSE and UNINSTALL TEAMVIEWER 6).

I concluded that I started with TEAMVIEWER 5 for LINUX and ended up with a WINE install and a TEAMVIEWER 6 for WINDOWS.

Hmmm .. OK.  I will just uninstall TV 5 for Linux ...which I did with Package Manager .. Mark for complete removal.  It is gone (?? see below).

Now, for the problems:

Wine/teamviewer 6 is still on the Applications list.  When I click on TV6, LICENSE, or UNINSTALL TV6, nothing happens .. at all (menu closes back to desktop).

I am ASSUMING the upgrade to TV6 (Windows) is somehow dependent on TV5 Linux .. though that does not seem sensible to me.

I can find no way to uninstall WINE or TV6 for Windows.  A terminal command of wine uninstall gives (implying WINE is not installed):

jb@john-xubuntu:~/Desktop$ wine uninstall
The program 'wine' can be found in the following packages:
 * wine1.2
 * wine1.3
 * wine1.0
Try: sudo apt-get install <selected package>
jb@john-xubuntu:~/Desktop

It occurred to me to reinstall TV5 but is is (now) not to be found by Package Manager .. of any version.  No TV in Package Manager.

So .. I tried to find installations of Wine, and Teamviewer of any kind in terminal.

Locate teamviwer:

jb@john-xubuntu:~/Desktop$ locate teamviewer
/home/jb/.teamviewer
/home/jb/.teamviewer/5
/home/jb/.teamviewer/5/.update-timestamp
/home/jb/.teamviewer/5/dosdevices
/home/jb/.teamviewer/5/drive_c
/home/jb/.teamviewer/5/fs_rgb.reg
/home/jb/.teamviewer/5/system.reg
/home/jb/.teamviewer/5/user.reg
/home/jb/.teamviewer/5/userdef.reg
/home/jb/.teamviewer/5/winelog
/home/jb/.teamviewer/5/dosdevices/c:
/home/jb/.teamviewer/5/dosdevices/z:
/home/jb/.teamviewer/5/drive_c/Program Files
/home/jb/.teamviewer/5/drive_c/users
/home/jb/.teamviewer/5/drive_c/windows
/home/jb/.teamviewer/5/drive_c/Program Files/Common Files
/home/jb/.teamviewer/5/drive_c/Program Files/Internet Explorer
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer
/home/jb/.teamviewer/5/drive_c/Program Files/Internet Explorer/iexplore.exe
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer.exe
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_ar.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_cs.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_da.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_de.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_en.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_es.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_fi.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_fr.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_it.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_ja.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_ko.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_nl.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_no.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_pl.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_pt.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_ru.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_sv.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_tr.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/tvwine.dll.so
/home/jb/.teamviewer/5/drive_c/users/Public
/home/jb/.teamviewer/5/drive_c/users/jb
/home/jb/.teamviewer/5/drive_c/users/Public/Application Data
/home/jb/.teamviewer/5/drive_c/users/Public/Desktop
/home/jb/.teamviewer/5/drive_c/users/Public/Documents
/home/jb/.teamviewer/5/drive_c/users/Public/Favorites
/home/jb/.teamviewer/5/drive_c/users/Public/Music
/home/jb/.teamviewer/5/drive_c/users/Public/Pictures
/home/jb/.teamviewer/5/drive_c/users/Public/Start Menu
/home/jb/.teamviewer/5/drive_c/users/Public/Templates
/home/jb/.teamviewer/5/drive_c/users/Public/Videos
/home/jb/.teamviewer/5/drive_c/users/Public/Start Menu/Programs
/home/jb/.teamviewer/5/drive_c/users/Public/Start Menu/Programs/Administrative Tools
/home/jb/.teamviewer/5/drive_c/users/Public/Start Menu/Programs/StartUp
/home/jb/.teamviewer/5/drive_c/users/jb/Application Data
/home/jb/.teamviewer/5/drive_c/users/jb/Cookies
/home/jb/.teamviewer/5/drive_c/users/jb/Desktop
/home/jb/.teamviewer/5/drive_c/users/jb/Favorites
/home/jb/.teamviewer/5/drive_c/users/jb/Local Settings
/home/jb/.teamviewer/5/drive_c/users/jb/My Documents
/home/jb/.teamviewer/5/drive_c/users/jb/My Music
/home/jb/.teamviewer/5/drive_c/users/jb/My Pictures
/home/jb/.teamviewer/5/drive_c/users/jb/My Videos
/home/jb/.teamviewer/5/drive_c/users/jb/NetHood
/home/jb/.teamviewer/5/drive_c/users/jb/PrintHood
/home/jb/.teamviewer/5/drive_c/users/jb/Recent
/home/jb/.teamviewer/5/drive_c/users/jb/SendTo
/home/jb/.teamviewer/5/drive_c/users/jb/Start Menu
/home/jb/.teamviewer/5/drive_c/users/jb/Temp
/home/jb/.teamviewer/5/drive_c/users/jb/Templates
/home/jb/.teamviewer/5/drive_c/users/jb/Application Data/TeamViewer
/home/jb/.teamviewer/5/drive_c/users/jb/Application Data/TeamViewer/Connections.txt
/home/jb/.teamviewer/5/drive_c/users/jb/Application Data/TeamViewer/TeamViewer5_Logfile.log
/home/jb/.teamviewer/5/drive_c/users/jb/Local Settings/Application Data
/home/jb/.teamviewer/5/drive_c/users/jb/Local Settings/History
/home/jb/.teamviewer/5/drive_c/users/jb/Local Settings/Temporary Internet Files
/home/jb/.teamviewer/5/drive_c/users/jb/Start Menu/Programs
/home/jb/.teamviewer/5/drive_c/users/jb/Start Menu/Programs/StartUp
/home/jb/.teamviewer/5/drive_c/windows/command
/home/jb/.teamviewer/5/drive_c/windows/explorer.exe
/home/jb/.teamviewer/5/drive_c/windows/fonts
/home/jb/.teamviewer/5/drive_c/windows/help
/home/jb/.teamviewer/5/drive_c/windows/hh.exe
/home/jb/.teamviewer/5/drive_c/windows/inf
/home/jb/.teamviewer/5/drive_c/windows/inf.done
/home/jb/.teamviewer/5/drive_c/windows/notepad.exe
/home/jb/.teamviewer/5/drive_c/windows/profiles
/home/jb/.teamviewer/5/drive_c/windows/regedit.exe
/home/jb/.teamviewer/5/drive_c/windows/system
/home/jb/.teamviewer/5/drive_c/windows/system.ini
/home/jb/.teamviewer/5/drive_c/windows/system32
/home/jb/.teamviewer/5/drive_c/windows/temp
/home/jb/.teamviewer/5/drive_c/windows/twain.dll
/home/jb/.teamviewer/5/drive_c/windows/twain_32.dll
/home/jb/.teamviewer/5/drive_c/windows/win.ini
/home/jb/.teamviewer/5/drive_c/windows/winhelp.exe
/home/jb/.teamviewer/5/drive_c/windows/winhlp32.exe
/home/jb/.teamviewer/5/drive_c/windows/winsxs
/home/jb/.teamviewer/5/drive_c/windows/profiles/All Users
/home/jb/.teamviewer/5/drive_c/windows/profiles/All Users/Start Menu
/home/jb/.teamviewer/5/drive_c/windows/profiles/All Users/Start Menu/Programs
/home/jb/.teamviewer/5/drive_c/windows/profiles/All Users/Start Menu/Programs/TeamViewer 5
/home/jb/.teamviewer/5/drive_c/windows/winsxs/manifests
/home/jb/.teamviewer/5/drive_c/windows/winsxs/manifests/x86_microsoft.windows.common-controls_6595b64144ccf1df_6.0.2600.2982_none_deadbeef.manifest
/usr/bin/teamviewer
/usr/share/applications/teamviewer-teamviewer.desktop
/var/lib/dpkg/info/teamviewer5.list
/var/lib/dpkg/info/teamviewer5.postinst
/var/lib/dpkg/info/teamviewer5.postrm
/var/lib/dpkg/info/teamviewer5.preinst
/var/lib/dpkg/info/teamviewer5.prerm
jb@john-xubuntu:~/Desktop$


jb@john-xubuntu:~/Desktop$ locate wine
/home/jb/.teamviewer/5/winelog
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/tvwine.dll.so
/usr/share/app-install/desktop/q4wine.desktop
/usr/share/app-install/desktop/wine-winetricks.desktop
/usr/share/app-install/desktop/wine.desktop
/usr/share/app-install/desktop/wine1.2.desktop
/usr/share/app-install/desktop/wine1.3.desktop
/usr/share/app-install/desktop/winefish.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_winefish-icon.png
/usr/share/app-install/icons/folder-wine.png
/usr/share/app-install/icons/q4wine.png
/usr/share/app-install/icons/wine-winetricks.svg
/usr/share/app-install/icons/wine.svg
jb@john-xubuntu:~/Desktop$

I thought I 'completely removed' it (TV5).

How do I undo this mess?  I would like to put my machine to NO WINE, and NO TEAMVIEWER ... anywhere (including not on my list of Applications).

Once I get everything 'fixed', I will (probably) install the TV6 deb from the TV website .. but that is not the priority at this point.

  Any help is appreciated in advance.

---

### Post by Ozymandias_117 on 2011-06-30
When completely removing a program, it will leave anything in your home directory. (Which is what most of the teamview is) Also, locate works off a database, which may not have been updated since you uninstalled it. This may account for the rest of the leftover files. Try these commands and see if you still get anything back:
```
sudo updatedb
locate teamview | grep -v /home
```

---

### Post by jfbooth on 2011-07-01
Thank you for your reply.  Here is the output of the commands:

jb@john-xubuntu:~/Desktop$ sudo updatedb
[sudo] password for jb: 
jb@john-xubuntu:~/Desktop$ locate teamviewer | grep -v /home
/home/jb/.teamviewer
/home/jb/.local/share/icons/e727_teamviewer.xpm
/home/jb/.teamviewer/5
/home/jb/.teamviewer/5/.update-timestamp
/home/jb/.teamviewer/5/dosdevices
/home/jb/.teamviewer/5/drive_c
/home/jb/.teamviewer/5/fs_rgb.reg
/home/jb/.teamviewer/5/system.reg
/home/jb/.teamviewer/5/user.reg
/home/jb/.teamviewer/5/userdef.reg
/home/jb/.teamviewer/5/winelog
/home/jb/.teamviewer/5/dosdevices/c:
/home/jb/.teamviewer/5/dosdevices/z:
/home/jb/.teamviewer/5/drive_c/Program Files
/home/jb/.teamviewer/5/drive_c/users
/home/jb/.teamviewer/5/drive_c/windows
/home/jb/.teamviewer/5/drive_c/Program Files/Common Files
/home/jb/.teamviewer/5/drive_c/Program Files/Internet Explorer
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer
/home/jb/.teamviewer/5/drive_c/Program Files/Internet Explorer/iexplore.exe
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer.exe
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_ar.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_cs.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_da.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_de.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_en.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_es.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_fi.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_fr.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_it.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_ja.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_ko.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_nl.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_no.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_pl.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_pt.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_ru.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_sv.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/TeamViewer_Resource_tr.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/tvwine.dll.so
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/update
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version5/update/update.exe
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/CopyRights.txt
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/License.txt
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer.exe
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Desktop.exe
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_ar.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_bg.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_cs.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_da.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_de.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_el.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_en.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_es.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_fi.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_fr.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_he.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_hr.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_hu.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_id.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_it.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_ja.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_ko.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_lt.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_nl.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_no.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_pl.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_pt.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_ro.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_ru.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_sk.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_sr.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_sv.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_th.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_tr.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_uk.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_vi.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_zhCN.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Resource_zhTW.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/TeamViewer_Service.exe
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/tv_w32.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/tv_w32.exe
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/tv_x64.dll
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/tv_x64.exe
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/uninstall.exe
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/w2k
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/x86
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/w2k/TeamViewerVPN.inf
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/w2k/teamviewervpn.sys
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/x86/TVMonitor.inf
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/x86/TVMonitor.sys
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/x86/TeamViewerVPN.inf
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/x86/teamviewervpn.cat
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/x86/teamviewervpn.sys
/home/jb/.teamviewer/5/drive_c/Program Files/TeamViewer/Version6/x86/tvmonitor.cat
/home/jb/.teamviewer/5/drive_c/users/Public
/home/jb/.teamviewer/5/drive_c/users/jb
/home/jb/.teamviewer/5/drive_c/users/Public/Application Data
/home/jb/.teamviewer/5/drive_c/users/Public/Desktop
/home/jb/.teamviewer/5/drive_c/users/Public/Documents
/home/jb/.teamviewer/5/drive_c/users/Public/Favorites
/home/jb/.teamviewer/5/drive_c/users/Public/Music
/home/jb/.teamviewer/5/drive_c/users/Public/Pictures
/home/jb/.teamviewer/5/drive_c/users/Public/Start Menu
/home/jb/.teamviewer/5/drive_c/users/Public/Templates
/home/jb/.teamviewer/5/drive_c/users/Public/Videos
/home/jb/.teamviewer/5/drive_c/users/Public/Start Menu/Programs
/home/jb/.teamviewer/5/drive_c/users/Public/Start Menu/Programs/Administrative Tools
/home/jb/.teamviewer/5/drive_c/users/Public/Start Menu/Programs/StartUp
/home/jb/.teamviewer/5/drive_c/users/Public/Start Menu/Programs/TeamViewer 6
/home/jb/.teamviewer/5/drive_c/users/Public/Start Menu/Programs/TeamViewer 6/License.lnk
/home/jb/.teamviewer/5/drive_c/users/Public/Start Menu/Programs/TeamViewer 6/TeamViewer 6.lnk
/home/jb/.teamviewer/5/drive_c/users/Public/Start Menu/Programs/TeamViewer 6/Uninstall TeamViewer 6.lnk
/home/jb/.teamviewer/5/drive_c/users/jb/Application Data
/home/jb/.teamviewer/5/drive_c/users/jb/Cookies
/home/jb/.teamviewer/5/drive_c/users/jb/Desktop
/home/jb/.teamviewer/5/drive_c/users/jb/Favorites
/home/jb/.teamviewer/5/drive_c/users/jb/Local Settings
/home/jb/.teamviewer/5/drive_c/users/jb/My Documents
/home/jb/.teamviewer/5/drive_c/users/jb/My Music
/home/jb/.teamviewer/5/drive_c/users/jb/My Pictures
/home/jb/.teamviewer/5/drive_c/users/jb/My Videos
/home/jb/.teamviewer/5/drive_c/users/jb/NetHood
/home/jb/.teamviewer/5/drive_c/users/jb/PrintHood
/home/jb/.teamviewer/5/drive_c/users/jb/Recent
/home/jb/.teamviewer/5/drive_c/users/jb/SendTo
/home/jb/.teamviewer/5/drive_c/users/jb/Start Menu
/home/jb/.teamviewer/5/drive_c/users/jb/Temp
/home/jb/.teamviewer/5/drive_c/users/jb/Templates
/home/jb/.teamviewer/5/drive_c/users/jb/Application Data/TeamViewer
/home/jb/.teamviewer/5/drive_c/users/jb/Application Data/TeamViewer/Connections.txt
/home/jb/.teamviewer/5/drive_c/users/jb/Application Data/TeamViewer/MRU
/home/jb/.teamviewer/5/drive_c/users/jb/Application Data/TeamViewer/TeamViewer5_Logfile.log
/home/jb/.teamviewer/5/drive_c/users/jb/Application Data/TeamViewer/TeamViewer6_Logfile.log
/home/jb/.teamviewer/5/drive_c/users/jb/Application Data/TeamViewer/MRU/690774199.tvc
/home/jb/.teamviewer/5/drive_c/users/jb/Local Settings/Application Data
/home/jb/.teamviewer/5/drive_c/users/jb/Local Settings/History
/home/jb/.teamviewer/5/drive_c/users/jb/Local Settings/Temporary Internet Files
/home/jb/.teamviewer/5/drive_c/users/jb/Local Settings/Temporary Internet Files/Content.IE5
/home/jb/.teamviewer/5/drive_c/users/jb/Local Settings/Temporary Internet Files/Content.IE5/2TSV0HPS
/home/jb/.teamviewer/5/drive_c/users/jb/Local Settings/Temporary Internet Files/Content.IE5/615841LE
/home/jb/.teamviewer/5/drive_c/users/jb/Local Settings/Temporary Internet Files/Content.IE5/UD05UEYM
/home/jb/.teamviewer/5/drive_c/users/jb/Local Settings/Temporary Internet Files/Content.IE5/YLEIXXU7
/home/jb/.teamviewer/5/drive_c/users/jb/Local Settings/Temporary Internet Files/Content.IE5/index.dat
/home/jb/.teamviewer/5/drive_c/users/jb/Local Settings/Temporary Internet Files/Content.IE5/UD05UEYM/update_6.0.10722[0]
/home/jb/.teamviewer/5/drive_c/users/jb/Local Settings/Temporary Internet Files/Content.IE5/YLEIXXU7/TVversion5[0]
/home/jb/.teamviewer/5/drive_c/users/jb/Recent/690774199.tvc.lnk
/home/jb/.teamviewer/5/drive_c/users/jb/Start Menu/Programs
/home/jb/.teamviewer/5/drive_c/users/jb/Start Menu/Programs/StartUp
/home/jb/.teamviewer/5/drive_c/users/jb/Temp/TeamViewer
/home/jb/.teamviewer/5/drive_c/users/jb/Temp/TeamViewer/Version6
/home/jb/.teamviewer/5/drive_c/windows/command
/home/jb/.teamviewer/5/drive_c/windows/explorer.exe
/home/jb/.teamviewer/5/drive_c/windows/fonts
/home/jb/.teamviewer/5/drive_c/windows/help
/home/jb/.teamviewer/5/drive_c/windows/hh.exe
/home/jb/.teamviewer/5/drive_c/windows/inf
/home/jb/.teamviewer/5/drive_c/windows/inf.done
/home/jb/.teamviewer/5/drive_c/windows/notepad.exe
/home/jb/.teamviewer/5/drive_c/windows/profiles
/home/jb/.teamviewer/5/drive_c/windows/regedit.exe
/home/jb/.teamviewer/5/drive_c/windows/system
/home/jb/.teamviewer/5/drive_c/windows/system.ini
/home/jb/.teamviewer/5/drive_c/windows/system32
/home/jb/.teamviewer/5/drive_c/windows/temp
/home/jb/.teamviewer/5/drive_c/windows/twain.dll
/home/jb/.teamviewer/5/drive_c/windows/twain_32.dll
/home/jb/.teamviewer/5/drive_c/windows/win.ini
/home/jb/.teamviewer/5/drive_c/windows/winhelp.exe
/home/jb/.teamviewer/5/drive_c/windows/winhlp32.exe
/home/jb/.teamviewer/5/drive_c/windows/winsxs
/home/jb/.teamviewer/5/drive_c/windows/profiles/All Users
/home/jb/.teamviewer/5/drive_c/windows/profiles/All Users/Start Menu
/home/jb/.teamviewer/5/drive_c/windows/profiles/All Users/Start Menu/Programs
/home/jb/.teamviewer/5/drive_c/windows/profiles/All Users/Start Menu/Programs/TeamViewer 5
/home/jb/.teamviewer/5/drive_c/windows/winsxs/manifests
/home/jb/.teamviewer/5/drive_c/windows/winsxs/manifests/x86_microsoft.windows.common-controls_6595b64144ccf1df_6.0.2600.2982_none_deadbeef.manifest
jb@john-xubuntu:~/Desktop$

jb@john-xubuntu:~/Desktop$ locate wine | grep -v /home
/usr/share/app-install/desktop/q4wine.desktop
/usr/share/app-install/desktop/wine-winetricks.desktop
/usr/share/app-install/desktop/wine.desktop
/usr/share/app-install/desktop/wine1.2.desktop
/usr/share/app-install/desktop/wine1.3.desktop
/usr/share/app-install/desktop/winefish.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_winefish-icon.png
/usr/share/app-install/icons/folder-wine.png
/usr/share/app-install/icons/q4wine.png
/usr/share/app-install/icons/wine-winetricks.svg
/usr/share/app-install/icons/wine.svg
jb@john-xubuntu:~/Desktop$

---

### Post by jfbooth on 2011-07-01
I think I fixed all this myself.  Thanks for the help.

---

