---
title: "How to configure Eclipse + XDebug + Firefox"
date: 2010-09-06
forum: General Help
---

### Post by Enav on 2010-09-06
**This "howto" is based on the following model:**
-Ubuntu v 10.04
-Eclipse v 3.5.2
-Local LAMP server
 
**Requirements:**
-LAMP already installed
-Eclipse already installed

**Server configuration:**
-Open a terminal
-run: sudo apt-get install php5-xdebug
-run: sudo nano /etc/php5/conf.d/xdebug.ini
-Don't delete the content of this file, just go to the end of the file add 2 blank lines and paste the next configuration:

xdebug.remote_enable=On
xdebug.remote_host="localhost"
xdebug.remote_port=9000
xdebug.remote_handler="dbgp"

-save changes
-run: sudo service apache2 restart

**Eclipse configuration:**
-Open eclipse
-On the eclipse main menu go to: Help--> Install New Software...
-open the dropDownList "work with"
-select "--All Available Sites--"
-On the filter text field put: php
-Check out: "Programming Languages" 
-Check out: "Web, XML, and Java EE Development"
-Follow the wizard instruction until finish
-On the eclipse main menu go to: Window--> Preferences
-Navigate on the tree menu to: PHP--> Debug
-open the dropDownList "work with"
-On "PHP Debugger" select "XDebug"
-Leave alone "Server" and "PHP Executables"
-Save changes and close the window
-On the eclipse main menu go to: Run--> Debug configurations...
-Do a double click over "PHP Web Page" just to add a new setting
-On the DropDowList "Server Debugger" select "XDebug"
-On the file section browse and select the "index.php" of your project or whatever file you need to start your application
-Uncheck "Break at Fist Line"
-Apply changes and close the window
-On the eclipse main menu go to: Window--> Web Browser--> Default System Web Browser


**Testing xdebug**
-Open a project with source code that already is hosted in your LAMP server
-Place a "break point" at some point of you script
-Press "F11" to start the debugger
-Your code should stop at the break point
-Now move the mouse over variables so watch its values

That is all i hope you enjoy this HowTo  ):P


For further information: 
- [http://devzone.zend.com/article/2930](http://devzone.zend.com/article/2930)
- [http://2tbsp.com/content/getting_started_eclipse_php_development_tools_%28pdt%29]("http://2tbsp.com/content/getting_started_eclipse_php_development_tools_%28pdt%29")

---

### Post by Takilian Rueshin on 2011-02-28
Very Thanks.

---

### Post by warri0r on 2011-08-25
It works, thanks

---

### Post by paul888 on 2011-09-18
Hi,
After i finished the configuration.
I clicked F11 -> Ant Build -> ok
and then appeared the error message:
error Build Failed.
Reason: unable to find an ANT file to run.):P

When i configure part 3.
Run -> Debug Config -> PHP Web page -> File then Browse (In select file, no file available).
I cannot find the index.php file. Why?[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by binarios on 2011-09-30
Hi. I'm trying to install the "all in one" 3.3.2 Eclipse/PDT with XDebug.
I've got it working so that I can see that XDebug is loaded (for example, in phpinfo()), but when I try to create a new Debug Launch Configuration,
and click on "New_Configuration" under "PHP Web Script with XDebug", I get the following error: "An error has occurred. See error log for more details.

org.eclipse.php.internal.core.util.FileUtils.fileExists(Ljav a/lang/String;)Z ".

Here is the first part of the eclipse error log:

java.lang.NoSuchMethodError:
   org.eclipse.php.internal.core.util.FileUtils.fileExists(Ljava/lang/String;)Z

at org.eclipse.php.xdebug.ui.launching.XDebugPHPServerTab.isValid(XDebugPHPServerTab.java:508)

at org.eclipse.php.xdebug.ui.launching.XDebugPHPServerTab.initializeFrom(XDebugPHPServerTab.java:406) 
at org.eclipse.debug.ui.AbstractLaunchConfigurationTabGroup.initializeFrom(AbstractLaunchConfigurationTabGroup.java:86) 
at org.eclipse.debug.internal.ui.launchConfigurations.LaunchConfigurationTabGroupWrapper.initializeFrom(LaunchConfigurationTabGroupWrapper.java:194) 
at org.eclipse.debug.internal.ui.launchConfigurations.LaunchConfigurationTabGroupViewer.displayInstanceTabs(LaunchConfigurationTabGroupViewer.java:751) 
at org.eclipse.debug.internal.ui.launchConfigurations.LaunchConfigurationTabGroupViewer$8.run(LaunchConfigurationTabGroupViewer.java:623) 
at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:70)

Thanks for any help you can give me. 
Regards

---

### Post by binarios on 2011-09-30
Hi. I'm trying to install the "all in one" 3.3.2 Eclipse/PDT with XDebug.
I've got it working so that I can see that XDebug is loaded (for example, in phpinfo()), but when I try to create a new Debug Launch Configuration,
and click on "New_Configuration" under "PHP Web Script with XDebug", I get the following error: "An error has occurred. See error log for more details.

org.eclipse.php.internal.core.util.FileUtils.fileExists(Ljava/lang/String; )Z ".

Here is the first part of the eclipse error log:

java.lang.NoSuchMethodError:
   org.eclipse.php.internal.core.util.FileUtils.fileExists(Ljav a/lang/String; )Z ".

at org.eclipse.php.xdebug.ui.launching.XDebugPHPServerTab.isValid(XDebugPHPServerTab.java:508 )

at org.eclipse.php.xdebug.ui.launching.XDebugPHPServerTab.initializeFrom(XDebugPHPServerTab.java:406) 
at org.eclipse.debug.ui.AbstractLaunchConfigurationTabGroup.initializeFrom(AbstractLaunchConfigurationTabGroup.java:86) 
at org.eclipse.debug.internal.ui.launchConfigurations.LaunchConfigurationTabGroupWrapper.initializeFrom(LaunchConfigurationTabGroupWrapper.java:194) 
at org.eclipse.debug.internal.ui.launchConfigurations.LaunchConfigurationTabGroupViewer.displayInstanceTabs(LaunchConfigurationTabGroupViewer.java:751) 
at org.eclipse.debug.internal.ui.launchConfigurations.LaunchConfigurationTabGroupViewer$8.run(LaunchConfigurationTabGroupViewer.java:623) 
at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:70)

Thanks for any help you can give me. 
Regards

---

### Post by fmmarzoa on 2012-01-01
> -On the file section browse and select the "index.php" of your project or whatever file you need to start your application

When I press "Browse" button I get a disabled "Select a File from the Project" with a void square below, and an error message of "No entries available" over the Cancel button, (the OK is disabled).

---

### Post by rsvancara on 2012-01-01
Great tutorial.  I have been looking for alternatives to Komodo IDE.

---

### Post by meetai on 2012-10-22
I am guessing that "No entries available" implies you have no PHP projects defined in your
workspace.

> **fmmarzoa said:**
> When I press "Browse" button I get a disabled "Select a File from the Project" with a void square below, and an error message of "No entries available" over the Cancel button, (the OK is disabled).

---

### Post by wildmanne39 on 2012-10-22
Old thread closed.

---

