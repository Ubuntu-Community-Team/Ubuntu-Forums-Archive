---
title: "problems updating with Package Manager or apt-get"
date: 2012-09-24
forum: General Help
---

### Post by parminides on 2012-09-24
I'm running 12.04 Unity on my HP laptop.

My Package Manager is not working. First of all, there's an icon on the upper panel. Clicking on it reveals a message (see attached image file nopackage2.jpg) that says there was an error opening the cache. It also recommends that I run Package Manager or apt-get to find more information.

Package Manager says it couldn't initialize the package information (see attached image file nopackage.jpg).

Both the warning icon and Package Manager say "E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/list/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-amd64_Packages, E:The package list or status file could not be parsed or opened."

If I run sudo apt-get update I get many errors associated with GPG keys and signature verifications.

```

Reading package lists... Error!
W: GPG error: http://us.archive.ubuntu.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 0D18601A1EE8660B Launchpad PPA for Darik Horn
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```

My other computer, which also runs 12.04 Unity, is set up almost identically and isn't having this problem. Any ideas?

---

### Post by drmrgd on 2012-09-24
I'm not sure if it's an apt cache lists error causing the GPG error or vice versa.  First, though, let's try to fix the package lists error and see what happens.  From a terminal do:

```
sudo rm -rf /var/lib/apt/lists/*
```

After that, run apt-get update and report back any errors you get from there.  I'm hoping that rebuilding the MergeList will clear up all of your problems.

---

### Post by parminides on 2012-09-24
That seems to have fixed it. I didn't notice any error messages with apt-get update, and the red warning icon disappeared from the top panel. Thanks so much.

But I think I'll wait a day or two before I declare the thread solved.

---

### Post by parminides on 2012-09-25
Update ran successfully yesterday, so I declare it solved. Thanks for providing me the solution.

---

### Post by flyingthings93 on 2012-10-06
Worked for me, too.  Thanks.

---

### Post by spencerownside on 2012-11-30
I have been getting similar errors for a while now also. I followed the above directions but did not get the same results. When I run the 'apt update' command this is kicking out in my terminal:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

Any ideas please?

---

### Post by plucky on 2012-11-30
> **spencerownside said:**
> I have been getting similar errors for a while now also. I followed the above directions but did not get the same results. When I run the 'apt update' command this is kicking out in my terminal:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

Any ideas please?


That is trying to access the repository for 10.10 Maverick which has reached End of Life,which means the repositories are closed.

That is why you are getting the 404 Not Found warning.

Either upgrade to a supported version or disable the Maverick Repository.

Good Luck

---

