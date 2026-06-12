---
title: "x11nvc eclipse fails to start"
date: 2010-03-05
forum: General Help
---

### Post by BatteryKing on 2010-03-05
Running Ubuntu Desktop 9.10 64-bit and Eclipse 3.5.2.

The specific problem I have is if I start Eclipse while sitting at the console (no x11vnc) it starts up fine.  However if I start / restart through x11vnc, eclipse fails with a out of heap space error.  Tweaking memory settings in eclipse.ini has no effect.

I have gone back and forth a couple of times on this now and this behaviour of eclipse failing to start while x11vnc is running seems to be consistent.

---

### Post by krunge on 2010-03-05
Could you paste in the full eclipse stacktrace?

---

### Post by BatteryKing on 2010-03-08
Here is what is in my workspace/.medadata/.log file:
!SESSION 2010-03-05 12:34:52.086 -----------------------------------------------
eclipse.buildId=
java.version=1.6.0_0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Framework arguments:  -product org.eclipse.epp.package.php.product
Command-line arguments:  -os linux -ws gtk -arch x86_64 -product org.eclipse.epp.package.php.product

!ENTRY com.adobe.ide.coldfusion.core 4 0 2010-03-05 12:34:56.429
!MESSAGE Problem loading version node  from dictionaryconfig.xml

!ENTRY com.adobe.ide.coldfusion.core 4 0 2010-03-05 12:34:56.498
!MESSAGE Problem loading version node  from dictionaryconfig.xml

!ENTRY org.eclipse.osgi 4 0 2010-03-05 12:34:58.647
!MESSAGE Application error
!STACK 1
java.lang.OutOfMemoryError: Java heap space
        at org.eclipse.ui.part.ResourceTransfer.nativeToJava(ResourceTransfer.java:162)
        at org.eclipse.swt.dnd.Clipboard.getContents(Clipboard.java:309)
        at org.eclipse.swt.dnd.Clipboard.getContents(Clipboard.java:241)
        at org.eclipse.ui.views.navigator.PasteAction$1.run(PasteAction.java:194)
        at org.eclipse.swt.widgets.Synchronizer.syncExec(Synchronizer.java:179)
        at org.eclipse.ui.internal.UISynchronizer.syncExec(UISynchronizer.java:150)
        at org.eclipse.swt.widgets.Display.syncExec(Display.java:4113)
        at org.eclipse.ui.views.navigator.PasteAction.updateSelection(PasteAction.java:189)
        at org.eclipse.ui.actions.BaseSelectionListenerAction.selectionChanged(BaseSelectionListenerAction.java:124)
        at org.eclipse.ui.views.navigator.RefactorActionGroup.updateActionBars(RefactorActionGroup.java:155)
        at org.eclipse.ui.views.navigator.MainActionGroup.updateActionBars(MainActionGroup.java:319)
        at org.eclipse.ui.views.navigator.ResourceNavigator.updateActionBars(ResourceNavigator.java:1412)
        at org.eclipse.ui.views.navigator.ResourceNavigator.createPartControl(ResourceNavigator.java:327)
        at org.eclipse.ui.internal.ViewReference.createPartHelper(ViewReference.java:367)
        at org.eclipse.ui.internal.ViewReference.createPart(ViewReference.java:226)
        at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:595)
        at org.eclipse.ui.internal.PartPane.setVisible(PartPane.java:313)
        at org.eclipse.ui.internal.ViewPane.setVisible(ViewPane.java:529)
        at org.eclipse.ui.internal.presentations.PresentablePart.setVisible(PresentablePart.java:180)
        at org.eclipse.ui.internal.presentations.util.PresentablePartFolder.select(PresentablePartFolder.java:270)
        at org.eclipse.ui.internal.presentations.util.LeftToRightTabOrder.select(LeftToRightTabOrder.java:65)
        at org.eclipse.ui.internal.presentations.util.TabbedStackPresentation.selectPart(TabbedStackPresentation.java:473)
        at org.eclipse.ui.internal.PartStack.refreshPresentationSelection(PartStack.java:1256)
        at org.eclipse.ui.internal.PartStack.createControl(PartStack.java:668)
        at org.eclipse.ui.internal.PartStack.createControl(PartStack.java:576)
        at org.eclipse.ui.internal.PartSashContainer.createControl(PartSashContainer.java:568)
        at org.eclipse.ui.internal.PerspectiveHelper.activate(PerspectiveHelper.java:272)
        at org.eclipse.ui.internal.Perspective.onActivate(Perspective.java:982)
        at org.eclipse.ui.internal.WorkbenchPage.onActivate(WorkbenchPage.java:2626)
        at org.eclipse.ui.internal.WorkbenchWindow$27.run(WorkbenchWindow.java:2965)
        at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:70)
        at org.eclipse.ui.internal.WorkbenchWindow.setActivePage(WorkbenchWindow.java:2946)

