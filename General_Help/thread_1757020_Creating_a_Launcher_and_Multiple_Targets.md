---
title: "Creating a Launcher and Multiple Targets"
date: 2011-05-13
forum: General Help
---

### Post by Rikeshar on 2011-05-13
Hello everyone, I'm having an issue creating a launcher. I'm trying to have it execute the command:

```
WINEPREFIX=/home/zach/.PlayOnLinux/wineprefix/EVE mumble-overlay wine explorer /desktop=EVE,1680x1050 "C:\Program Files\CCP\EVE\eve.exe"
```When I run this though, it tells me: 

```
Could not launch 'EVE Online'

Failed to execute child process "WINEPREFIX=/home/zach/.PlayOnLinux/wineprefix/EVE" (No such file or directory)
```If I add quotes to both end of the command I get the same thing except the child press is listed as:

```
"WINEPREFIX=/home/zach/.PlayOnLinux/wineprefix/EVE mumble-overlay wine explorer /desktop=EVE,1680x1050 C:ProgramFilesCCPEVEeve.exe"
```If I just run this in the terminal though, it loads up fine. Any ideas?

Also, if I want to set a launcher to launch more than one application at a time, how would I do that?

---

