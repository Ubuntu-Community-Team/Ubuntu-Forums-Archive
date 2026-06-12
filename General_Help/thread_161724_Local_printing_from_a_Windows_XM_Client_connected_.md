---
title: "Local printing from a Windows XM Client connected to a freenx server"
date: 2006-04-17
forum: General Help
---

### Post by rvergara on 2006-04-17
I am running freenx under 5.10. I can connect from a remote Windows XP client without any problem. However I am not able to print using a local priter connected to the LAN where the Windows client is connected to.

I have set up "enable printer and file sharing" in the No Machine software running in the Windows XP client. This is done in Configure->Services.

According to the documentation i should get a dialog prompt when connecting to the freenx server:

"When connected to the remote server a dialog will ask you to select your printer driver from the list of drivers detected on the system. Please choose the appropriate model of your printer from the list."

A complete procedure on this in the following link: [http://www.nomachine.com/ar/view.php?ar_id=AR01C00136](http://www.nomachine.com/ar/view.php?ar_id=AR01C00136)

After not being able to print locally and exploring the whole NoMachine site, I found the following in the administrator´s guide:

"Sharing Files and Printers

If you want to enable additional services, like printing and file- system access from clients using the SMB protocol, please remember that the 'setuid' bit must be set on the 'smbmnt' and the 'smbumount' binaries on the server. The binaries are usually located in the /usr/bin directory. You can set the setuid bit by running the command 'chmod u+s ' for any of the files that are to be changed."

I changed the setuid in both smbmnt and smbumount to no avail.

Has anybody being able to print to a local print from a Windows XP client connected to an Ubuntu freenx server?

Any help would be appreciated.

Regards


Ramiro

---

### Post by rvergara on 2006-04-18
freenx anybody???

I really need to solve this issue.

Regards

Ramiro

---

### Post by rvergara on 2006-04-26
I cannot believe I am the only ubuntu user trying to locally print from a remote windows XP client connected to an Ubuntu freenx server.

Help!!!!

Thanks

Ramiro

---

### Post by rvergara on 2006-05-06
Apparently, this most needed feature to use Linux servers as application server in the enterprise has not been resolved/tried much in the community since I got no replies.

After spending a good number of days trying different possibilities I came up with the following solution. It is a good working solution although no final as I explained down in the note. I will also submit a How To with this info but I thought it was a good idea to post it here in the original thread. Here it is:

Freenx has opened a whole new set of possibilities for deployment of enterprise applications. Any thin client can remotely access enterprise applications running in a central freenx server via Internet and still have good to excellent performance. However in order to fully realize the benefits of this solution, it is required that the remote clients have local printing capability.

Local printing is not functional for Gnome (nor KDE) based Ubuntu freenx servers out of the box and but is the intention of this how to, explain how to get this capability set up. The solution is not final and still require fine tuning as I will explain later in this note. I am sure than a more experienced user than I will be able to refine the solution.

I will assume that Freenx is already installed, if not you can follow instructions in the following thread [http://www.ubuntuforums.org/showthread.php?t=97277]("http://www.ubuntuforums.org/showthread.php?t=97277")
It is also assumed that you have previously installed Samba in your system (you specifically need smbfs installed)

1. Configure your windows client to share printer and folders
Open your No Machine client and click on the configure button, go to the services tab and tick the share printer and folders field. click on the add button and you will see a listing of printers and folders that you have previously shared in your windows XP PC. Select the printer that you want to use to print locally and click OK.

2. Install the Linux driver for your local printer
Yes, you need to install the linux driver for the printer that the windows XP client needs for lo çcal printing, this may sound a bit acward but it absolutely required. Check first if you already have the driver required in your Ubuntu freenx server, if you do not know how to do that just try to install a new printer in System->Administration->Printers and advance until you are asked for a make and model of the printer. If your specific printer is there you are do not need to do anything else and you can proceed to step 3. If you did not find your specific driver, do not panic, go to [http://www.linuxprinting.org]("http://www.linuxprinting.org") and click on the driver listing. Find your driver and follow the instructions for installation in your Ubuntu server.

3. Fix the nxnode.conf file

Open a terminal and type the following:

```
gksudo nautilus
```

drill down to ->usr->lib->nx, right click on nxnode.conf and open with gedit (text editor). click on file and save as oldnxnode.conf or any other name of your choosing. This will just be a back up of your original file just in case you need it. go to lines 800, 803 and 833 and delete the option "-noautokill" in each one of those sentences.

Go again to file and save as nxnode.conf, close gedit, right click on nxnode.conf and click on properties, tick execute for user, group and others.

4. Open cups ports
This is the one needing refinement. cups read by default port 631 only. Your freenx sessions use ports 10000 and on. For gnome to listen to these ports and automatically configure your shared windows printer you need to open these ports. using nautilus browse to /etc/cups/cups.conf, open it with gedit and enter the following code around line 450 and include one line per port as follows:

```
Port 10000
Port 10001
Port 10002
Port 10003
```

etc.

Since I was planning to have a maximum of 4 different sessions I did not include more ports to be opened. However this is not a good solution, one port should be dynamically opened for every session in order to limit exposure. I am sure that somebody from the Ubuntu community will come up with a smart solution to refine this setting.

5. set setuid for smbmnt and smbumount
Using your gksudo nautilus session opened in step 3, drill down to /usr/bin/smbmnt and smbumount in the same path. Right click on each of both files and click on properties, choose the access tab and tick the setuid box. close the properties windows

6. Reset your cups and samba service
I just go to system->services and untick and tick the cups and samba services, this will force the cups service to read cups.conf and the samba access settings again.

You are done, your printer should be now set and it will show up when you select print from any application running in your Ubuntu Freenx server and being accessed from a No Machine windows client. When the newly windows printer is selected, the output will be forwarded automatically to this printer.

Hope this helps.

Regards

Ramiro

---

