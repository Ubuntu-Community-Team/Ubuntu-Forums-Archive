---
title: "Cannot change mode to rwxr-xr-x"
date: 2009-10-02
forum: General Help
---

### Post by souman on 2009-10-02
Hi,

Whenever I try to unzip a tar.bz file I am getting the following message.

***tar: ns-allinone-2.34/gt-itm/include: Cannot change mode to rwxr-xr-x: Operation not permitted***

Here i was trying to unzip the ns-allinone-2.34.tar.gz file.

I am getting this message after doing the following 
Initially I changed the permission for /usr/src to 777. 
Then I was getting some error message when I tried to run the command ***sudo su.***
So I ran the following  commands 

[LIST]
[*]        ***ls -l /usr/bin/sudo***
[*]***        chown root:root/usr/bin/sudo***
[*]***        chmod 4755 /usr/bin/sudo***
[*]***        reboot***.
[/LIST]
As the fat32 volume was not getting mounted after this so I edit the *** /etc/fstab***, and add
the following two line there,

[LIST]
[*]***/dev/sda6 /media/SONGS vfat defaults,umask=000 0 0***
[*]***/dev/sda5 /media/IITB vfat defaults,umask=000 0 0***
[/LIST]
[B][I]
So please reply how to solve this. Do I need to change any permission to the drive or need to make some changes in [/I][/B]*** /etc/fstab file***[B][I]???

[/I][/B][I]Thanks,
[/I]Souman

---

### Post by Giblet5 on 2009-10-02
As for the mode problem, it's because you don't have permission. Maybe you don't own the directory (created it as root?).

Why are you changing the perms on sudo? Its mode is 4755 right out of the box. And why did you reboot just because you changed a file's perms?

OK, you edited fstab. Did the drives mount after ```
sudo mount -a
``` or not?

Safety Tip: One question, one thread. All three of these are unrelated.

---

### Post by souman on 2009-10-04
All the drive are mounted.
I change the permission and owner because ```
sudo su 
``` was not executing.
I was in the recovery command prompt so I reboot the syatem.
Now the output of ls -l, is
```
total 108
lrwxrwxrwx  1 root root     6 2009-08-13 23:11 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2009-08-13 23:11 cdrom0
drwxrwxrwx  1 root root  8192 2009-10-02 13:46 GAMES & OTHERS
drwxrwxrwx  9 root root 16384 1970-01-01 05:30 IITB
drwxrwxrwx 12 root root 49152 1970-01-01 05:30 SONGS
drwxrwxrwx  1 root root 24576 2009-10-04 22:06 VIDEOS
drwxrwxrwx  1 root root  8192 2009-10-04 17:01 XP
```So I think I have all the permission but still I am having the same problem.

So plz help, how to solve this.

---

