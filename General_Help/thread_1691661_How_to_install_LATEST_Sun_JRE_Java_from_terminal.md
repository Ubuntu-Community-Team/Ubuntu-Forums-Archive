---
title: "How to install LATEST Sun JRE Java from terminal"
date: 2011-02-20
forum: General Help
---

### Post by runeh76 on 2011-02-20
Remove the old version

First you'll want to remove the old JRE or openJDK (if you have it). 

When JRE is installed from the repositories, do it like this:

System - Administration - Synaptic Package Manager

Query: sun java

Tick all installed packages and choose complete removal.

When it's installed manually in /opt/java, see the instruction at the bottom of this column (under the header Removal).

If you don't have JRE, then you'll probably have openJDK. That one should be completely removed as well. That can also be done with Synaptic Package Manager (query: openjdk).


Get JRE

Get the right file from the Java website: [http://www.java.com](http://www.java.com)

For 32 bit you want Linux (self-extracting file); the name of this file ends on i586.bin. You don't want Linux RPM (self extracting file), of which the file name ends on i586-rpm.bin, because RPM is not built for Ubuntu, but for other Linux distro's.

Note: Store the file in the folder Downloads. So in /home/YourUserName/Downloads. Firefox puts downloaded files there by default, but not all web browsers do it like that.

For example: user John should place the file in /home/John/Downloads.  When in doubt, check it: upper panel of your desktop - Places - Downloads.

This is important for the terminal commands that you'll execute later on, because otherwise they won't be correct.


Install JRE (32-bit)

Note: the terminal commands in this how-to possibly refer to an older version of JRE. When there's a newer version, you can simply adapt the file names in the terminal commands.

This how-to has been written for JRE 6 update 24 (32 bit version).


1. Go to the folder opt, with the following command:

Applications - Accessories - Terminal

Type (use copy/paste: rapidly click three times on the blue line, in order to select the entire line).
cd /opt

Press Enter.


2. Create a new subfolder, with the following command line. 
Type (copy/paste):
sudo mkdir java

Press Enter.

Type your password. You won't see anything, not even dots, this is normal.
Press Enter.


3. Go to the new folder, with the following command.
Type (copy/paste):
cd java

Press Enter.


4. Create a new subfolder, with the following command.
Type (copy/paste):
sudo mkdir 32

Press Enter.


5. Move the JRE file that you just downloaded, into this newest folder, with the following command.
Type (copy/paste):
sudo mv ~/Downloads/jre-6u24-linux-i586.bin /opt/java/32

Press Enter.


6. Make the file executable, with the following command.
Type (copy/paste):
sudo chmod 755 /opt/java/32/jre-6u24-linux-i586.bin

Press Enter.

Now you're going to install JRE, by executing this file.


7. First, go to the new folder, with the following command.
Type (copy/paste):
cd /opt/java/32

Press Enter.


8. Execute the file, with the following command.
Type (copy/paste):
sudo ./jre-6u24-linux-i586.bin

Press Enter.

Now the license agreement appears. 
Press as many times on the space bar, until you see the following text:
Do you agree to the above license terms? [yes or no]

Type:
yes

Press Enter.

Note: it's possible that you won't see a license agreement. For example because you've already accepted it previously, during the installation of an older version of JRE from the repositories.


Inform the system and make the new JRE the default

9. Now you'll want to tell the system, that there's a new Java version available.

Type (copy/paste):
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32/jre1.6.0_24/bin/java" 1

Press Enter.

Note: are you updating from a previous Java version, which you have removed manually? Then you'll need to execute the above command twice, because you'll get an error message the first time.


10. Tell the system, that the new Java must be the default:

Type (copy/paste):
sudo update-alternatives --set java /opt/java/32/jre1.6.0_24/bin/java

Press Enter.


Install the Firefox plugin

11. Installing the Firefox plugin is simple. First execute the following command, in order to create a certain folder (if it doesn't exist already).

Type in the terminal (copy/paste):
mkdir ~/.mozilla/plugins

Press Enter.

If it exists already, you'll see a notification of that.


12. Now remove the IcedTea plugin, if it has been installed.

Type (copy/paste):
sudo apt-get remove icedtea6-plugin

Press Enter.


13. Remove a former version of the Java plugin (may or may not be present, run the command just to make sure).

Type (copy/paste):

rm ~/.mozilla/plugins/libnpjp2.so

Press Enter.


14. Now you can install the plugin, by creating a symbolic link (you tell Firefox, where the plugin is located).

Type (copy/paste):
ln -s /opt/java/32/jre1.6.0_24/lib/i386/libnpjp2.so ~/.mozilla/plugins/

Press Enter.


Final check

Now close and restart Firefox. Check if everything has succeeded. Type in the url bar of Firefox (not in the terminal!):

about:plugins

Press Enter.

And scroll down, until you see something approximately similar to this:
Java(TM) Plug-in 1.6.0_24

You can also use this website:
[http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp)


Other user accounts: repeat three commands

Are there any other user accounts on the computer? Then repeat the following three commands in each user account:

rm ~/.mozilla/plugins/libnpjp2.so

and then (in case the plugins folder doesn't exist yet):

mkdir ~/.mozilla/plugins

and then:

ln -s /opt/java/32/jre1.6.0_24/lib/i386/libnpjp2.so ~/.mozilla/plugins/


Sun Java 6 Plugin Control Panel

You can call up the Control Panel as follows (in each user account):

Type (copy/paste):
/opt/java/32/jre1.6.0_24/bin/ControlPanel

Press Enter.

Note: this command is only for JRE update 24. You'll need to adapt it when you use another version.


Removal

Do you wish to remove JRE again? It's very easy, to remove a manually installed JRE. As follows:

Close Firefox (otherwise the java plugin will be in use).

Now open file manager Nautilus with root rights, using the following terminal command.

Applications - Accessories - Terminal

Type (copy/paste):
gksudo nautilus

Press Enter.

File system - opt

Click on the folder java and delete it.

Then remove the Java plugin:

Type in the terminal (copy/paste):

rm ~/.mozilla/plugins/libnpjp2.so

Press Enter.


Source:  [http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-32-bit-](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-32-bit-)

---

### Post by t3s7a on 2011-03-29
Great post runeh76.

_________________

Got this error at the update-alternatives, but it's working great anyway. Probably it was already set...


```
update-alternatives: error: alternative /<myPath>/java for java not registered, not setting.
```

---

