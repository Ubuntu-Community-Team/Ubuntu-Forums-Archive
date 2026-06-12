---
title: "Update Manager Problems"
date: 2012-05-08
forum: General Help
---

### Post by CrsHrs on 2012-05-08
Hey guys, ever since I updated my O.S. (to like 12.1 I think, it was the most recent update) now I keep getting the "do not enter" symbol on my task bar (upper right.) It says about an error with the update manager and now I can not open it to update anything. Anyone know the problem and/or how to fix it?
-Chris

---

### Post by Enigmapond on 2012-05-08
Sounds like a broken package...need more info. Like, the error...

---

### Post by plucky on 2012-05-08
> **CrsHrs said:**
> Hey guys, ever since I updated my O.S. (to like 12.1 I think, it was the most recent update) now I keep getting the "do not enter" symbol on my task bar (upper right.) It says about an error with the update manager and now I can not open it to update anything. Anyone know the problem and/or how to fix it?
-Chris

Open a terminal (CTRL+ALT+T) and run ```
sudo apt-get update
``` and post the output.

Good Luck

---

### Post by CrsHrs on 2012-05-08
W: Failed to fetch gzip:/var/lib/apt/lists/partial/www.bashterritory.com_pytube_releases_Packages  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.

^that was the end result
-Chris

---

### Post by codingman on 2012-05-08
I think that you have some broken packages and it is best to reinstall, or edit root and go risky.

---

### Post by CrsHrs on 2012-05-08
how would I re-install. Like re-do the whole O.S. with the boot disk? I hope to God not. 
-Chris

---

### Post by plucky on 2012-05-08
> **CrsHrs said:**
> W: Failed to fetch gzip:/var/lib/apt/lists/partial/www.bashterritory.com_pytube_releases_Packages  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.

^that was the end result
-Chris

Open a terminal and delete the files in that directory with ```
sudo rm /var/lib/apt/lists/partial/* -vf
``` Then run ```
sudo apt-get update
```

and post the full output.

Did you try to do a Partial Update?


> I think that you have some broken packages and it is best to reinstall, or edit root and go risky. 

Better to learn how to fix the system rather than re-installing.
Use re-installing as a last resort.
If you have nothing useful to say,better say nothing.

---

### Post by CrsHrs on 2012-05-08
Please help the helpless geek here!

---

### Post by vegarend on 2012-05-08
I've seen this before when dependencies are broken, maybe the icon appears for other reasons as well. Anyways I would try one of these in terminal:

```
 sudo apt-get autoclean 
```
```
 sudo aptitude autoclean 
```

In my experience aptitude has a better understanding of packages and dependencies and is most likely to work. It is not installed by default I think, so you will have to do that:

```
 sudo apt-get install aptitude 
```

---

### Post by CrsHrs on 2012-05-08
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/www.bashterritory.com_pytube_releases_en
E: The package lists or status file could not be parsed or opened.

I can't even do the sudo aptitude autoclean
I swear I have the worst luck with Linux

-Chris

---

### Post by drs305 on 2012-05-08
Try this to clear the error. Be careful with this command, as a typo can seriously damage your system:

```
sudo rm /var/lib/apt/lists/www.bashterritory.com_pytube_releases_en
sudo apt-get clean  && sudo apt-get update
```

If you still have problems, deselect the bashterritory repository: 
Update-Manager > Settubgs > Other Software, If you have Ubuntu Tweak installed, you can also edit repositories from there.

---

### Post by CrsHrs on 2012-05-08
rm: cannot remove `/var/lib/apt/lists/www.bashterritory.com_pytube_releases_en': No such file or directory

^I got this error.

I can't even get into the Update Manager I receive this message, this might help you though.

[I]An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/www.bashterritory.com_pytube_releases_en%5fUS, E:The package lists or status file could not be parsed or opened.'[/I]

---

### Post by drs305 on 2012-05-08
Open a file manager as root and investigate the folder to see if the file (or variation) is there:
```
gksu nautilus /var/lib/apt/lists/
```

---

### Post by vegarend on 2012-05-09
I've seen a slightly modified version of plucky's suggestion in another forum:

```

