---
title: "how to completely remove wine to start over"
date: 2006-02-03
forum: General Help
---

### Post by psilo357 on 2006-02-03
i need to completely remove wine from my system, i cannot get it to work correct, and i think i may have installed it in multiple directories.  I used synaptic package manager to install and uninstall, but when i type find in my terminal, i get all these damn wine files, how do i rid myself of them?

./.wine
./.wine/dosdevices
./.wine/dosdevices/c:
./.wine/dosdevices/z:
./.wine/dosdevices/d:
./.wine/dosdevices/e:
./.wine/dosdevices/f:
./.wine/dosdevices/g:
./.wine/dosdevices/h:
./.wine/dosdevices/i:
./.wine/dosdevices/j:
./.wine/drive_c
./.wine/drive_c/windows
./.wine/drive_c/windows/command
./.wine/drive_c/windows/command/start.exe
./.wine/drive_c/windows/fonts
./.wine/drive_c/windows/inf
./.wine/drive_c/windows/inf/wine.inf
./.wine/drive_c/windows/system
./.wine/drive_c/windows/system32
./.wine/drive_c/windows/system32/drivers
./.wine/drive_c/windows/system32/wcmd.exe
./.wine/drive_c/windows/system32/control.exe
./.wine/drive_c/windows/system32/help.exe
./.wine/drive_c/windows/system32/msiexec.exe
./.wine/drive_c/windows/system32/notepad.exe
./.wine/drive_c/windows/system32/progman.exe
./.wine/drive_c/windows/system32/regsvr32.exe
./.wine/drive_c/windows/system32/winmine.exe
./.wine/drive_c/windows/system32/winver.exe
./.wine/drive_c/windows/temp
./.wine/drive_c/windows/temp/48e9_dvddecrypter.0.xpm
./.wine/drive_c/windows/notepad.exe
./.wine/drive_c/windows/regedit.exe
./.wine/drive_c/windows/rundll32.exe
./.wine/drive_c/windows/uninstall.exe
./.wine/drive_c/windows/winhelp.exe
./.wine/drive_c/windows/winhlp32.exe
./.wine/drive_c/windows/winebrowser.exe
./.wine/drive_c/windows/win.ini
./.wine/drive_c/windows/system.ini
./.wine/drive_c/windows/profiles
./.wine/drive_c/windows/profiles/randy
./.wine/drive_c/windows/profiles/randy/Local Settings
./.wine/drive_c/windows/profiles/randy/Local Settings/Temporary Internet Files
./.wine/drive_c/windows/profiles/randy/Local Settings/History
./.wine/drive_c/windows/profiles/randy/Local Settings/Application Data
./.wine/drive_c/windows/profiles/randy/Cookies
./.wine/drive_c/windows/profiles/randy/Start Menu
./.wine/drive_c/windows/profiles/randy/Start Menu/Programs
./.wine/drive_c/windows/profiles/randy/Start Menu/Programs/StartUp
./.wine/drive_c/windows/profiles/randy/Start Menu/Programs/DVD Decrypter
./.wine/drive_c/windows/profiles/randy/Start Menu/Programs/DVD Decrypter/Uninstall.lnk
./.wine/drive_c/windows/profiles/randy/Start Menu/Programs/DVD Decrypter/DVD Decrypter.lnk
./.wine/drive_c/windows/profiles/randy/Start Menu/Programs/DVD Decrypter/DVD Decrypter Read Me.lnk
./.wine/drive_c/windows/profiles/randy/Favorites
./.wine/drive_c/windows/profiles/randy/Application Data
./.wine/drive_c/windows/profiles/randy/Recent
./.wine/drive_c/windows/profiles/randy/SendTo
./.wine/drive_c/windows/profiles/randy/NetHood
./.wine/drive_c/windows/profiles/randy/Templates
./.wine/drive_c/windows/profiles/randy/PrintHood
./.wine/drive_c/windows/profiles/All Users
./.wine/drive_c/windows/profiles/All Users/Start Menu
./.wine/drive_c/windows/profiles/All Users/Start Menu/Programs
./.wine/drive_c/windows/profiles/All Users/Start Menu/Programs/StartUp
./.wine/drive_c/windows/profiles/All Users/Desktop
./.wine/drive_c/windows/profiles/All Users/Favorites
./.wine/drive_c/windows/profiles/All Users/Application Data
./.wine/drive_c/windows/profiles/All Users/Templates
./.wine/drive_c/windows/profiles/All Users/Documents
./.wine/drive_c/Program Files
./.wine/drive_c/Program Files/Common Files
./.wine/drive_c/Program Files/DVD Decrypter
./.wine/drive_c/Program Files/DVD Decrypter/DVDDecrypter.exe
./.wine/drive_c/Program Files/DVD Decrypter/ReadMe.txt
./.wine/drive_c/Program Files/DVD Decrypter/Sounds
./.wine/drive_c/Program Files/DVD Decrypter/Sounds/Success.wav
./.wine/drive_c/Program Files/DVD Decrypter/Sounds/Error.wav
./.wine/drive_c/Program Files/DVD Decrypter/uninstall.exe
./.wine/config
./.wine/system.reg
./.wine/userdef.reg
./.wine/user.reg
./.dvdshrinkrc
./instructions.odt
./DVD_VIDEO.log
./bewitched.log
./.windows-label



thanks for the help

peace

---

### Post by jdonat on 2006-02-04
just delete the /.wine directory . 

"rm -rf .wine"

the directory will be re-created when you re-install wine and run it for the first time. be aware that any applications you had installed with wine will be deleted as well.

---

### Post by kingsidy on 2006-02-04
first delete through synaptic. open up synapic search for wine and check on remove completely. then delete the .wine folder in your home directory just like jdonat said. in nautilus, press control + H in order to view hidden files and delete the .wine directory.

---

