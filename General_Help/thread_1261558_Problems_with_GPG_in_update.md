---
title: "Problems with GPG in update"
date: 2009-09-08
forum: General Help
---

### Post by the_real_fourthdimension on 2009-09-08
Hey All

I put 9.04 on a friend's laptop a week ago.  It runs beautifully, but today she encountered a problem with her update manager.  Here's the error message:
```

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://us.archive.ubuntu.com jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```
I told her to run sudo apt-get update, which gave her this message:
```

Get:1 http://security.ubuntu.com jaunty-security Release.gpg [189B]
Get:2 http://archive.canonical.com jaunty Release.gpg [189B]                 
Get:3 http://us.archive.ubuntu.com jaunty Release.gpg [189B]         
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Ign http://archive.canonical.com jaunty/partner Translation-en_US    
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US       
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US 
Ign http://archive.canonical.com jaunty Release                      
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US   
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US 
Hit http://archive.canonical.com jaunty/partner Packages             
Get:4 http://security.ubuntu.com jaunty-security Release [49.6kB]    
Get:5 http://us.archive.ubuntu.com jaunty-updates Release.gpg [189B]
Err http://security.ubuntu.com jaunty-security Release
  
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Get:6 http://us.archive.ubuntu.com jaunty Release [74.6kB]
Ign http://us.archive.ubuntu.com jaunty Release 
Get:7 http://us.archive.ubuntu.com jaunty-updates Release [49.6kB]
Err http://us.archive.ubuntu.com jaunty-updates Release
  
Hit http://us.archive.ubuntu.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Fetched 759B in 2s (330B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://us.archive.ubuntu.com jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```
Does anyone know how to fix the GPG signature?
Thanks a lot!

---

### Post by cranecreek on 2009-09-08
Can you post the contents of:

```
/etc/apt/sources.list
```

I'm sure that someone will be able to help once we see that

---

### Post by drs305 on 2009-09-08
The easiest thing to try is to switch servers. Synaptic, Settings, Repositories, Download from..., Other, and select another server. Then Reload. Sometimes this happens during an update to the server.

---

### Post by zero-n on 2009-11-06
different servers but the problem is still there.

---

### Post by approaching on 2009-11-06
I seem to be having the same issue with not updating properly on my netbook. This is the contents of my /etc/apt/sources.list:
```

# deb cdrom:[Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)]/ jaunty main multiverse restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

#for internet explorer
# deb http://us.archive.ubuntu.com/ubuntu edgy universe

```

I could post the error message i am getting as well, but it seems to be identical, so here is just the error messages (grep ftw)

```

Err http://security.ubuntu.com karmic-security Release
Err http://us.archive.ubuntu.com karmic-updates Release
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com karmic-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://us.archive.ubuntu.com karmic Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com karmic-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.


```

---

### Post by drs305 on 2009-11-06
> **zero-n said:**
> different servers but the problem is still there.

Try running these commands to reimport the key:
```

gpg --keyserver keyserver.ubuntu.com --recv-keys 437D05B5 && gpg --export --armor 437D05B5 | sudo apt-key add -
sudo apt-get update

```

---

### Post by approaching on 2009-11-06
i still get the same error. is that key public? ie, can it be shared between people, or do i have to generate my own?

here is the error:

```

Err http://security.ubuntu.com karmic-security Release
Err http://us.archive.ubuntu.com karmic-updates Release
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com karmic-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://us.archive.ubuntu.com karmic Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com karmic-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by zero-n on 2009-11-07
```
gpg --keyserver keyserver.ubuntu.com --recv-keys 437D05B5 && gpg --export --armor 437D05B5 | sudo apt-key add -

```

The above command give me this result:
```
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: can't open `/home/dso/.gnupg/pubring.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0

```

---

### Post by approaching on 2009-11-11
that command seems to run fine, but the apt update still doesn't run without error.

```

gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" 1 new signature
gpg: 3 marginal(s) needed, 1 complete(s) needed, PGP trust model
gpg: depth: 0  valid:   2  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 2u
gpg: next trustdb check due at 2014-09-07
gpg: Total number processed: 1
gpg:         new signatures: 1
OK

```

---

### Post by drs305 on 2009-11-11
You might just try deleting the Ubuntu keys and reinstalling whatever key code comes up the next time you attempt to run the update. You can delete the Ubuntu archive key from Synaptic in Settings, Repositories, Authentication tab.

---

### Post by approaching on 2009-11-12
I tried deleting the sources in synaptic as prescribed, but that didn't do anything. poking around some more, i found this bug page:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24234](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24234)

on it, i found some commands that at least let me update. 

```

sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

```

I do still get these errors when i do a apt-get update:

```

W: GPG error: http://security.ubuntu.com karmic-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://us.archive.ubuntu.com karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://us.archive.ubuntu.com karmic-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5


```

---

### Post by littlewing0906 on 2009-11-21
[https://bugs.launchpad.net/ubuntu/+s...apt/+bug/24234](https://bugs.launchpad.net/ubuntu/+s...apt/+bug/24234)

I just downloaded the latest EasyPeasy and I had the same error as you- I checked the directions you posted and I was able to get rid of the error. I had a prompt about authentication come up in GNOME and I ran it, and then did apt-get update and upgrade and the original error went away. Thanks for the link!

---

### Post by Husain_17 on 2010-11-05
I had the same problem, however I tried the following and it worked:

```
nano /etc/apt/sources.list
```I got the following lines.

```
deb http://[COLOR=Red]sa.[/COLOR]archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://[COLOR=Red]sa.[/COLOR]archive.ubuntu.com/ubuntu/ maverick main restricted
```I removed the country abbr. colored in red and got it working :)

---

### Post by rungss on 2010-12-02
> **drs305 said:**
> You might just try deleting the Ubuntu keys and reinstalling whatever key code comes up the next time you attempt to run the update. You can delete the Ubuntu archive key from Synaptic in Settings, Repositories, Authentication tab.

I think of doing that but fear what if I deleted the Keys for Other Repositories which I have added over the Years.

How can I delete the Authentication Keys selectively for Ubuntu ones?

---

### Post by drs305 on 2010-12-02
> **rungss said:**
> How can I delete the Authentication Keys selectively for Ubuntu ones?

Open Synaptic or Software Sources (System, Admininstration, Synaptic or Software Sources): Settings > Repositories > Authentication tab. You can delete individual keys displayed on that page by highlighting a key and clicking the Remove button. There is a brief description of what each key is for - some are more obvious than others...

---

### Post by rungss on 2010-12-06
> **drs305 said:**
> Open Synaptic or Software Sources (System, Admininstration, Synaptic or Software Sources): Settings > Repositories > Authentication tab. You can delete individual keys displayed on that page by highlighting a key and clicking the Remove button. There is a brief description of what each key is for - some are more obvious than others...

Thanks a lot for the Response.

I removed a couple of Authentication Items which seemed to be from Ubuntu.

After that I was never asked to reimport the Signature or something.


When I tried to update from command Line.

```
sudo apt-get update
```

I got the following error message at the end.

> 
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed Release: The following signatures were invalid: NODATA 3 NODATA 4
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-i386_Packages)


Further to that, I went to the Authentication Tab of the Synaptec and Clicked on Restore Defaults which I thought would re-validate my Ubuntu Authentication Keys.

But When I clicked on Reload Button, I again received the following message.

> W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed Release: The following signatures were invalid: NODATA 3 NODATA 4

---

### Post by drs305 on 2010-12-06
It could be that the server was having problems, and you could try again. But generally, if you get a "public key not available" (NO_PUBKEY) you can add it by running the following command. You can use the entire key or just the last 8 characters. You can also combine keys in the same command, separated by a space.

> 
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  16126D3A3E5C1192 40976EAF437D05B5


To remove a bad or invalid key (BADSIG), you can run this command (replace the key code). In the example I didn't use the one from your thread, as it should have been updated when you ran the above command and may no longer be a problem:
> sudo apt-key del A040830F7FAC5991

Note that these messages do not prevent you from using a repository reporting a missing key, it is warning you that it cannot verify the location you are using is a safe site and it leaving the decision to you.

---

### Post by WitchCraft on 2011-01-07
Great, works.

---

### Post by neaj on 2011-01-14
> **WitchCraft said:**
> Great, works.

Not here, for some reason .. I did
$ sudo apt-key del 16126D3A3E5C1192
before importing the key again as well. 

See [http://ubuntuforums.org/showpost.php?p=10355115&postcount=14](http://ubuntuforums.org/showpost.php?p=10355115&postcount=14)

---

### Post by bkaplan on 2011-01-22
> **drs305 said:**
> It could be that the server was having problems, and you could try again. But generally, if you get a "public key not available" (NO_PUBKEY) you can add it by running the following command. You can use the entire key or just the last 8 characters. You can also combine keys in the same command, separated by a space.



To remove a bad or invalid key (BADSIG), you can run this command (replace the key code). In the example I didn't use the one from your thread, as it should have been updated when you ran the above command and may no longer be a problem:


Note that these messages do not prevent you from using a repository reporting a missing key, it is warning you that it cannot verify the location you are using is a safe site and it leaving the decision to you.


This worked for me, too.  Thank you!

---

### Post by mmmmna on 2011-01-22
Installed Opera a few days ago. To do that, I went to the Opera website to get the latest release. IIRC, the Opera package launched gdebi.

Yesterday, I launched Synaptic, I reloaded, I marked and applied all upgrades. Opera was listed as being upgraded. Inside of a few days? Huh. Could happen.

Anyhow, today I launched Synaptic and I get this error:[quote="Synaptic"]W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061[/quote]I had the above error about 6 times in a row over a half hour period, whenever I launched Synaptic. Because I did not know what the proper solution was, I would simply quit Synaptic and try again later.

Is this some kind of obtuse way of showing that the referenced server is down? In any event, I can't recall manually added the Opera server, I do not recall seeing any message where I approved the addition, either. Maybe that addition happened during the GDEBI session, but I forget (is there a history function in GDEBI?).


My method of resolution (not really a solution): Eventually the error stopped on its own, so after that problem cleared, I went into the Synaptic repo list (Settings - Repositories)  and unchecked that repo, I can always re-enable the repo when I feel the need.

I'm using Kubuntu 10.04 LTS for 64 bit Desktop.
HTH.

---

### Post by Zill on 2011-01-27
> **mmmmna said:**
> Installed Opera a few days ago. To do that, I went to the Opera website to get the latest release. IIRC, the Opera package launched gdebi.

Yesterday, I launched Synaptic, I reloaded, I marked and applied all upgrades. Opera was listed as being upgraded. Inside of a few days? Huh. Could happen.

Anyhow, today I launched Synaptic and I get this error:
> W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061
Opera has been updated a couple of times recently.  Unfortunately, the updates have coincided with the old 2010 Opera authentication key expiring, requiring a [new 2011 key]("http://deb.opera.com/") to be issued.
I believe the old key (9D1A0061) has now expired and so no longer works.  The new key is 4E7532C8 and so this should be entered with the following code:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4E7532C8
```
Of course, the key can be added via Synaptic if preferred.  You can check the keyring with the following code:
```
sudo apt-key list
```
On a related point, I have found that Opera only seems to retain the key for one upgrade - then the key mysteriously disappears from the apt-key keyring :-(  It is then necessary to re-import the key after upgrading Opera to a new version.

Ideas please - Is this by design or a bug?

---

### Post by asamf on 2011-04-06
well............the easy way to solve this is to delet all the keys by running the folowing command.............................XD
> sudo rm /var/lib/apt/lists/* -vf


---

