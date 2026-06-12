---
title: "Error installing chromium-browser: unable to execute data (xz)"
date: 2010-11-15
forum: General Help
---

### Post by kc600 on 2010-11-15
Installing chromium-browser on maverick, i get:

```
sudo apt-get install chromium-browser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  chromium-browser-inspector chromium-codecs-ffmpeg
Suggested packages:
  chromium-browser-l10n
The following NEW packages will be installed:
  chromium-browser chromium-browser-inspector chromium-codecs-ffmpeg
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.7MB/16.0MB of archives.
After this operation, 60.0MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://archive.ubuntu.com/ubuntu/ maverick-updates/universe chromium-browser-inspector all 7.0.517.44~r64615-0ubuntu0.10.10.1 [618kB]
Get:2 http://archive.ubuntu.com/ubuntu/ maverick-updates/universe chromium-browser amd64 7.0.517.44~r64615-0ubuntu0.10.10.1 [15.0MB]
Fetched 15.7MB in 15s (1,032kB/s)                                              
(Reading database ... 179471 files and directories currently installed.)
Unpacking chromium-browser-inspector (from .../chromium-browser-inspector_7.0.517.44~r64615-0ubuntu0.10.10.1_all.deb) ...
dpkg-deb (subprocess): unable to execute data (xz): No such file or directory
dpkg-deb: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/chromium-browser-inspector_7.0.517.44~r64615-0ubuntu0.10.10.1_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Selecting previously deselected package chromium-codecs-ffmpeg.
Unpacking chromium-codecs-ffmpeg (from .../chromium-codecs-ffmpeg_0.6+svn20100904r58574+58998-0ubuntu1_amd64.deb) ...
Unpacking chromium-browser (from .../chromium-browser_7.0.517.44~r64615-0ubuntu0.10.10.1_amd64.deb) ...
dpkg-deb (subprocess): unable to execute data (xz): No such file or directory
dpkg-deb: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/chromium-browser_7.0.517.44~r64615-0ubuntu0.10.10.1_amd64.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/chromium-browser-inspector_7.0.517.44~r64615-0ubuntu0.10.10.1_all.deb
 /var/cache/apt/archives/chromium-browser_7.0.517.44~r64615-0ubuntu0.10.10.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Anyone know what's going on?

---

### Post by kc600 on 2010-11-15
This happened with all "Google chrome" browsers, also google-chrome-stable.

The first error i saw in the log had something to do with "xz", so i googled for it. It turns out to be a zip tool. I checked to see if it was installed:

```
$ sudo apt-get install xz-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xz-utils is already the newest version.
xz-utils set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

It was installed, so i tried re-installing:
```
$ sudo apt-get install --reinstall xz-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 160kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ maverick/main xz-utils amd64 4.999.9beta+20100527-1 [160kB]
Fetched 160kB in 0s (417kB/s)  
(Reading database ... 179471 files and directories currently installed.)
Preparing to replace xz-utils 4.999.9beta+20100527-1 (using .../xz-utils_4.999.9beta+20100527-1_amd64.deb) ...
Unpacking replacement xz-utils ...
Processing triggers for man-db ...
Setting up xz-utils (4.999.9beta+20100527-1) ...
```

After this i, was able to install chromium-browser and google-chrome-stable again.

---

### Post by kundancool on 2011-01-29
A bunch of thanks to you  This helped me installing Wine as I had same problem with Wine > sudo apt-get install --reinstall xz-utils saved my day!

---

