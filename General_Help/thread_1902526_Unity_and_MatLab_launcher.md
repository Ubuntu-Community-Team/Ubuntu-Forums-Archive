---
title: "Unity and MatLab launcher"
date: 2011-12-31
forum: General Help
---

### Post by layers on 2011-12-31
I have installed MatLab and it works fine, if I put this into terminal:```
'/usr/local/MATLAB/R2010b/bin/matlab'
```

So, I went ahead and made a .desktop for it, and it doesn't launch!```
[Desktop Entry]
Name=MatLab
Comment=Perform arithmetic, scientific or financial calculations
Exec=/usr/local/MATLAB/R2010b/bin/matlab 
Icon=/usr/local/MATLAB/R2010b/X11/icons/matlab.png
Terminal=false
Type=Application
StartupNotify=true
Categories=GNOME;GTK;Utility;Calculator

```What is the problem here, it is exactly the same. 

I tried adding the '...', but same thing.:?:

---

### Post by layers on 2011-12-31
like, whenever I click on launcher from Unity bar, the screen shows up, and then disappears. Is there a way to capture any feedback like that?

---

### Post by overdamped on 2012-03-06
You have to use the -desktop flag. See Mathwork's Documentation for start options for MATLAB:

[http://www.mathworks.com/help/techdoc/ref/matlabunix.html](http://www.mathworks.com/help/techdoc/ref/matlabunix.html)

Desktop entries conform to the freedesktop.org specification:

[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)

They may be placed in serveral locations (e.g. /usr/share/applications ~/.local/share/applications)

Here's what my matlab.desktop file looks like:

```

[Desktop Entry]
Version=1.0
Name=Matlab R2012a
GenericName=Matlab R2012a
Comment=Matlab R2012a: The Language of Technical Computing

Exec=sh /usr/local/MATLAB/R2012a/bin/matlab -desktop
Icon=/usr/share/icons/matlab_logo.png
StartupNotify=true
Terminal=false
Type=Application
Categories=Engineering
MimeType=text/x-matlab

```Note: If you use the mime type, be sure to update the desktop database of the folder you placed your .desktop file (e.g. if you placed it in /usr/share/applications).

```
sudo update-desktop-database /usr/share/applications
```

An nice icon can had here:
[http://en.wikipedia.org/wiki/File:Matlab_Logo.png](http://en.wikipedia.org/wiki/File:Matlab_Logo.png)

---

### Post by dabliss on 2012-03-22
After trying these various suggestions, make sure you restart your computer!  That made all the difference for me.

---

### Post by MvMan on 2012-06-11
> **overdamped said:**
> You have to use the -desktop flag. See Mathwork's Documentation for start options for MATLAB:

[http://www.mathworks.com/help/techdoc/ref/matlabunix.html](http://www.mathworks.com/help/techdoc/ref/matlabunix.html)

Desktop entries conform to the freedesktop.org specification:

[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)

They may be placed in serveral locations (e.g. /usr/share/applications ~/.local/share/applications)

Here's what my matlab.desktop file looks like:

```

[Desktop Entry]
Version=1.0
Name=Matlab R2012a
GenericName=Matlab R2012a
Comment=Matlab R2012a: The Language of Technical Computing

Exec=sh /usr/local/MATLAB/R2012a/bin/matlab -desktop
Icon=/usr/share/icons/matlab_logo.png
StartupNotify=true
Terminal=false
Type=Application
Categories=Engineering
MimeType=text/x-matlab

```Note: If you use the mime type, be sure to update the desktop database of the folder you placed your .desktop file (e.g. if you placed it in /usr/share/applications).

```
sudo update-desktop-database /usr/share/applications
```

An nice icon can had here:
[http://en.wikipedia.org/wiki/File:Matlab_Logo.png](http://en.wikipedia.org/wiki/File:Matlab_Logo.png)

Thanks this is the right way, but how can i give the permission to my matlab? because it can't write the files:

> 
Warning: Unable to create com.mathworks.mde.explorer.Explorer, for details see
 /home/mvman/MATLABDesktopCreateError.log
Exception in thread "AWT-EventQueue-0" java.lang.RuntimeException: com.mathworks.services.settings.SettingValidationException: IMsgIDException for "matlab.desktop.currentfolder.lastfolder.GroupColumn": The multipleSet operation on node (or key), Multiple Keys, failed because you do not have write permission on level user of the Settings file.
	at com.mathworks.mlwidgets.explorer.model.table.ExplorerTableConfigurationSerializer.saveGroupMode(ExplorerTableConfigurationSerializer.java:91)
	at com.mathworks.mlwidgets.explorer.model.table.ExplorerTableConfigurationSerializer.save(ExplorerTableConfigurationSerializer.java:65)
	at com.mathworks.widgets.grouptable.GroupingTableConfiguration$1.propertyChange(GroupingTableConfiguration.java:157)
	at java.beans.PropertyChangeSupport.firePropertyChange(Unknown Source)
	at java.beans.PropertyChangeSupport.firePropertyChange(Unknown Source)
	at com.mathworks.widgets.grouptable.GroupingTableConfiguration$4$1.run(GroupingTableConfiguration.java:995)
	at java.awt.event.InvocationEvent.dispatch(Unknown Source)
	at java.awt.EventQueue.dispatchEvent(Unknown Source)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(Unknown Source)
	at java.awt.EventDispatchThread.pumpEventsForFilter(Unknown Source)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(Unknown Source)
	at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
	at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
	at java.awt.EventDispatchThread.run(Unknown Source)
Caused by: com.mathworks.services.settings.SettingValidationException: IMsgIDException for "matlab.desktop.currentfolder.lastfolder.GroupColumn": The multipleSet operation on node (or key), Multiple Keys, failed because you do not have write permission on level user of the Settings file.
	at com.mathworks.services.settings.Setting.nativeSet(Native Method)
	at com.mathworks.services.settings.Setting.set(Setting.java:887)
	at com.mathworks.services.settings.Setting.set(Setting.java:745)
	at com.mathworks.services.settings.Setting.set(Setting.java:687)
	at com.mathworks.mlwidgets.explorer.model.table.ExplorerTableConfigurationSerializer.saveGroupMode(ExplorerTableConfigurationSerializer.java:88)
	... 13 more
The desktop configuration was not saved successfully


here is also the log file:

```

