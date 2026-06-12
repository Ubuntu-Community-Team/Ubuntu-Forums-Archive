---
title: "Failed to download repository information?"
date: 2010-10-14
forum: General Help
---

### Post by binarylife on 2010-10-14
when I check the update manager it gives me this error :

W:GPG error: [http://archive.canonical.com](http://archive.canonical.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.bz2)  Hash Sum mismatch
, E:Some index files failed to download, they have been ignored, or old ones used instead.

..................
and  also i tried sudo apt-get update && sudo apt-get upgrade:

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.bz2)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

+++++++++++++++++
how can i fix it ? 
thanks

---

### Post by sikander3786 on 2010-10-14
Did you try changing the download server?

Also, try this,

```
sudo apt-get clean
```

```
sudo apt-get update
```

---

### Post by binarylife on 2010-10-14
> **sikander3786 said:**
> Did you try changing the download server?

Also, try this,

```
sudo apt-get clean
```

```
sudo apt-get update
```

yes ,i've changed it to main server.

and i tried sudo apt-get clean then update 
but same error 

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.bz2)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by sikander3786 on 2010-10-14
Ok. Please see post # 6 in this thread.

[http://ubuntuforums.org/showthread.php?t=1586151](http://ubuntuforums.org/showthread.php?t=1586151)

And if it doesn't work, this one will surely work. Post # 16

[http://ubuntuforums.org/showthread.php?t=75813&page=2](http://ubuntuforums.org/showthread.php?t=75813&page=2)

---

### Post by binarylife on 2010-10-14
> **sikander3786 said:**
> Ok. Please see post # 6 in this thread.

[http://ubuntuforums.org/showthread.php?t=1586151](http://ubuntuforums.org/showthread.php?t=1586151)

And if it doesn't work, this one will surely work. Post # 16

[http://ubuntuforums.org/showthread.php?t=75813&page=2](http://ubuntuforums.org/showthread.php?t=75813&page=2)

yes that worked for me , I tried this 
```
sudo apt-get update -o Acquire::http::No-Cache=True
```
and now it is fixed .
thanks a lot man ! : )

---

### Post by sikander3786 on 2010-10-14
If you want to, you can make those changes permanent by editing /etc/apt/apt.conf so the problem doesn't repeat itself.

```
APT 
{
// Options for the downloading routines
  Acquire
  {
    http
    {
      No-Cache "true";
    };
  };
}
```

Regards.

---

### Post by perspectoff on 2010-10-14
> **binarylife said:**
> yes that worked for me , I tried this 
```
sudo apt-get update -o Acquire::http::No-Cache=True
```
and now it is fixed .
thanks a lot man ! : )

Oh man, that has solved so many problems for me!

Now my servers and lots of other stuff work correctly again.

I had guessed that the caching of networking was a problem for a while, but did not know how to correct it.

I noticed the problem disappeared whenever I had restarted networking with

 sudo /etc/init.d/networking restart

which I had assumed cleared the networking cache.

Where, exactly, is the caching problem? Network Manager or somewhere else?

---

### Post by DeadParrot on 2010-10-26
That's what I get, when I run 
sudo apt-get update -o Acquire::http::No-Cache=True

```


Get:4 http://gb.archive.ubuntu.com maverick-proposed/main i386 Packages [36.8kB]
Err http://ppa.launchpad.net maverick/main Sources                             
  404  Not Found
Get:5 http://gb.archive.ubuntu.com maverick-proposed/multiverse i386 Packages [14B]
Get:6 http://gb.archive.ubuntu.com maverick-proposed/universe i386 Packages [18.5kB]
Err http://ppa.launchpad.net maverick/main i386 Packages                       
  404  Not Found
Fetched 86.9kB in 13s (6,494B/s)                                               
W: Failed to fetch http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by sikander3786 on 2010-10-27
> **DeadParrot said:**
> That's what I get, when I run 
sudo apt-get update -o Acquire::http::No-Cache=True

```


Get:4 http://gb.archive.ubuntu.com maverick-proposed/main i386 Packages [36.8kB]
Err http://ppa.launchpad.net maverick/main Sources                             
  404  Not Found
Get:5 http://gb.archive.ubuntu.com maverick-proposed/multiverse i386 Packages [14B]
Get:6 http://gb.archive.ubuntu.com maverick-proposed/universe i386 Packages [18.5kB]
Err http://ppa.launchpad.net maverick/main i386 Packages                       
  404  Not Found
Fetched 86.9kB in 13s (6,494B/s)                                               
W: Failed to fetch http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```
Those 404 errors mean that the servers for Launcpad PPAs are down. Disable the problematic PPAs from Software Center > Edit > Software Sources > Other Software Tab and retry **sudo apt-get update**.

Nothing problematic there.

---

### Post by Mamadex on 2011-03-17
Here's most solution guideline to repair this problem in error of when you run *sudo apt-get update*:
> Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  Hash Sum mismatch Some index files failed to download, they have been ignored, or old ones used instead.

1. backup from **/var/cache/apt/archives** folder
2. run **sudo apt-get clean**
3. delete **/var/lib/apt/lists** content
4. run **sudo apt-get update** (before perform this step it's better to set *Download sources from* to *Main server* in the Ubuntu Software Center or run /etc/apt/sources.list)
5. copy the backup folder (line:1) to /var/cache/apt/archives folder
6. Install Apps with those debs you had now :D

---

### Post by Mamadex on 2011-03-18
but it may occurs again!

---

### Post by shivapprasad on 2011-09-11
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_n-muench_vlc_ubuntu_dists_natty_main_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

Can anyone tell what this error is?

---

