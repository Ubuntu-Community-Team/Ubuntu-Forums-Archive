---
title: "Wireless VPN Connection Help Needed"
date: 2006-04-27
forum: General Help
---

### Post by Schnoid on 2006-04-27
Hello,

I'm a complete Ubuntu n00b.  Really enjoying using Ubuntu, but I have a big problem.

At my university, the only way to access the internet is through a VPN connection on a wireless network.

I've got the wireless card in my machine to connect to the access point, that's all OK, but, I'm struggling getting the PPPoE connection and the VPN connection to work.

I've ran "sudo pppoeconf" and it seemed to set everything up fine.  It then said to type "pon dsl-provider" to start the connection.  When I do this though, it returns plugin "rp-pppoe.so loaded"  I don't think this is connected.

It may be trying to use the eth0 instead of ath0 but I'm really not sure.

Any help/suggestions greatly appreciated, as I cannot get the machine on the Internet any other way.

Thanks in advance.

Schnoid. ](*,)

---

### Post by Schnoid on 2006-04-27
Also, tried to run 'pppoe -I ath0' to set default interface to ath0, but get 3 lines of symbols and drops back to command line

---

### Post by hajk on 2006-04-27
If you want to set up a VPN connection through a wireless access point, why are you then trying to establish a DSL connection to your internet provider via a telephone line with pppoe?

You should ask the IT people at your university what VPN clients they're using: if it is a Cisco VPN client, then you could use vpnc in Ubuntu; otherwise the pptp client could be used. You also need a few connection details (in addition to your ID and password): the vpn-server IP and the group secret -- just ask the IT people.

---

### Post by Schnoid on 2006-04-28
I'm trying to set up a PPPoE connection first because that's how it's configured.

Using windows, you set up a Broadband Internet connection over the wireless and then use a VPN over that Broadband connection.

I thought that the broadband connection was the PPPoE in Linux and then the VPN ran on top of that?  Or am I wrong?

I've tried the IT people they've only got config instructions for Red Hat 9.

Once again, any help gratefully received.

Schnoid.

---

### Post by hajk on 2006-04-28
Well, that's just not the way it works... you only need to set up a wireless connection to an internet access point and -- once that connection is established -- you need to set up the VPN tunnel within that connection to the university VPN server (using the Red Hat info that you already have).
If you are already at the university you can connect to any available access point.

First, am I right in assuming that you have a wireless card or dongle based on the Atheros chip? In other words, when you open System -> Administration -> Networking, does it show a wireless interface called ath0? If so, then you need to click on Properties, enable the interface, choose the university access point as essid,  enter any security information like wep-key, and set the DHCP choice (most likely). OK these choices, and then activate the interface, making sure ath0 is the default gateway.

Next, you need to establish a VPN tunnel through the established connection, making a new interface tun0 in the process. Look at the Red Hat information: it should mention something like Cisco VPN client: in that case you install the vpnc package and follow the man page for it. Or perhaps it says PPTP, in that case you use the package pptp. Use any info you need from the Red Hat instructions, they will also in large part be suitable for Ubuntu. Let us know if you get stuck.

---

### Post by Schnoid on 2006-05-03
OK, hajk, I've been trying and I'm still really confused and can't get it work.  So, I've been to the IT people and these are the only instructions they have, and they're for Red Hat 9.

I dont have the graphical configuration tool mentioned in them and I can't get it because of not being able to go online.

Any help much appreciated.

Schnoid.   


