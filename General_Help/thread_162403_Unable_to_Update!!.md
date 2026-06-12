---
title: "Unable to Update!!"
date: 2006-04-18
forum: General Help
---

### Post by Gautam Arjun on 2006-04-18
Hi all, 
             I switched from gnome to KDE about 2 days ago - I managed to get the ADSL working fine and ihe web works flawlessly. However, each time I try to use Adept Updater, or apt-get from the Konsole -  It's unable to reach the archives!!! - Can someone here help me sort this out??

Thanks in Advance,
Gautam

---

### Post by Nequeo on 2006-04-18
[QUOTE=Gautam Arjun]Hi all, 
             I switched from gnome to KDE about 2 days ago - I managed to get the ADSL working fine and ihe web works flawlessly. However, each time I try to use Adept Updater, or apt-get from the Konsole -  It's unable to reach the archives!!! - Can someone here help me sort this out??

Thanks in Advance,
Gautam[/QUOTE]

Off the top of my head, that sounds like a Proxy issue. Do you have any proxies set in Firefox? (Look under Tools--->Options--->Connection Settings).

Also, could you please post back the exact error message you're getting from apt-get? Thanks!

---

### Post by Gautam Arjun on 2006-04-19
Hi, Thanks for replying! - I don't get any error messages, the connection just times out....My suspicions are that it is unable to resolve the hosts - I never had a problem under gnome once I set up my internet correctly - I used static settings there. In Kubuntu, Network settings are DHCP and works just fine. Strangely, If i manually set up the eth network interface with the static settings I used in Gnome, It does not work.
The Message I'm getting using apt-get is:

Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy Release.gpg
  Could not connect to in.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-updates Release.gpg
  Could not connect to in.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-backports Release.gpg
  Could not connect to in.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Could not connect to in.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Could not connect to in.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)  Could not connect to in.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
gautam@ubuntu:~$

---

### Post by Nequeo on 2006-04-19
[QUOTE=Gautam Arjun]
Could not connect to in.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[/QUOTE]

There's your problem! The IP address of archive.ubuntu.com is NOT 1.0.0.0 Now we just have to work out what's gone wacky with your DNS resolution. 

Can you please type in the following commands into a terminal and post the output?

'ifconfig'

'cat /etc/resolv.conf'

'cat /etc/hosts'

That should shed a bit more light on the matter. 

Cheersm

---

