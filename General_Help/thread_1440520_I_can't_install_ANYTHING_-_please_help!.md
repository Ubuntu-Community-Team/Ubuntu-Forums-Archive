---
title: "I can't install ANYTHING - please help!"
date: 2010-03-27
forum: General Help
---

### Post by Singer&amp;Cal on 2010-03-27
Hi,
 
I'm trying to install some applications on my new Kubuntu 8.04 system, but apt-get, aptitude and all the other install/remove programs fail to get the package listings. Apt-get always says, "Could not resolve wingen8". I have tried everything perscribed for any problem with apt-get, but nothing helps.](*,) Help would be greatly appreciated...
 
Thanks in advance,
Cal (age 10)

---

### Post by s_ø on 2010-03-27
Are you certain about the "could not resolve wingen8" message. A quick google gives no results.
Is it a fresh install?

---

### Post by darolu on 2010-03-27
What do you get with:
```
$ sudo apt-get update
```

---

### Post by drs305 on 2010-03-27
Do you know what "wingen8" is?

If not, open your text editor as root (kdesu ...) and check the contents of /etc/resolve.conf and /etc/hosts and see if you have an entry for wingen8. If so, at least temporarily place a comment symbol at the start of the line and save the file. Run "sudo apt-get update" and see if it updates correctly.

If *wingen8* isn't mentioned in either of those two files, check /etc/apt/sources.list.

---

### Post by Singer&amp;Cal on 2010-03-27
Thanks for your help! I haven't seen any forum where the people respond as fast as you do!

s_ø: It's only applicable to my system. But I don't know what it's used for...:-k

darolu: Here's what I get when I use the command you suggested:

```
[sudo] password for calvin:
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release.g
pg
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Tran
slation-en_US
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricte
d Translation-en_US
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Pack
ages
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricte
d Packages
Err cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Pack
ages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update can
not be used to add new CD-ROMs
Err cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricte
d Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update can
not be used to add new CD-ROMs
Err http://archive.canonical.com hardy Release.gpg
  Could not resolve 'wingen8'
Err http://archive.canonical.com hardy/partner Translation-en_US
  Could not resolve 'wingen8'
Err http://us.archive.ubuntu.com hardy Release.gpg
  Could not resolve 'wingen8'
Err http://us.archive.ubuntu.com hardy/main Translation-en_US
  Could not resolve 'wingen8'
Err http://us.archive.ubuntu.com hardy/restricted Translation-en_US
  Could not resolve 'wingen8'
Err http://us.archive.ubuntu.com hardy/universe Translation-en_US
  Could not resolve 'wingen8'
Err http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
  Could not resolve 'wingen8'
Err http://us.archive.ubuntu.com hardy-backports Release.gpg
  Could not resolve 'wingen8'
Err http://us.archive.ubuntu.com hardy-backports/main Translation-en_US
  Could not resolve 'wingen8'
Err http://us.archive.ubuntu.com hardy-backports/restricted Translation-en_US
  Could not resolve 'wingen8'
Err http://us.archive.ubuntu.com hardy-backports/universe Translation-en_US
  Could not resolve 'wingen8'
Err http://us.archive.ubuntu.com hardy-backports/multiverse Translation-en_US
  Could not resolve 'wingen8'
Err http://archive.ubuntu.com hardy Release.gpg
  Could not resolve 'wingen8'
Err http://archive.ubuntu.com hardy/main Translation-en_US
  Could not resolve 'wingen8'
Err http://archive.ubuntu.com hardy/restricted Translation-en_US
  Could not resolve 'wingen8'
Err http://archive.ubuntu.com hardy/universe Translation-en_US
  Could not resolve 'wingen8'
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg
Could not resolve 'wingen8'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Tra
nslation-en_US.bz2  Could not resolve 'wingen8'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i1
8n/Translation-en_US.bz2  Could not resolve 'wingen8'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n
/Translation-en_US.bz2  Could not resolve 'wingen8'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i1
8n/Translation-en_US.bz2  Could not resolve 'wingen8'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/Rel
ease.gpg  Could not resolve 'wingen8'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/mai
n/i18n/Translation-en_US.bz2  Could not resolve 'wingen8'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/res
tricted/i18n/Translation-en_US.bz2  Could not resolve 'wingen8'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/uni
verse/i18n/Translation-en_US.bz2  Could not resolve 'wingen8'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/mul
tiverse/i18n/Translation-en_US.bz2  Could not resolve 'wingen8'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg
Could not resolve 'wingen8'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/
Translation-en_US.bz2  Could not resolve 'wingen8'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Cou                                                                                                   ld not resolve 'wingen8'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Transl                                                                                                   ation-en_US.bz2  Could not resolve 'wingen8'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/                                                                                                   Translation-en_US.bz2  Could not resolve 'wingen8'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Tr                                                                                                   anslation-en_US.bz2  Could not resolve 'wingen8'

W: Failed to fetch cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/                                                                                                   dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-R                                                                                                   OM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/                                                                                                   dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make thi                                                                                                   s CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Some index files failed to download, they have been ignored, or old ones used                                                                                                    instead.
W: You may want to run apt-get update to correct these problems

```

