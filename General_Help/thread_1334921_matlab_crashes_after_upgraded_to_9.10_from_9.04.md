---
title: "matlab crashes after upgraded to 9.10 from 9.04"
date: 2009-11-22
forum: General Help
---

### Post by shutian on 2009-11-22
Hello,
I upgraded ubuntu from 9.04 to 9.10. When I use matlab, it can start. But when I set path, it crashes.
do you possibly know how to solve the problem? thanks in advance.

An unexpected exception has been detected in native code outside the VM.
Unexpected Signal : 11 occurred at PC=0x3E44305
Function=XFreeFontSet+0x15
Library=/usr/lib/libX11.so.6

Current Java thread:
        at sun.awt.motif.X11InputMethod.disposeXIC(Native Method)
        at sun.awt.motif.X11InputMethod.disposeImpl(Unknown Source)
        - locked <0xacc54120> (a sun.awt.motif.X11InputMethod)
        at sun.awt.motif.X11InputMethod.dispose(Unknown Source)
        at sun.awt.im.InputContext.dispose(Unknown Source)
        at java.awt.Window$1DisposeAction.run(Unknown Source)
        - locked <0xacc563d8> (a java.lang.Object)
        at java.awt.Window.dispose(Unknown Source)
        at java.awt.Dialog.disposeImpl(Unknown Source)
        at java.awt.Dialog.dispose(Unknown Source)
        at javax.swing.JFileChooser.showDialog(Unknown Source)
        at com.mathworks.mwswing.dialog.MJFolderChooser.unixFolderBrowse(MJFolderChooser.java:222)
        at com.mathworks.mwswing.dialog.MJFolderChooser.browseForFolder(MJFolderChooser.java:159)
        - locked <0xb0f4c270> (a java.lang.Class)
        at com.mathworks.mlwidgets.path.PathBrowser$PathBrowserActionListener.actionPerformed(PathBrowser.java:358)
        at javax.swing.AbstractButton.fireActionPerformed(Unknown Source)
        at javax.swing.AbstractButton$ForwardActionEvents.actionPerformed(Unknown Source)
        at javax.swing.DefaultButtonModel.fireActionPerformed(Unknown Source)
        at javax.swing.DefaultButtonModel.setPressed(Unknown Source)
        at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(Unknown Source)
        at java.awt.AWTEventMulticaster.mouseReleased(Unknown Source)
        at java.awt.Component.processMouseEvent(Unknown Source)
        at java.awt.Component.processEvent(Unknown Source)
        at java.awt.Container.processEvent(Unknown Source)
        at java.awt.Component.dispatchEventImpl(Unknown Source)
        at java.awt.Container.dispatchEventImpl(Unknown Source)
        at java.awt.Component.dispatchEvent(Unknown Source)
        at java.awt.LightweightDispatcher.retargetMouseEvent(Unknown Source)
        at java.awt.LightweightDispatcher.processMouseEvent(Unknown Source)
        at java.awt.LightweightDispatcher.dispatchEvent(Unknown Source)
        at java.awt.Container.dispatchEventImpl(Unknown Source)
        at java.awt.Window.dispatchEventImpl(Unknown Source)
"java.log.1958" 428 lines, 34335 characters

---