### Post by LewRockwellFAN on 2011-01-06
For what it is worth I have had similar problems extracting tarballs of executable programs. I just extracted one for an opensim (3d virtual reality sim) server and got repeated error messages like "Cannot change mode to rwxr-xr-x: Operation not permitted". I found this thread by googling that message. OP, if you are still around, did you ever solve this? Clearly, even when you posted this you already understood the permission jungle better than I do. I tried extracting from a sudo session of the Thunar file browser (which I like cause it doesn't have the memory leak from Hell that has lurked in Nautilus as long as I have been messing with it, just waiting to bite you when you least expect it) but still had the same problem. Why o why isn't there some sort of super-super-extra-super user account that can do ANYTHING? Sometime I feel like screaming "It's my @#$!!#@#! fscking computer! I'll mess it up if I want to you uppity OShole!" -Hysterical Rant Ends Here- Thank you. I'll take a sedative now, nurse.

---

### Post by perspectoff on 2011-01-06
Oh brother.

Just prefix the commands with sudo.

sudo chmod 755 filename.tar

sudo chown bigdaddy:clowngroup filename.tar

etc.

---

### Post by LewRockwellFAN on 2011-01-07
Thanks, Perspectoff. I'm not absolutely sure I followed that. I opened a terminal and cd'ed to the directory in question. Then I entered:
 sudo chmod 755 '/media/SG-c-FAT-5/0_new_stuff_notonWDyet/software/linux/opensim server/opensim/opensim-0.7.0.2-bin.tar.gz'
Then Bash asked for my password, accepted it, and returned the prompt.
Then I right clicked on the tar.gz and clicked extract.
Then I got a lot of errors like this:

tar: opensim-0.7.0.2-bin/doc: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/addon-modules: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/share/Schemas: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/share/php: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/share/junkCA: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/share/RegionLoading: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/share: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/obj/Release/TempPE: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/obj/Release: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/obj/Debug/TempPE: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/obj/Debug: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/obj: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/ScriptEngines: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Regions: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/config-include/storage: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/config-include: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Library: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/addon-modules: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/AnimationsLibrary: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/ClothingLibrary: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/ObjectsLibrary: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/TexturesLibrary: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/ScriptsLibrary: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/NotecardsLibrary: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/SoundsLibrary: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/PhotosLibrary: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/GesturesLibrary: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/LandmarksLibrary: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/BodyPartsLibrary: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/OpenSimLibrary: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/data: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/LandmarksAssetSet: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/NotecardsAssetSet: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/Avatar/Newruth: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/Avatar: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ObjectsAssetSet: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/AnimationsAssetSet: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ClothingAssetSet: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/MyAssetSet: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/GesturesAssetSet: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/PhotosAssetSet: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/BodyPartsAssetSet: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Terrain: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Physics: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/bin: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: opensim-0.7.0.2-bin: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: Exiting with failure status due to previous errors

The I deleted the failed extraction and closed Nautilus and opened Thunar as root with sudo thunar. I navigated to the directory and opened the tar.gz with Archive Manager from the context menu and extracted it. I again got a lot of error messages that I assume to have meant essentially the same thing although they were worded differerntly:

tar: opensim-0.7.0.2-bin/doc/doxygen.conf: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/doc: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/README.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/addon-modules/README: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/addon-modules: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/share/Schemas/SceneObjectPart0.xsd: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/share/Schemas/SceneObjectPart1.xsd: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/share/Schemas: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/share/php/generateUserFunction.php: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/share/php: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/share/junkCA/README.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/share/junkCA/Certificate commands OpenSSL.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/share/junkCA/CA.key: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/share/junkCA/CA2.pem: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/share/junkCA/CA.srl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/share/junkCA/CA.crt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/share/junkCA: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/share/RegionLoading/HOWTO_REMOTE_REGION_LOADING.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/share/RegionLoading/example_web.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/share/RegionLoading: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/share: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/obj/Release/TempPE: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/obj/Release/SmartThreadPool.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/obj/Release/SmartThreadPool.csproj.FileListAbsolute.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/obj/Release: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/obj/Debug/TempPE: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/obj/Debug: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/obj: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/WorkItemsGroup.cs: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/SmartThreadPool.csproj.user: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/WorkItemInfo.cs: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/PriorityQueue.cs: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/WIGStartInfo.cs: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/Interfaces.cs: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/WorkItem.cs: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/STPStartInfo.cs: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/SmartThreadPool.cs: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/SmartThreadPool.csproj: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/WorkItemFactory.cs: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/STPPerformanceCounter.cs: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/AssemblyInfo.cs: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/CallerThreadContext.cs: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/WorkItemsQueue.cs: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/Exceptions.cs: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool/SmartThreadPool.dll.build: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty/SmartThreadPool: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdParty: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/HttpServer_OpenSim.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/AprSharp.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/http_loginform.html.example: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.Framework.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/ScriptEngines/Default.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/ScriptEngines: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/nunit.framework.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/libeay32.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.ini: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/ode.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/libapriconv.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/AprSharp.pdb: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.vshost.exe.manifest: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Robust.32BitLaunch.exe: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenMetaverse.Utilities.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.CoreModules.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/libode-x86_64.so: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/libdb44d.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/DotNetOpenId.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.exe.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Iesi.Collections.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.32BitLaunch.pdb: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/LaunchSLClient.ini: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/HttpServer.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/DotNetOpenMail.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/protobuf-net.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/libaprutil.pdb: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Fadd.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/libopenjpeg-dotnet-2.1.3.0-dotnet-1.dylib: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Data.MySQL.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Services.Interfaces.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/openjpeg-dotnet-x86_64.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Ode.NET.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/mssql_connection.ini.example: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Framework.Communications.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Newtonsoft.Json.XML: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Framework.RegionLoader.Web.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Google.ProtocolBuffers.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/PhysX-wrapper.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.ApplicationPlugins.RemoteController.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/pCampBotSentences.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/libopenjpeg-dotnet-2.1.3.0-dotnet-1.so: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Framework.Servers.Tests.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/libopenjpeg-dotnet-2.1.3.0-dotnet-1-i686.so: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.UserStatistics.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Tests.Clients.UserAccountClient.exe: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Services.FriendsService.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Services.PresenceService.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/C5.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.ScriptEngine.Tests.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.ClientStack.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenMetaverse.StructuredData.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSimExport.exe.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/HttpServer_OpenSim.pdb: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/shutdown_commands.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Robust.HG.ini.example: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Services.exe.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.Framework.Tests.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/CookComputing.XmlRpcV2.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Services.AuthorizationService.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/sqlite-3.6.21.so: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Services.FreeswitchService.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Framework.Servers.HttpServer.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Data.Null.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Services.InventoryService.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Fadd.Globalization.Yaml.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Castle.DynamicProxy.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/NDesk.Options.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.ScriptEngine.XEngine.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/avatar-texture.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.ScriptEngine.Shared.CodeTools.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.ConsoleClient.exe.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Framework.Tests.dll.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.ApplicationPlugins.Rest.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Regions/.keep: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Regions: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.ScriptEngine.Tests.dll.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.Framework.Tests.dll.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/config-include/StandaloneCommon.ini.example: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/config-include/StandaloneCommon.ini: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/config-include/CenomeCache.ini.example: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/config-include/storage/SQLiteStandalone.ini: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/config-include/storage/SQLiteLegacyStandalone.ini: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/config-include/storage: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/config-include/Standalone.ini: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/config-include/Grid.ini: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/config-include/FlotsamCache.ini.example: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/config-include/GridCommon.ini.example: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/config-include/GridHypergrid.ini: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/config-include/StandaloneHypergrid.ini: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/config-include/SimianGrid.ini: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/config-include: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Library/.keep: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Library: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/HttpServer_OpenSim.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/http_404.html.example: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/opensim-ode.sh: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/libaprutil.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Data.MSSQL.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Newtonsoft.Json.pdb: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenMetaverse.StructuredData.XML: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Client.MXP.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.ConsoleClient.exe: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Framework.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenMetaverseTypes.XML: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Mono.Data.Sqlite.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/addon-modules/README: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/addon-modules: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Nini.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/svn_client-1.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Services.Base.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Grid.UserServer.exe.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/intl3_svn.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Newtonsoft.Json.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/http_500.html.example: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/SubversionSharp.pdb: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/BulletDotNET.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.Physics.Manager.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/libbulletnet.so: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/System.Data.SQLite.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.DataSnapshot.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/openjpeg-dotnet.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Kds.Serialization.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Framework.Statistics.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Robust.exe: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Services.HypergridService.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/SimpleApp.exe.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Data.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/xunit.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Grid.GridServer.exe.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.ScriptEngine.Shared.YieldProlog.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenMetaverse.Http.XML: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/RAIL.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenMetaverseTypes.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.ScriptEngine.Shared.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/AnimationsLibrary/AnimationsLibraryFolders.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/AnimationsLibrary/AnimationsLibraryItems.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/AnimationsLibrary: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/ClothingLibrary/ClothingLibraryFolders.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/ClothingLibrary/ClothingLibraryItems.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/ClothingLibrary: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/Libraries.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/ObjectsLibrary/ObjectsLibraryFolders.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/ObjectsLibrary/ObjectsLibraryItems.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/ObjectsLibrary: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/TexturesLibrary/TexturesLibraryItems.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/TexturesLibrary/TexturesLibraryFolders.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/TexturesLibrary: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/README.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/ScriptsLibrary/ScriptsLibraryFolders.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/ScriptsLibrary/ScriptsLibraryItems.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/ScriptsLibrary: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/NotecardsLibrary/NotecardsLibraryFolders.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/NotecardsLibrary/NotecardsLibraryItems.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/NotecardsLibrary: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/SoundsLibrary/SoundsLibraryItems.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/SoundsLibrary/SoundsLibraryFolders.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/SoundsLibrary: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/PhotosLibrary/PhotosLibraryItems.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/PhotosLibrary/PhotosLibraryFolders.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/PhotosLibrary: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/GesturesLibrary/GesturesLibraryFolders.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/GesturesLibrary/GesturesLibraryItems.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/GesturesLibrary: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/LandmarksLibrary/LandmarksLibraryItems.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/LandmarksLibrary/LandmarksLibraryFolders.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/LandmarksLibrary: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/BodyPartsLibrary/BodyPartsLibraryItems.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/BodyPartsLibrary/BodyPartsLibraryFolders.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/BodyPartsLibrary: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/OpenSimLibrary/OpenSimLibrary.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/OpenSimLibrary/OpenSimLibraryFolders.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory/OpenSimLibrary: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/inventory: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.32BitLaunch.exe: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Grid.ScriptServer.exe.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/libode.dylib: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Modified.XnaDevRu.BulletX.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Framework.Console.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/XMLRPC.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/MySql.Data.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.ClientStack.LindenUDP.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Mono.GetOptions.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/libode.so: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenMetaverse.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Services.AvatarService.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Server.Handlers.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Services.GridService.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Grid.GridServer.addin.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Mono.Data.SqliteClient.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Prebuild.exe: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Server.Base.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.ApplicationPlugins.RegionModulesController.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/PhysX_Wrapper_Dotnet.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Ode.NET.dll.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Services.Connectors.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Robust.ini.example: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/SmartThreadPool.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Services.LLLoginService.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/libapr.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Framework.Configuration.HTTP.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/BclExtras35.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/MXP.pdb: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.32BitLaunch.exe.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Tools.Configger.exe: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.exe: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/libapriconv.pdb: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/DotSets.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.ScriptEngine.Shared.Instance.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/libbulletnet.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenMetaverse.XML: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/MonoXnaCompactMaths.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Data.SQLite.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Services.UserAccountService.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Client.Sirikata.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenMetaverse.Utilities.XML: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Framework.Communications.Tests.dll.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Tests.Common.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Services.AuthenticationService.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Services.AssetService.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Data.SQLiteLegacy.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/defaultstripe.png: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Mono.PEToolkit.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Robust.32BitLaunch.exe.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.CoreModules.Tests.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Tools.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.Physics.OdePlugin.Tests.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Framework.Servers.Tests.dll.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Data.Tests.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.CoreModules.Tests.dll.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.ScriptEngine.Shared.Api.Runtime.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Npgsql.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/PumaCode.SvnDotNet.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/BulletDotNET.pdb: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Castle.Core.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/GlynnTucker.Cache.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Tools.lslc.exe: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Tests.Clients.GridClient.exe: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.vshost.exe: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/libopenjpeg-dotnet-2.1.3.0-dotnet-1-x86_64.so: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/startup_commands.txt.example: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Framework.Servers.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.ApplicationPlugins.Rest.Regions.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Framework.Capabilities.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/startuplogo.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Framework.Serialization.Tests.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/protobuf-net.pdb: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Framework.RegionLoader.Filesystem.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.OptionalModules.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.TestSuite.exe: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/pCampBot.exe: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Robust.exe.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.addin.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Framework.Configuration.XML.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/CSJ2K.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/MXP.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Framework.AssetLoader.Filesystem.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/excuses: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Client.VWoHTTP.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Grid.MessagingServer.exe.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.ApplicationPlugins.LoadRegions.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Castle.DynamicProxy2.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Mono.Addins.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/data/LICENSE-README-IMPORTANT.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/data/avataranimations.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/data/prototype.js: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/data/updater.js: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/data: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.ApplicationPlugins.Rest.Inventory.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.ScriptEngine.Shared.Api.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Region.RegionCombinerModule.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Mono.Addins.dll.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/libapr.pdb: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/LandmarksAssetSet/LandmarksAssetSet.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/LandmarksAssetSet: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/NotecardsAssetSet/welcomeNote.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/NotecardsAssetSet/exampleNote.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/NotecardsAssetSet/NotecardsAssetSet.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/NotecardsAssetSet: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/Avatar/Newruth/Settings.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/Avatar/Newruth/female bottom.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/Avatar/Newruth/female face.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/Avatar/Newruth/open sim hair base.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/Avatar/Newruth/eyes.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/Avatar/Newruth/female body.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/Avatar/Newruth: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/Avatar: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ObjectsAssetSet/ObjectsAssetSet.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ObjectsAssetSet: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/README.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/AnimationsAssetSet/bouncy_ball_super.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/AnimationsAssetSet/give_and_handshake.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/AnimationsAssetSet/bouncy_ball_left.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/AnimationsAssetSet/place_marker.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/AnimationsAssetSet/autograph_right.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/AnimationsAssetSet/bouncy_ball_run.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/AnimationsAssetSet/tpose.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/AnimationsAssetSet/bouncy_ball_right.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/AnimationsAssetSet/bouncy_ball_walk.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/AnimationsAssetSet/tpose2.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/AnimationsAssetSet/index.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/AnimationsAssetSet/handshake_01.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/AnimationsAssetSet/windsurf_left.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/AnimationsAssetSet: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/KanEd-Test10.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/llSay.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/llSetParcelMusicURL.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/KanEd-Test01.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/KanEd-Test08.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/llRemoveFromLandPassList.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/KanEd-Test16.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/KanEd-Test07.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/KanEd-Test13.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/llAllowInventoryDrop.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/osWeatherMap.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/KanEd-Test09.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/KanEd-Test04.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/llAddToLandPassList.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/KanEd-Test05.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/KanEd-Test14.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/llApplyImpulse.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/llResetLandPassList.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/llAdjustSoundVolume.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/KanEd-Test11.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/KanEd-Test06.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/llSetRot.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/ScriptsAssetSet.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/llAcos.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/GrafittiBoard.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/osTextBoard.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/llAvatarOnSitTarget.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/llAbs.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/KanEd-Test15.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/llAtan2.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/llRemoveFromLandBanList.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/llAsin.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/KanEd-Test02.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/KanEd-Test12.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/llAddToLandBanList.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/llResetLandBanList.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/llBase64ToString.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/KanEd-Test03.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet/llAngleBetween.lsl: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ScriptsAssetSet: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ClothingAssetSet/newpants.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ClothingAssetSet/ClothingAssetSet.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ClothingAssetSet/newshirt.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/ClothingAssetSet: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/MyAssetSet/MyAssetSet.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/MyAssetSet: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/OSSndSnapshot.ogg: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/OSSndClick.ogg: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/OSSndHealthReductionM.ogg: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/OSSndHealthReductionF.ogg: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/OSSndWindowOpen.ogg: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/OSSndObjectRezIn.ogg: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/OSSndInvalidOp.ogg: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/OSSndAlert.ogg: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/OSSndTeleportOut.ogg: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/OSSndMoneyChangeUp.ogg: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/OSSndStartIM.ogg: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/SoundsAssetSet.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/OSSndTyping.ogg: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/OSSndNewIncomingIMSession.ogg: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/OSSndObjectCreate.ogg: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/OSSndPieMenuAppear.ogg: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/OSSndObjectDelete.ogg: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/OSSndWindowClose.ogg: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/OSSndMoneyChangeDown.ogg: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/OSSndBadKeystroke.ogg: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet/OSSndPieMenuSliceHighlight.ogg: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/SoundsAssetSet: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/GesturesAssetSet/raise_hand.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/GesturesAssetSet/me_.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/GesturesAssetSet/can_we_move_along_.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/GesturesAssetSet/clap.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/GesturesAssetSet/no.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/GesturesAssetSet/wink_.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/GesturesAssetSet/definitely_YES.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/GesturesAssetSet/dance1.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/GesturesAssetSet/take_it_outside.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/GesturesAssetSet/LOL.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/GesturesAssetSet/suprised.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/GesturesAssetSet/not_sure.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/GesturesAssetSet/dance3.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/GesturesAssetSet/GesturesAssetSet.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/GesturesAssetSet/Wave.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/GesturesAssetSet/whoohoo_.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/GesturesAssetSet/dance2.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/GesturesAssetSet: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/PhotosAssetSet/PhotosAssetSet.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/PhotosAssetSet: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/ivy.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/map_base.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/5bc11cd6-2f40-071e-a8da-0903394204f9.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/se_face.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/a6162133-724b-54df-a12f-51cd070ad6f3.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/db9d39ec-a896-c287-1ced-64566217021e.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/4-tile2.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/96b4de31-f4fa-337d-ec78-451e3609769e.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/pastelbrick.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/roof01.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/se_lower.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/gravel.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/e569711a-27c2-aad4-9246-0c910239a179.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/water3.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/greybrick.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/snow1.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/brick_mono.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/Terrain Mountain-179cdabd-398a-9b6b-1391-4dc333ba321f.texture: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/cement_block.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/822ded49-9a6c-f61c-cb89-6df54f42cdf4.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/stone1wall.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/wood1.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/steel.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/Terrain Grass-abb783e6-3e93-26c0-248a-247666855da3.texture: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/glasstile2.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/735198cf-6ea0-2550-e222-21d3c6a341ae.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/hg2.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/thatch.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/brick1_256.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/2a4880b6-b7a3-690a-2049-bfbe38eafb9f.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/073c9723-540c-5449-cdd4-0e87fdc159e3.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/rooftiles1.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/bricks.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/mosaic02.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/18fb888b-e8f1-dce7-7da7-321d651ea6b0.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/6c9fa78a-1c69-2168-325b-3e03ffa348ce.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/4-tile3.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/default_media.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/stonetile.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/grass2.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/fe_lower.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/a85ac674-cb75-4af6-9499-df7c5aaf7a28.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/cedar.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/83b77fc6-10b4-63ec-4de7-f40629f238c5.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/default_avatar.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/7c0cf89b-44b1-1ce2-dd74-07102a98ac2a.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/fe_face.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/moon.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/rooftiles2_roy.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/map1.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/fe_upper.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/cdd9a9fc-6d0b-f90d-8416-c72b6019bca8.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/Terrain Dirt-b8d3965a-ad78-bf43-699b-bff8eca6c975.texture: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/Terrain Rock-beb169c7-11ea-fff2-efe5-0f24dc881df2.texture: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/d9258671-868f-7511-c321-7baef9e948a4.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/058c75c0-a0d5-f2f8-43f3-e9699a89c2fc.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/8a515889-eac9-fb55-8eba-d2dc09eb32c8.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/7a2b3a4a-53c2-53ac-5716-aac7d743c020.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/hardwood.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/rockbuilding.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/d691a01c-13b7-578d-57c0-5caef0b4e7e1.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/2d784476-d0db-9979-0cff-9408745a7cf3.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/seawater.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/f2d7b6f6-4200-1e9a-fd5b-96459e950f94.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/d21e44ca-ff1c-a96e-b2ef-c0753426b7d9.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/8f458549-173b-23ff-d4ff-bfaa5ea2371b.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/granite.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/poplar.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/shingle.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/6c4727b8-ac79-ba44-3b81-f9aa887b47eb.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/le_upper.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/street2.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/re_upper.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/cobbles.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/water1.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/ca4e8c27-473c-eb1c-2f5d-50ee3f07d85c.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/clear.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/fgrass.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/b8eed5f0-64b7-6e12-b67f-43fa8e773440.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/brick2_256.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/se_upper.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/67931331-0c02-4876-1255-28770896c6a2.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/le_lower.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/papaya_bark.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/default_clear.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/4726f13e-bd07-f2fb-feb0-bfa2ac58ab61.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/9deab416-9c63-78d6-d558-9a156f12044c.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/blank.jpc: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/mahogany.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/79504bf5-c3ec-0763-6563-d843de66d0a1.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/skins_license.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/5894e2e7-ab8d-edfa-e61c-18cf16854ba3.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/papaya.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/redtri_tile.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/palm1.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/30047cec-269d-408e-0c30-b2603b887268.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/coffee.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/99bd60a2-3250-efc9-2e39-2fbcadefbecc.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/plywood.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/rooftiles2_peach.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/creambrick.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/2caf1179-7861-6ff3-4b7d-46e17780bdfa.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/92e66e00-f56f-598a-7997-048aa64cde18.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/femalebody.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/TexturesAssetSet.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/le_face.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/femalebottom.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/grass.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/fb2ae204-3fd1-df33-594f-c9f882830e66.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/femaleface.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/pine1_10m.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/saguaro_8m.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/rocks.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/re_face.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/licenses.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/0187babf-6c0d-5891-ebed-4ecab1426683.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/10d2a01a-0818-84b9-4b96-c2eb63256519.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/peaches.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/maple.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/cloud.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/64367bd1-697e-b3e6-0b65-3f862a577366.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/re_lower.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/graniteblock.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/6de37e4e-7029-61f5-54b8-f5e63f983f58.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/ae874d1a-93ef-54fb-5fd3-eb0cb156afc0.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/rockwallbig.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/testpic2.jp2: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet/8872f2b8-31db-42d8-580a-b3e4a91262de.j2c: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/TexturesAssetSet: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/AssetSets.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/BodyPartsAssetSet/BodyPartsAssetSet.xml: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/BodyPartsAssetSet/newhair.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/BodyPartsAssetSet/little_goblin_shape.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/BodyPartsAssetSet/base_shape.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/BodyPartsAssetSet/goblin_skin.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/BodyPartsAssetSet/base_skin.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/BodyPartsAssetSet/jim_shape.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/BodyPartsAssetSet/jim_skin.dat: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets/BodyPartsAssetSet: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/assets: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.ini.example: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Terrain/OpenSim.Region.CoreModules.World.Terrain.DefaultEffects.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Terrain: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenMetaverse.dll.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/pCampBot.exe.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/libdb_dotNET43.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/log4net.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/RegionConfig.ini.example: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Tests.Clients.PresenceClient.exe: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Axiom.MathLib.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/SubversionSharp.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.ConsoleClient.ini.example: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/sqlite3.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.vshost.exe.config: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Framework.Serialization.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Client.Linden.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/ssleay32.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/OpenSim.Framework.Tests.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Physics/OpenSim.Region.Physics.OdePlugin.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Physics/OpenSim.Region.Physics.POSPlugin.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Physics/OpenSim.Region.Physics.BulletDotNETPlugin.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Physics/OpenSim.Region.Physics.PhysXPlugin.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Physics/OpenSim.Region.Physics.BulletXPlugin.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Physics/OpenSim.Region.Physics.BasicPhysicsPlugin.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Physics/OpenSim.Region.Physics.Meshing.dll: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin/Physics: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/bin: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/C# Webserver.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/Mono.Xna (MonoXnaCompactMaths).txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/Prototype.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/MySQL.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/GTCache.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/MXP.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/Bullet for Xna (ModifiedBulletX).txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/CSJ2K.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/BclExtras.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/Newtonsoft-JsonDotNet.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/Npgsql.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/GoogleProtoBuffer.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/ODE.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/CSCompilerTools.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/SvnDotNet.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/DotNetOpenid.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/XML-RPC.NET.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/ApachePortableRuntime.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/OpenJpeg.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/libsl.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/Nini.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/DefaultTerrain.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/C5.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/IronPython.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/Axiom.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/Protobuf-net.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/SmartThreadPool.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses/BulletLicense.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/ThirdPartyLicenses: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/LICENSE.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin/CONTRIBUTORS.txt: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: opensim-0.7.0.2-bin: Cannot change ownership to uid 1017, gid 1018: Operation not permitted
tar: Exiting with failure status due to previous errors

OK, maybe I just need to study permissions more. But I'm still at sea on this.

---

### Post by LewRockwellFAN on 2011-01-08
I also tried:
f@f-U-32:/media/SG-c-FAT-5/0_new_stuff_notonWDyet/software/linux/opensim server/opensim$ sudo tar -xf opensim-0.7.0.2-bin.tar.gz 
and got the same types of error messages.

OP, did you ever solve this? Can anyone point me to explicit instructions on the general case of how to unpack tarballs containing executable programs?

---

### Post by LewRockwellFAN on 2011-01-08
I'm still clueless about the problem as posed. But at least a few people reading this thread because of similar problems might could use the work-around I found applicable to my own problem:

The archive I was trying to extract was also available as a zip. I downloaded the zip and extracted it with Archive Manager with no problems and no error messages.

---

### Post by LewRockwellFAN on 2011-01-23
I had another similar tar to extract and instead of archive manager used the terminal and "tar -xvf filename" and it worked perfectly. So I went back to the one I mentioned above that failed and tried the same command on it. It worked fine and the expanded files functioned correctly also.
Note that using the tar command I didn't need to use sudo for it to work. I set my terminal to unlimited history and carefully looked for error messages and didn't see any. Whereas when I tried this earlier with Archive Manager, "extract here", and "tar -xf", I did NOT get functional files from the expansion I conclude the error messages were not erroneous but that the extraction really was defective. I don't see why the -v should make any difference. I assume the relevant change is that I've ditched Natty Narwhal and gone back to 10.04, Lucid Lynx. Dunno. But it works for me now.

---

### Post by directhex on 2011-01-23
You can't chmod files on a FAT32 filesystem, as FAT32 has no permissions model

---

