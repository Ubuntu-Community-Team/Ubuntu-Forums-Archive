---
title: "Problems installing/running Alice 2.0 in Ubuntu 10.10"
date: 2011-06-21
forum: General Help
---

### Post by marshall1001 on 2011-06-21
I'm having trouble getting Alice 2.0 to run on my Ubuntu 10.10 machine. I extract the tarball to /opt as per usual and change ownership of the folder to myself so that I can actually run it.

When moving into the folder in terminal I ./run-alice as I was told to in the README but it gets stuck. Here's the output:

```

matt@Bertha:/opt/Alice/Required$ ./run-alice
attempting to register mp3 capability... 
java.lang.reflect.InvocationTargetException
Registered succesfully
*sys-package-mgr*: processing new jar, '/opt/Alice/Required/gnu/getopt-1.0.7.jar'
*sys-package-mgr*: can't write cache file for '/opt/Alice/Required/gnu/getopt-1.0.7.jar'
*sys-package-mgr*: processing new jar, '/opt/Alice/Required/jython-2.1/jython.jar'
*sys-package-mgr*: can't write cache file for '/opt/Alice/Required/jython-2.1/jython.jar'
*sys-package-mgr*: processing new jar, '/opt/Alice/Required/lib/alice.jar'
*sys-package-mgr*: can't write cache file for '/opt/Alice/Required/lib/alice.jar'
*sys-package-mgr*: processing new jar, '/opt/Alice/Required/jogl/lib/jogl.jar'
*sys-package-mgr*: can't write cache file for '/opt/Alice/Required/jogl/lib/jogl.jar'
*sys-package-mgr*: processing new jar, '/opt/Alice/Required/xerces-2_6_2/resolver.jar'
*sys-package-mgr*: can't write cache file for '/opt/Alice/Required/xerces-2_6_2/resolver.jar'
*sys-package-mgr*: processing new jar, '/opt/Alice/Required/vecmath/lib/ext/vecmath.jar'
*sys-package-mgr*: can't write cache file for '/opt/Alice/Required/vecmath/lib/ext/vecmath.jar'
*sys-package-mgr*: processing new jar, '/opt/Alice/Required/xerces-2_6_2/xercesImpl.jar'
*sys-package-mgr*: can't write cache file for '/opt/Alice/Required/xerces-2_6_2/xercesImpl.jar'
*sys-package-mgr*: processing new jar, '/opt/Alice/Required/xerces-2_6_2/xml-apis.jar'
*sys-package-mgr*: can't write cache file for '/opt/Alice/Required/xerces-2_6_2/xml-apis.jar'
*sys-package-mgr*: processing new jar, '/opt/Alice/Required/xerces-2_6_2/xmlParserAPIs.jar'
*sys-package-mgr*: can't write cache file for '/opt/Alice/Required/xerces-2_6_2/xmlParserAPIs.jar'
*sys-package-mgr*: processing new jar, '/opt/Alice/Required/JMF-2.1.1e/lib/customizer.jar'
*sys-package-mgr*: can't write cache file for '/opt/Alice/Required/JMF-2.1.1e/lib/customizer.jar'
*sys-package-mgr*: processing new jar, '/opt/Alice/Required/JMF-2.1.1e/lib/jmf.jar'
*sys-package-mgr*: can't write cache file for '/opt/Alice/Required/JMF-2.1.1e/lib/jmf.jar'
*sys-package-mgr*: processing new jar, '/opt/Alice/Required/JMF-2.1.1e/lib/mediaplayer.jar'
*sys-package-mgr*: can't write cache file for '/opt/Alice/Required/JMF-2.1.1e/lib/mediaplayer.jar'
*sys-package-mgr*: processing new jar, '/opt/Alice/Required/JMF-2.1.1e/lib/multiplayer.jar'
*sys-package-mgr*: can't write cache file for '/opt/Alice/Required/JMF-2.1.1e/lib/multiplayer.jar'
*sys-package-mgr*: processing new jar, '/opt/Alice/Required/mp3/lib/ext/mp3plugin.jar'
*sys-package-mgr*: can't write cache file for '/opt/Alice/Required/mp3/lib/ext/mp3plugin.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/jce.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-6-openjdk/jre/lib/jce.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/charsets.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-6-openjdk/jre/lib/charsets.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/netx.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-6-openjdk/jre/lib/netx.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/plugin.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-6-openjdk/jre/lib/plugin.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/rhino.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-6-openjdk/jre/lib/rhino.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunpkcs11.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunpkcs11.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/ext/localedata.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-6-openjdk/jre/lib/ext/localedata.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/ext/dnsns.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-6-openjdk/jre/lib/ext/dnsns.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunjce_provider.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunjce_provider.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-6-openjdk/jre/lib/ext/gnome-java-bridge.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-6-openjdk/jre/lib/ext/gnome-java-bridge.jar'
*sys-package-mgr*: can't write index file
java.lang.IndexOutOfBoundsException: Invalid index
	at javax.swing.DefaultRowSorter.convertRowIndexToModel(DefaultRowSorter.java:514)
	at sun.swing.FilePane$SortableListModel.getElementAt(FilePane.java:657)
	at javax.swing.plaf.basic.BasicListUI.updateLayoutState(BasicListUI.java:1359)
	at javax.swing.plaf.basic.BasicListUI.maybeUpdateLayoutState(BasicListUI.java:1310)
	at javax.swing.plaf.basic.BasicListUI.getCellBounds(BasicListUI.java:951)
	at javax.swing.JList.getCellBounds(JList.java:1617)
	at javax.swing.JList.ensureIndexIsVisible(JList.java:1133)
	at sun.swing.FilePane.ensureIndexIsVisible(FilePane.java:1665)
	at sun.swing.FilePane.doDirectoryChanged(FilePane.java:1591)
	at sun.swing.FilePane.propertyChange(FilePane.java:1638)
	at java.beans.PropertyChangeSupport.fire(PropertyChangeSupport.java:298)
	at java.beans.PropertyChangeSupport.firePropertyChange(PropertyChangeSupport.java:291)
	at java.beans.PropertyChangeSupport.firePropertyChange(PropertyChangeSupport.java:229)
	at java.awt.Component.firePropertyChange(Component.java:8118)
	at javax.swing.JFileChooser.setCurrentDirectory(JFileChooser.java:585)
	at edu.cmu.cs.stage3.alice.authoringtool.AuthoringTool.worldsDirectoryChanged(AuthoringTool.java:478)
	at edu.cmu.cs.stage3.alice.authoringtool.AuthoringTool.dialogInit(AuthoringTool.java:631)
	at edu.cmu.cs.stage3.alice.authoringtool.AuthoringTool.<init>(AuthoringTool.java:413)
	at edu.cmu.cs.stage3.alice.authoringtool.JAlice.main(JAlice.java:131)
```

Any ideas?

---

### Post by stephen730 on 2011-06-22
Hmm, just taking a stab here, u got the super user priv? it looks like you can't write to the files here... It can't write the index or cache file which I'm assuming they need.

> *sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-6-openjdk/jre/lib/ext/gnome-java-bridge.jar' *sys-package-mgr*: can't write index file java.lang.IndexOutOfBoundsException: Invalid index

---

