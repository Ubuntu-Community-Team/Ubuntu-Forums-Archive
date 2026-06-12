---
title: "Installing drivers for Samsung 4623F"
date: 2011-12-26
forum: General Help
---

### Post by daldude on 2011-12-26
How do I install the drivers for ye Samsung SXC-4623F?
The instructions on the CD are totally confusing and not at all helpful.

This is what it says about installing The drivers it is totally confusing and not at all clear or easy to figure out how to do it.

               
[LIST=1]
[*]                   Make sure that the machine is connected to your computer and powered on.
[*]                   When the Administrator Login window appears, type in root in the Login field and enter the system password.
                                                                                                                   [IMG]file:///media/NTFS_DATA/Samsung%20SCX-4623F%20Multi%20Funtion%20Printer%20Support%20%20CD/MANUAL/Samsung%20SCX-4623%20Series/common/note.png[/IMG]                                                  
                                                                                                 You must log in as a super user (root) to install the machine software. If you are not a super user, ask your system administrator.
[*]                   From the Samsung website, download and unpack the Unified Linux Driver package to your computer.
[*]                   Click [IMG]file:///media/NTFS_DATA/Samsung%20SCX-4623F%20Multi%20Funtion%20Printer%20Support%20%20CD/MANUAL/Samsung%20SCX-4623%20Series/common/i-linux-2.png[/IMG] at the bottom of the desktop. When the Terminal screen appears, type in the following:
                   [root@localhost root]#tar zxf [FilePath]/UnifiedLinuxDriver.tar.gz[root@localhost root]#cd [FilePath]/cdroot/Linux[root@localhost Linux]#./install.sh
                                                                                                                   [IMG]file:///media/NTFS_DATA/Samsung%20SCX-4623F%20Multi%20Funtion%20Printer%20Support%20%20CD/MANUAL/Samsung%20SCX-4623%20Series/common/note.png[/IMG]                                                  
                                                                                                 If you do not use the graphical interface and failed to install the software, you have to use the driver in the text mode. Follow the steps 3 to 4, and then follow the instructions on the terminal screen.
[*]                   When the welcome screen appears, click Next.
[*]                   When the installation is complete, click Finish.
[/LIST]
             
             The installation program has added the Unified Driver Configurator desktop icon and the Unified Driver group to the system menu for your convenience. If you have any difficulties, consult the on screen help that is available through your system menu or can otherwise be called from the driver package Windows applications, such as Unified Driver Configurator or Image Manager.
                                                                                      **Installing the SmartPanel**

                 
               
             
                            
[LIST=1]
[*]                   Make sure that the machine is connected to your computer and powered on.
[*]                   When the Administrator Login window appears, type in root in the Login field and enter the system password.
                                                                                                                   [IMG]file:///media/NTFS_DATA/Samsung%20SCX-4623F%20Multi%20Funtion%20Printer%20Support%20%20CD/MANUAL/Samsung%20SCX-4623%20Series/common/note.png[/IMG]                                                  
                                                                                                 You must log in as a super user (root) to install the machine software. If you are not a super user, ask your system administrator.
[*]                   From the Samsung website, download and unpack the Smart Panel package to your computer.
[*]                   Click [IMG]file:///media/NTFS_DATA/Samsung%20SCX-4623F%20Multi%20Funtion%20Printer%20Support%20%20CD/MANUAL/Samsung%20SCX-4623%20Series/common/i-linux-2.png[/IMG] at the bottom of the desktop. When the Terminal screen appears, type in the following:
                   [root@localhost root]#tar zxf [FilePath]/SmartPanel.tar.gz[root@localhost root]#cd [FilePath]/cdroot/Linux/smartpanel[root@localhost smartpanel]#./install.sh
                                                                                                                   [IMG]file:///media/NTFS_DATA/Samsung%20SCX-4623F%20Multi%20Funtion%20Printer%20Support%20%20CD/MANUAL/Samsung%20SCX-4623%20Series/common/note.png[/IMG]                                                  
                                                                                                 If you do not use the graphical interface and failed to install the software, you have to use the driver in the text mode. Follow the steps 3 to 4, and then follow the instructions on the terminal screen.
[/LIST]
             
           
                                                                           **Installing the Printer Setting Utility**

                 
               
             
                            
[LIST=1]
[*]                   Make sure that the machine is connected to your computer and powered on.
[*]                   When the Administrator Login window appears, type in root in the Login field and enter the system password.
                                                                                                                   [IMG]file:///media/NTFS_DATA/Samsung%20SCX-4623F%20Multi%20Funtion%20Printer%20Support%20%20CD/MANUAL/Samsung%20SCX-4623%20Series/common/note.png[/IMG]                                                  
                                                                                                 You must log in as a super user (root) to install the machine software. If you are not a super user, ask your system administrator.
[*]                   From the Samsung website, download and unpack the Printer Setting Utility package to your computer.
[*]                   Click [IMG]file:///media/NTFS_DATA/Samsung%20SCX-4623F%20Multi%20Funtion%20Printer%20Support%20%20CD/MANUAL/Samsung%20SCX-4623%20Series/common/i-linux-2.png[/IMG] at the bottom of the desktop. When the Terminal screen appears, type in the following:
                   [root@localhost root]#tar zxf [FilePath]/PSU.tar.gz[root@localhost root]#cd [FilePath]/cdroot/Linux/psu[root@localhost psu]#./install.sh
[/LIST]
             
                                                                                     [IMG]file:///media/NTFS_DATA/Samsung%20SCX-4623F%20Multi%20Funtion%20Printer%20Support%20%20CD/MANUAL/Samsung%20SCX-4623%20Series/common/note.png[/IMG]                                      
                                                                         If you do not use the graphical interface and failed to install the software, you have to use the driver in the text mode. Follow the steps 3 to 4, and then follow the instructions on the terminal screen.
                                                                
                                                                                     [IMG]file:///media/NTFS_DATA/Samsung%20SCX-4623F%20Multi%20Funtion%20Printer%20Support%20%20CD/MANUAL/Samsung%20SCX-4623%20Series/common/note.png[/IMG]                                      
                                                                         If the printer driver does not work properly, uninstall the driver and reinstall it. 
                     Follow the steps below steps to uninstall the driver for Linux.
                                            
[LIST=1]
[*]                           Make sure that the machine is connected to your computer and powered on.
[*]                           When the Administrator Login window appears, type in “root” in the Login field and enter the system password.
                           You must log in as a super user (root) to uninstall the printer driver. If you are not a super user, ask your system administrator.
[*]                           Click the icon at the bottom of the desktop. When the Terminal screen appears, type in:
                           [root@localhost root]#cd /opt/Samsung/mfp/uninstall/[root@localhost uninstall]#./uninstall.sh
[*]                           Click Uninstall.
[*]                           Click Next.
[*]                           Click Finish.
[/LIST]

Can anyone explain step by step in plain non tecnical computer programmer language how to install the printer and scanner drivers for the Samsung SXF-4623F?

The best I could do was get the printer part of the drivers to install but not the scanner which is what I wanted it mostly for .
I have Ubuntu 10.04 LTS 64 bit.

---

