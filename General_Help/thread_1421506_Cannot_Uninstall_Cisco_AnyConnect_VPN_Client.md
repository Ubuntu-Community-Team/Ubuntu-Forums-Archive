---
title: "Cannot Uninstall Cisco AnyConnect VPN Client"
date: 2010-03-04
forum: General Help
---

### Post by 2uRcJQ34G1 on 2010-03-04
[FONT="Verdana"][SIZE="3"][COLOR="Navy"]Hiya,

In order to gain access to my university network remotely I was asked to open a website that would act as a gateway. Upon opening the site I was asked to run a Java application, which installed a _Cisco AnyConnect VPN_ client on the system. However, now I do not need this, but I cannot find a way to uninstall it. It does not appear in the Synaptic Manager or the the ubuntu Software centre, so I cannot find the package to uninstall it. The software does appear in the 'Internet' section in the Application drop down menu and runs without the need of Firefox. I read the Cisco release notes but I could not find a way to uninstall the software. Does anyone else have a clue??

Thanks in advance.[/COLOR][/SIZE][/FONT]

---

### Post by 2uRcJQ34G1 on 2010-03-04
Just so you know, this client is different from the **network-manager-vpnc** package.

---

### Post by gmargo on 2010-03-04
If it shows up in the menu, you can use the menu editor to get a clue.  Open the menu editor (System -> Preferences -> Main Menu, click on 'Internet' (Under 'Applications') in the left panel.  Now the right panel should show the menu entries for the Internet section. Click the right panel entry you're interested in (Cisco VPN?) then click the 'Properties' button and see what is in the 'Command' field.  You will probably see a java command with an argument .jar file.  Or perhaps a shell script that does the same.

---

### Post by 2uRcJQ34G1 on 2010-03-06
Sorry, this thread is dead. I started a new thread and now the issue has been reolved.
[http://ubuntuforums.org/showthread.php?t=1421486]("http://ubuntuforums.org/showthread.php?t=1421486")

---

