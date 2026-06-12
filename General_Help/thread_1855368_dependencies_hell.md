---
title: "dependencies hell"
date: 2011-10-06
forum: General Help
---

### Post by Drenriza on 2011-10-06
Hi all.

If i have a package installed, how can i check what packages it depends on (dependencies)?
I ask this because i have a system disconnected from the web, and i would like to download some packages and ship it to the system. But i also need the packages dependencies, how do i do this?

Thanks on advance.
Kind regards.

---

### Post by elliotn on 2011-10-06
use Keryx it downloads parkages with all depends, or u can use dpkg-repack (check the How to) somewhere in the forums

---

### Post by EthioJOB on 2011-10-06
Open Synaptic (System > Administration > Synaptic Package Manager) and look for the package you want to install (or already installed). If uninstalled, good; right-click and select mark for installation. 

Then a dialog box will come informing you of other necessary dependencies that need to installed as well. Select OK, apply or whatever and it will mark all the necessary packages and dependencies that need to be installed. 

Then go to File > Generate download script and select the location (flash drive) where you want that script placed. Then you take that script - preferably to a internet connected linux pc - and double click the script. Select Run in terminal, and it will download all the packages in the location where the script is found. 

If the connected PC is windows, then simply open the script with notepad and copy-paste each of the links in seperate windows/tabs of the browser and the packages will be downloaded directly.

Then you take the packages back to your system and open Synaptic, then go to File > Add downloaded packages (or something like that) and direct it to the folder where the packages are found. 

NB- The packages will appear dim. Its ok. Also you may need to wait for a little while as it may take some time depending on the size of the packages.

Then a dialog box will appear asking for your confirmation of the installation of packages,  which you will accept (or apply).

Then all you have to do is wait while synaptic does it job.

Of course, synaptic must be updated. 

Another option is to open synaptic and locate the package you installed, right-click and select properties and select the dependencies tab. It will list all the dependencies. keryx is good for ubuntu 10.04, but it got a little to complicated for me on 10.10 (an installable version as executables were disabled).

---

### Post by elliotn on 2011-10-06
sudo apt-get -s install packagename

then the list of dependencies to be installed will appear but that won't list the already installed dependencies

---

### Post by Drenriza on 2011-10-06
i need to do this from the command line since it has no GUI installed.
I found this guide [http://ubuntuforums.org/showthread.php?t=819396&highlight=dpkg-repack](http://ubuntuforums.org/showthread.php?t=819396&highlight=dpkg-repack) but isn't their a way to specify what packages you want to "backup for transfer" instead of ALL system packages and their dependencies.

---