---

### Post by krunge on 2010-03-08
How much memory does, say, top or ps report x11vnc and eclipse are using just before this failure?

---

### Post by BatteryKing on 2010-03-08
x11vnc is using 31MB.
I actually got it to restart this last time around after getting more heap errors while doing x11vnc remoting and now it is showing immediately after starting
RES: 791m, SHR: 37m, VIRT: 2717m.
This is after I bumped up MaxPermSize to 1024m, Xms to 512m, and Xmx to 1024m in an attempt to get around this problem.  It seems in this state with all of this extra memory allocated, it finally starts granted there are no updates being applied or any other dialogues coming up while remoting.  (A dialogue box came up while remoting earlier today and caused another heap error.)  However when not remoting, non of this seems to be an issue.

---

### Post by krunge on 2010-03-08
So does eclipse use about 791MB of RES memory even when x11vnc is not running?

What is the total amount of RAM and swap on the machine?

---

### Post by BatteryKing on 2010-03-08
This is with x11vnc going.

This machine has 12 GBs of RAM and an additional 12 GBs of swap.  That should be enough, right?

---

### Post by krunge on 2010-03-08
> **BatteryKing said:**
> This is with x11vnc going.

And how much does eclipse use with x11vnc not going?

---

### Post by BatteryKing on 2010-03-08
I got it restarted without x11vnc and here are the stats for Eclipse:
RES: 788m, SHR: 35m, VIRT: 2771m.

---

### Post by krunge on 2010-03-08
Not exactly sure what to try next.

See if this makes a difference, add this to the x11vnc cmdline:
```
-noxdamage
```
Also, post your full x11vnc cmdline here.

---

### Post by BatteryKing on 2010-03-08
Now that you are looking into the problem, it wants to play nice either way with or without -xdamage.  I guess this problem is more transient than I originally thought.  Next time around if it happens with the noxdamage parameter I will make sure to restart x11vnc to see if this only happens after extended runs.  (All of the times I can remember this happening it happened after the x11vnc session had be going for over an hour and all of my tests here are within a minute or two of instantiating x11vnc.)

Well here is my current config file:
display :0
usepw
clear_mods
clear_keys
repeat
noxdamage

---

### Post by krunge on 2010-03-08
Another thing to watch is the memory usage of the X server.

---

### Post by BatteryKing on 2010-03-09
With the noxdamage option I left it on overnight and eclipse restarted successfully the this morning.

---

### Post by BatteryKing on 2010-03-11
So for two days I left x11vnc open with the noxdamage option off and the problem cropped up again today.  Unfortunately I first thought to restart x11vnc before I thought to get a memory reading in order to make sure it was x11vnc that was somehow interfering.  I do know the system never went into swap and it is running 64-bit Ubuntu 9.10 desktop.  However after the incident there is 2 GBs of unused memory (neither cache nor applications) so it is possible that something running either running in 32-bit mode or memory limited may have used up its entire memory space.

Would you like me to first see if this can be reproduced with noxdamage turned on or repeat the test with noxdamage disabled?

---

### Post by krunge on 2010-03-11
Maybe write a script that dumps 'ps wwaux' output to a logfile every 30 seconds (maybe add the output of the 'date' and 'free' commands as well.) Then run it in the mode that you feel has the best chance to reproduce the problem.

I noticed a problem some time ago with strange screen savers that they could induce a huge amount of DAMAGE rectangles on x11vnc's event queue.  This could get it to +250MB of memory usage (perhaps more the longer the screen saver runs.)  I am wondering if you are seeing something like this.

---

