---
title: "Installing Garmin Map Update"
date: 2010-03-09
forum: General Help
---

### Post by TaoWanderer on 2010-03-09
Hello all.  I just switched over to Ubuntu completely from Windows a few months ago.  I love it, except for a few mysteries here and there that needed to be solved.  Here is my latest mystery:

I'm trying to figure out how to install this map update from Garmin Website, garmin_rmu_cnnant2010_40.exe for my Nuvi 265WT GPS unit.  It wouldn't even let me download it at first without the Garmin Communicator, which Garmin wouldn't let me install because it said my browser wasn't compatible, Firefox for Ubuntu.  So I downloaded and installed Firefox for Windows with Wine and was able to download my map update.  

Now when I try to run the map update with Wine by double clicking or right clicking, nothing happens .  If I try to run it from the Terminal window it says:

```
ramji@Kaiser:~/Downloads$ wine garmin_rmu_cnnant2010_40.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\ramji\\Downloads\\garmin_rmu_cnnant2010_40.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\ramji\\Downloads\\garmin_rmu_cnnant2010_40.exe" failed, status c0000135
```

So I installed VirtualBox OSE with Windows XP as the guest virtual machine and installed the Guest Additions and transfered the map update into the virtual machine and when I try to run it from in there it says:

This application has failed to start because the application configuration is incorrect.  Reinstalling the application may fix this problem.

I'm kinda at a dead end now, not sure what else I can do.  I'd really hate to have to go to a dual boot just because of this one program.  Any ideas are greatly appreciated.

---

### Post by gabak on 2010-06-04
here it explain how to do it

[http://jhau.maliwi.de/linux/gpssw.html](http://jhau.maliwi.de/linux/gpssw.html)

---