sudo rm /var/lib/apt/lists/* -vf

```

You can try that followed by apt-get clean/autoclean/update.

---

### Post by CrsHrs on 2012-05-12
Its gotten to the point I can't even open the software center, it keeps failing and I cannot send a crash report because it failing as well.

---

### Post by drs305 on 2012-05-12
Don't know if you have done everything already suggested, but here are some things you can try if you haven't already. This time we'll use a GUI app.

Open nautilus as root and these folders:
```
gksu nautilus  /var/lib/apt/lists/ /var/cache/apt/archives /var/lib/dpkg /etc/apt/ &

```

1. In the /var/lib/apt/lists folder, delete everything but the 'partial' folder. If there is a 'lock' file, make sure you don't have Synaptic, Update Manager or Ubuntu Software Center open.

2. In the /var/cache/apt/archives folder, delete everything except the partial folder, then open partial and delete anything therein.

3. Go to the /var/lib/dpkg/ folder. Rename "status" to "status-bad", make a copy of "status-old" and then rename the original "status-old" to "status".

4. In the /etc/apt folder, rename the sources.list.d folder to something else to 'deactivate' all your extra repositories.

Run the following to clean out any residual files:
```
sudo apt-get clean autoclean autoremove
```

Try running your updates again and see if there is any improvement. If not, reverse steps 3 & 4, and give us the exact error messages you are still receiving.

---

### Post by CrsHrs on 2012-05-14
I tried to run update manager and then when I checked for updates it said it could not download repository.

---

### Post by CrsHrs on 2012-05-14
This is the update manager problem

W:GPG error: [http://www.bashterritory.com](http://www.bashterritory.com)  InRelease: File /var/lib/apt/lists/partial/www.bashterritory.com_pytube_releases_InRelease doesn't start with a clearsigned message, W:Failed to fetch gzip:/var/lib/apt/lists/partial/www.bashterritory.com_pytube_releases_Packages  Encountered a section with no Package: header
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by drs305 on 2012-05-14
In Step 1 of my previous post I didn't tell you to enter the 'partial' folder and delete the contents there as well, but you should.

---

### Post by raja.genupula on 2012-05-14
have you tried #14 , it will remove all the old cache and creates a new cache for you .
try it .

let us know what you got .

---

### Post by matt_symes on 2012-05-14
Hi


Check you sources files as well.


[www.bashterritory.com](www.bashterritory.com) does not point to a repository. Type it into a browser and see.


Can you post the output of


```
grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```


If the terminal bothers you then we can instruct you on how to get that information using the GUI.


Kind regards

---

### Post by CrsHrs on 2012-05-15
When I try to check for updates I receive this error
Failed to load the package list

This is a serious problem. Try again later. If this problem appears again, please report an error to the developers.

E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/www.bashterritory.com_pytube_releases_Packages, E:The package lists or status file could not be parsed or opened.

---

### Post by matt_symes on 2012-05-15
Hi

Can you post the output from post #21 please.

Kind regards

---

### Post by CrsHrs on 2012-05-20
/etc/apt/sources.list:
/etc/apt/sources.list:# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
/etc/apt/sources.list:# newer versions of the distribution.
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list:## distribution.
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list:## review or updates from the Ubuntu security team.
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list:## security team.
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list:## or updates from the Ubuntu security team.
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list:## 'partner' repository.
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list:# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
/etc/apt/sources.list:# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
/etc/apt/sources.list:
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by third-party
/etc/apt/sources.list:## developers who want to ship their latest software.
/etc/apt/sources.list:deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
/etc/apt/sources.list:deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
/etc/apt/sources.list:deb [http://www.bashterritory.com/pytube/releases/](http://www.bashterritory.com/pytube/releases/) /
/etc/apt/sources.list:deb [http://www.bashterritory.com/pytube/releases/](http://www.bashterritory.com/pytube/releases/) /
/etc/apt/sources.list:
/etc/apt/sources.list:
/etc/apt/sources.list:
grep: /etc/apt/sources.list.d/*: No such file or directory

Sorry here it is.

---

### Post by Joseph Rudolf on 2012-05-20
Good mrng...

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 531EE72F4C9D234C
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

I always got this message whenever I run updates... please help.. Thx.

Rudolf

---

### Post by MoebusNet on 2012-05-20
I had what seems to be the same problem:

[http://ubuntuforums.org/showthread.php?t=1983220](http://ubuntuforums.org/showthread.php?t=1983220)

What worked for me was what 2F4U came up with in post #2 of the thread:

```
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update
```

---

### Post by matt_symes on 2012-05-22
Hi

@CrsHrs

Here is you problem. It's in your sources.list file.

> deb [http://www.bashterritory.com/pytube/releases/](http://www.bashterritory.com/pytube/releases/) /
deb [http://www.bashterritory.com/pytube/releases/](http://www.bashterritory.com/pytube/releases/) /

Press Alt + F2 together and type 

```
gksudo gedit /etc/apt/sources.list
```

Remove the last 2 lines that contain bash territory. Save the file and then from the terminal type

```
sudo apt-get update
```

Kind regards

---

### Post by matt_symes on 2012-05-22
Hi

> **Joseph Rudolf said:**
> Good mrng...

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 531EE72F4C9D234C
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

I always got this message whenever I run updates... please help.. Thx.

Rudolf

@Joseph Rudolf

You are missing some GPG keys used to verify those ppas. Open a terminal and type..

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 531EE72F4C9D234C
```

Enter your password. It will not be echoed to the screen.

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5A9A06AEF9CB8DB0
```

```
sudo apt-get update
```

Kind regards

---

### Post by voicesinthefan on 2012-05-22
> **MoebusNet said:**
> I had what seems to be the same problem:

[http://ubuntuforums.org/showthread.php?t=1983220](http://ubuntuforums.org/showthread.php?t=1983220)

What worked for me was what 2F4U came up with in post #2 of the thread:

```
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update
```

This fixed it for me as well.

---

