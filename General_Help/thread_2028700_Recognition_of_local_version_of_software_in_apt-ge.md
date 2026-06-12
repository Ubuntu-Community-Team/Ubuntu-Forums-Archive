---
title: "Recognition of local version of software in apt-get"
date: 2012-07-18
forum: General Help
---

### Post by aerojh on 2012-07-18
Hi,

I'm setting up Xubuntu 12.04 (amd64) on some computers and am running into some problems with package management.

I am using Centrify Express to add the machines to Active Directory and as part of that have installed the Centrify packaged samba over the version in the repos. (I am posting this here over the Centrify forums as I believe the issue is more directly related to (Xu|U)buntu and package management than Centrify itself.)

As far as I can tell the Centrify samba bundles most of the samba packages in a single .deb file. The problem resulting from this is that certain packages (e.g. libsmbclient) are installed in /opt by the Centrify package and apt-get doesn't know that these packages are installed, so it thinks that packages that depend on these libs have unmet dependencies (an example of such a package is vlc-nox). I also can't install packages that depend on samba such as nautilus-share.

What I haven't been able to figure out is how to get apt-get to recognized the locally installed versions of these libs. As far as using the libs goes, I think I can just symlink the locations in /lib (or wherever the repo versions are installed; I can get these locations from other machines not on the domain with samba from the Ubuntu repos) to the Centrify versions.

Thanks!

---

### Post by Cheesehead on 2012-07-18
> **aerojh said:**
> The problem resulting from this is that certain packages (e.g. libsmbclient) are installed in /opt by the Centrify package and apt-get doesn't know that these packages are installed, so it thinks that packages that depend on these libs have unmet dependencies (an example of such a package is vlc-nox). I also can't install packages that depend on samba such as nautilus-share.

Something seems strange there.
As part of installing the package, the package manager **must** change the package state to installed.

I can certainly understand **version** problems when you install a third-party deb, but forgetting the package is installed should never happen.

Could you please post a complete set of those unmet-dependency error messages? If you really have (expected) version problems due to the third-party deb, you may be able to apt-pin (or upgrade or downgrade) to a solution.

What version of Ubuntu are you running?

---

### Post by aerojh on 2012-07-18
> **Cheesehead said:**
> Something seems strange there.
As part of installing the package, the package manager **must** change the package state to installed.

I can certainly understand **version** problems when you install a third-party deb, but forgetting the package is installed should never happen.

Could you please post a complete set of those unmet-dependency error messages? If you really have (expected) version problems due to the third-party deb, you may be able to apt-pin (or upgrade or downgrade) to a solution.

The problem here is that there is a package for their overall samba distribution, which **does** have its state as installed, but it includes packages that are packaged separately in the Ubuntu repos.

So, the Centrify samba is installed as [font="Courier New"]centrifydc-samba[/font], but packages it contains, such as the aforementioned [font="Courier New"]libsmbclient[/font], are not marked as installed.
**Edit:** I should be clearer here, the [font="Courier New"]centrifydc-samba[/font] package **contains** [font="Courier New"]libsmbclient[/font] etc., but these are **not** separate packages.

An example with [font="Courier New"]vlc[/font] is:
```

You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 vlc-nox : Depends: libsmbclient (>= 3.0.24) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

If I run [font="Courier New"]sudo apt-get -f install[/font]:
```

$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libsmbclient
The following NEW packages will be installed:
  libsmbclient
0 upgraded, 1 newly installed, 0 to remove and 38 not upgraded.
4 not fully installed or removed.
Need to get 0 B/2,159 kB of archives.
After this operation, 6,876 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 195666 files and directories currently installed.)
Unpacking libsmbclient (from .../libsmbclient_2%3a3.6.3-2ubuntu2.3_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libsmbclient_2%3a3.6.3-2ubuntu2.3_amd64.deb (--unpack):
 trying to overwrite '/usr/share/man/man7/libsmbclient.7.gz', which is also in package centrifydc-samba 3.5.11-4.5.3.573
dpkg-deb (subprocess): data: internal gzip write error: Broken pipe
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg-deb (subprocess): failed in write on buffer copy for failed to write to pipe in copy: Broken pipe
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libsmbclient_2%3a3.6.3-2ubuntu2.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

> **Cheesehead said:**
> What version of Ubuntu are you running?

I am running Xubuntu 12.04. Output of [font="Courier New"]uname -a[/font] is (hostname redacted):
```

Linux hostname 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

(The information in the sidebar under my user info is from when I created my Ubuntu Forums account a few months ago prior to needing 50 posts to edit that info.)

---

