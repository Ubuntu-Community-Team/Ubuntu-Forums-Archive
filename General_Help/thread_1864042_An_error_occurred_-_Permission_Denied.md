---
title: "An error occurred - Permission Denied"
date: 2011-10-18
forum: General Help
---

### Post by Dennis Primm on 2011-10-18
I downloaded Wubi and tried installing Ubuntu 11.10, but received the following message:
Ubuntu Error
An error occurred
Permission Denied
For more info, please see log file
C:\users\dennis\appdata\local\temp\wubi-11.10-rev245.log

I received this error message two times (I retried installing it after the first time it failed with the error message).  I have really screwed up my system!!!  I looked at the log file, and it is HUGE (142kB), but couldn't make out what I was supposed to do, so I'm asking for your help on this one.  I tried to upload the file, but it's too large as it said it is an invalid file.  I can send you the log file if you need it, but I'll need your help in telling me where/how to send it.

Also, I then made the mistake of formatting the drive (E:\) that Ubuntu was installed on and now I have a menu entry (I guess in Grub2) when I boot up for Ubuntu that doesn't exist.  Can you tell me how to clear that or can I install Ubuntu from a CD and then everything will be AOK?

I've done this installation many times before, but have never had this happen to me.

Can you please tell me how to fix this?  I really need your help.

Sincerely,

Dennis Primm

---

