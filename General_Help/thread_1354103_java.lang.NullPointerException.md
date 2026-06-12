---
title: "java.lang.NullPointerException"
date: 2009-12-13
forum: General Help
---

### Post by chuina on 2009-12-13
Hi, all,

Recently i installed a program named zekr in my Ubuntu9.10.
But i can't launch it :(, because of these messages below:

chuina@desktop:~$ zekr 
Launching Zekr...
java.lang.NullPointerException
    at org.apache.velocity.context.InternalContextAdapterImpl.put(InternalContextAdapterImpl.java:269)
    at org.apache.velocity.runtime.parser.node.ASTSetDirective.render(ASTSetDirective.java:213)
    at org.apache.velocity.runtime.parser.node.SimpleNode.render(SimpleNode.java:336)
    at org.apache.velocity.Template.merge(Template.java:328
    at org.apache.velocity.Template.merge(Template.java:235)
    at net.sf.zekr.engine.theme.TemplateEngine.getUpdated(TemplateEngine.java:115)
    at net.sf.zekr.common.config.VelocityInputStream.<init>(VelocityInputStream.java:29)
    at net.sf.zekr.common.config.ResourceManager.<init>(ResourceManager.java:30)
    at net.sf.zekr.common.config.ResourceManager.getInstance(ResourceManager.java:40)
    at net.sf.zekr.ui.splash.AbstractSplachScreen.<init>(AbstractSplachScreen.java:16)
    at net.sf.zekr.ui.splash.AdvancedSplashScreen.<init>(AdvancedSplashScreen.java:31)
    at net.sf.zekr.ZekrMain.startZekr(ZekrMain.java:41)
    at net.sf.zekr.ZekrMain.main(ZekrMain.java:79)

(I'm not sure where to post this thread but since its java related , so i post it here)
What should I do to run this program ??
Thanks for your valuable help.

---

### Post by chuina on 2009-12-13
Hi, all,

Recently i installed a program named zekr in my Ubuntu9.10.
But i can't launch it :(, because of these messages below:

```
chuina@desktop:~$ zekr 
Launching Zekr...
java.lang.NullPointerException
    at org.apache.velocity.context.InternalContextAdapterImpl.put(InternalContextAdapterImpl.java:269)
    at org.apache.velocity.runtime.parser.node.ASTSetDirective.render(ASTSetDirective.java:213)
    at org.apache.velocity.runtime.parser.node.SimpleNode.render(SimpleNode.java:336)
    at org.apache.velocity.Template.merge(Template.java:328
    at org.apache.velocity.Template.merge(Template.java:235)
    at net.sf.zekr.engine.theme.TemplateEngine.getUpdated(TemplateEngine.java:115)
    at net.sf.zekr.common.config.VelocityInputStream.<init>(VelocityInputStream.java:29)
    at net.sf.zekr.common.config.ResourceManager.<init>(ResourceManager.java:30)
    at net.sf.zekr.common.config.ResourceManager.getInstance(ResourceManager.java:40)
    at net.sf.zekr.ui.splash.AbstractSplachScreen.<init>(AbstractSplachScreen.java:16)
    at net.sf.zekr.ui.splash.AdvancedSplashScreen.<init>(AdvancedSplashScreen.java:31)
    at net.sf.zekr.ZekrMain.startZekr(ZekrMain.java:41)
    at net.sf.zekr.ZekrMain.main(ZekrMain.java:79)
```(I'm not sure where to post this thread but since its java related , so i post it here)
What should I do to run this program ??
Thanks for your valuable help.

[Actually this is duplicate thread]

---

### Post by Mighty_Joe on 2009-12-14
Which version of Java are you using?
```
java -version
```

You'll probably get more help posting on the [Zekr Google Group]("http://groups.google.com/group/zekr/topics") since this appears to be an application error.

---

### Post by SevenMachines on 2009-12-14
see [bug #491906 ]("https://bugs.launchpad.net/ubuntu/+source/zekr/+bug/491906")

---

### Post by chuina on 2009-12-14
Hi , there all , thanks for response.
Here is the Version.

```
chuina@desktop:~$ java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-3ubuntu1)
OpenJDK Client VM (build 14.0-b16, mixed mode, sharing)
```
Waiting for more instruction...

---

### Post by cariboo on 2009-12-14
Please don't create multiple threads on the same subject. Ihave merged you two threads, and moved them to an area where you will probably get answered quicker.

---

### Post by chuina on 2009-12-23
i have solution my problem, though indirectly.

I just freshly install Ubuntu 9.10 for multibooting.
Then follow the steps through this: 
[http://zekr.org/wiki/Installation#Zekr_Repository](http://zekr.org/wiki/Installation#Zekr_Repository)

Now it is working.

---

