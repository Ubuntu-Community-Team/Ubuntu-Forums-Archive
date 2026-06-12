---
title: "Update Broken and Synaptic Won't Open"
date: 2012-05-12
forum: General Help
---

### Post by amhainen on 2012-05-12
When I run 'sudo apt-get update', I get the following:

```
Reading package lists... Error!
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG A8AA1FAA3F055C03 Launchpad PPA for Daniel Richter
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG BA23BB04715BE097 Launchpad FreeFileSync .deb
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG A777609328949509 Launchpad Gwendal Le Bihan
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG D834D91FA49CCDDB Launchpad PPA for System Load Indicator developers
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 5A6D0F1DAE7A42A0 Launchpad PPA for MyUnity
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 94E58C34A8670E8C Launchpad PPA for Screenlets
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```

I tried opening Synaptic, but it won't open and says:

> 
E: Encountered a selection with no Package: header
E: Problem with MergeList /var/lib/apt/lists/
extras.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E:_cache->open() failed, please report.

I hope this counts as reporting...and that someone can help me. Thx.

---

### Post by Rubi1200 on 2012-05-12
Hi,
you can try this and see if it helps:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

the first command removes corrupted package lists, the second refreshes them.

Let us know.

---

### Post by amhainen on 2012-05-12
Thanks, Rubi...Worked Great!!

I've used Ubuntu (casually) since Breezy and I've never seen that error before.

---

### Post by Rubi1200 on 2012-05-12
You are more than welcome :-)

Glad this solved the issue.

---

### Post by oxman on 2012-05-20
Rubi1200
I ran into this today. Same message of fubar as per amhainen:

 	Quote:
 	 	 		 			 				```

E: Encountered a selection with no Package: header
E: Problem with MergeList /var/lib/apt/lists/
extras.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E:_cache->open() failed, please report. 			 		

```

The system would not let me file a report either. Neither through apt-get,  update-manager or synaptic. Seems like a serious bug. I followed your suggestion and all is well.
Thank you very much.

---

### Post by NosamLuap on 2012-07-24
> **Rubi1200 said:**
> Hi,
you can try this and see if it helps:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

the first command removes corrupted package lists, the second refreshes them.

Let us know.

Another vote of thanks for this Rubil - worked for me too :)

---

### Post by Trigio on 2012-07-31
LOL, we need a Thank You button for this one.

Wife came with the same problem a few minutes ago and already solved :P

As i know she does not mess with the 'internals' (that's my job); what is the cause of this error? Seems like it happens around the same time for some of us.

Greets ans thanx again,
T.

---

### Post by Moglagh on 2012-08-01
Thank You Very Much. I just turned my computer on and this problem came up. I am running Ubuntu 12.4 on a Lenovo 4440. This solution worked perfectly!

---

### Post by dimmelis on 2012-12-16
Won't work for me. :(
The response for 
sudo rm /var/lib/apt/lists/* -vf
is
**rm: cannot remove `/var/lib/apt/lists/partial': Is a directory**

And then for
sudo apt-get update 
I get: 
[B]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]

---

### Post by donaldt on 2012-12-18
Hitch hiking on this thread.  I have a similar problem.  My update manager is broken, will not complete an update and freezes the computer.  Have to re-boot to correct.

12.04 worked well for many months, now will not complete an "update manager" process.

Previous use of [sudo apt-get update && sudo apt-get dist-upgrade] prior to running Update Manager would usually enable update manager to function normally.  

Now, the terminal will not complete an upgrade and I get this message at the end:

[N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension 
W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/Release.gpg)  Unable to connect to archive.getdeb.net:http: 

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/apps/source/Sources](http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/apps/source/Sources)  Unable to connect to archive.getdeb.net:http: 

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/apps/binary-i386/Packages](http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/apps/binary-i386/Packages)  Unable to connect to archive.getdeb.net:http: 

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/apps/i18n/Translation-en_US](http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/apps/i18n/Translation-en_US)  Unable to connect to archive.getdeb.net:http: 

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/apps/i18n/Translation-en](http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/apps/i18n/Translation-en)  Unable to connect to archive.getdeb.net:http: 

E: Some index files failed to download. They have been ignored, or old ones used instead. 
donald@donald-Aspire-3810T:~$ 

I'm not Ubuntu smart enough to figure this out.  What should I do to clear the problems?

Thanks if you can help.

Donaldt

---

### Post by polki@mac.com on 2012-12-19
getdeb.net is down and has been for a while. You'll just have to untick them in Software Sources until they're up again.

---