java.io.FileNotFoundException: /home/mvman/.matlab/R2012a/MATLABDesktop.xml (Permission denied)
	at java.io.FileOutputStream.open(Native Method)
	at java.io.FileOutputStream.<init>(Unknown Source)
	at java.io.FileOutputStream.<init>(Unknown Source)
	at com.mathworks.widgets.desk.Desktop$38.call(Desktop.java:3698)
	at com.mathworks.widgets.desk.Desktop$38.call(Desktop.java:3689)
	at com.mathworks.widgets.desk.Desktop.deferredCall(Desktop.java:7381)
	at com.mathworks.widgets.desk.Desktop.saveLayout(Desktop.java:3689)
	at com.mathworks.widgets.desk.Desktop.close(Desktop.java:4258)
	at com.mathworks.widgets.desk.Desktop$DeferredCloser.run(Desktop.java:4340)
	at com.mathworks.mwswing.SynchronousInvokeUtility$SynchronousEventAdapter.executeOnSwingThread(SynchronousInvokeUtility.java:94)
	at com.mathworks.mwswing.SynchronousInvokeUtility$SynchronousEvent.run(SynchronousInvokeUtility.java:112)
	at com.mathworks.jmi.AWTUtilities$Invoker$5.runWithOutput(AWTUtilities.java:525)
	at com.mathworks.jmi.AWTUtilities$Invoker$2.watchedRun(AWTUtilities.java:441)
	at com.mathworks.jmi.AWTUtilities$WatchedRunnable.run(AWTUtilities.java:373)
	at java.awt.event.InvocationEvent.dispatch(Unknown Source)
	at java.awt.EventQueue.dispatchEvent(Unknown Source)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(Unknown Source)
	at java.awt.EventDispatchThread.pumpEventsForFilter(Unknown Source)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(Unknown Source)
	at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
	at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
	at java.awt.EventDispatchThread.run(Unknown Source)

```




[B][COLOR="Red"]P.S:
I solve it by giving the permission to the ~/.matlab. it solved.
Thanks[/COLOR][/B]

---

### Post by vinothgm on 2012-09-12
> **MvMan said:**
> Thanks this is the right way, but how can i give the permission to my matlab? because it can't write the files:



here is also the log file:

```

java.io.FileNotFoundException: /home/mvman/.matlab/R2012a/MATLABDesktop.xml (Permission denied)
    at java.io.FileOutputStream.open(Native Method)
    at java.io.FileOutputStream.<init>(Unknown Source)
    at java.io.FileOutputStream.<init>(Unknown Source)
    at com.mathworks.widgets.desk.Desktop$38.call(Desktop.java:3698)
    at com.mathworks.widgets.desk.Desktop$38.call(Desktop.java:3689)
    at com.mathworks.widgets.desk.Desktop.deferredCall(Desktop.java:7381)
    at com.mathworks.widgets.desk.Desktop.saveLayout(Desktop.java:3689)
    at com.mathworks.widgets.desk.Desktop.close(Desktop.java:4258)
    at com.mathworks.widgets.desk.Desktop$DeferredCloser.run(Desktop.java:4340)
    at com.mathworks.mwswing.SynchronousInvokeUtility$SynchronousEventAdapter.executeOnSwingThread(SynchronousInvokeUtility.java:94)
    at com.mathworks.mwswing.SynchronousInvokeUtility$SynchronousEvent.run(SynchronousInvokeUtility.java:112)
    at com.mathworks.jmi.AWTUtilities$Invoker$5.runWithOutput(AWTUtilities.java:525)
    at com.mathworks.jmi.AWTUtilities$Invoker$2.watchedRun(AWTUtilities.java:441)
    at com.mathworks.jmi.AWTUtilities$WatchedRunnable.run(AWTUtilities.java:373)
    at java.awt.event.InvocationEvent.dispatch(Unknown Source)
    at java.awt.EventQueue.dispatchEvent(Unknown Source)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(Unknown Source)
    at java.awt.EventDispatchThread.pumpEventsForFilter(Unknown Source)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(Unknown Source)
    at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
    at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
    at java.awt.EventDispatchThread.run(Unknown Source)

```[B][COLOR=Red]P.S:
I solve it by giving the permission to the ~/.matlab. it solved.
Thanks[/COLOR][/B]

[COLOR=DarkGreen][B]Since matlab is installed as root user (sudo)  we have to add with root group
sudo usermod -g root username
sudo chmod g+rwx .matlab/[/B][/COLOR]

---

