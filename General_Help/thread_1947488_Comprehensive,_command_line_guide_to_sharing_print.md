---
title: "Comprehensive, command line guide to sharing printer from server"
date: 2012-03-26
forum: General Help
---

### Post by bpb_21 on 2012-03-26
Is there a really good, comprehensive guide out there for setting up and sharing (only on one's local network) a USB attached printer from Ubuntu Server 11.10, only using the command line on the server?  I haven't found anything in the official documentation or the community documentation that distinguishes between "sharing" a printer "on the network" and setting up a "shared, network-enabled" printer (two separate scenarios).

I'm trying to learn how to be proficient on the command line and for the past couple of months it's been a complete disaster.  So far I've managed to set up an HP Officejet 5610, connected via USB, to a Ubuntu Server 11.10, and it will print from a Windows 7 client, but printing from a Ubuntu 11.10 client keeps asking for some autentication I don't remember setting up or having (all possible user passwords have been tried and failed).  Scanning from this MFD is impossible (well, it's possible but not for me on the command line).

I'd really like to learn this, but I'm not finding the resources I need.  Any and all help is always appreciated.

---

### Post by norima on 2012-03-27
,would be a great help for me either...

---

### Post by norima on 2012-03-27
well, im using the kubuntu 11.10 and my kubuntu 11.10 client is seeing the shared printer but just wont work (wew) i think i need a little sleep...

---

### Post by bpb_21 on 2012-03-27
What, I think, would really help would be "example" configuration files.  Like an example smb.conf set up for sharing a printer to all on one's local network (but no outside access).  Assuming a fresh install of the server environment (which you would have to do) one could post common initial configurations like this for various typical setups.
Anyway, just a thought.  I've reinstalled my server again (good thing I have my actual data on another drive) and am making headway, but it could be more streamlined.

---

### Post by drdos2006 on 2012-03-27
In a terminal, run:
sudo gedit /etc/cups/cupsd.conf

Look for : 
# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all

Add the following line:
	BrowseProtocols all
You may also have to change this next section in your cupsd.conf file

# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock
Listen 192.168.1.12:631

(192.168.1.12 is the IP address of the machine with the printer on it, 631 is the port number to listen on).

From the client machine on the network try to connect to the networked printer using IPP to the IP address of the server machine, verify the printer is shared, download the drivers.

I am running Ubuntu 10.4 LTS.

regards

---

