---
title: "Update Error"
date: 2012-05-20
forum: General Help
---

### Post by RichieB07 on 2012-05-20
I tried to run Update Manager and got this error:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en%5fUS, E:The package lists or status file could not be parsed or opened.'

I found a solution online that invovled the /var/lib/apt/lists file, did it, and it worked for about an hour, but popped up again.  This is after a sudo apt-get update and upgrade.  This is the forum post I tried ( I tried the dpkg one and the rm one, neither work): [http://ubuntuforums.org/showthread.php?t=863742&page=8](http://ubuntuforums.org/showthread.php?t=863742&page=8)

Anyone know how to fix this?  It's on 64-bit 12.04.

---

### Post by RichieB07 on 2012-05-20
When I try to get into Synaptic, it throws up this error:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en%5fUS
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Hope that helps, cause I have no idea how to fix this.

---

### Post by RichieB07 on 2012-05-21
Anyone?  I can't get anything on my system to update because of this; no Update Manager, Synaptic, or even Ubuntu Tweak to update the Sources.

---

### Post by raja.genupula on 2012-05-21
open your terminal and paste this 

```
sudo rm -rf /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_i1 8n_Translation-en%5fUS

sudo apt-get update
```
let us know what you got :)

---

### Post by RichieB07 on 2012-05-21
> **raja.genupula said:**
> open your terminal and paste this 

```
sudo rm -rf /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_i1 8n_Translation-en%5fUS

sudo apt-get update
```let us know what you got :)

While it was updating, I saw this:

Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en_US         
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
  Bad header line
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
  Bad header line
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
  Bad header line

And at the end it posted all this:

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise InRelease: File /var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease: File /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease: File /var/lib/apt/lists/partial/ppa.launchpad.net_otto-kesselgulasch_gimp_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease: File /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_InRelease doesn't start with a clearsigned message
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease: File /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/precise/partner/source/Sources)  0  Ok [IP: 91.189.92.191 80]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  0  Ok

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/binary-amd64/Packages](http://archive.canonical.com/ubuntu/dists/precise/partner/binary-amd64/Packages)  0  Ok [IP: 91.189.92.191 80]

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_precise_partner_i18n_Translation-en%5fUS  Encountered a section with no Package: header

W: Failed to fetch copy:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en%5fUS  Encountered a section with no Package: header

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages)  0  Ok

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/jupiter/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/webupd8team/jupiter/ubuntu/dists/precise/main/source/Sources)  0  Ok

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/i18n/Translation-en_US](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/i18n/Translation-en_US)  Bad header line

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/i18n/Translation-en](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/i18n/Translation-en)  Bad header line

W: Failed to fetch copy:/var/lib/apt/lists/partial/ppa.launchpad.net_webupd8team_jupiter_ubuntu_dists_precise_main_i18n_Translation-en%5fUS  Encountered a section with no Package: header

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/jupiter/ubuntu/dists/precise/main/i18n/Translation-en](http://ppa.launchpad.net/webupd8team/jupiter/ubuntu/dists/precise/main/i18n/Translation-en)  Bad header line

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by raja.genupula on 2012-05-22
open your terminal and  paste them one by one 

```
sudp rm -rf /var/lib/apt/lists/*

sudo apt-get update
```

---

### Post by RichieB07 on 2012-05-22
> **raja.genupula said:**
> open your terminal and  paste them one by one 

```
sudp rm -rf /var/lib/apt/lists/*

sudo apt-get update
```

I'm pretty sure these are all the same errors, but it had this at the end:

W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease: File /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease: File /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise InRelease: File /var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease: File /var/lib/apt/lists/partial/ppa.launchpad.net_otto-kesselgulasch_gimp_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease: File /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_InRelease doesn't start with a clearsigned message
W: Failed to fetch copy:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_main_source_Sources  Encountered a section with no Package: header

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Index

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/precise/partner/source/Sources)  0  Ok [IP: 91.189.92.191 80]

W: Failed to fetch [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/dists/precise/main/source/Sources)  0  Ok

