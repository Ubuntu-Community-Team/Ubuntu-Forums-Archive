---
title: "wine - strange error massage"
date: 2009-12-04
forum: General Help
---

### Post by Rob1937 on 2009-12-04
Hello 
I am runnung xubuntu 9.04  dual boot with win xp.
 I have installed wine from Synaptic Package Manager.
When I try to run any windows program I get the error message:

[/media/SEA_DISC/0-LINUX share/NetMeter_v112.exe]
  End-of-central-directory signature not found.  Either this file is not a zipfile, or it constitutes one disk of a multi-part archive.  In the latter case the central directory and zipfile comment will be found on the last disk(s) of this archive.
note:  /media/SEA_DISC/0-LINUX share/NetMeter_v112.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/SEA_DISC/0-LINUX share/NetMeter_v112.exe or
 /media/SEA_DISC/0-LINUX share/NetMeter_v112.exe.zip, and cannot find /media/SEA_DISC/0-LINUX share/NetMeter_v112.exe.ZIP, period.

I uninstalled and re-installed wine but this did not help.

Any advice would be much appreciated.

---

### Post by amingv on 2009-12-04
Are you sure you have wine installed? What is the output of
```
wine --version
```

If it's some message saying it's not installed or that the command is not found, then do

```
sudo aptitude install wine
```

If you do have wine installed, then it seems it's not set as the preferred application for opening *.exe files, and that the archive manager is actually the program trying to open them, you can fix that like this:

Right click on the .exe file you're trying to open, then click on properties.
Pick the "Open with" tab and make sure "Wine Windows Program Loader" is the one option that is marked.
If that option is not there, then click on "Add" and pick "Wine Windows Program Loader" from the list.

Please bear in mind these instructions are for Gnome and may be a little different in Xubuntu, but they'll push you in the right direction.
(Maybe a XFCE user can help me with specifics?)

If you do this correctly you should be able to run .exe files and, of course, if you have any inconvenience do not hesitate to ask.

---

