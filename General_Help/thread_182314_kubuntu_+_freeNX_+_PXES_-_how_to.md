---
title: "kubuntu + freeNX + PXES - how to?"
date: 2006-05-25
forum: General Help
---

### Post by Scubes13 on 2006-05-25
Hello everyone!

I have currently installed freenx onto a Kubuntu Breezy Badger system. 
(See this post for information on installing freenx on Ubuntu/Kubuntu -  [http://www.ubuntuforums.org/showthread.php?t=1968](http://www.ubuntuforums.org/showthread.php?t=1968) - plenty of info to get it working, no need to repeat it in this thread: )

I am currently utilizing the freenx server via the NX Client from two Windows machines.

I am looking to replace my Windows boxes with several thin client boxes.

So, my problem.... I have yet to figure out how to setup the Terminal Server so that it will allow Thin Clients to boot from it via PXE. 

I understand that the process is as follows:
1. Thin Client Boots 
2. The PXE network card (or PXES CD) obtains an IP address from the DHCP Server.
3. The DHCP lease specifies a local tftp server address and file for the PXE client to grab from the Terminal Server.
4. The PXE client grabs the file from the Terminal Server and boots from the image that is downloaded.
5. The image that is downloaded is a PXES boot image with an NX Client
6. The NX Client asks for the user's authorization
7. NX Client then connects the the Terminal Server running freeNX and then the NX session is initiated

Now, I have freeNX up and running. (As already mentioned.) 

I am basically looking for information on how to setup tftpd, pxes, dhcpd and any other dependancies so that this process will happen.

Does anyone have any idea on what I should do for this?

Has anyone been able to boot from freenx with thin clients?

Any and all information is greatly appreciated!

Bring on the documentation as well. I love to read! ;)

Thanks,
Kevin L.

---

### Post by Scubes13 on 2006-05-27
Ok, so I have made some progress. So, here is an update.

First, I needed to get tftpd up and running. So, on the Ubuntu Thin Client Server-to-be - I first used apt-get to install tftpd-hpa (server) and tftp-hpa (client - for testing)

```
# sudo apt-get tftpd-hpa tftp-hpa

```
(Note the following are a modified version of instructions found from Tero Karvinen at [http://myy.helia.fi/~karte/ubuntu_pxe.html](http://myy.helia.fi/~karte/ubuntu_pxe.html) )

So, next, I modified the tftpd-hpa configuration to force tftpd-hpa to run as a service (daemon) and to point to the directory that will house tftpd's downloadable files:

```
# sudo nano /etc/default/tftpd-hpa
```

I modified this file as follows:

```
RUN_DAEMON="yes"
OPTIONS="-l -s /home/pxe/"
```

Next, I created a user for the tftpd service as follows:

```
# sudo adduser pxe/
```

I now modified the user so that my normal user could modify the new pxe user's directory. Use your own username and group instead of tkarvine.

```
# whoami 
tkarvine
# sudo chown pxe.tkarvine /home/pxe/
# sudo chmod g+rwx /home/pxe
```

Now, we need to start the tftpd-hpa service:

```
# sudo /etc/init.d/tftpd-hpa start
```

Let's copy a file in the tftpd-hpa directory that we can test downloading and verify that the copy worked:
```
# cp /etc/default/tftpd-hpa /home/pxe
# ls /home/pxe/tftp*
 tftpd-hpa
```

And now let us test the tftpd-hpa service locally:
```

# cd ~
# tftp localhost -c get tftpd-hpa
# ls tftp*
 tftpd-hpa

```
If you see the file "tftpd-hpa" in the directory you connected to the tftpd-hpa server from, then your tftpd-hpa service is working correctly.

Now, we can clean up the two test files by removing the following:
```
# rm ~/tftpd-hpa
# rm /home/pxe/tftpd-hpa
```

That's all for setting up tftpd services.

Next, let's get our DHCP service working so that it points our PXE clients to the correct tftpd server and boot file.

For my DHCP services, I utilized pfSense on a local firewall. (I am using version 1.0-BETA3. Setting up pfSense from the ground up is outside the scope of this. See pfSense at [www.pfSense.org](www.pfSense.org) for tutorials, docs, etc.) In pfSense, click under Diagnostics, then click on Command.

First, we need to mount the working directory as writable for making our changes. In the command dialog, type the following:

```
# mount -w /
```

and press the "Execute" button.

Once the screen refreshes, we must edit the config.xml file. To do this, click again on the Diagnostics link and then click on Edit. In the "Save/Load from path:"  dialog, type:

```
# /cf/conf/config.xml
```

Once you press the "Load" button, you will be given access to edit the config.xml file. We must now make our changes to add the location of our tftpd-hpa server and the file for the PXE client to download.

First, find the section of the config.xml file that looks similar to the following:
```

        <dhcpd>
		<lan>
			<enable>yes</enable>
			<range>
				<from>192.168.1.25</from>
				<to>192.168.1.50</to>
			</range>
			<defaultleasetime/>
			<maxleasetime/>
			<failover_peerip/>
			<gateway/>
		</lan>
	</dhcpd>
```

Modify the above by adding in the following information:

```
        <dhcpd>
		<lan>
			<enable>yes</enable>
			<range>
				<from>192.168.1.25</from>
				<to>192.168.1.50</to>
			</range>
			<defaultleasetime/>
			<maxleasetime/>
			<failover_peerip/>
			<gateway/>
			<next-server>192.168.1.10</next-server>
			<filename>pxelinux.0</filename>
		</lan>
	</dhcpd>
```

As you can guess, the <next-server> __IP__ </next-server> line points the PXE client to the appropriate tftp server that hosts the PXE files.

The <filename> ___filename____ </filename> line tells the PXE client which file to download from the tftp server. As shown above, this is normally "pxelinux.0" when using PXE.

Now, once you have made these changes, press the "Save" button to save your configuration changes.

Next, we must mount the system as read-only once again. So, click on Diagnostics, then click on Command. In the Command dialog, type:

```
# mount -r /
```

and press the "Execute" button.

Although we have yet to configure PXES (as I am still trying to figure it out), we can still test to see if the DHCP server is pushing the correct information out to the PXE clients at boot-time. You should be able to fire up a PC (or even VM-Ware Player - hint, download VMWare Player and at boot time of the virtual machine, press F12 to do a PXE boot. This is nice if you do not have a PXE enabled network card.) If the PC supports PXE boot, then you should see something such as the following during boot-time:

```
TFTP.
PXE-T01: File not found
PXE-E3B: TFTP Error - File Not found
PXE-M0F: Exiting Intel PXE ROM.
Operating System not found
```

Do not worry if you receive a message like the above. Again, we have yet to setup PXE on the server, so there are no files there for the PXE client to download. Thus, no file found.

Whew, well... I am going to try to clean up some of the text from this post, and then I suppose I will continue playing around with PXES. I am very lost on the kernel building, configuration and so forth. If anyone wishes to help out, I welcome any and all assistance.

Basically, as I see it, the only thing left to do is build the kernel for the pxes boot and to configure the session correctly. Then it is a matter of copying the appropriate files to the tftpd hosted directory and testing with several PXE client machines.

Again, all input is welcome. Especially if I goofed something above. 

Thanks for reading,
Kevin L.

---

### Post by hakker.de on 2006-05-29
A very concise reading on this topic is:

[http://www.gentoo.org/doc/en/diskless-howto.xml](http://www.gentoo.org/doc/en/diskless-howto.xml)

though from another distro-camp, it is very distro-agnostic.

Basically, you need a boot-loader (normally a file called pxelinux.0 in $TFTPDIR from the syslinux package) which loads a boot configuration file (normally a file in $TFTPDIR/pxelinux.cfg/ and named like the MAC address of the client), which looks similar to a lilo config file.

The rest is like booting from harddisk.

---

