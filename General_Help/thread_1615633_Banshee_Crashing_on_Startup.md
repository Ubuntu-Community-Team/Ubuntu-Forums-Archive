---
title: "Banshee Crashing on Startup"
date: 2010-11-07
forum: General Help
---

### Post by daniellog on 2010-11-07
Hi Guys,

I'm having problems with Banshee on Kubuntu 10.10. I have installed it from the repo and when launched it crashes straight away. I've run it through konsole and get the following output...

```
[Info  13:43:07.341] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, x86_64) @ 2010-10-26 18:20:51 UTC]
[Warn  13:43:08.761] DBus support could not be started. Disabling for this session.
[Info  13:43:09.031] Migrating album-art cache directory
[Info  13:43:09.035] Migrated 0 files in 0.002363s
[Warn  13:43:13.314] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  13:43:13.314] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  13:43:13.334] Updating web proxy from GConf
[Warn  13:43:13.478] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  13:43:13.478] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  13:43:13.479] All services are started 4.716542
[Warn  13:43:13.776] Migrating Internet Radio Stations - System.IO.DirectoryNotFoundException: Directory '/root/.config/banshee-1/plugins/stations/user' not found. (in `mscorlib')
  at System.IO.Directory.GetFileSystemEntries (System.String path, System.String searchPattern, FileAttributes mask, FileAttributes attrs) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.GetFiles (System.String path, System.String searchPattern) [0x00000] in <filename unknown>:0 
  at Banshee.InternetRadio.XspfMigrator.Migrate () [0x00000] in <filename unknown>:0 
[Info  13:43:14.093] nereid Client Started
[Info  13:43:14.236] AppleDeviceSource is ignoring unmounted volume floppy0
[Warn  13:43:14.236] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')                                                                       
  at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0                                              
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 
The program 'Banshee' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 3625 error_code 8 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

``` 

Any help you can give me will be most appreciated!

---

### Post by Yomi on 2010-11-10
I'm having similar a similar problem, but it only happens after I try to play a song. I ran it in terminal and I get this error. 

 Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
  at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 


I'm sort of new to Ubuntu, and I have no idea what to do, although I've tried uninstalling and reinstalling.

---

### Post by daniellog on 2010-11-13
Found a fix,

```
mkdir ~/banshee-icon
sudo mv /usr/lib/banshee-1/Extensions/Banshee.Notification* ~/banshee-icon
```

---

### Post by 2-7offsuit on 2010-11-13
Hey daniellog, that did it! I was getting a more generic error before I renamed ~/.config/banshee-1.

---

### Post by Gyoja on 2010-12-12
daniellog -

i had the same problem and your fix worked for me as well. thanks!

---