### Post by bcbc on 2011-10-18
You can just copy the bottom bit of the log. Post it between the [code] tags (click on # above)

You need to manually uninstall the bits of ubuntu that remain: https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F

If you install directly to the partition formerly known as D: and install the grub bootloader, then yes that should work. But it's best to boot from the CD and select "Try it" first to make sure 11.10 runs okay before installing. 

(And then be careful if you format the partition again, you need to make sure you don't orphan the grub2 bootloader or windows won't boot.)

---

### Post by Dennis Primm on 2011-10-19
I don't know what you mean by "Post it between the [code] tags (click on # above)". I'm overwhelmed. I could attach it via the Attach Files, but I don't know where you're referencing. 

I don't know how to perform the uninstall task you referenced.  I'm a newbie at this.  

I apologize...  Sincerely, Dennis

---

### Post by bcbc on 2011-10-19
When you're typing your reply, there is a [SIZE="3"]**#**[/SIZE] sign just above the input box. Clicking on it adds [CODE[SIZE="1"] [/SIZE]][/CODE] where you were typing. If you paste the log content between those it will format it nicely.

Usually Wubi will uninstall itself nicely, but I think you might have interfered with that by formatting the E: drive. In that case you have to manually delete the remaining bits. That's what that link showed how to do.

Did you install on Windows XP or Vista/7?

---

### Post by Dennis Primm on 2011-10-21
I installed it on Vista (32-bit).  I see what you mean by the # sign now, so I'm going to give it a try.  Here's the log file if this works...

```
10-18 08:21 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
10-18 08:21 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
10-18 08:21 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
10-18 08:21 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
10-18 08:21 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
10-18 08:21 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
10-18 08:21 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
10-18 08:21 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
10-18 08:21 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
10-18 08:21 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
10-18 08:21 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
10-18 08:21 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
10-18 08:21 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
10-18 08:21 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
10-18 08:21 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
10-18 08:21 INFO   root: Running the uninstaller...
10-18 08:21 INFO   CommonBackend: This is the uninstaller running
10-18 08:21 DEBUG  WindowsFrontend: __init__...
10-18 08:21 DEBUG  WindowsFrontend: on_init...
10-18 08:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dennis\AppData\Local\Temp\pyl274E.tmp\translations, languages=['en_US', 'en']
10-18 08:21 INFO   root: Received settings
10-18 08:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dennis\AppData\Local\Temp\pyl274E.tmp\translations, languages=['en_US', 'en']
10-18 08:21 DEBUG  TaskList: # Running tasklist...
10-18 08:21 DEBUG  TaskList: ## Running Remove bootloader entry...
10-18 08:21 DEBUG  WindowsBackend: Removing bcd entry {787b505f-f918-11e0-a42d-001bb9736718}
10-18 08:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
10-18 08:21 DEBUG  WindowsBackend: undo_bootini C:
10-18 08:21 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 313309.878906 mb free ntfs)
10-18 08:21 DEBUG  WindowsBackend: undo_bootini D:
10-18 08:21 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 19909.6953125 mb free ntfs)
10-18 08:21 DEBUG  WindowsBackend: undo_bootini E:
10-18 08:21 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 58915.1210938 mb free ntfs)
10-18 08:21 DEBUG  WindowsBackend: undo_bootini H:
10-18 08:21 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
10-18 08:21 DEBUG  WindowsBackend: undo_bootini I:
10-18 08:21 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
10-18 08:21 DEBUG  WindowsBackend: undo_bootini J:
10-18 08:21 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 0.0 mb free )
10-18 08:21 DEBUG  WindowsBackend: undo_bootini K:
10-18 08:21 DEBUG  WindowsBackend: undo_configsys Drive(K: removable 0.0 mb free )
10-18 08:21 DEBUG  WindowsBackend: undo_bootini L:
10-18 08:21 DEBUG  WindowsBackend: undo_configsys Drive(L: hd 279439.90625 mb free ntfs)
10-18 08:21 DEBUG  WindowsBackend: undo_bootini N:
10-18 08:21 DEBUG  WindowsBackend: undo_configsys Drive(N: hd 279438.90625 mb free ntfs)
10-18 08:21 DEBUG  WindowsBackend: undo_bootini O:
10-18 08:21 DEBUG  WindowsBackend: undo_configsys Drive(O: removable 0.0 mb free )
10-18 08:21 DEBUG  WindowsBackend: undo_bootini P:
10-18 08:21 DEBUG  WindowsBackend: undo_configsys Drive(P: hd 362728.316406 mb free ntfs)
10-18 08:21 DEBUG  TaskList: ## Finished Remove bootloader entry
10-18 08:21 DEBUG  TaskList: ## Running Remove target dir...
10-18 08:21 DEBUG  CommonBackend: Deleting E:\ubuntu
10-18 08:21 DEBUG  TaskList: ## Finished Remove target dir
10-18 08:21 DEBUG  TaskList: ## Running Remove registry key...
10-18 08:21 DEBUG  TaskList: ## Finished Remove registry key
10-18 08:21 DEBUG  TaskList: # Finished tasklist
10-18 08:21 INFO   root: Almost finished uninstalling
10-18 08:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dennis\AppData\Local\Temp\pyl274E.tmp\translations, languages=['en_US', 'en']
10-18 08:21 INFO   root: Finished uninstallation
10-18 08:21 DEBUG  root: application.quit
10-18 08:21 DEBUG  WindowsFrontend: frontend.quit
10-18 08:21 DEBUG  WindowsFrontend: frontend.on_quit
10-18 08:21 DEBUG  root: application.on_quit
10-18 08:21 INFO   root: sys.exit

```

Wow, looks like it worked.  Thank you very much!!!  If you need more of the log file, just let me know.  

To tell you the truth, I followed that link on how to manually uninstall bits of Wubi, and I've come to the realization that I'm pretty stupid. HA! HA! I'll look at it again, but I'm getting to the point that I'm about ready to install Vista all over again just to get back to the starting point.  I've got Macrium Reflect and have cloned my C: drive, but cannot figure out how to get the P: drive (the C: clone) to restore.  What a dummy huh?  Thank you for all your help.  I'll try to get rid of the other bits of Wubi and I'll let you know what happened.

---

### Post by Dennis Primm on 2011-10-21
I tried EasyBCD to delete the menu entries for Ubuntu and for Vista Recovery, but it didn't work.  I checked "Ubuntu" and clicked on the "Remove" button and it didn't work.  I'm using the copy/version I downloaded from CNET.  Do I need the paid version?  Any help for that?

Here's the EasyBCD bootloader information:
There are a total of 3 entries listed in the bootloader.

Default: Microsoft Windows Vista
Timeout: 10 seconds
EasyBCD Boot Device: C:\

Entry #1
Name: Microsoft Windows Vista
BCD ID: {current}
Drive: C:\
Bootloader Path: \Windows\system32\winload.exe

Entry #2
Name: Ubuntu
BCD ID: {787b505e-f918-11e0-a42d-001bb9736718}
Drive: E:\
Bootloader Path: \ubuntu\winboot\wubildr.mbr

Entry #3
Name: Windows Vista (TM) Home Premium (recovered) 
BCD ID: {787b5060-f918-11e0-a42d-001bb9736718}
Drive: P:\
Bootloader Path: \Windows\system32\winload.exe

Prior to using EasyBCD, I also looked for C:\ubuntu and C:\wubildr* to remove them, but they don't exist anymore.

I really appreciate your help bcbc!!!

---

