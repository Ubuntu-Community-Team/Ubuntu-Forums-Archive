---
title: "Frostwire not running [error log included]"
date: 2009-06-29
forum: General Help
---

### Post by Addikit on 2009-06-29
Frostwire wont launch and I have the newest Java if I'm not mistaken. I'm still new to Ubuntu, so I'm not exactly sure how I would uninstall Frostwire and then reinstall Java to see if I can fix it. I assume I can uncheck Java in Synaptic though.

Any help would be appreciated =]



```

Error: Could not open jar file: FrostWire.jar
/usr/lib/frostwire/unpack200.py:10: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
lw-all.jar=87D1B8FCA6514EE54DFBD13F27EBE164
httpcore-nio-4.0-beta2.jar=8993AAFEFBC65D60F86C049024FA0310
messages.jar=26699708FDDBCE2EE64DB2A9B92AA3DE
httpcore-niossl-4.0-alpha7.jar=AD0A68739C093802B4FB0909B80724B6
FrostWire.jar=F6F602CFD22B2A2BB2B226B4B6E8A43B
jmdns.jar=F61E94168AE87EC532C8D0EAC646C602
jogg.jar=D7158C6BE281C7CFB0CD465D3E38B578
jflac.jar=9CB8B5FF827563223C0E2E1839B593AB
daap.jar=6580251125124101D643B770B0DE006D
forms.jar=BAF81035F5507958C7DA459591D9E51C
jaudiotagger.jar=E26869F145A5CDCFF36C0E199336DE0C
aopalliance.jar=531C1CCBF674C048960C6505FD70F927
jdic.jar=7EC4DCDE24979510DB429D01C17EB2DE
commons-codec-1.3.jar=198BBDF29A8EFD936629A08CF1AA47F0
log4j.jar=ADEEC7CAA0C5B3EF7461DB841DD3468C
foxtrot.jar=453729BA2BA2C9CA5B5FDD387D80BB28
jcraft.jar=B64B52EBB5FF8EB24921C24718E348AD
jython.jar=4F1007C908363C9B8B6CCCBF895B82EC
onion-common.jar=98DF1F561DFDDC49E84AC23A15623322
themes.jar=8B67B4A58FBC58F47929008B4B91C0C6
looks.jar=2104D8A3855074A625C23F00598EEA7B
junit.jar=1815E5900DAE3CD1153DFA0D5A7013DD
tritonus.jar=EC93636020CC420E8658627FA8F1F5EF
ProgressTabs.jar=5ED641ADC982C69036C5BD912043CB89
httpcore-4.0-beta2.jar=BB05452D6A2524B272B50E5DA126ED60
httpclient-4.0-alpha3.jar=5477E63678A68361CA332D067D74A7D0
vorbisspi.jar=5243091A899D4FDD3DF4658F1F35EC00
guice-1.0.jar=5ABC7FE2AD6FA03C32D1E066202FDD5F
gettext-commons.jar=9D0ADAE2891EA3EB2B993FBE44AEAA4F
jl.jar=B592FB0C7097E6AE090596CADF18923E
jdic_stub.jar=FB56DFA7979F98AA769E4E8691ABDDC5
mp3spi.jar=3EEDE9F242CB5E41309F06E26D5C10AB
onion-fec.jar=A81777A25CD126A82145CDEA9E90546F
commons-logging.jar=BD2F6D6660AEC075E19F49435F9A421E
icu4j.jar=0BAA17E78B089CB05DC0B7D46C3332FB
clink.jar=FB93F7BFE45E5624D434F73F546810A2
jorbis.jar=209490C77A48996D484BA28367EA922B

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_0]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO: :./lw-all.jar:./httpcore-nio-4.0-beta2.jar:./messages.jar:./httpcore-niossl-4.0-alpha7.jar:./FrostWire.jar:./jmdns.jar:./jogg.jar:./jflac.jar:./daap.jar:./forms.jar:./jaudiotagger.jar:./aopalliance.jar:./jdic.jar:./commons-codec-1.3.jar:./log4j.jar:./foxtrot.jar:./jcraft.jar:./jython.jar:./onion-common.jar:./themes.jar:./looks.jar:./junit.jar:./tritonus.jar:./ProgressTabs.jar:./httpcore-4.0-beta2.jar:./httpclient-4.0-alpha3.jar:./vorbisspi.jar:./guice-1.0.jar:./gettext-commons.jar:./jl.jar:./jdic_stub.jar:./mp3spi.jar:./onion-fec.jar:./commons-logging.jar:./icu4j.jar:./clink.jar:./jorbis.jar
Invalid or corrupt jarfile FrostWire.jar


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu7)
OpenJDK Server VM (build 14.0-b08, mixed mode)
```
Update: I tried this guide [https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire) and that didn't resolve it either, also I uninstalled Frostwire using 
```
sudo dpkg --remove frostwire
```then followed the guide, then reinstalled using the .deb package and it still didn't work, so I guess I should uninstall Froswire and reinstall Java?

