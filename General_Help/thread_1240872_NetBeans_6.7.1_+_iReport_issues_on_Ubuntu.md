---
title: "NetBeans 6.7.1 + iReport issues on Ubuntu"
date: 2009-08-15
forum: General Help
---

### Post by Coding Monkey on 2009-08-15
Hi all

I apologise if this is the wrong place to ask; but this is related to an application installed on Ubuntu, and I've found people on the forums to be very knowledgeable about a wide range of subjects. 

I installed NetBeans 6.7.1 and version 3.5.2 of the iReport plugin on Ubuntu 8.10. Whenever I try to open the report editor in NetBeans (by opening a .jrxml file), the project tree goes crazy (in terms of rendering) and I get the following exception. (Please forgive me, it's a bit big.)

```
java.lang.NoClassDefFoundError: Could not initialize class net.sf.jasperreports.swing.JRViewerController
   at com.jaspersoft.ireport.designer.JrxmlPreviewView.<init>(JrxmlPreviewView.java:48)
   at com.jaspersoft.ireport.designer.JrxmlEditorSupport.<init>(JrxmlEditorSupport.java:104)
   at com.jaspersoft.ireport.designer.JrxmlEditorSupport.create(JrxmlEditorSupport.java:116)
   at com.jaspersoft.ireport.JrxmlDataObject.<init>(JrxmlDataObject.java:28)
   at com.jaspersoft.ireport.JrxmlDataLoader.createMultiObject(JrxmlDataLoader.java:31)
   at org.openide.loaders.MultiFileLoader.handleFindDataObject(MultiFileLoader.java:141)
   at org.openide.loaders.DataObjectPool.handleFindDataObject(DataObjectPool.java:158)
   at org.openide.loaders.DataLoader.findDataObject(DataLoader.java:404)
   at org.openide.loaders.DataLoader.findDataObject(DataLoader.java:377)
   at org.openide.loaders.DataLoaderPool.findDataObject(DataLoaderPool.java:531)
   at org.openide.loaders.DataLoaderPool.findDataObject(DataLoaderPool.java:489)
   at org.openide.loaders.DataObject.find(DataObject.java:496)
   at org.openide.loaders.FolderChildren.createNodes(FolderChildren.java:199)
   at org.openide.loaders.FolderChildren.createNodes(FolderChildren.java:66)
   at org.openide.nodes.Children$Keys$KE.nodes(Children.java:1610)
   at org.openide.nodes.EntrySupport$Lazy$EntryInfo.getNode(EntrySupport.java:1553)
   at org.openide.nodes.EntrySupport$Lazy$EntryInfo.getNode(EntrySupport.java:1519)
   at org.openide.nodes.EntrySupport$Lazy.getNode(EntrySupport.java:1473)
   at org.openide.nodes.FilterNode$Children$LazySupport$FilterNodeEntry.nodes(FilterNode.java:1862)
   at org.openide.nodes.EntrySupport$Lazy$EntryInfo.getNode(EntrySupport.java:1553)
   at org.openide.nodes.EntrySupport$Lazy$EntryInfo.getNode(EntrySupport.java:1519)
   at org.openide.nodes.EntrySupport$Lazy.getNode(EntrySupport.java:1473)
   at org.openide.nodes.FilterNode$Children$LazySupport$FilterNodeEntry.nodes(FilterNode.java:1862)
   at org.openide.nodes.EntrySupport$Lazy$EntryInfo.getNode(EntrySupport.java:1553)
   at org.openide.nodes.EntrySupport$Lazy$EntryInfo.getNode(EntrySupport.java:1519)
   at org.openide.nodes.EntrySupport$Lazy.getNodes(EntrySupport.java:1174)
   at org.openide.nodes.Children.getNodes(Children.java:441)
   at org.openide.explorer.view.VisualizerNode.getChildren(VisualizerNode.java:260)
   at org.openide.explorer.view.VisualizerNode.getChildren(VisualizerNode.java:245)
   at org.openide.explorer.view.VisualizerNode.getChildCount(VisualizerNode.java:322)
   at javax.swing.tree.DefaultTreeModel.getChildCount(DefaultTreeModel.java:168)
   at javax.swing.tree.FixedHeightLayoutCache$FHTreeStateNode.expand(FixedHeightLayoutCache.java:1135)
   at javax.swing.tree.FixedHeightLayoutCache.ensurePathIsExpanded(FixedHeightLayoutCache.java:645)
   at javax.swing.tree.FixedHeightLayoutCache.setExpandedState(FixedHeightLayoutCache.java:282)
   at javax.swing.plaf.basic.BasicTreeUI.updateExpandedDescendants(BasicTreeUI.java:1648)
   at javax.swing.plaf.basic.BasicTreeUI$Handler.treeExpanded(BasicTreeUI.java:3721)
   at javax.swing.JTree.fireTreeExpanded(JTree.java:2659)
   at javax.swing.JTree.setExpandedState(JTree.java:3430)
   at javax.swing.JTree.expandPath(JTree.java:2166)
   at javax.swing.plaf.basic.BasicTreeUI.toggleExpandState(BasicTreeUI.java:2209)
   at javax.swing.plaf.basic.BasicTreeUI.handleExpandControlClick(BasicTreeUI.java:2196)
   at javax.swing.plaf.basic.BasicTreeUI.checkForClickInExpandControl(BasicTreeUI.java:2154)
   at javax.swing.plaf.basic.BasicTreeUI$Handler.handleSelection(BasicTreeUI.java:3516)
   at javax.swing.plaf.basic.BasicTreeUI$Handler.mousePressedDND(BasicTreeUI.java:3502)
   at javax.swing.plaf.basic.BasicTreeUI$Handler.mousePressed(BasicTreeUI.java:3461)
   at java.awt.AWTEventMulticaster.mousePressed(AWTEventMulticaster.java:262)
   at java.awt.AWTEventMulticaster.mousePressed(AWTEventMulticaster.java:262)
   at java.awt.AWTEventMulticaster.mousePressed(AWTEventMulticaster.java:262)
   at java.awt.AWTEventMulticaster.mousePressed(AWTEventMulticaster.java:262)
   at java.awt.AWTEventMulticaster.mousePressed(AWTEventMulticaster.java:262)
   at java.awt.AWTEventMulticaster.mousePressed(AWTEventMulticaster.java:262)
   at java.awt.Component.processMouseEvent(Component.java:6131)
   at javax.swing.JComponent.processMouseEvent(JComponent.java:3265)
   at java.awt.Component.processEvent(Component.java:5899)
   at java.awt.Container.processEvent(Container.java:2023)
   at java.awt.Component.dispatchEventImpl(Component.java:4501)
   at java.awt.Container.dispatchEventImpl(Container.java:2081)
   at java.awt.Component.dispatchEvent(Component.java:4331)
   at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4301)
   at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3962)
   at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3895)
   at java.awt.Container.dispatchEventImpl(Container.java:2067)
   at java.awt.Window.dispatchEventImpl(Window.java:2458)
   at java.awt.Component.dispatchEvent(Component.java:4331)
[catch] at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
   at org.netbeans.core.TimableEventQueue.dispatchEvent(TimableEventQueue.java:104)
   at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
   at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
   at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
   at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
   at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
   at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
```


I tried uninstalling and reinstalling NetBeans and the plugin, with no luck.

I did a bit of googling, but I couldn't find anything particularly useful; maybe I was just looking in the wrong places. I would really appreciate it if someone could help me to get this fixed. Thanks a lot.

Note:  I've also posted this on the NetBeans forums.  [http://forums.netbeans.org/viewtopic.php?t=16216]("http://forums.netbeans.org/viewtopic.php?t=16216")

---

### Post by Coding Monkey on 2009-08-16
Bump.

---

### Post by bangeko on 2009-12-16
Copy all .jar in iReport to usr/lib/jvm/java-6-sun/jre/lib/ext.

---

