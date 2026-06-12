---
title: "Apt_Get floored by virgin !"
date: 2011-03-04
forum: General Help
---

### Post by iains on 2011-03-04
A week or so ago I had the unfortunate experience of upgrading my Virgin 
20Mb system to 30Mb with their new Super-Hubs.

I'm not going into details here but an engineer came and 'set it up' for 
me - including activating the system.

It's working sort-of OK.

Anyhow today I had a message on my Ubuntu 10.10 system

> E: Encountered a section with no Package: header
> E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_multiverse_binary-amd64_Packages
> E: The package lists or status file could not be parsed or opened.
> E: _cache->open() failed, please report.

It occurred to me that I hadn't been updated recently.

I looked at file " 
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_multiverse_binary-amd64_Packages"

which contained
> <html>
> 	<head>
> 		<title>Broadband Activation</title>
> 		<style type="text/css">
> 		body { text-align:center; }
> 		</style>
> 	</head>
> 	<body>
> 		<a href="https://act2.virginmedia.com/Activation/start.do">Please click on this link to proceed with Broadband Activation...</a>
> 	</body>
> </html>

How the H*** did that happen !!!

Luckily I had taken a backup 2 days earlier and recovered the file and I 
think I'm OK

iain

---

### Post by tgm4883 on 2011-03-04
> **iains said:**
> A week or so ago I had the unfortunate experience of upgrading my Virgin 
20Mb system to 30Mb with their new Super-Hubs.

I'm not going into details here but an engineer came and 'set it up' for 
me - including activating the system.

It's working sort-of OK.

Anyhow today I had a message on my Ubuntu 10.10 system

> E: Encountered a section with no Package: header
> E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_multiverse_binary-amd64_Packages
> E: The package lists or status file could not be parsed or opened.
> E: _cache->open() failed, please report.

It occurred to me that I hadn't been updated recently.

I looked at file " 
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_multiverse_binary-amd64_Packages"

which contained
> <html>
> 	<head>
> 		<title>Broadband Activation</title>
> 		<style type="text/css">
> 		body { text-align:center; }
> 		</style>
> 	</head>
> 	<body>
> 		<a href="https://act2.virginmedia.com/Activation/start.do">Please click on this link to proceed with Broadband Activation...</a>
> 	</body>
> </html>

How the H*** did that happen !!!

Luckily I had taken a backup 2 days earlier and recovered the file and I 
think I'm OK

iain

Your system went to check for updates by downloading a webpage. When it went to download the page, your ISP redirected them to the activation page. Apparently there is no error checking for that sort of thing, so it downloaded the redirected web page.

---

### Post by iains on 2011-03-04
So as soon as my system was online it took any rubbish that came down the wire 
worrying 
no checking that the file was in the correct format
very worrying !
iain

---

### Post by flipper T on 2011-03-04
i'm also with virgin and had the upgrade at the start of january.

anyway, what prompted this error ? an update to the hub firmware or an ubuntu update ?

interested as would like to avoid,

presumably i should back up ...


/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_multiverse_binary-amd64_Packages


...now ?

---

### Post by flipper T on 2011-03-04
ps my copy of this file appears to have nothing to do with virgin, but rather the flash 64 bit installer...now i'm lost

---

### Post by tgm4883 on 2011-03-04
> **iains said:**
> So as soon as my system was online it took any rubbish that came down the wire 
worrying 
no checking that the file was in the correct format
very worrying !
iain

Not exactly that worrying. It downloaded a webpage from the internet and couldn't do anything with it. 

I would bet that the next time you ran apt-get update it would have resolved itself.

:EDIT:

You can file a bug against it and see if the developer will do anything about it.

---

### Post by iains on 2011-03-05
I assume the automatic apt-get routine was trying to download this file from the repository when the engineer made the connection and the html was the first file that came down. My internet connection had been down for two days and it must have come up just as apt-get was trying to check the repositories.

So the error was the result of a chance of timing.

If I had deleted the spurious "security.ubuntu.com_ubuntu_dists_maverick-security_multiverse_binary-amd64_Packages" file an update would have replaced it ?

---

### Post by plucky on 2011-03-05
> **iains said:**
> I assume the automatic apt-get routine was trying to download this file from the repository when the engineer made the connection and the html was the first file that came down. My internet connection had been down for two days and it must have come up just as apt-get was trying to check the repositories.

So the error was the result of a chance of timing.

If I had deleted the spurious "security.ubuntu.com_ubuntu_dists_maverick-security_multiverse_binary-amd64_Packages" file an update would have replaced it ?

You can delete all the list files in that directory as they will be downloaded whenever you do a ```
sudo apt-get update
``` from a terminal.

Good Luck

---

