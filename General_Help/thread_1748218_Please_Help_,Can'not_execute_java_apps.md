---
title: "Please Help ,Can'not execute java apps"
date: 2011-05-03
forum: General Help
---

### Post by khosro_68 on 2011-05-03
Hello brothers please help me.
i am using ubuntu 9.10 and i want to execute JAP ,
the java -version on my system replies this:
```
khosro@khosro-laptop:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.4.1

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```
i have installed jdk1.6.0_25 in "/usr/jdk1.6.0_25/"  directory.
my environment file is:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```
when i want to execute JAP with make command it says:
```
    //~ Static variables/initializers &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
                                                                   ^
./src/jarify/JarConstants.java:35: warning: unmappable character for encoding UTF8
    //~ Static variables/initializers &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
                                                                    ^
./src/jarify/JarConstants.java:35: warning: unmappable character for encoding UTF8
    //~ Static variables/initializers &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
                                                                     ^
./src/jarify/JarConstants.java:35: warning: unmappable character for encoding UTF8
    //~ Static variables/initializers &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
                                                                      ^
./src/jarify/JarConstants.java:35: warning: unmappable character for encoding UTF8
    //~ Static variables/initializers &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
                                                                       ^
./src/jarify/JarConstants.java:35: warning: unmappable character for encoding UTF8
    //~ Static variables/initializers &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
                                                                        ^
./src/jarify/JarConstants.java:35: warning: unmappable character for encoding UTF8
    //~ Static variables/initializers &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
                                                                         ^
./src/jarify/JarConstants.java:35: warning: unmappable character for encoding UTF8
    //~ Static variables/initializers &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
                                                                          ^
./src/jarify/JarConstants.java:35: warning: unmappable character for encoding UTF8
    //~ Static variables/initializers &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
./src/anon/infoservice/InfoServiceDBEntry.java:283: warning: [unchecked] unchecked call to addElement(E) as a member of the raw type java.util.Vector
            m_listenerInterfaces.addElement(new ListenerInterface(listenerInterfaceNode));
                                           ^
./src/anon/infoservice/InfoServiceDBEntry.java:388: warning: [unchecked] unchecked call to addElement(E) as a member of the raw type java.util.Vector
            m_listenerInterfaces.addElement(enumListeners.nextElement());
                                           ^
./src/anon/infoservice/InfoServiceDBEntry.java:567: warning: [unchecked] unchecked call to addElement(E) as a member of the raw type java.util.Vector
            r_listenerInterfacesList.addElement(listenerInterfacesEnumeration.nextElement());
                                               ^
./src/anon/infoservice/InfoServiceDBEntry.java:862: warning: [unchecked] unchecked call to addElement(E) as a member of the raw type java.util.Vector
                    mixCascades.addElement(new MixCascade(mixCascadeNode));
                                          ^
./src/anon/infoservice/InfoServiceDBEntry.java:904: warning: [unchecked] unchecked call to addElement(E) as a member of the raw type java.util.Vector
                paymentInstances.addElement(new PaymentInstanceDBEntry(paymentInstanceNode));
.
.
.                                           ^
Note: Some input files additionally use or override a deprecated API.
Note: Some input files additionally use unchecked or unsafe operations.
100 errors
100 warnings
make: *** [InfoService.jar] Error 1

```

and when i want to compile it manually it says:

```
import HTTPClient.NVPair;
                 ^
./anon/infoservice/InfoServiceDBEntry.java:39: package HTTPClient does not exist
import HTTPClient.HTTPConnection;
                 ^
./anon/infoservice/InfoServiceDBEntry.java:40: package HTTPClient does not exist
import HTTPClient.HTTPResponse;
                 ^
./anon/crypto/JAPCertificate.java:55: package org.bouncycastle.asn1 does not exist
import org.bouncycastle.asn1.ASN1Sequence;
                            ^
./anon/crypto/JAPCertificate.java:56: package org.bouncycastle.asn1 does not exist
import org.bouncycastle.asn1.ASN1OctetString;
                            ^
./anon/crypto/JAPCertificate.java:57: package org.bouncycastle.asn1 does not exist
.
.
.
./gui/dialog/JAPDialog.java:2728: warning: non-varargs call of varargs method with inexact argument type for last parameter;
cast to java.lang.Class for a varargs call
cast to java.lang.Class[] for a non-varargs call and to suppress this warning
                            classActiveEvent.getMethod("dispatch", null).invoke(event, null);
                                                                   ^
./gui/dialog/JAPDialog.java:2728: warning: non-varargs call of varargs method with inexact argument type for last parameter;
cast to java.lang.Object for a varargs call
cast to java.lang.Object[] for a non-varargs call and to suppress this warning
                            classActiveEvent.getMethod("dispatch", null).invoke(event, null);
                                                                                       ^
Note: Some input files use or override a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
Note: Some input files use unchecked or unsafe operations.
Note: Recompile with -Xlint:unchecked for details.
100 errors
61 warnings
```

i really dont know what can i do.
please help.

---

### Post by techunit on 2011-05-03
Did you mark the file as executable? Right click on the file click properties, and click the permissions tab. Check as executable as application.

Good Luck

---

### Post by imigueldiaz on 2011-05-03
could you post the result of:

echo $JAVA_HOME

which java

which javac

I believe that you aren't using Sun JDK...

Best

---

### Post by khosro_68 on 2011-05-03
hi bro.
i do it but get same output

---

### Post by khosro_68 on 2011-05-03
khosro@khosro-laptop:~$ echo $JAVA_HOME

khosro@khosro-laptop:~$

---

### Post by khosro_68 on 2011-05-03
Please Help!!!#-o

---

### Post by imigueldiaz on 2011-05-04
> **khosro_68 said:**
> Please Help!!!#-o

Sorry for the delay, I was out from computer until today

Which method have you used to install SUN JDK (synaptic package, by hand...)?

If you have installed synaptic package, try to use the command:

```

sudo update-java-alternative

```

To declare Sun JDK as default system JDK. Else you must declare on PATH the SUN JDK binaries path **before** than other JDK path (for java and javac to take preference).


Best

---

