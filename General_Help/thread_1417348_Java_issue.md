---
title: "Java issue"
date: 2010-02-27
forum: General Help
---

### Post by gabrielcik on 2010-02-27
Ciao!

Every time i load this java application:
[http://www.life.com.ua/index.php?area=mylife&lng=en&page=3-500](http://www.life.com.ua/index.php?area=mylife&lng=en&page=3-500)

I get this error:

"Found unsigned entry in resource"

This application works without problem in windows but give the same error also in leopard...

It is a voip application released by an Ukrainian provider for to call any subscriber through the net for free for a limited number of hours/month.

Can you pls say me in what way i can make java ignore this problem?
To say java i know it is unsigned, but i don't care :KS

(one of my friend was able to bypass this problem, but he is using fedora and in ubuntu i was not able to do the same)

Thank you

---

### Post by gabrielcik on 2010-03-03
Nobody know how to solve this problem?

This is the message i get:

Launch file

<?xml version="1.0" encoding="UTF-8"?>
<jnlp spec="1.0+" codebase="http://www.life.com.ua/freeworld/webstart">
    <information>
        <title>Free World</title>
        <vendor>Please Wait ...</vendor>
        <homepage href="http://www.life.com.ua/freeworld/webstart" />
        <description>A Java Audio SIP Softphone</description>
        <icon href='images/icon.gif'/>
        <icon kind='splash' href='images/splash.jpg'/>
    </information>
    <security>
        <all-permissions/>
    </security>
    <resources>
        <j2se version="1.4+" java-vm-args="-Xms32m -Xmx64m" href="http://java.sun.com/products/autodl/j2se"/>
        <jar href="argela.jar" />
        <jar href="argela-cgw.jar" />
        <jar href="argela-cgw-common.jar" />
        <jar href="argela-cgw-plugins.jar" />
        <jar href="argela-cgw-gui.jar" />
        <jar href="argela-cgw-media.jar" />
        <jar href="argela-cgw-sip.jar" />
        <jar href="JainSipApi1.1.jar"/>
        <jar href="Stun4J.jar" />
        <jar href="log4j-1.2.8.jar"/>
        <jar href="nist-sdp-1.0.jar"/>
        <jar href="nist-sip-1.2.jar"/>
        <jar href="commons-codec-1.3.jar"/>
        <jar href="commons-httpclient-3.0.1.jar"/>
        <jar href="commons-logging-1.0.4.jar"/>
    </resources>
    <resources os="Windows" arch="x86">
        <jar href="jmf-win/jmf.jar" />
        <jar href="jmf-win/sound.jar" />
        <nativelib href="jmf-win/jmf-native.jar"/>
    </resources>
    <resources os="Linux" arch="i386">
        <jar href="jmf-lin/libjmutil.so.jar"/>
        <jar href="jmf-lin/jmf.jar"/>
        <nativelib href="jmf-lin/jmf-native.jar"/>
    </resources>
    <resources os="Linux" arch="x86">
        <jar href="jmf-lin/libjmutil.so.jar"/>
        <jar href="jmf-lin/jmf.jar"/>
        <nativelib href="jmf-lin/jmf-native.jar"/>
    </resources>
    <resources os="Solaris" arch="SPARC">
        <jar href="jmf-sol/libjmutil.so.jar"/>
        <jar href="jmf-sol/jmf.jar"/>
        <nativelib href="jmf-sol/jmf-native.jar"/>
    </resources>
    <resources os="SunOS" arch="SPARC">
        <jar href="jmf-sol/libjmutil.so.jar"/>
        <jar href="jmf-sol/jmf.jar"/>
        <nativelib href="jmf-sol/jmf-native.jar"/>
    </resources>
    <resources os="Mac OS">
        <jar href="jmf-all/jmf.jar"/>
    </resources>
    <application-desc main-class="tr.com.argela.sipclient.Starter">
        <argument>en</argument>
        <argument>iPlanetDirectoryPro=null</argument>
        <argument>http://www.life.com.ua/freeworld/xml.php?p=%2Cen</argument>
        <argument>http://www.life.com.ua/freeworld/ad_banner.php</argument>
        <argument>0</argument>
        <argument>212.58.162.134</argument>
        <argument>212.58.162.136</argument>
    </application-desc>
</jnlp>

Exception

<?xml version="1.0" encoding="UTF-8"?>
<jnlp spec="1.0+" codebase="http://www.life.com.ua/freeworld/webstart">
    <information>
        <title>Free World</title>
        <vendor>Please Wait ...</vendor>
        <homepage href="http://www.life.com.ua/freeworld/webstart" />
        <description>A Java Audio SIP Softphone</description>
        <icon href='images/icon.gif'/>
        <icon kind='splash' href='images/splash.jpg'/>
    </information>
    <security>
        <all-permissions/>
    </security>
    <resources>
        <j2se version="1.4+" java-vm-args="-Xms32m -Xmx64m" href="http://java.sun.com/products/autodl/j2se"/>
        <jar href="argela.jar" />
        <jar href="argela-cgw.jar" />
        <jar href="argela-cgw-common.jar" />
        <jar href="argela-cgw-plugins.jar" />
        <jar href="argela-cgw-gui.jar" />
        <jar href="argela-cgw-media.jar" />
        <jar href="argela-cgw-sip.jar" />
        <jar href="JainSipApi1.1.jar"/>
        <jar href="Stun4J.jar" />
        <jar href="log4j-1.2.8.jar"/>
        <jar href="nist-sdp-1.0.jar"/>
        <jar href="nist-sip-1.2.jar"/>
        <jar href="commons-codec-1.3.jar"/>
        <jar href="commons-httpclient-3.0.1.jar"/>
        <jar href="commons-logging-1.0.4.jar"/>
    </resources>
    <resources os="Windows" arch="x86">
        <jar href="jmf-win/jmf.jar" />
        <jar href="jmf-win/sound.jar" />
        <nativelib href="jmf-win/jmf-native.jar"/>
    </resources>
    <resources os="Linux" arch="i386">
        <jar href="jmf-lin/libjmutil.so.jar"/>
        <jar href="jmf-lin/jmf.jar"/>
        <nativelib href="jmf-lin/jmf-native.jar"/>
    </resources>
    <resources os="Linux" arch="x86">
        <jar href="jmf-lin/libjmutil.so.jar"/>
        <jar href="jmf-lin/jmf.jar"/>
        <nativelib href="jmf-lin/jmf-native.jar"/>
    </resources>
    <resources os="Solaris" arch="SPARC">
        <jar href="jmf-sol/libjmutil.so.jar"/>
        <jar href="jmf-sol/jmf.jar"/>
        <nativelib href="jmf-sol/jmf-native.jar"/>
    </resources>
    <resources os="SunOS" arch="SPARC">
        <jar href="jmf-sol/libjmutil.so.jar"/>
        <jar href="jmf-sol/jmf.jar"/>
        <nativelib href="jmf-sol/jmf-native.jar"/>
    </resources>
    <resources os="Mac OS">
        <jar href="jmf-all/jmf.jar"/>
    </resources>
    <application-desc main-class="tr.com.argela.sipclient.Starter">
        <argument>en</argument>
        <argument>iPlanetDirectoryPro=null</argument>
        <argument>http://www.life.com.ua/freeworld/xml.php?p=%2Cen</argument>
        <argument>http://www.life.com.ua/freeworld/ad_banner.php</argument>
        <argument>0</argument>
        <argument>212.58.162.134</argument>
        <argument>212.58.162.136</argument>
    </application-desc>
</jnlp>

I pasted the message i got on my mac (the message of ubuntu is almost identical)

---

### Post by derrick81787 on 2010-03-03
Humm... I don't really know, but maybe it has something to do with the version of Java you are running?  Can you paste the output of this command from a terminal
```
java -version
```

If you are not running Sun's version of Java (it isn't the default) then things might go better if you install it.  You can do so by
```
sudo apt-get install sun-java6-jre
```

If you go ahead and install Sun's Java, then please paste the results of **java -version** before and after the installation.

Thanks,
Derrick

---

### Post by gabrielcik on 2010-03-03
I use Sun java

This is what i get:

java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Server VM (build 14.1-b02, mixed mode)

Thank you

---

### Post by derrick81787 on 2010-03-08
> **gabrielcik said:**
> I use Sun java

This is what i get:

java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Server VM (build 14.1-b02, mixed mode)

Thank you

Sorry for the delay.  I was really hoping it was the Java version because sometimes people have trouble with the default and don't even realize that they aren't running Sun's version.  Unfortunately, I don't really know how to help you any more than that.  Sorry for the disappointment, but I hope you find a solution.

---

