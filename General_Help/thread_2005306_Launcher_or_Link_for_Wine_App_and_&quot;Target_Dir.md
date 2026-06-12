---
title: "Launcher or Link for Wine App and &quot;Target Directory&quot;"
date: 2012-06-17
forum: General Help
---

### Post by DHag on 2012-06-17
I am running Ubuntu 12.04. I have Wine installed. All working very well.

I have a Windows application that maintains a configuration file named "EBL_WhatsUp.cfg." The application runs from the folder "/home/david/.wine/drive_c/EBL/." The executable name is "WhatsUp.exe."

".exe" files are automatically associated with Wine. When I open the executable directly in its folder, it runs with no problem.

When I create a new Desktop launcher, the command is 
"wine /home/david/.wine/drive_c/EBL/WhatsUp.exe."
Running from the Desktop launcher, the application displays the error "Can not open configuration file: EBL\EBL_WhatsUp.cfg."

I thought this was a good path, but it turns out that the application is looking for this config file in the Desktop folder, and the application does not have permissions to create the file on the Desktop.

I created a link to the executable, and it worked. I moved the link to the Desktop. Using the link from the Desktop, the application launched, and created "EBL_WhatsUp.cfg" on the Desktop. No error. However, I don't want this config file on the Desktop. I want it in the application's folder.

As a temporary workaround, I created a folder on the Desktop, then put the link in the folder. Now, the config file is created in that folder, but at least it's not on the Desktop directly.

In Windows, application shortcuts have a "target directory" setting, which solves this issue. Set this to the path where the executable is running, and that's where the executable will look for all its associated files. However, I can't find an equivalent setting in Ubuntu.

How can I set up a Desktop launcher for this application, or a link on the Desktop, so that the application will look for its config file in its own folder?

---

### Post by mc4man on 2012-06-17
You could try adding a Path= line to your launcher, may help, hurt or may have no effect. To edit open the launcher in a text editor like gedit (just drop launcher in gedit window

Based on the _orig.setup_ it could be something like 
```
Path=/home/david/.wine/dosdevices/c:/EBL
```

( you could also with the above try variations on the Exec=
```
Exec=wine C:\\\\EBL\\\\WhatsUp.exe
```
or (quotes are in the command
```
Exec=env WINEPREFIX="/home/david/.wine" wine C:\\\\EBL\\\\WhatsUp.exe
```

[http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html)

---

