---
title: "How to install flash ?"
date: 2009-11-24
forum: General Help
---

### Post by kikloo on 2009-11-24
Hi,

I am trying to install Adboe Flash player so i can play games etc. but after downloading and running it, it said: 

Error: Dependency is not satifiable: libnspr4-dev


What to do ?

---

### Post by MelDJ on 2009-11-24
did you get the package for your version of ubuntu? 
try sudo apt-get install libnspr4-dev

---

### Post by kikloo on 2009-11-24
> **MelDJ said:**
> did you get the package for your version of ubuntu? 
try sudo apt-get install libnspr4-dev

Hi,

When i ran the command above it gave me the following:

---
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libnspr4-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libnspr4-0d
E: Package libnspr4-dev has no installation candidate
---

Also i got flash earlier from Adobe's website. Firefox opened that page and i selected deb for Ubuntu 8.4+. But that gave the earlier error.

How to fix ?

Thanks.

---

### Post by audiomick on 2009-11-24
These might help:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[http://ubuntuforums.org/showthread.php?t=1310795](http://ubuntuforums.org/showthread.php?t=1310795)

---

### Post by kikloo on 2009-11-24
> **audiomick said:**
> These might help:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[http://ubuntuforums.org/showthread.php?t=1310795](http://ubuntuforums.org/showthread.php?t=1310795)

Hi,

Okay thanks. How to install Filezilla ? I earlier downloaded files from their site but that don't run, so i searched on google and did the sudo filezilla thing and it said that it will create icon in Applications > Internet > Filezilla but its not there ?

How to install ?

Thanks.

---

### Post by audiomick on 2009-11-24
Filezilla is availavle via the GUI Package manager
System > Administration > package manager
search filezilla
Get it from there, and all should be well

---

### Post by mkvnmtr on 2009-11-24
Is there some reason that the Adobe flash in your package manager is not satisfactory? It is very easy to install and seems to come with all the other packages you need.

---

### Post by kikloo on 2009-11-24
> **audiomick said:**
> These might help:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[http://ubuntuforums.org/showthread.php?t=1310795](http://ubuntuforums.org/showthread.php?t=1310795)

While installing the first url i got this:

---
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
---

How to fix ?

Thanks.

---

### Post by kikloo on 2009-11-24
> **audiomick said:**
> Filezilla is availavle via the GUI Package manager
System > Administration > package manager
search filezilla
Get it from there, and all should be well

It is not showing filezilla in Synaptic Package Manager under System > Administrator. What to do ?

Thanks.

---

### Post by kikloo on 2009-11-24
> **mkvnmtr said:**
> Is there some reason that the Adobe flash in your package manager is not satisfactory? It is very easy to install and seems to come with all the other packages you need.

I don't see Adobe Flash Player in Synaptic Package Manager. I don't know which version you guys are using of Ubuntu but i am using latest 9.10 and it does'nt have Adobe Flash Player and FileZilla and both them are refusing to install.

Thanks.

---

### Post by qwerty2009 on 2009-11-24
Install restricted extras using this comand in terminal 

"sudo apt-get install ubuntu-restricted-extras" without quotes 

or search for ubuntu-restricted-extras in software centre if you prefer to do it graphically

---

### Post by mkvnmtr on 2009-11-24
I am looking in my package manager now. Type in the quick search box adobe.
Look for adobe flash plugin. The one that is supported by ubuntu.


To see it in the package you need to enable the main repository. On my system that is the first box in software sources.

---

### Post by audiomick on 2009-11-24
I don't know exactly where filezilla comes from, but if you can't see it, it is probably because you haven't got "universe" and "multiverse" selected in your Package Sources.
In Synaptic options > package sources
(or something like that; I am translating out of a German installation :-) )

Bear in mind that Ubuntu has reasons for not having these sources selected by default, so you should take the time to inform yourself at some point what these reasons are. Info is available in the Ubuntu Documentation.

If it doesn't turn up after you have enabled these sources, it might be at Medibuntu, but I don't think so.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by mkvnmtr on 2009-11-24
On my system filezilla is in the get-deb repository. You have no need to install it to get flash. After you have everything working to your satisfaction google get-deb to see if it hase any packages you think you would like to try.

---

### Post by qwerty2009 on 2009-11-24
All your codec problems would be solved if you just install ubuntu-restricted-extras

---

### Post by audiomick on 2009-11-24
Firstly, qwerty is more than likely right. Do what he says.
Secondly, have a look at this:
[http://ubuntuforums.org/showthread.php?t=1310795](http://ubuntuforums.org/showthread.php?t=1310795)

---

### Post by kikloo on 2009-11-24
> **qwerty2009 said:**
> All your codec problems would be solved if you just install ubuntu-restricted-extras

Hi,

When i am trying to install this i get:

Requires installation of untrusted packages:
The action would require the installation of packages from not authenticated sources.

w32codecs


What is this now ?

Thanks.

---

### Post by 3rdalbum on 2009-11-24
> **kikloo said:**
> Hi,

When i am trying to install this i get:

Requires installation of untrusted packages:
The action would require the installation of packages from not authenticated sources.

w32codecs


What is this now ?

Thanks.

You didn't follow the steps for adding the Medibuntu keyring - it's a digital signing key that ensures that the software you are downloading has not been tampered with in transit. You can just click OK and install without the key for now.

Two more things:

1. Do you really need Filezilla? You can connect directly to FTP servers from Gnome. Places > Connect To Server.

2. In order to install Filezilla, either use Synaptic Package Manager or type the following:

```
sudo apt-get install filezilla
```

Seems you missed out a few crucial words. "sudo filezilla" would just run Filezilla as root - which is not a good idea.

---

### Post by bodhi.zazen on 2009-11-24
To install flash :

```
sudo apt-get install flashplugin-nonfree
```

[http://packages.ubuntu.com/karmic/flashplugin-nonfree](http://packages.ubuntu.com/karmic/flashplugin-nonfree)

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

Works on both 32 and 64 bit Ubuntu.

---

### Post by kikloo on 2009-11-24
> **bodhi.zazen said:**
> To install flash :

```
sudo apt-get install flashplugin-nonfree
```

[http://packages.ubuntu.com/karmic/flashplugin-nonfree](http://packages.ubuntu.com/karmic/flashplugin-nonfree)

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

Works on both 32 and 64 bit Ubuntu.

So many ways to do 1 thing and none working so far now. Anyways i am downloading that karmic thing dunno what is it though...when it is over i will try your method also.

Thanks.

---

### Post by Darael on 2009-11-24
For it complianing about unauthenticated packages, run this:
```
sudo apt-get -y --allow unauthenticated install medibuntu-keyring
```

That should sort out that problem.

---

### Post by Bigneil on 2009-11-24
i always go through the sticky in the multi-media+video section when setting up an ubuntu computer, it gives a complete run down of all the multi-media stuff relevant to each version of ubuntu. Including common errors and how to combat them.

---

### Post by bodhi.zazen on 2009-11-24
> **kikloo said:**
> So many ways to do 1 thing and none working so far now. Anyways i am downloading that karmic thing dunno what is it though...when it is over i will try your method also.

Thanks.

yes, too many cooks spoil the broth ...

In general:


[list]
[*]If it is available in the ubuntu repositories, use those first.
[*]If not, you can try a 3rd party repository. Go with the most trusted repositories first. I suggest Launchpad ppa > mediabuntu > Debian > 3rd party repos.
[indent]**Keep in mind, just because it is a .bed does NOT mean it is compatible with Ubuntu.**[/indent]
[*]Go direct to the 3rd party source. This often means compiling, but not always, some apps are distributed as binaries.
[*]Use something like Alien to convert a rpm.
[/list]


If you want to learn how to manage a 3rd party repo, take a look here :

[Repositories/Ubuntu - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Repositories/Ubuntu") 

For 3rd party repositories, in general you need to first add a repository to your sources list ( /etc/apt/sources.list ) either via the command line / direct edit or via a gui application. You then import the key.

This advice comes from much experience with such things and keeps everything as compatible and as easy to update as possible.

In this case, why are we installing an application from adobe or mediabuntu if the application is available in the Ubuntu repositories ? Doing so only makes it more complicated then it should be and I am sorry but is probably not he best of advice.

IMO valid reasons to go outside the Ubuntu repositories would be if there is some feature a newer version has or some reason the application in the Ubuntu repositories will not work.

Try the application in the Ubuntu repository first, and if that fails, remove it and try another method.

So my advice to you is to stop and think about what you are doing before blindly following advice.

-----

Stating that flash is not working is insufficient information. Why is it not working ? What error message did you get ?

---

