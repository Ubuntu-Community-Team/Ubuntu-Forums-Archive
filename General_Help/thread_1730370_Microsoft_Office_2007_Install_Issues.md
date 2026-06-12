---
title: "Microsoft Office 2007 Install Issues"
date: 2011-04-16
forum: General Help
---

### Post by phosphide on 2011-04-16
Hi all,

Recently installed Microsoft Office 2007 using PlayonLinux. Installation went great, but now I am running into an issue. I get this error message when I try to run any of the programs:

[quote=""]The program WINWORD.EXE has encountered a serious problem and needs to close. We are sorry for the inconvenience.

This can be caused by a problem in the program or a deficiency in Wine. You may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application.

If this problem is not present under Windows and has not been reported yet, you can report it at [http://bugs.winehq.org](http://bugs.winehq.org)[/quote]

I tried searching around a little bit on google and the wine forums but couldn't find any solutions. I can post the terminal output if necessary.

I am using the HP Mobile Workstation 8510w and using Ubuntu 10.10. I can post more specs if necessary as well.

---

### Post by Jechem on 2011-04-16
You can re-install it again, wiping the config files. Most probably there was something missing during the installation process even if it went fine. Sometimes C++ doesn't load properly. That's how I solved my problem before.

---

### Post by phosphide on 2011-04-16
> **Jechem said:**
> You can re-install it again, wiping the config files. Most probably there was something missing during the installation process even if it went fine. Sometimes C++ doesn't load properly. That's how I solved my problem before.

Hmm, I'd rather not do that but it's certainly an option.

---

### Post by jfreak_ on 2011-04-16
> **phosphide said:**
> Hmm, I'd rather not do that but it's certainly an option. Just want to check before hand (I'm still fairly noobish at Unix), what is the command to run in the terminal?

sudo wine
wine winword.exe

Or would I need to put the entire path of the .exe? 

Because when I run the first option, it says winword.exe doesn't exist.
You'll have to cd into the directory where it is installed ( in home/USERNAME/.wine/path/to/winword)

or you can navigate to winword in nautilus and rightclick and open with wine

---

### Post by phosphide on 2011-04-16
> **jfreak_ said:**
> You'll have to cd into the directory where it is installed ( in home/USERNAME/.wine/path/to/winword)

or you can navigate to winword in nautilus and rightclick and open with wine

Sorry, I just edited my post above. I figured it out in the terminal and to run in Wine. Though I'm still getting the initial error.

---

### Post by Jechem on 2011-04-16
I think you don't have a choice but purge it and re-install.

---

### Post by phosphide on 2011-04-16
> **Jechem said:**
> I think you don't have a choice but purge it and re-install.

I guess I could give it a shot. Though, how does purging work within wine? Just like any other program, or do I have to do it in a windows way?

---

### Post by phosphide on 2011-04-16
Well, I actually figured it out. Just had to change the settings for Wine to Win XP instead of Vista. Easy fix. :)

Edit: Or so I thought. Now only word works. Darnit. Everything else fails to load.

---

### Post by Jechem on 2011-04-16
Well winxp should have been the default. you can do uninstall program through playonlinux or directly from wine. you can also purge playonlinux if all else fails.

```
sudo apt-get purge playonlinux
```

---

### Post by phosphide on 2011-04-16
It was on XP by default, I had changed it when messing around with a couple of things.

By the way, here is the terminal output for Excel, Powerpoint, and Word. Word works fine but the others don't.

Terminal Output for Powerpoint

```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:msvcrt:_controlfp_s ((nil) 65536 196608) semi-stub
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x000007d1,(nil),0x0002,0x00000000,0x32ef48,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000007d1,(nil),0x0002,0x00000000,0x14dbf8,(nil)): stub
err:eventlog:ReportEventW L"Microsoft Office PowerPoint"
err:eventlog:ReportEventW L"PowerPoint failed to start correctly last time.  Starting PowerPoint in safe mode will help you correct or isolate a startup problem in order to successfully start the program.  Some functionality may be disabled in this mode.\n\nDo you want to start PowerPoint in safe mode?"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:msimtf:DllGetClassObject ({c1ee01f2-b3b6-4a6a-9ddd-e988c088ec82} {00000001-0000-0000-c000-000000000046} 0x3287f4)
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {c1ee01f2-b3b6-4a6a-9ddd-e988c088ec82} could be created for context 0x1
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:win:EnumDisplayDevicesW ((null),0,0x32a004,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10078 0x00000000
fixme:mscoree:GetRequestedRuntimeInfo ((null), L"v2.0.0", (null), 0x00000000, 0x00000051, (nil), 0x00000000, (nil), 0x32a674, 0x0000001e, 0x32a66c) stub
fixme:mscoree:GetCORVersion (0x32a674, 30, 0x32a66c): semi-stub!
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Sessions"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0002,0x0000,0x00001b5b,(nil),0x0004,0x00000000,0x32a554,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:msvcr90:__clean_type_info_names_internal (0x3be8a128) stub
fixme:msvcr90:__clean_type_info_names_internal (0x334d0b14) stub
fixme:msvcr90:__clean_type_info_names_internal (0x3083010c) stub
fixme:msvcr90:__clean_type_info_names_internal (0x3b2cbf50) stub
```

Terminal Output for Excel

```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:msvcrt:_controlfp_s ((nil) 65536 196608) semi-stub
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:thread:SetThreadIdealProcessor (0xb0): stub
fixme:thread:SetThreadIdealProcessor (0xb8): stub
fixme:msimtf:DllGetClassObject ({c1ee01f2-b3b6-4a6a-9ddd-e988c088ec82} {00000001-0000-0000-c000-000000000046} 0x32ddc0)
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {c1ee01f2-b3b6-4a6a-9ddd-e988c088ec82} could be created for context 0x1
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:win:EnumDisplayDevicesW ((null),0,0x32d60c,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10078 0x00000000
fixme:mscoree:GetRequestedRuntimeInfo ((null), L"v2.0.0", (null), 0x00000000, 0x00000051, (nil), 0x00000000, (nil), 0x32dc7c, 0x0000001e, 0x32dc74) stub
fixme:mscoree:GetCORVersion (0x32dc7c, 30, 0x32dc74): semi-stub!
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x1005c 0x00000000
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Sessions"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00001b58,(nil),0x0006,0x00000000,0x32ed14,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x10078
```

Word

```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:msvcrt:_controlfp_s ((nil) 65536 196608) semi-stub
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:mscoree:GetRequestedRuntimeInfo ((null), L"v2.0.0", (null), 0x00000000, 0x00000051, (nil), 0x00000000, (nil), 0x32eefc, 0x0000001e, 0x32eef4) stub
fixme:mscoree:GetCORVersion (0x32eefc, 30, 0x32eef4): semi-stub!
fixme:bitblt:client_side_dib_copy potential optimization: client-side color-index mode DIB copy
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Microsoft Office\\Office12\\msproof6.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Microsoft Office\\Office12\\msproof6.dll") not found
fixme:setupapi:SetupDiOpenDeviceInterfaceW 0x1c4ab0 L"winealsa: default" 00000000 0x32e2a8
fixme:advapi:GetCurrentHwProfileW (0x32e1ec)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Microsoft Office\\Office12\\msproof6.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Microsoft Office\\Office12\\msproof6.dll") not found
fixme:time:GetCalendarInfoW Unimplemented caltype 1

```

Does this mean I am missing the MS C++ Library or something equivalent?

---

### Post by Jechem on 2011-04-16
While installing Office did you remember it downloading visual basic 2005 or 2008? it should have been downloaded automatically or the download and installation did not finish. I think you should do the installation again. You can uninstall  MS Office through playonlinux or directly on wine then re-install again with playonlinux. It should get the right dependencies before continuing to install Office 2007.

---

### Post by phosphide on 2011-04-17
> **Jechem said:**
> While installing Office did you remember it downloading visual basic 2005 or 2008? it should have been downloaded automatically or the download and installation did not finish. I think you should do the installation again. You can uninstall  MS Office through playonlinux or directly on wine then re-install again with playonlinux. It should get the right dependencies before continuing to install Office 2007.

Yes, I remember it installing the libraries. It took about 2-3 minutes to install all the packages. The only thing I fear is loosing my product key. I went through the verification process and online registration. I'm not entirely worried as I have another pc that works just fine, I just don't want to install again and then register and then Microsoft give me a bunch of bs that the product key doesn't work.

Though, after recently updating Wine, the only issue I am running into is that it says,"Microsoft Office Excel has not been installed for the current user. Please run setup to install the application."

---

### Post by Jechem on 2011-04-17
> **phosphide said:**
> 
Though, after recently updating Wine, the only issue I am running into is that it says,"Microsoft Office Excel has not been installed for the current user. Please run setup to install the application."

If you continue with it, it will just reconfigure wine and Excel. It'll be fine. As with the product key, I haven't encountered any problems with using the product key again and again because of a re-install. It's ok as long as it's on the same computer.

---

### Post by phosphide on 2011-04-17
> **Jechem said:**
> If you continue with it, it will just reconfigure wine and Excel. It'll be fine. As with the product key, I haven't encountered any problems with using the product key again and again because of a re-install. It's ok as long as it's on the same computer.

Ah, I thought if you registered online that essentially used the product key. Cool, let's see what happens.

---

### Post by phosphide on 2011-04-18
So, reinstalled and everything is working great. Except for some reason the gui to let me enter my product key doesn't seem to work. It won't let me click in the area and type in the product key. This is fine for me, at least for now.

---

### Post by Jechem on 2011-04-18
Is it when you click Options> Resources> Activate Microsoft Office? What does it say when you check About Microsoft Office? Is it in trial? Sometimes the gui just needs a restart to work properly. it should have worked after the simulated restart. Well, if you can use it and no error comes up about product activation then it should be fine.

---

### Post by phosphide on 2011-04-18
> **Jechem said:**
> Is it when you click Options> Resources> Activate Microsoft Office? What does it say when you check About Microsoft Office? Is it in trial? Sometimes the gui just needs a restart to work properly. it should have worked after the simulated restart. Well, if you can use it and no error comes up about product activation then it should be fine.

Nope. For some reason it won't let me enter the product key into the the 25 character text area. I can click the continue button and the information button, but the product key area doesn't work. It worked before. Weird errors are coming now. I've just about had it with this though. I don't mind using Open Office, I just prefer MS office.

And yes, it is in trial mode.

---

### Post by Jechem on 2011-04-18
Open Office is also good but sometimes the format can get screwed when opened in MS Office even if saved in .docx format. When you have more time you can purge playonlinux and reinstall again. I've got mine working properly after a few purges and reinstalls. Hope you get yours working properly in the future. Good luck.

BTW, I'm using 10.04 64bit with Office2007 32bit. Much more stable than my Windows7 + Office2010 Pro.

---

### Post by phosphide on 2011-04-18
> **Jechem said:**
> Open Office is also good but sometimes the format can get screwed when opened in MS Office even if saved in .docx format. When you have more time you can purge playonlinux and reinstall again. I've got mine working properly after a few purges and reinstalls. Hope you get yours working properly in the future. Good luck.
Yup. I recently ran into a huge issue with a school project. (The project even included how well Open Office was. Epic fail) This laptop is really just my have fun laptop, but I would have liked to have ms office on it for compatibility issue. Were you able to get Outlook or Access to work?

[quote=""]BTW, I'm using 10.04 64bit with Office2007 32bit. Much more stable than my Windows7 + Office2010 Pro.[/QUOTE]
I guess I'll just keep giving it a shot. See what happens.

---

### Post by Jechem on 2011-04-18
Sorry haven't used Outlook or Access. I have no plans of using it for the moment.

---

### Post by phosphide on 2011-04-18
> **Jechem said:**
> Sorry haven't used Outlook or Access. I have no plans of using it for the moment.

Eh, I was just curious. Now I'm running into problems trying to remove ms office.

sigh

Says it is missing the uninstall executer. How can you remove a problem from the terminal but in wine?

---

### Post by Jechem on 2011-04-18
If you don't have anything else using wine or playonlinux, you can uninstall it completely, MS Office will be uninstalled with it.

---

### Post by phosphide on 2011-04-18
> **Jechem said:**
> If you don't have anything else using wine or playonlinux, you can uninstall it completely, MS Office will be uninstalled with it.

When I uninstalled Wine, MS office remained behind.

---

### Post by whatswrongwu on 2011-04-18
4 hours later...got it to work..thnx for the posts which help tremendously! sudo apt-get purge playonlinux helped ! thank you..Mike Paget

---

### Post by Jechem on 2011-04-18
> **phosphide said:**
> When I uninstalled Wine, MS office remained behind.

Did you do sudo apt-get purge wine? It should have done the trick. You can try uninstalling it through playonlinux. Or you can try deleting it in /home/username/.Playonlinux/installed. Hopefully that works.

---

### Post by Jechem on 2011-04-18
> **whatswrongwu said:**
> 4 hours later...got it to work..thnx for the posts which help tremendously! sudo apt-get purge playonlinux helped ! thank you..Mike Paget

Glad that you got it working properly.:D

---

### Post by Mark Phelps on 2011-04-18
> **phosphide said:**
>  ...Were you able to get Outlook or Access to work?

Sorry to tell you, but you're NOT going to get those to work.  Access and Outlook continue to be the two main Office components that will not work.

---

