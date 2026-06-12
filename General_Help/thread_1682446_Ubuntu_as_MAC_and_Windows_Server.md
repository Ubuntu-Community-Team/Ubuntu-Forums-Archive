---
title: "Ubuntu as MAC and Windows Server"
date: 2011-02-05
forum: General Help
---

### Post by ChasHutch on 2011-02-05
We three Mac Books, three Windows Laptops and a Ubuntu Desktop in use in our house.  All of these need to be backed up and have one place to put all user files. I have been running the beta and RC of Win 2008 (Vail) home server but have always had issues with easily having the MBPs connect to the usb external drives and I don't like the fact that there is additional "connector" software running on each machine and there is no automated backup for the macs.

Here is my question.  I would like to have a server running somewhere in the house (could be a VM) with USB drives attached that will easily and quickly allow both my mac and windows home users to have persistent drive attachment to backup their drives. The ability to store all of our media in one place would be nice too. I know Ubuntu desktop (or server) can do this but is there some software that is independent of the attaching OS (OSX or Windows) that can just be attached ONCE (even if it requires some SSO or login script) and stay connected with home drives for each user?

Thoughts?

---

### Post by ChasHutch on 2011-05-20
Nobody answered so I guess no one actually needs this information but... I found the solution and thought I would at least post a link:

If you want to use your ubuntu server to allow your macs access to the storage... [it's this easy]("http://missingreadme.wordpress.com/2010/05/08/how-to-set-up-afp-filesharing-on-ubuntu/"):

---

### Post by drdos2006 on 2011-05-20
I just saw your post, sounds interesting, would be interested in your comments once you get the network up and running.



Here is a networking HOWTO which I found comprehensive and invaluable for me. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop and run the server as a virtual machine using Virtualbox. It may be too late for you but every bit of knowledge helps.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood





```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

### Post by rg4w on 2011-05-20
> **ChasHutch said:**
> If you want to use your ubuntu server to allow your macs access to the storage... [it's this easy]("http://missingreadme.wordpress.com/2010/05/08/how-to-set-up-afp-filesharing-on-ubuntu/"):
Great link - thanks!

Much easier to setup than to read the grey-on-black text on that page. ;)

---

### Post by kevinthecomputerguy on 2011-05-21
Sounds like you wont need this info now, but incase you do, your Mac and Ubuntu clients can connect to windows shares no problem, if you type them like this
 
smb://192.168.1.100
 
Where 192.168.1.100 is the windows or **s**a**mb**a share machine your trying to connect to.
 
You can type that from any file choser windows in mac, or in Ubuntu open any folder and click on "Go" then "Location"
 
See pic
[http://woodel.com/page3_files/p3_image148.jpg](http://woodel.com/page3_files/p3_image148.jpg)

---

