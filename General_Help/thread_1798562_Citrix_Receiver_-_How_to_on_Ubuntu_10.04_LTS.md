---
title: "Citrix Receiver - How to on Ubuntu 10.04 LTS"
date: 2011-07-06
forum: General Help
---

### Post by seawolf167 on 2011-07-06
Citrix Receiver - How to on Ubuntu 10.04 LTS

I had to install and get the Citrix Receiver working on a Ubuntu 10.04 LTS computer, the procedure for doing so is as follows. Please let me know if any clarification is needed, I got everything working 100% as far as I can tell.

The version details for this computer are:

```
Linux *computer-name *2.6.32-24-generic #43-Ubuntu SMP *time-stamp* i686 GNU/Linux
```To start with, do not attempt to use the Citrix Client running through Wine, it is absolute garbage, nothing was working for me.

Start off by downloading the items below, the latest compatible linux release of the Citrix client at the time of writing is 11.100. Note that the latest Windows release is 12.1.

You'll need to download and install two items. The first is "openmotif-2.3.3-1", which is an update from the current version available from the repos, which is "openmotif-2.2.3-4". The direct download link can be found [here]("http://www.motifzone.net/files/public_downloads/openmotif/2.3/2.3.3/openmotif-2.3.3-1.el5.3.i386.rpm") for "openmotif-2.3.3-1.el5.3.i386.rpm". Other versions for other distros can be found [here]("http://www.motifzone.net/filebrowser/openmotif/2.3/2.3.1").

The second item to download is the current Citrix Client, called the Citrix Receiver, available [here]("http://www.citrix.com/English/SS/downloads/details.asp?downloadID=3323#top"). I used the .deb file "icaclient_11.100_i386.patched.deb"

If you don't already have *alien*, you will need it to convert the openmotif .rpm file to a .deb file. This can be installed from the repos 

```
sudo apt-get install alien
```Start by changing your working directory to your download location, by default it is ~/Downloads

```
cd ~/Downloads
```Next, convert the openmotif .rpm package to a .deb (I got an warning when converting, but was safely able to ignore it)

```
sudo alien --to-deb openmotif-2.3.3-1.el5.3.i386.rpm
```and install

```
sudo dpkg -i openmotif-2.3.3-1.el5.3.i386.deb
```Then install the Citrix Receiver

```
sudo dpkg -i icaclient_11.100_i386.patched.deb
```You will have to accept the EULA when it comes up for it to continue. After the installation finishes, you can delete the .deb and .rpm files

```
rm openmotif-2.3.3-1.el5.3.i386.rpm
rm openmotif-2.3.3-1.el5.3.i386.deb
rm icaclient_11.100_i386.patched.deb
```The program will install under Applications -> Internet -> Citrix Receiver.

Your system administrator should also give you your company link so you can view your desktop. You will probably not have an "Outlook" icon (I didn't have one, even though it appeared under a Windows 7 install), but you can access the "Desktop" and from there view Outlook. I was able to use Firefox 3.6.18 successfully. I didn't try any other browsers as I ran out of time.

Make sure that you log out of your connection when you are finished or you will have issues when you are physically at the computer, as the desktop will be locked as in use.

Hopefully this helps anyone that needs to get it working and isn't sure where to start or what to do!

---

