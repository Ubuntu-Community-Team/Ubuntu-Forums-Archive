---
title: "Unable to launch .jnlp file"
date: 2010-01-15
forum: General Help
---

### Post by kcode on 2010-01-15
Hi,

I'm unable to launch .jnlp file. 
```

~/cpp$ javaws ../Desktop/ContestAppletProd.jnlp 
15 Jan, 2010 1:09:22 PM com.sun.corba.se.impl.ior.IORImpl getProfile
WARNING: "IOP00511201: (INV_OBJREF) IOR must have at least one IIOP profile"
org.omg.CORBA.INV_OBJREF:   vmcid: SUN  minor code: 1201  completed: No
        at com.sun.corba.se.impl.logging.IORSystemException.iorMustHaveIiopProfile(IORSystemException.java:473)
        at com.sun.corba.se.impl.logging.IORSystemException.iorMustHaveIiopProfile(IORSystemException.java:495)
        at com.sun.corba.se.impl.ior.IORImpl.getProfile(IORImpl.java:334)
        at com.sun.corba.se.impl.encoding.CDRInputStream_1_0.read_Object(CDRInputStream_1_0.java:787)
        at com.sun.corba.se.impl.encoding.CDRInputStream_1_0.read_Object(CDRInputStream_1_0.java:761)
        at com.sun.corba.se.impl.encoding.CDRInputStream.read_Object(CDRInputStream.java:231)
        at com.sun.corba.se.impl.resolver.INSURLOperationImpl.getIORFromString(INSURLOperationImpl.java:116)
        at com.sun.corba.se.impl.resolver.INSURLOperationImpl.operate(INSURLOperationImpl.java:126)
        at com.sun.corba.se.impl.orb.ORBImpl.string_to_object(ORBImpl.java:838)
        at org.GNOME.Accessibility.AccessUtil.getRegistryObject(AccessUtil.java:143)
        at org.GNOME.Accessibility.JavaBridge.registerApplication(JavaBridge.java:1058)
        at org.GNOME.Accessibility.JavaBridge.<init>(JavaBridge.java:341)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
        at java.lang.Class.newInstance0(Class.java:372)
        at java.lang.Class.newInstance(Class.java:325)
        at java.awt.Toolkit.loadAssistiveTechnologies(Toolkit.java:786)
        at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:874)
        at javax.swing.ImageIcon.<init>(ImageIcon.java:136)
        at javax.swing.ImageIcon.<init>(ImageIcon.java:155)
        at net.sourceforge.jnlp.runtime.JNLPRuntime.loadWindowIcon(JNLPRuntime.java:457)
        at net.sourceforge.jnlp.runtime.JNLPRuntime.getDefaultBaseDir(JNLPRuntime.java:256)
        at net.sourceforge.jnlp.runtime.Boot.getBaseDir(Boot.java:405)
        at net.sourceforge.jnlp.runtime.Boot.run(Boot.java:169)
        at java.security.AccessController.doPrivileged(Native Method)
        at net.sourceforge.jnlp.runtime.Boot.main(Boot.java:160)
net.sourceforge.nanoxml.XMLParseException: XML Parse Exception during parsing of the XML definition at line 4: Unexpected end of data reached
        at net.sourceforge.nanoxml.XMLElement.unexpectedEndOfData(XMLElement.java:1169)
        at net.sourceforge.nanoxml.XMLElement.readChar(XMLElement.java:940)
        at net.sourceforge.nanoxml.XMLElement.skipSpecialTag(XMLElement.java:878)
        at net.sourceforge.nanoxml.XMLElement.sanitizeInput(XMLElement.java:1293)
        at net.sourceforge.jnlp.Parser$1.run(Parser.java:959)
        at java.lang.Thread.run(Thread.java:636)
netx: Invalid XML document syntax.

```

Thanks

---

### Post by Mighty_Joe on 2010-01-15
[Second hit in Google]("http://jaqoup.wordpress.com/2009/06/23/topcoder-arena-launcher-in-ubuntu/"), the first being your own question.  It sounds like the problem is using OpenJDK rather than Sun Java.

---

### Post by kcode on 2010-01-17
Solution : Default java was ```
/usr/lib/jvm/java-6-openjdk/jre/bin/java
``` which had to be ```
/usr/lib/jvm/java-6-sun/jre/bin/java
``` which can be changed by ```
sudo update-alternatives --config java
```
Thanks @Mighty_Joe

---