W: Failed to fetch copy:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_main_source_Sources  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_otto-kesselgulasch_gimp_ubuntu_dists_precise_main_i18n_Translation-en  Encountered a section with no Package: header

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/i18n/Index](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_precise_main_i18n_Index

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/jupiter/ubuntu/dists/precise/main/i18n/Index](http://ppa.launchpad.net/webupd8team/jupiter/ubuntu/dists/precise/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/ppa.launchpad.net_webupd8team_jupiter_ubuntu_dists_precise_main_i18n_Index

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by sikander3786 on 2012-05-22
Try again:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
```

And re-post the errors, if any. :)

---

### Post by RichieB07 on 2012-05-22
> **sikander3786 said:**
> Try again:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
```And re-post the errors, if any. :)

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease: File /var/lib/apt/lists/partial/ppa.launchpad.net_otto-kesselgulasch_gimp_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease: File /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease: File /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise InRelease: File /var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease: File /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_InRelease doesn't start with a clearsigned message
W: Failed to fetch copy:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_main_source_Sources  Encountered a section with no Package: header

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Index

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Index](http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_precise_partner_i18n_Index

W: Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_otto-kesselgulasch_gimp_ubuntu_dists_precise_main_i18n_Translation-en%5fUS  Encountered a section with no Package: header

W: Failed to fetch copy:/var/lib/apt/lists/partial/ppa.launchpad.net_otto-kesselgulasch_gimp_ubuntu_dists_precise_main_i18n_Translation-en  Encountered a section with no Package: header

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/source/Sources)  0  Ok

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/i18n/Index](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_precise_main_i18n_Index

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/jupiter/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/webupd8team/jupiter/ubuntu/dists/precise/main/source/Sources)  0  Ok

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/jupiter/ubuntu/dists/precise/main/i18n/Index](http://ppa.launchpad.net/webupd8team/jupiter/ubuntu/dists/precise/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/ppa.launchpad.net_webupd8team_jupiter_ubuntu_dists_precise_main_i18n_Index

E: Some index files failed to download. They have been ignored, or old ones used instead.


I thought it might have been some error cause of a setting in Firestarter, so I disabled the firewall and that didn't fix it either.

---

### Post by sikander3786 on 2012-05-22
Ok, please post the outputs:

```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d
```

---

### Post by RichieB07 on 2012-05-22
> **sikander3786 said:**
> Ok, please post the outputs:

```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d
```
[FONT=monospace][/FONT]
[FONT=monospace]cat output:
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main


ls output:
google-chrome.list.save
otto-kesselgulasch-gimp-precise.list
otto-kesselgulasch-gimp-precise.list.save
tualatrix-ppa-precise.list
tualatrix-ppa-precise.list.save
webupd8team-jupiter-precise.list
webupd8team-jupiter-precise.list.save

[/FONT]

---

### Post by sikander3786 on 2012-05-22
Ok, please try these commands one-by-one:

```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.bad
sudo mkdir -p lists/partial
sudo apt-get clean
cd
sudo apt-get update
```

We would get to the PPA errors later, once we figure out the more important ones.

---

### Post by RichieB07 on 2012-05-22
> **sikander3786 said:**
> Ok, please try these commands one-by-one:

```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.bad
sudo mkdir -p lists/partial
sudo apt-get clean
cd
sudo apt-get update
```We would get to the PPA errors later, once we figure out the more important ones.

After running that it let me run update manager, didn't throw out the huge list of errors, but after updating and running sudo apt-get update I still see this in the terminal:

Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en


Other than that, the huge list of errors seems to be gone.

---

### Post by sikander3786 on 2012-05-23
Everything is fixed then. For the 'Ign' thing, please take a look here:

[http://ubuntuforums.org/showthread.php?t=1553520](http://ubuntuforums.org/showthread.php?t=1553520)

In short, it is not an error.

---

### Post by RichieB07 on 2012-05-23
> **sikander3786 said:**
> Everything is fixed then. For the 'Ign' thing, please take a look here:

[http://ubuntuforums.org/showthread.php?t=1553520](http://ubuntuforums.org/showthread.php?t=1553520)

In short, it is not an error.

Thanks for all your help.  I noticed this all happened when I installed the PPA for GIMP 2.8, but now that I could update I got rid of that PPA and nothing it wrong now.  Guess there's a reason Canonical reviews things before they go into the Software Center, haha.

---

### Post by amittan on 2012-08-28
Finding similar problem and it is not solved by cleaning the lists and other steps mentioned in below chain.
Please help. Here I am sending outputs for reference.
cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

$ ls /etc/apt/sources.list.d >> shows nothing

---

### Post by TommyMiles on 2013-05-07
Getting same errors.  Went through steps above and "Failed to fetch"/ "Encountered a section with no Package: header" errors appear on these translation files from two different sources. This is the second day running this install (12.04, 2D), and second day of having to clean out lists/sources, various advice from these forums and elsewhere (suggesting I'm not alone in this).  Regardless, these particular files always seem to break, then brings down Software Center on start.  Same files tagged in errors when firefox trys to get Flash plugin. 

Here's just the errors from sudo apt-get update

> W: Failed to fetch gzip:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en%5fUS  Encountered a section with no Package: header


W: Failed to fetch gzip:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en  Encountered a section with no Package: header


W: Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_ravefinity-project_ppa_ubuntu_dists_precise_main_i18n_Translation-en  Encountered a section with no Package: header


W: Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_tiheum_equinox_ubuntu_dists_precise_main_i18n_Translation-en%5fUS  Encountered a section with no Package: header


W: Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_tiheum_equinox_ubuntu_dists_precise_main_i18n_Translation-en  Encountered a section with no Package: header


W: Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_precise_main_i18n_Translation-en%5fUS  Encountered a section with no Package: header


W: Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_precise_main_i18n_Translation-en  Encountered a section with no Package: header


E: Some index files failed to download. They have been ignored, or old ones used instead.










> **amittan said:**
> Finding similar problem and it is not solved by cleaning the lists and other steps mentioned in below chain.
Please help. Here I am sending outputs for reference.
cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

$ ls /etc/apt/sources.list.d >> shows nothing

---

### Post by TommyMiles on 2013-05-07
And here's what happens when software-center starts/crashes

> 2013-05-07 12:20:50,306 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-05-07 12:20:50,309 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-05-07 12:20:50,532 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-05-07 12:20:50,623 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-05-07 12:20:50,873 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 243, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 145, in open
    self._cache = apt_pkg.Cache(progress)
SystemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_ravefinity-project_ppa_ubuntu_dists_precise_main_i18n_Translation-en%5fUS, E:The package lists or status file could not be parsed or opened.
2013-05-07 12:20:52,539 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 176, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1422, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1352, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 154, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 171, in init_view
    self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 238, in __init__
    self.build(desktopdir)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 511, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 271, in _build_homepage_view
    self._append_whats_new()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 450, in _append_whats_new
    whats_new_cat = self._update_whats_new_content()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 439, in _update_whats_new_content
    docs = whats_new_cat.get_documents(self.db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 124, in get_documents
    nonblocking_load=False)
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 317, in set_query
    self._blocking_perform_search()
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 212, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'


Note this bit:

> SystemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_ravefinity-project_ppa_ubuntu_dists_precise_main_i18n_Translation-en%5fUS, E:The package lists or status file could not be parsed or opened.


---

### Post by TommyMiles on 2013-05-07
And here's what happens when software-center starts/crashes (mk.II, as forums replaces code with smiley faces unless box checked.  Might be something else you'll want to look into.)

> 2013-05-07 12:20:50,306 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-05-07 12:20:50,309 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-05-07 12:20:50,532 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-05-07 12:20:50,623 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-05-07 12:20:50,873 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 243, in open
self._cache = apt.Cache(GtkMainIterationProgress())
File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
self.open(progress)
File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 145, in open
self._cache = apt_pkg.Cache(progress)
SystemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_ravefinity-project_ppa_ubuntu_dists_precise_main_i18n_Translation-en%5fUS, E:The package lists or status file could not be parsed or opened.
2013-05-07 12:20:52,539 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
if (not pkgname in self.cache and
File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
File "/usr/bin/software-center", line 176, in <module>
app.run(args)
File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1422, in run
self.show_available_packages(args)
File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1352, in show_available_packages
self.view_manager.set_active_view(ViewPages.AVAILABLE)
File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 154, in set_active_view
view_widget.init_view()
File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 171, in init_view
self.apps_filter)
File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 238, in __init__
self.build(desktopdir)
File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 511, in build
self._build_homepage_view()
File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 271, in _build_homepage_view
self._append_whats_new()
File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 450, in _append_whats_new
whats_new_cat = self._update_whats_new_content()
File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 439, in _update_whats_new_content
docs = whats_new_cat.get_documents(self.db)
File "/usr/share/software-center/softwarecenter/db/categories.py", line 124, in get_documents
nonblocking_load=False)
File "/usr/share/software-center/softwarecenter/db/enquire.py", line 317, in set_query
self._blocking_perform_search()
File "/usr/share/software-center/softwarecenter/db/enquire.py", line 212, in _blocking_perform_search
matches = enquire.get_mset(0, self.limit, None, xfilter)
File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
if (not pkgname in self.cache and
File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'


Note this bit:

> SystemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_ravefinity-project_ppa_ubuntu_dists_precise_main_i18n_Translation-en%5fUS, E:The package lists or status file could not be parsed or opened.


---

### Post by TommyMiles on 2013-05-07
Just did this 


```
sudo rm /var/lib/apt/lists/ppa.launchpad.net_ravefinity-project_ppa_ubuntu_dists_precise_main_i18n_Translation-en%5fUS



``` 

And problem fixed.  Until of course apt-get downloads that file again from ppa.launchpad.net_ravefinity-project_ppa_ubuntu_dists_precise_main...

---

