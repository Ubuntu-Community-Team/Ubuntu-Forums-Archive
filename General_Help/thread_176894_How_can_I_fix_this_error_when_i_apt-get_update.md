---
title: "How can I fix this error when i apt-get update??"
date: 2006-05-15
forum: General Help
---

### Post by morbid_bean on 2006-05-15
After i do sudo apt-get update...i get this.






Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
  Sub-process gzip returned an error code (1)
Fetched 5B in 6s (1B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by fer5437 on 2006-05-15
I had face that problem before last 2 week after I update it to Dapper. So for my solution is I use update manager in System -> Administrator -> Update Manager. It solve my problem, I using Dapper now but not too sure it same with Breezy or not.
You can try it.

---

### Post by barbarian on 2006-05-15
just comment this out with # or try later..

---

### Post by morbid_bean on 2006-05-15
I did that and my system is up to date...i also noticed an error when i open up the synaptic package manager....

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by jonnyfive on 2006-05-15
I am having the same issue you are having and update manager is not fixing it.](*,)

---

### Post by jonnyfive on 2006-05-15
This is the error I get when I apt-get.

```
Hit http://wine.lowvoice.nl breezy/main Packages
Err http://koti.mbnet.fi breezy/ Packages
  404 Not Found
Hit http://wine.lowvoice.nl breezy/main Sources
Err http://koti.mbnet.fi breezy/ Sources
  404 Not Found
Fetched 5B in 2s (2B/s)
Failed to fetch http://theli.free.fr/packages/breezy/./Packages.gz  404 Not Found
Failed to fetch http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz  404 Not Found
Failed to fetch http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list http://koti.mbnet.fi breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://theli.free.fr ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I also get an error in synaptic pakage manager 
```
W: Couldn't stat source package list http://koti.mbnet.fi breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://theli.free.fr ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)

```

How do I go about correcting this problem.

---

### Post by morbid_bean on 2006-05-15
[QUOTE=jonnyfive]This is the error I get when I apt-get.

```
Hit http://wine.lowvoice.nl breezy/main Packages
Err http://koti.mbnet.fi breezy/ Packages
  404 Not Found
Hit http://wine.lowvoice.nl breezy/main Sources
Err http://koti.mbnet.fi breezy/ Sources
  404 Not Found
Fetched 5B in 2s (2B/s)
Failed to fetch http://theli.free.fr/packages/breezy/./Packages.gz  404 Not Found
Failed to fetch http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz  404 Not Found
Failed to fetch http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list http://koti.mbnet.fi breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://theli.free.fr ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I also get an error in synaptic pakage manager 
```
W: Couldn't stat source package list http://koti.mbnet.fi breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://theli.free.fr ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)

```

How do I go about correcting this problem.[/QUOTE]


