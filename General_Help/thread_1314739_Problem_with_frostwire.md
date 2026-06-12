---
title: "Problem with frostwire"
date: 2009-11-04
forum: General Help
---

### Post by tkblackbelt on 2009-11-04
Hi im running ubuntu 9.10 and when I installed frostwire and java but when i try to run frostwire normally from the menu nothing happens and when i run it in terminal this happens

chuck@chuck-laptop:~$ frostwire
HOSTNAME IS chuck-laptop
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_15]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO: :./lw-all.jar:./forms.jar:./commons-logging.jar:./jdic.jar:./clink.jar:./jflac.jar:./jdic_stub.jar:./onion-fec.jar:./ProgressTabs.jar:./tritonus.jar:./gettext-commons.jar:./commons-codec-1.3.jar:./messages.jar:./onion-common.jar:./aopalliance.jar:./themes.jar:./icu4j.jar:./httpcore-niossl-4.0-alpha7.jar:./jl.jar:./jcraft.jar:./vorbisspi.jar:./foxtrot.jar:./junit.jar:./looks.jar:./jmdns.jar:./FrostWire.jar:./httpcore-4.0-beta2.jar:./log4j.jar:./jorbis.jar:./httpclient-4.0-alpha3.jar:./daap.jar:./jaudiotagger.jar:./mp3spi.jar:./guice-1.0.jar:./jogg.jar:./jython.jar:./httpcore-nio-4.0-beta2.jar
Invalid or corrupt jarfile FrostWire.jar


**************************************************  ****************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) 64-Bit Server VM (build 14.1-b02, mixed mode)

---

### Post by tkblackbelt on 2009-11-04
Bump

---

### Post by tkblackbelt on 2009-11-04
Ok i found a fix you just have to download the tar file and completly remove any other versions of frostwire and then extract the tar file and rename it to frostwire and copy it to usr lib and use the gnome main menu editor to run it.

---

