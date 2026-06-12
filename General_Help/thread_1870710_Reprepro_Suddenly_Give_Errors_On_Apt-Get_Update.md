---
title: "Reprepro Suddenly Give Errors On Apt-Get Update"
date: 2011-10-27
forum: General Help
---

### Post by deauththis on 2011-10-27
I setup a small repo via reprepro and sync'd it into my web server.
The repo worked fine and I never really had any issues, until today.

Now all of the sudden I get this when I do an apt-get update:

```

Get:4 http://corsrv.us lucid/main Packages [6,239B]                                                                                                           
68% [4 Packages bzip2 0B]bzip2: (stdin) is not a bzip2 file.
Err http://corsrv.us lucid/main Packages
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 19.6kB in 2min 2s (160B/s)
W: GPG error: http://corsrv.us lucid Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch http://corsrv.us/reprepro/dists/lucid/main/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```My repo is setup at: [http://corsrv.us/packages](http://corsrv.us/packages)
deb [http://corsrv.us/packages]("http://corsrv.us/reprepro") lucid main

I deleted the whole thing trying to test and fix it..
Currently it only has "driftnet" in the repository

If you guys have any idea that'd be great, I've completely re-done this thing several times and I have no idea what could possibly be causing the issue.
Note: I do not use a GPG key and I have never set it up to use one because I don't want to have to remember a key as I'm creating the repo in-part so that I can easily have a single line to add for my favorite .debs and for a small distro that I manage for a small group.



EDIT

The issue is not my computer, I've tried this on 3 different linux desktops, an xubuntu and ubuntu 10.04s and a 10.04.2 lts


note: reprepro is now packages in the url


EDIT

I changed the domain name to: [http://packages.corsrv.us](http://packages.corsrv.us) and now it works... who the hell knows why is anyones guess

---