---

### Post by balagosa on 2009-06-30
From what I can read on the error, you lack Frostwire.jar or it is **corrupted**. This is not an official fix but I am trying to help you.

Let's try this approach.

1) Download the TarBall file from Frostwire [website]("http://www.frostwire.com/download/?os=tarball&")
2) The default location for it to be saved would be the Desktop so we need to unpack it.
```
cd Desktop
tar xvzf frostwire-4.18.0.noarch.tar.gz
```
3) Let us copy Frostwire.jar from the newly created folder to your frostwire direcory in /usr/lib/frostwire
```
cd ~/frostwire-4.18.0.noarch
sudo cp -f FrostWire.jar /usr/lib/frostwire
```


The reason I am suggesting this because I also had an error upon running Frostwire from a fresh install. The installer given to me (without me having the freedom to choose) was a deb file. So I tried downloading the tarball file and copied everything inside that archive into the Frostwire folder. Worked perfectly for me.

---

### Post by Soul-Sing on 2009-06-30
> From what I can read on the error, you lack Frostwire.jar or it is corrupted. This is not an official fix but I am trying to help you.

I have seen these error before on this subforum, strange...
Mostly it is a sun java issue, which is not set as the [COLOR="Red"]default [/COLOR]java.

---

### Post by Addikit on 2009-06-30
> **balagosa said:**
> From what I can read on the error, you lack Frostwire.jar or it is **corrupted**. This is not an official fix but I am trying to help you.

Let's try this approach.

1) Download the TarBall file from Frostwire [website]("http://www.frostwire.com/download/?os=tarball&")
2) The default location for it to be saved would be the Desktop so we need to unpack it.
```
cd Desktop
tar xvzf frostwire-4.18.0.noarch.tar.gz
```3) Let us copy Frostwire.jar from the newly created folder to your frostwire direcory in /usr/lib/frostwire
```
cd ~/frostwire-4.18.0.noarch
sudo cp -f FrostWire.jar /usr/lib/frostwire
```
The reason I am suggesting this because I also had an error upon running Frostwire from a fresh install. The installer given to me (without me having the freedom to choose) was a deb file. So I tried downloading the tarball file and copied everything inside that archive into the Frostwire folder. Worked perfectly for me.


Okay, I just tried this method and this is what happened:

```

---@---Desktop:~$ frostwire
HOSTNAME IS ---Desktop
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_13]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO: :./lw-all.jar:./httpcore-nio-4.0-beta2.jar:./messages.jar:./httpcore-niossl-4.0-alpha7.jar:./FrostWire.jar:./jmdns.jar:./jogg.jar:./jflac.jar:./daap.jar:./forms.jar:./jaudiotagger.jar:./aopalliance.jar:./jdic.jar:./commons-codec-1.3.jar:./log4j.jar:./foxtrot.jar:./jcraft.jar:./jython.jar:./onion-common.jar:./themes.jar:./looks.jar:./junit.jar:./tritonus.jar:./ProgressTabs.jar:./httpcore-4.0-beta2.jar:./httpclient-4.0-alpha3.jar:./vorbisspi.jar:./guice-1.0.jar:./gettext-commons.jar:./jl.jar:./jdic_stub.jar:./mp3spi.jar:./onion-fec.jar:./commons-logging.jar:./icu4j.jar:./clink.jar:./jorbis.jar
com.limegroup.gnutella.gui.GUILoader$StartupFailedException: file [FrostWire.jar] has hash of [938013BA4B2364E888BD23456E4ADB60] instead of expected [9F3B820E6FDB18E9C912A0C2F5EF0A90]
    at com.limegroup.gnutella.gui.GUILoader.verifyHashes(GUILoader.java:315)
    at com.limegroup.gnutella.gui.GUILoader.sanityCheck(GUILoader.java:281)
    at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:57)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Error: FrostWire version 4.17
Java version 1.6.0_13 from Sun Microsystems Inc.
Linux v. 2.6.28-13-generic on i386
Free/total memory: 31962496/33030144

com.limegroup.gnutella.gui.GUILoader$StartupFailedException: file [FrostWire.jar] has hash of [938013BA4B2364E888BD23456E4ADB60] instead of expected [9F3B820E6FDB18E9C912A0C2F5EF0A90]
    at com.limegroup.gnutella.gui.GUILoader.verifyHashes(GUILoader.java:315)
    at com.limegroup.gnutella.gui.GUILoader.sanityCheck(GUILoader.java:281)
    at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:57)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at com.limegroup.gnutella.gui.Main.main(Main.java:44)

STARTUP ERROR!
```


I just recently discovered (prior to this) that if I do ```
sudo frostwire
``` I don't get that Frostwire.jar error, just the Java error.

---

### Post by hibliss on 2009-06-30
Try gtk-gnutella.

---