I dont know man...i wish i knew how to fix this :( :( :(

---

### Post by djheadley on 2006-05-15
I use Breezy and Synaptic and get this error also.  When it happens I just tell it to reload the sources list.

---

### Post by vh1 on 2006-05-16
[QUOTE=jonnyfive]This is the error I get when I apt-get.

```
Hit http://wine.lowvoice.nl breezy/main Packages
Err http://koti.mbnet.fi breezy/ Packages
  404 Not Found
Hit http://wine.lowvoice.nl breezy/main Sources
Err http://koti.mbnet.fi breezy/ Sources
  404 Not Found
Fetched 5B in 2s (2B/s)
Failed to fetch http://theli.free.fr/packages/breezy/./Packages.gz  404 Not Found
Failed to fetch http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz  404 Not Found
Failed to fetch http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list http://koti.mbnet.fi breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://theli.free.fr ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I also get an error in synaptic pakage manager 
```
W: Couldn't stat source package list http://koti.mbnet.fi breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://theli.free.fr ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)

```

How do I go about correcting this problem.[/QUOTE]

could you please post the contents of your /etc/apt/sources.list file? I suspect it contains some errors

---

### Post by blackjack6.21.91 on 2006-05-16
i think it means that your sources.list is screwed up

---

### Post by jonnyfive on 2006-05-16
How do you fix your .sources list?

---

### Post by jonnyfive on 2006-05-16
When I reload my synaptic repositories I get this error
```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
```
```
http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz: 404 Not Found
http://theli.free.fr/packages/breezy/./Packages.gz: 404 Not Found
http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz: 404 Not Found

```

---

### Post by drotter on 2006-05-16
sudo gedit /etc/apt/sources.list

comment out those three sources by putting "##" infront of it.  Save and do sudo apt-get update

that will fix it.
There's nothing wrong with your set up.  Those repos are apperantly down.

---

### Post by gam3r4eva on 2006-05-21
That fixed it for me drotter.  Thanks.

---

### Post by PerfMonk on 2006-05-23
[QUOTE=blackjack6.21.91]i think it means that your sources.list is screwed up[/QUOTE]

Could it be that you don't have last version of automatix.  I had the same problem with those source:

[http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz:](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz:) 404 Not Found
[http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz:](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz:) 404 Not Found
[http://theli.free.fr/packages/breezy/./Packages.gz:](http://theli.free.fr/packages/breezy/./Packages.gz:) 404 Not Found

I think you have to download last version of automatix and replay your setup.
This should fix everthing.

regards,
          BT

---

### Post by PapaLeon on 2006-05-24
I am having a similar problem to the one reported by the original poster. When I try to run sudo apt-get update I get this error message:

```
Get:1 http://us.archive.ubuntu.com breezy Release.gpg [189B]
Ign http://wine.budgetdedicated.com breezy Release.gpg
Hit http://us.archive.ubuntu.com breezy Release
Ign http://us.archive.ubuntu.com breezy/main Packages
Hit http://wine.budgetdedicated.com breezy Release
Hit http://us.archive.ubuntu.com breezy/restricted Packages
Ign http://us.archive.ubuntu.com breezy/universe Packages
Ign http://wine.budgetdedicated.com breezy/main Packages
Hit http://wine.budgetdedicated.com breezy/main Packages
Ign http://us.archive.ubuntu.com breezy/multiverse Packages
Ign http://us.archive.ubuntu.com breezy/main Sources
Hit http://us.archive.ubuntu.com breezy/restricted Sources
Hit http://us.archive.ubuntu.com breezy/universe Sources
Hit http://us.archive.ubuntu.com breezy/multiverse Sources
Get:2 http://us.archive.ubuntu.com breezy/main Packages [767kB]
99% [2 Packages gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com breezy/main Packages
  Sub-process gzip returned an error code (1)
Get:3 http://us.archive.ubuntu.com breezy/universe Packages [3028kB]
Get:4 http://us.archive.ubuntu.com breezy/multiverse Packages [116kB]
99% [3 Packages gzip 0]
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com breezy/universe Packages
  Sub-process gzip returned an error code (1)
Get:5 http://us.archive.ubuntu.com breezy/main Sources [305kB]
99% [4 Packages gzip 0]
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com breezy/multiverse Packages
  Sub-process gzip returned an error code (1)
99% [Working]
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com breezy/main Sources
  Sub-process gzip returned an error code (1)
Fetched 5B in 2s (2B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

and when I start synaptic I get: 
```
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

```

My sources.list hasn't changed since I upgraded to breezy, and it obviously worked fine then so I'm fairly certain that it is not the problem. The gzip error I believe indicates that the file isn't a valid gzip archive, but I dont know if that means there's a problem on my end or what. Please to be helping me out here.

---

### Post by aysiu on 2006-05-24
Try the  bottom of this page:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

If that doesn't work, try the top of the page.

---

### Post by PapaLeon on 2006-05-24
the bit on the bottom of the page worked. thanks dooder, I can relax now.

---

### Post by dsicher on 2006-06-08
this just worked for me 
put the ubuntu install disc in you drive
then go into synaptic  Edit>Add Cd-rom 
it scaned the disc automatically and copied some stuff
after that i haven't gotten the error message

---

