---
title: "synaptic package manager dpkg"
date: 2009-10-03
forum: General Help
---

### Post by linkingeek on 2009-10-03
By mistake i deleted my dpkg folder from var>lib>dpkg and now problems are pouring in 
now whenever i open synaptic manager it shows errors 

E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

please help, i am now in big problem
i also downloaded "synaptic-0.57.tar.gz" from synaptic website but terminal.
./configure works but "make install" gives following:
make: *** No rule to make target `install'.  Stop.

---

### Post by drs305 on 2009-10-03
> **linkingeek said:**
> E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Can you retrieve the folder from the Trash bin (/root/.local/share/Trash)?

Although your problem may be bigger, the first step is probably to try and restore the lists. You can do this by opening Synaptic. Go to Settings > Repositories. In the Ubuntu Software *and* Other/Third Party tabs:
Note which ones are currently selected, then deselect them. 
Reload, then reselect each of the repositories that were previously enbabled and Reload again. 
Note: The first "Reload" is probably not necessary and may even generate a message, but that is ok. Just continue.

This should remove the existing lists, if there are any, and recreate them by downloading new ones.
You will still be missing the /var/lib/dpkg/status file, which will probably generate an error message.
You can create a new status file with the following command, although it will be an empty file:
```

sudo touch /var/lib/dpkg/status

```
The problem is that this file, while deleting the error message, will not provide meaningful information on the status of your installed apps. Normally you could restore the status-old file, but that would have also been deleted when you removed the folder.

There is a command to restore the contents of the status file but it escapes me at the moment and I have to log off. Someone will be able to provide it.  If not, I'll be back in about ten hours.

---

### Post by linkingeek on 2009-10-03
problem is synaptic package manager closes by itself after the dialog of errors,
after deselecting and resecting software sources i got this.

E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_jaunty_main_binary-amd64_Packages)

---

### Post by drs305 on 2009-10-03
Sorry nobody has posted a solution, but I'm back and should be able to help.

The original error message said the problem was with the *lists* file and/or a bad/missing status file. Any missing or corrupted "list" files should have been corrected by deselecting and reselecting them in Synaptic.

For the missing *status* file, the instructions in the previous post would not have fully restored things.

First, have you recreated the dpkg folder already. I didn't ask that previously? If not, we will create it. Then we can restore an older copy of your dpkg *status* file.

You will have to open a terminal: Applications, Accessories, Terminal. Then run these commands:
```

sudo mkdir /var/lib/dpkg  # create dpkg folder if it doesn't exist
sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status # restore a backup *status* file
sudo dpkg --clear-avail  # will create a new, but empty, available file in /var/lib/dpkg
sudo apt-get update
sudo apt-get upgrade

```

Running these commands may restore your system. Deleting the dpkg folder removed many more files than just these. If you still get errors, post them and it's possible we will be able to restore some of the others.

---

### Post by linkingeek on 2009-10-03
terminal popped up with 
dolphin@ubuntu:~$ sudo apt-get --clear-avail
E: Command line option --clear-avail is not understood

also,in previous reply 
W: Duplicate sources.list entry [http://ppa.launchpad.net]("http://ppa.launchpad.net/") jaunty/main Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_jaunty_main_binary-amd64_Packages)

this message popped up by "software resources" and i copied "ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_jaunty_main_binary-amd64_Packages" file to /var/lib/dpkg/ and renamed it as status it also solved the problem of not opening "synaptic" 
but it forgot the previous installed markings for software.
By the way your command worked ->
sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status


Thamks,to tell about the backup file this will help in future.

---

### Post by drs305 on 2009-10-03
Sorry, sudo dpkg --clear-avail.  It's late here.

I can't tell if you still have a problem or if everything is resolved. As I said, it's late.   ;-)

*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by linkingeek on 2009-10-03
i was installing sun-java bin
this came up->
[http://www.flickr.com/photos/22600413@N06/3978311589/](http://www.flickr.com/photos/22600413@N06/3978311589/)
[IMG]http://www.flickr.com/photos/22600413@N06/3978311589/[/IMG]

---

### Post by drs305 on 2009-10-03
These are some of the folders/files I said would still be missing. 

You can create them with the following command. Whether just having an empty folder will be sufficient we will have to see:
```

sudo mkdir /var/lib/dpkg/updates

```

You can recreate other folders in /var/lib/dpkg with similar commands. Again, all you are doing is recreating an empty folder, which may or may not satisfy the requirements. Upon finding the folder, it may search for a file within, which of course won't exist.

---

### Post by linkingeek on 2009-10-03
after creating folder 
this came up while installing
[http://www.flickr.com/photos/22600413@N06/3978331499/](http://www.flickr.com/photos/22600413@N06/3978331499/)
[IMG]http://www.flickr.com/photos/22600413@N06/3978331499/[/IMG]

---

### Post by drs305 on 2009-10-03
At some point we will solve this or reach a point where a reinstall is required. These messages are being created by packages already downloaded and residing in the archive folders. 

If you clear the archives, the error messages may go away and when you download the files again APT may properly register them.

```
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade
```

The command 
```
dpkg --reconfigure -a
```
may also clear things up, but it also may break things. I just don't know based on the current state of your system.

---