drs305: I don't know what it *is*, and KWrite as root didn't turn up anything about it.

---

### Post by s_ø on 2010-03-27
can you post the contents of your /etc/apt/sources.list
```
sudo nano /etc/apt/sources.list
```

---

### Post by Singer&amp;Cal on 2010-03-27
Here it is:

```
deb cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted universe
```

---

### Post by Kevinator on 2010-03-27
Whatever "wingen8" is, it's not in the APT sources. The only other things I can think of would be a proxy, a DNS server, or a gateway. Please show us:

* The content of /etc/resolv.conf
* The content of /etc/network/interfaces
* The output from "nslookup archive.canonical.com"

---

### Post by Singer&amp;Cal on 2010-03-28
First resolv.conf:
```
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4621
#
### END INFO



nameserver 207.69.188.186
nameserver 207.69.188.187
```

Next, the interfaces file:
```
auto lo
iface lo inet loopback
```

Finally, the output of nslookup:

```
Server:         207.69.188.186
Address:        207.69.188.186#53

Non-authoritative answer:
Name:   archive.canonical.com
Address: 91.189.88.33

```

---

### Post by Kevinator on 2010-03-28
OK, how about /etc/hosts? If that's not the problem, then I'm out of specific ideas. It could be something affecting name lookup (the content of /etc/nsswitch.conf might help determine that) or some proxy, but I don't know anything about setting up proxies for APT.

---

### Post by drs305 on 2010-03-28
Here is a thread that dealt with various server/host issues. I'm not sufficiently knowledgeable to pick out the correct issue in your case, but the post may give you some ideas on how to proceed. 

