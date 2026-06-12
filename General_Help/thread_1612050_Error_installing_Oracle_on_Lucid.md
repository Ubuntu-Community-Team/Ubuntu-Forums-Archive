---
title: "Error installing Oracle on Lucid"
date: 2010-11-02
forum: General Help
---

### Post by damnated on 2010-11-02
I used this tutorial, and installed everything I needed, made every symbolic link, oracle user etc.

[http://www.pythian.com/news/13291/installing-oracle-11gr2-enterprise-edition-on-ubuntu-10-04-lucid-lynx/](http://www.pythian.com/news/13291/installing-oracle-11gr2-enterprise-edition-on-ubuntu-10-04-lucid-lynx/)

At the end, when I should start running the installer, this is what happens.

```
damnated@damnated-desktop:~$ sudo su -
[sudo] password for damnated: 
root@damnated-desktop:~# su - oracle
oracle@damnated-desktop:~$ cd database
oracle@damnated-desktop:~/database$ ./runInstaller 
Starting Oracle Universal Installer...

Checking Temp space: must be greater than 80 MB.   Actual 7695 MB    Passed
Checking swap space: must be greater than 150 MB.   Actual 3151 MB    Passed
Checking monitor: must be configured to display at least 256 colors
    >>> Could not execute auto check for display colors using command /usr/bin/xdpyinfo. Check if the DISPLAY variable is set.    Failed <<<<

Some requirement checks failed. You must fulfill these requirements before

continuing with the installation,

Continue? (y/n) [n] y


>>> Ignoring required pre-requisite failures. Continuing...
Preparing to launch Oracle Universal Installer from /tmp/OraInstall2010-11-02_10-36-00PM. Please wait ...oracle@damnated-desktop:~/database$ No protocol specified
Exception in thread "main" java.lang.NoClassDefFoundError
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:164)
    at java.awt.Toolkit$2.run(Toolkit.java:821)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:804)
    at com.jgoodies.looks.LookUtils.isLowResolution(Unknown Source)
    at com.jgoodies.looks.LookUtils.<clinit>(Unknown Source)
    at com.jgoodies.looks.plastic.PlasticLookAndFeel.<clinit>(PlasticLookAndFeel.java:122)
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:242)
    at javax.swing.SwingUtilities.loadSystemClass(SwingUtilities.java:1783)
    at javax.swing.UIManager.setLookAndFeel(UIManager.java:480)
    at oracle.install.commons.util.Application.startup(Application.java:758)
    at oracle.install.commons.flow.FlowApplication.startup(FlowApplication.java:164)
    at oracle.install.commons.flow.FlowApplication.startup(FlowApplication.java:181)
    at oracle.install.commons.base.driver.common.Installer.startup(Installer.java:265)
    at oracle.install.ivw.db.driver.DBInstaller.startup(DBInstaller.java:114)
    at oracle.install.ivw.db.driver.DBInstaller.main(DBInstaller.java:132)

```

And nothing after this. The terminal hangs there. Ideally, the installer gui should pop up. 
Also FYI I have no idea why it can't read the DISPLAY variable, it is set as <my ip>:0, but I don't think that is the problem. Suggestions on how to fix that are welcome as well, though.

---