1.
      The Roaring Penguin PPPoE Client
         1. Download the rpm to install the latest client from [http://www.roaringpenguin.com/pppoe/rp-pppoe-3.5-1.i386.rpm](http://www.roaringpenguin.com/pppoe/rp-pppoe-3.5-1.i386.rpm).
         2. Install this by double clicking it (you may be prompted for your root password), a box saying 'completed system preparation' should appear after a few seconds.
         3. Click 'continue' to complete the installation of this package.
         4. To configure the PPPoE connection you need to use a terminal window as a root user, you can login to the machine as root, or in the terminal type su - and the root password when prompted.
         5. Type adsl-setup and press return.
         6. A command prompt wizard will guide you through configuring the PPPoE connection. These instructions assume you do not already have any PPPoE or PPTP connections installed, so will configure the ppp0 device.
         7. Enter your nomadic username:
         8. For Student Users: Your username will be your six digit student number.
         9. For Staff Users: Your username is your staff user name.
        10. Type in the ethernet interface the connection will use (eth0 is likely if you only have one ethernet adapter in your system), press enter.
        11. Type no to have the link stay up continuously (you will need to manually start and stop it).
        12. For the IP address of your ISP's primary DNS server type server in lower case and press enter.
        13. For the password prompt enter your standard UWS domain password, and press enter. Re-type your password to confirm.
        14. For USERCTRL, type yes to allow you to start and stop the connection as a normal (non-root) user.
        15. When you are asked about FIREWALLING you should choose option 1 for a standard web-surfing workstation.
        16. Type no to stop the connection starting at boot up.
        17. Review the information you provided and if there are no errors, press y and enter.
        18. You are then told how to bring the connection up and down, at this stage do nothing as the VPN (PPTP) connection must be created next. 


      PPP Package

         1. Download an up-to-date version of a PPP package from [http://prdownloads.sourceforge.net/pptpclient/ppp-2.4.2_cvs_20030610-1.i386.rpm](http://prdownloads.sourceforge.net/pptpclient/ppp-2.4.2_cvs_20030610-1.i386.rpm) from Sourceforge.net using any of the mirror sites available.
         2. Double click on the file you have just downloaded to install the package on to your system (you may be prompted for your root password), a box saying 'completed system preparation' should appear after a few seconds.
         3. Click 'continue' to complete the installation of this package 


      Kernel-MPPE Package

         1. Download the package to provide MPPE support from [http://pptpclient.sourceforge.net/mppe/kernel-mppe-2.4.20-18.9.i686.rpm](http://pptpclient.sourceforge.net/mppe/kernel-mppe-2.4.20-18.9.i686.rpm) from Sourceforge.net, using any of the mirrors available. NB - this package is for kernel version 2.4.20-18.9, the default kernel on the standard desktop build of Red Hat Linux 9 assuming you have applied all available upgrades as of 04/07/03. If you have a different kernel you can download the appropriate package from [http://pptpclient.sourceforge.net/howto-redhat-90.phtml](http://pptpclient.sourceforge.net/howto-redhat-90.phtml).
         2. Double the click the file you have just downloaded to start the installation process (you may again need to enter your root password. A box saying 'completed system preparation' should appear after a few seconds.
         3. Click 'continue' to complete the installation of this package. 


      PPTP-Linux Package

         1. Download the PPTP client [http://prdownloads.sourceforge.net/pptpclient/pptp-linux-1.3.1-1.i386.rpm](http://prdownloads.sourceforge.net/pptpclient/pptp-linux-1.3.1-1.i386.rpm) from Sourceforge.net using any of the mirror sites available.
         2. Start the PPTP client installation by double clicking the file you have just downloaded (again you may need to enter your root password) - a box saying 'completed system preparation' should appear after a few seconds.
         3. Click 'continue'to complete the installation of this package. 


      PPTP-php-gtk (Graphical Configuration Tool) Package

         1. Download the graphical PPTP configuration tool rpm [http://prdownloads.sourceforge.net/pptpclient/pptp-php-gtk-20030505-rc1.i386.rpm](http://prdownloads.sourceforge.net/pptpclient/pptp-php-gtk-20030505-rc1.i386.rpm) from Sourceforge.net using any of the mirror sites available.
         2. Double click the file you have just downloaded (you may need to enter your root password) to start the installation of this package - a box saying 'completed system preparation' should appear after a few seconds.
         3. Click continue to complete the installation of this package to your system.
         4. Reboot your system 

Configure the VPN Connection

   1. Click the Red Hat Icon, System tools, Terminal to bring up a terminal window
   2. Start the graphical configuration interface by typing /usr/bin/pptpconfig and pressing enter (you may need to provide your root password)

      (Click on images for full size version)
      Screenshot of the PPTP configuration windows before information has been entered 	
          * A configuration box looking like this should appear 



      Screenshot of the PPTP configuration windows after the connecion has been entered 	
          * Fill in the details which were provided in the email sent to to confirm your nomadicService registration according to the instructions following:
          * Name: This is the name of the connection for your reference (eg Student VPN Server - roaming, Staff VPN Server - roaming). You should name this so it is distinguishable from any remote nomadic connection you may have or install later.
          * Server: as per email confirmation
          * User Name: For students this is your student number.
          * For Staff Users: Your username is your staff user name.
          * Password: Your standard UWS password 
        	 



        	
          * Click the Add button, and a Line will appear in the window towards the top of the configuration box, as shown here. Select this line by single clicking on it. 



        	
          * Click the Routing tab
          * Select All to Tunnel and then click Public Network Interface...
          * Enter the name of the interface you created the PPPoE connection as, in this example it is ppp0, click close.
          * Click the Encryption tab
          * Click to select the box titled Require Microsoft Point-to-Point Encryption (MPPE)
          * Click to select the box titled Refuse 40-bit Encryption
          * If you do not use the remote nomadic service and only have the one PPTP connection, you can set this to start as soon as you start PPTP Client. To do this: Click the Miscellaneous tab and tick the box marked Start tunnel when this program starts.
          * Click the Update button to save your changes.
          * Click quit. 



Connecting to the roaming service

   1. Connect your ethernet card to a nomadic outlet on campus (make sure it is a clearly marked nomadic outlet) or if you have a wireless card, move into the range of a nomadic wireless access point.
   2. You first need to bring up the PPPoE connection (ppp0 in this example). To do this, open a terminal window and type su - and enter, type your root password and press enter.
   3. Type ifup ppp0, press enter and the command prompt should return.
   4. Now bring up the PPTP connection by typing /usr/bin/pptpconfig and enter. You could also do this by clicking on the Red Hat icon, System settings, More system settings, PPTP client.
   5. Enter your password for root.
   6. If you chose to start the connection when the PPTP Client GUI is started, the connection will start automatically, otherwise select the connection you want (the nomadic roaming connection) and click start.
   7. Quit the PPTP client setup window and click the keys in the system tray to return to normal rights.
   8. You can test your connection by pinging [www.swan.ac.uk](www.swan.ac.uk).

---

### Post by hajk on 2006-05-03
OK Schnoid, things are looking up for you... though you may not think so right now.

First, I assume that your regular Internet connection is running OK -- you are posting messages here after all. From one of your earlier posts I gather that your interface is "ath0" (a wireless card using an Atheros chip), you can check with the command "sudo ifconfig". At any rate, this regular Internet connection must be up and running before proceeding any further with VPN.

Second, the Red Hat info mentions PPTP. In Ubuntu you only need to install the "pptp-linux" package, and then complete the installation manually. For example, the instructions in [http://www.ubuntuforums.org/showthread.php?t=164975&highlight=pptp](http://www.ubuntuforums.org/showthread.php?t=164975&highlight=pptp) 
are pretty clear, but perhaps a bit daunting for a Linux novice.

If you rather like a graphical method, then you could follow the instructions in 
[http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml) which are also pretty clear, I think.

As to the required information:

Name: use any short easily remembered (by you) name for the VPN connection.
Server: this is the VPN server in the email that you must have received.
User Name: your student number.
Password: your password.

Either way should do it. Good luck!

---