[http://ubuntuforums.org/showthread.php?t=876616]("http://ubuntuforums.org/showthread.php?t=876616")

---

### Post by Singer&amp;Cal on 2010-03-28
/etc/hosts:

```
127.0.0.1	localhost
127.0.1.1	nobacon
91.189.88.46    archive.ubuntu.com
91.189.88.46    security.ubuntu.com

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

/etc/nsswitch.conf:

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

---

### Post by Singer&amp;Cal on 2010-03-28
Very interesting...I tried the solution in the thread, but now it won't even try to update. It keeps saying: > E: Malformed line 39 in source list /etc/apt/sources.list (URI parse).:confused:

EDIT: Lightbulb over head: I'll copy off of this thread's copy of the file and paste it in.

---

### Post by drs305 on 2010-03-28
You can also generate a new sources.list for an Ubuntu release on this site:
[http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/")

---

### Post by Singer&amp;Cal on 2010-03-28
That didn't help. Now I just have more repositories for it to say 'Could not resolve wingen8' about.

---

### Post by cosine352 on 2010-03-28
please check the software sources. 
In a terminal type.
> gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk

see if the "Download from : Server for United States"
Please look at the screen shot attached.

---

### Post by sgosnell on 2010-03-28
On the software sources dialog, uncheck the CD-ROM checkbox.

---

### Post by Singer&amp;Cal on 2010-03-28
cosine352: I don't have gksu, so I can't do that. But I do know that I'm downloading from the US server.

sgosnell: I think the CD vaporized or something! It's not there in Adept Installer's Software Sources area.

---

### Post by s_ø on 2010-03-28
use gksudo.
Or open System>Administration>Software sources.

What does you sources.list look like now?

You said wingen8 is only applicable to your system, would it be a problem to try and remove whatever it is?

---

### Post by sgosnell on 2010-03-28
Open System/Administration/Software Sources.  On the Ubuntu Software tab, there is a box at the bottom which says "Installable from CD-ROM/DVD.  Inside the box there is a checkbox which says "CD-ROM with Ubuntu 8.04", or something like that.  Uncheck the checkbox there.  Reload the repositories.  If that doesn't fix it, report back.  I haven't used 8.04 in a long time, but I think it's trying to access the CD, and not finding one in the drive.

---

### Post by Kevinator on 2010-03-28
Wow, this thread is really filling up with wild guesses. Maybe we should stick to diagnosing the problem, guys.

Singer&Cal, you have some stuff in /etc/hosts that shouldn't be there, so lets get rid of it. Specifically these two lines:

91.189.88.46    archive.ubuntu.com
91.189.88.46    security.ubuntu.com

I suppose someone told you to add these in an attempt to fix your problem, right? Well, it's clearly not working, and it's also clear that you can successfully resolve these hosts with DNS, so the /etc/hosts entries aren't helping you (and may cause problems). Get gid of them.

Now we're going to get down to what's really causing the problem. First, I'm predicting that you don't have any actual networking problems that are preventing you from accessing the Ubuntu archives, so let's test that theory. Try this from the command line:

telnet us.archive.ubuntu.com 80

You should see output like this:

Trying 91.189.88.46...
Connected to us.archive.ubuntu.com.
Escape character is '^]'.

Now, assuming that's correct, type <ctrl>]q to get out (that's CTRL+right square bracket, followed by q, then Enter).

If that went as predicted, I think we can assume the problem is in your APT configuration and go from there. Otherwise please post the output.

The next thing I want you to do is show us your APT configuration, which you can get by entering this:

apt-config dump

---

### Post by m4tic on 2010-03-28
why are people replying in gnome terms, cal uses kubuntu 8.04

---

### Post by m4tic on 2010-03-28
try both of these, 
s u d o d p k g - - c l e a r - a v a i l
s u d o d p k g c o n f i g u r e - a

use aptitude to resolve any conflicts

---

### Post by Kevinator on 2010-03-28
> **m4tic said:**
> try both of these, 
s u d o d p k g - - c l e a r - a v a i l
s u d o d p k g c o n f i g u r e - a

use aptitude to resolve any conflicts

This sounds like a pretty drastic thing to try, especially without knowing what the actual problem is.

---

### Post by Singer&amp;Cal on 2010-03-29
(Sorry about the delay - I had things that couldn't wait)

m4tic: That didn't help - I don't think it's conflicts.

Kevinator: Telnet worked fine on the website. Here's the output of apt-get dump:

```
$ apt-config dump
APT "";
APT::Architecture "i386";
APT::Build-Essential "";
APT::Build-Essential:: "build-essential";
APT::Install-Recommends "0";
APT::Install-Suggests "0";
APT::Acquire "";
APT::Acquire::Translation "environment";
APT::Authentication "";
APT::Authentication::TrustCDROM "true";
APT::NeverAutoRemove "";
APT::NeverAutoRemove:: "^linux-image.*";
APT::NeverAutoRemove:: "^linux-restricted-modules.*";
APT::NeverAutoRemove:: "^linux-ubuntu-modules-.*";
APT::Never-MarkAuto-Sections "";
APT::Never-MarkAuto-Sections:: "metapackages";
APT::Never-MarkAuto-Sections:: "restricted/metapackages";
APT::Never-MarkAuto-Sections:: "universe/metapackages";
APT::Never-MarkAuto-Sections:: "multiverse/metapackages";
APT::Install-Recommends-Sections "";
APT::Install-Recommends-Sections:: "metapackages";
APT::Install-Recommends-Sections:: "restricted/metapackages";
APT::Install-Recommends-Sections:: "universe/metapackages";
APT::Install-Recommends-Sections:: "multiverse/metapackages";
APT::Periodic "";
APT::Periodic::Update-Package-Lists "0";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "0";
APT::Update "";
APT::Update::Post-Invoke-Success "";
APT::Update::Post-Invoke-Success:::: "touch /var/lib/apt/periodic/update-success-stamp 2>/dev/null || true";
APT::Archives "";
APT::Archives::MaxAge "30";
APT::Archives::MinAge "2";
APT::Archives::MaxSize "500";
Dir "/";
Dir::State "var/lib/apt/";
Dir::State::lists "lists/";
Dir::State::cdroms "cdroms.list";
Dir::State::mirrors "mirrors/";
Dir::State::userstatus "status.user";
Dir::State::status "/var/lib/dpkg/status";
Dir::Cache "var/cache/apt/";
Dir::Cache::archives "archives/";
Dir::Cache::srcpkgcache "srcpkgcache.bin";
Dir::Cache::pkgcache "pkgcache.bin";
Dir::Etc "etc/apt/";
Dir::Etc::sourcelist "sources.list";
Dir::Etc::sourceparts "sources.list.d";
Dir::Etc::vendorlist "vendors.list";
Dir::Etc::vendorparts "vendors.list.d";
Dir::Etc::main "apt.conf";
Dir::Etc::parts "apt.conf.d";
Dir::Etc::preferences "preferences";
Dir::Bin "";
Dir::Bin::methods "/usr/lib/apt/methods";
Dir::Bin::dpkg "/usr/bin/dpkg";
Dir::Log "var/log/apt";
Dir::Log::Terminal "term.log";
aptitude "";
aptitude::Keep-Unused-Pattern "^linux-image.*$ | ^linux-restricted-modules.*$ | ^linux-ubuntu-modules.*$";
aptitude::Get-Root-Command "sudo:/usr/bin/sudo";
Unattended-Upgrade "";
Unattended-Upgrade::Allowed-Origins "";
Unattended-Upgrade::Allowed-Origins:: "Ubuntu hardy-security";
DPkg "";
DPkg::Pre-Install-Pkgs "";
DPkg::Pre-Install-Pkgs:: "/usr/sbin/dpkg-preconfigure --apt || true";
DPkg::Post-Invoke "";
DPkg::Post-Invoke:: "if [ -d /var/lib/update-notifier ]; then  touch /var/lib/update-notifier/dpkg-run-stamp; fi";
Acquire "";
Acquire::http "";
Acquire::http::Proxy "http://wingen8:8081/";

```

---

### Post by zuerston on 2010-03-29
> **Singer&Cal said:**
> (Sorry about the delay - I had things that couldn't wait)

m4tic: That didn't help - I don't think it's conflicts.

Kevinator: Telnet worked fine on the website. Here's the output of apt-get dump:

```
$ apt-config dump
APT "";
APT::Architecture "i386";
APT::Build-Essential "";
APT::Build-Essential:: "build-essential";
APT::Install-Recommends "0";
APT::Install-Suggests "0";
APT::Acquire "";
APT::Acquire::Translation "environment";
APT::Authentication "";
APT::Authentication::TrustCDROM "true";
APT::NeverAutoRemove "";
APT::NeverAutoRemove:: "^linux-image.*";
APT::NeverAutoRemove:: "^linux-restricted-modules.*";
APT::NeverAutoRemove:: "^linux-ubuntu-modules-.*";
APT::Never-MarkAuto-Sections "";
APT::Never-MarkAuto-Sections:: "metapackages";
APT::Never-MarkAuto-Sections:: "restricted/metapackages";
APT::Never-MarkAuto-Sections:: "universe/metapackages";
APT::Never-MarkAuto-Sections:: "multiverse/metapackages";
APT::Install-Recommends-Sections "";
APT::Install-Recommends-Sections:: "metapackages";
APT::Install-Recommends-Sections:: "restricted/metapackages";
APT::Install-Recommends-Sections:: "universe/metapackages";
APT::Install-Recommends-Sections:: "multiverse/metapackages";
APT::Periodic "";
APT::Periodic::Update-Package-Lists "0";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "0";
APT::Update "";
APT::Update::Post-Invoke-Success "";
APT::Update::Post-Invoke-Success:::: "touch /var/lib/apt/periodic/update-success-stamp 2>/dev/null || true";
APT::Archives "";
APT::Archives::MaxAge "30";
APT::Archives::MinAge "2";
APT::Archives::MaxSize "500";
Dir "/";
Dir::State "var/lib/apt/";
Dir::State::lists "lists/";
Dir::State::cdroms "cdroms.list";
Dir::State::mirrors "mirrors/";
Dir::State::userstatus "status.user";
Dir::State::status "/var/lib/dpkg/status";
Dir::Cache "var/cache/apt/";
Dir::Cache::archives "archives/";
Dir::Cache::srcpkgcache "srcpkgcache.bin";
Dir::Cache::pkgcache "pkgcache.bin";
Dir::Etc "etc/apt/";
Dir::Etc::sourcelist "sources.list";
Dir::Etc::sourceparts "sources.list.d";
Dir::Etc::vendorlist "vendors.list";
Dir::Etc::vendorparts "vendors.list.d";
Dir::Etc::main "apt.conf";
Dir::Etc::parts "apt.conf.d";
Dir::Etc::preferences "preferences";
Dir::Bin "";
Dir::Bin::methods "/usr/lib/apt/methods";
Dir::Bin::dpkg "/usr/bin/dpkg";
Dir::Log "var/log/apt";
Dir::Log::Terminal "term.log";
aptitude "";
aptitude::Keep-Unused-Pattern "^linux-image.*$ | ^linux-restricted-modules.*$ | ^linux-ubuntu-modules.*$";
aptitude::Get-Root-Command "sudo:/usr/bin/sudo";
Unattended-Upgrade "";
Unattended-Upgrade::Allowed-Origins "";
Unattended-Upgrade::Allowed-Origins:: "Ubuntu hardy-security";
DPkg "";
DPkg::Pre-Install-Pkgs "";
DPkg::Pre-Install-Pkgs:: "/usr/sbin/dpkg-preconfigure --apt || true";
DPkg::Post-Invoke "";
DPkg::Post-Invoke:: "if [ -d /var/lib/update-notifier ]; then  touch /var/lib/update-notifier/dpkg-run-stamp; fi";
Acquire "";
Acquire::http "";
Acquire::http::Proxy "http://wingen8:8081/";

```

Its been 20 hours,they have left.  maybe should have posted BBL:D
I was getting into the read too and it came to a screeching halt!

---

### Post by Singer&amp;Cal on 2010-03-29
Well, I think it's the proxy. Do you know of any general-purpose proxies that will work?

---

### Post by Kevinator on 2010-03-29
Yeah, it's clearly the "Acquire::http:: Proxy" setting. We'll need to locate that in the config files and probably just clear it out.

Singer&Cal, do you have some reason to use a proxy? We've established that a direct connection works, so the proxy would seem unnecessary, unless it's for privacy or filtering.

You should be able to locate the configuration file responsible for this entry with the following:

grep -r wingen8 /etc/apt/apt.conf*

It could be a file installed by some package, so to check try running this:

dpkg -S /etc/apt/apt.conf.d/filename

(Replacing filename with whatever the grep command turned up.)

That may give you the name of the package responsible, and it may be something you don't want, in which case it can be removed. Otherwise, you can edit the file to remove the Acquire::http:: Proxy entry.

---

### Post by Singer&amp;Cal on 2010-03-29
It worked!!! Thank you SO much!!! (Note the lack of smilies.) No, wait...not yet. It always finds a repository to complain about.

---

### Post by Singer&amp;Cal on 2010-03-30
I hate to bother everybody again, but it's not working yet. It always finds some repository to not bother to download from. Usually it's the Ubuntu servers themselves! I don't know what to do at this point. I'm on dialup; could this be something to do with it?

---

### Post by drs305 on 2010-03-30
Assuming you no longer have the "wingen8" error message, please post the new error messages so we can look at them. Until we see the actual error messages we would just be guessing at the problem and possible solutions.

To occupy your time while you await responses you can try changing a few things in the sources.list. If you are not connecting to *any* server, you can change the server to one closer to your location to see if that helps. To do that, open Synaptic and select Settings, Repositories, and in the Ubuntu Software tab click on "Download from" and select another server. 

If there are specific repositories you cannot access, you can also untick any repository for which you are getting an error message (such as main, universe, etc) from either the Ubuntu Software or Other Software tab. Make any changes, select Close and then press "Reload" to see if the remainder are now working.

---

### Post by Singer&amp;Cal on 2010-04-01
I can't really post any specific error message. But I do know that it's failing to download, because the progress bar on a random server just stays at 0%. The repositories targeted are usually the Ubuntu servers themselves, but others are sometimes the culprit.
 
P.S. Sorry about the delay.

---

