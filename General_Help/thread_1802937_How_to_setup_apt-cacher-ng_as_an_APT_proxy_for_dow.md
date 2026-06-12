---
title: "How to setup apt-cacher-ng as an APT proxy for downloading software packages?"
date: 2011-07-12
forum: General Help
---

### Post by karthick87 on 2011-07-12
I have followed the below procedure,

```
sudo apt-get update 
sudo apt-get install apt-cacher-ng
```Edited the apt-cacher-ng configuration file acng.conf
 ```
sudo apt-get install nano
 sudo nano /etc/apt-cacher-ng/acng.conf
```I made the following change to acng.conf to

 ```
BindAddress: 0.0.0.0  
```Restarted apt-cacher-ng
 ```
sudo /etc/init.d/apt-cacher-ng restart
```Now in client machine
```
echo 'Acquire::http { Proxy "http://<server-ip>:3142"; };' | sudo tee /etc/apt/apt.conf.d/02proxy
```In server:
```
sudo mkdir /var/cache/apt-cacher-ng/_import
``````
sudo chown -R apt-cacher-ng /var/cache/apt-cacher-ng /var/cache/apt-cacher-ng/_import
```[COLOR=Red][B]Can anyone say me how to import the CD caches?


[/B][/COLOR]

---

### Post by karthick87 on 2011-07-13
Bump for a move...

---

### Post by gmargo on 2011-07-13
To import debian archive files (*.deb) into **apt-cacher-ng**'s cache, you must first run an "apt-get update" through the apt-cacher-ng proxy, so that the program has a copy of the Packages files for your release.  apt-cacher-ng will only import *.deb files that are referenced in current Packages files.

Then copy your *.deb files or pool directory into that **/var/cache/apt-cacher-ng/_import/** directory.  There is no need to flatten the directory structure; all subdirectories will be searched. Symbolic links should work too.

Now use your web browser to open [http://localhost:3142/](http://localhost:3142/) (or substitute appropriate IP address)

That page will say "The requested page is not accessible", blah, blah.  Near the bottom of that page is a link to the "Statistics report and configuration page", with this address: [http://localhost:3142/acng-report.html](http://localhost:3142/acng-report.html)

Click that link and you will be at the "Apt-Cacher NG maintenance page for <hostname>".  Near the bottom of that page is the "Import" section, with the "Start Import" button.  Click on that and wait until it's finished (it will print a bunch of stuff and sometimes seem to stop, but keep scrolling to the bottom and it will eventually finish.)

---

### Post by karthick87 on 2011-07-14
Do you want me to run,

```
sudo apt-get update
```

in client or in server?

---

### Post by gmargo on 2011-07-14
Client or server - it doesn't matter.  As long as you are updating through the apt-cacher-ng proxy.  Have you started and used the server yet?  Get that working before you worry about importing other .deb files.

---

### Post by karthick87 on 2011-07-15
I am getting the following output when i run apt-get update in client..

```
root@TME58:/etc/apt# apt-get update
Ign http://172.29.32.9 lucid Release.gpg
Ign http://172.29.32.9/in.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_IN
Ign http://172.29.32.9/in.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_IN
Ign http://172.29.32.9/in.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_IN
Ign http://172.29.32.9/in.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_IN
Ign http://172.29.32.9 lucid-updates Release.gpg
Ign http://172.29.32.9/in.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_IN
Ign http://172.29.32.9/in.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_IN
Ign http://172.29.32.9/in.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_IN
Ign http://172.29.32.9/in.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_IN
Ign http://172.29.32.9 lucid Release
Ign http://172.29.32.9 lucid-updates Release
Ign http://172.29.32.9 lucid/main Packages
Ign http://172.29.32.9 lucid/restricted Packages
Ign http://172.29.32.9 lucid/main Sources
Ign http://172.29.32.9 lucid/restricted Sources
Ign http://172.29.32.9 lucid/universe Packages
Ign http://172.29.32.9 lucid/universe Sources
Ign http://172.29.32.9 lucid/multiverse Packages
Ign http://172.29.32.9 lucid/multiverse Sources
Ign http://172.29.32.9 lucid-updates/main Packages
Ign http://172.29.32.9 lucid-updates/restricted Packages
Ign http://172.29.32.9 lucid-updates/main Sources
Ign http://172.29.32.9 lucid-updates/restricted Sources
Ign http://172.29.32.9 lucid-updates/universe Packages
Ign http://172.29.32.9 lucid-updates/universe Sources
Ign http://172.29.32.9 lucid-updates/multiverse Packages
Ign http://172.29.32.9 lucid-updates/multiverse Sources
Ign http://172.29.32.9 lucid/main Packages
Ign http://172.29.32.9 lucid/restricted Packages
Ign http://172.29.32.9 lucid/main Sources
Ign http://172.29.32.9 lucid/restricted Sources
Ign http://172.29.32.9 lucid/universe Packages
Ign http://172.29.32.9 lucid/universe Sources
Ign http://172.29.32.9 lucid/multiverse Packages
Ign http://172.29.32.9 lucid/multiverse Sources
Ign http://172.29.32.9 lucid-updates/main Packages
Ign http://172.29.32.9 lucid-updates/restricted Packages
Ign http://172.29.32.9 lucid-updates/main Sources
Ign http://172.29.32.9 lucid-updates/restricted Sources
Ign http://172.29.32.9 lucid-updates/universe Packages
Ign http://172.29.32.9 lucid-updates/universe Sources
Ign http://172.29.32.9 lucid-updates/multiverse Packages
Ign http://172.29.32.9 lucid-updates/multiverse Sources
Err http://172.29.32.9 lucid/main Packages
  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?
Err http://172.29.32.9 lucid/restricted Packages
  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?
Err http://172.29.32.9 lucid/main Sources
  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?
Err http://172.29.32.9 lucid/restricted Sources
  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?
Err http://172.29.32.9 lucid/universe Packages
  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?
Err http://172.29.32.9 lucid/universe Sources
  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?
Err http://172.29.32.9 lucid/multiverse Packages
  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?
Err http://172.29.32.9 lucid/multiverse Sources
  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?
Err http://172.29.32.9 lucid-updates/main Packages
  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?
Err http://172.29.32.9 lucid-updates/restricted Packages
  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?
Err http://172.29.32.9 lucid-updates/main Sources
  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?
Err http://172.29.32.9 lucid-updates/restricted Sources
  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?
Err http://172.29.32.9 lucid-updates/universe Packages
  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?
Err http://172.29.32.9 lucid-updates/universe Sources
  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?
Err http://172.29.32.9 lucid-updates/multiverse Packages
  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?
Err http://172.29.32.9 lucid-updates/multiverse Sources
  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?
W: Failed to fetch http://172.29.32.9:3142/in.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?

W: Failed to fetch http://172.29.32.9:3142/in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?

W: Failed to fetch http://172.29.32.9:3142/in.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?

W: Failed to fetch http://172.29.32.9:3142/in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?

W: Failed to fetch http://172.29.32.9:3142/in.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?

W: Failed to fetch http://172.29.32.9:3142/in.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?

W: Failed to fetch http://172.29.32.9:3142/in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?

W: Failed to fetch http://172.29.32.9:3142/in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?

W: Failed to fetch http://172.29.32.9:3142/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?

W: Failed to fetch http://172.29.32.9:3142/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?

W: Failed to fetch http://172.29.32.9:3142/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?

W: Failed to fetch http://172.29.32.9:3142/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?

W: Failed to fetch http://172.29.32.9:3142/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?

W: Failed to fetch http://172.29.32.9:3142/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?

W: Failed to fetch http://172.29.32.9:3142/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?

W: Failed to fetch http://172.29.32.9:3142/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by gmargo on 2011-07-15
Have you edited your **/etc/apt/sources.list** file to point at the proxy?  You should restore it to the default content (which you saved before you edited, right?)  All you need is the proxy specification which you have placed in **/etc/apt/apt.conf.d/02proxy**.

---

### Post by karthick87 on 2011-07-16
See the output now,

```
root@TME133:/etc/apt# apt-get update
Get:1 http://in.archive.ubuntu.com lucid Release.gpg [189B]
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_IN
Get:2 http://in.archive.ubuntu.com lucid-updates Release.gpg [198B]            
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_IN
Get:3 http://in.archive.ubuntu.com lucid Release [57.2kB]
Get:4 http://in.archive.ubuntu.com lucid-updates Release [44.7kB]
Ign http://in.archive.ubuntu.com lucid/main Packages
Ign http://in.archive.ubuntu.com lucid/restricted Packages
Ign http://in.archive.ubuntu.com lucid/main Sources
Ign http://in.archive.ubuntu.com lucid/restricted Sources
Ign http://in.archive.ubuntu.com lucid/universe Packages
Ign http://in.archive.ubuntu.com lucid/universe Sources
Ign http://in.archive.ubuntu.com lucid/multiverse Packages
Ign http://in.archive.ubuntu.com lucid/multiverse Sources
Ign http://in.archive.ubuntu.com lucid-updates/main Packages
Ign http://in.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://in.archive.ubuntu.com lucid-updates/main Sources
Ign http://in.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://in.archive.ubuntu.com lucid-updates/universe Packages
Ign http://in.archive.ubuntu.com lucid-updates/universe Sources
Ign http://in.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://in.archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://in.archive.ubuntu.com lucid/main Packages
Ign http://in.archive.ubuntu.com lucid/restricted Packages
Ign http://in.archive.ubuntu.com lucid/main Sources
Ign http://in.archive.ubuntu.com lucid/restricted Sources
Ign http://in.archive.ubuntu.com lucid/universe Packages
Ign http://in.archive.ubuntu.com lucid/universe Sources
Ign http://in.archive.ubuntu.com lucid/multiverse Packages
Ign http://in.archive.ubuntu.com lucid/multiverse Sources
Ign http://in.archive.ubuntu.com lucid-updates/main Packages
Ign http://in.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://in.archive.ubuntu.com lucid-updates/main Sources
Ign http://in.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://in.archive.ubuntu.com lucid-updates/universe Packages
Ign http://in.archive.ubuntu.com lucid-updates/universe Sources
Ign http://in.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://in.archive.ubuntu.com lucid-updates/multiverse Sources
Err http://in.archive.ubuntu.com lucid/main Packages
  502  Connection reset by peer
Err http://in.archive.ubuntu.com lucid/restricted Packages
  502  Connection reset by peer
Err http://in.archive.ubuntu.com lucid/main Sources
  502  Connection reset by peer
Err http://in.archive.ubuntu.com lucid/restricted Sources
  502  Connection reset by peer
Err http://in.archive.ubuntu.com lucid/universe Packages
  502  Connection reset by peer
Err http://in.archive.ubuntu.com lucid/universe Sources
  502  Connection reset by peer
Err http://in.archive.ubuntu.com lucid/multiverse Packages
  502  Connection reset by peer
Err http://in.archive.ubuntu.com lucid/multiverse Sources
  502  Connection reset by peer
Err http://in.archive.ubuntu.com lucid-updates/main Packages
  502  Connection reset by peer
Err http://in.archive.ubuntu.com lucid-updates/restricted Packages
  502  Connection reset by peer
Err http://in.archive.ubuntu.com lucid-updates/main Sources
  502  Connection reset by peer
Err http://in.archive.ubuntu.com lucid-updates/restricted Sources
  502  Connection reset by peer
Err http://in.archive.ubuntu.com lucid-updates/universe Packages
  502  Connection reset by peer
Err http://in.archive.ubuntu.com lucid-updates/universe Sources
  502  Connection reset by peer
Err http://in.archive.ubuntu.com lucid-updates/multiverse Packages
  502  Connection reset by peer
Err http://in.archive.ubuntu.com lucid-updates/multiverse Sources
  502  Connection reset by peer
Fetched 102kB in 23s (4,309B/s)
W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz  502  Connection reset by peer

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz  502  Connection reset by peer

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz  502  Connection reset by peer

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz  502  Connection reset by peer

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz  502  Connection reset by peer

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz  502  Connection reset by peer

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz  502  Connection reset by peer

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz  502  Connection reset by peer

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz  502  Connection reset by peer

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz  502  Connection reset by peer

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz  502  Connection reset by peer

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz  502  Connection reset by peer

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz  502  Connection reset by peer

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz  502  Connection reset by peer

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz  502  Connection reset by peer

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz  502  Connection reset by peer

E: Some index files failed to download, they have been ignored, or old ones used instead.
root@TME133:/etc/apt# 
```

---

### Post by gmargo on 2011-07-16
What do you have in the **/etc/apt-cacher-ng/backends_ubuntu** file?

It should contain a single URL of your preferred mirror.
So for you it should have:
```

http://in.archive.ubuntu.com/ubuntu/

```Initially, I had problems getting **apt-cacher-ng** to work, and it was because the "backends_ubuntu" file was empty instead of containing the proper URL.  And I debugged it by setting the "Proxy:" entry in the **/etc/apt-cacher-ng/acng.conf** file to go through a **squid** daemon, so that I could inspect the addresses that apt-cacher-ng was calling.

---

### Post by karthick87 on 2011-07-18
See the below error pls,

```
root@TME51:/etc/apt# apt-get update
Hit http://in.archive.ubuntu.com lucid Release.gpg
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_IN
Hit http://in.archive.ubuntu.com lucid-updates Release.gpg
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_IN
Hit http://in.archive.ubuntu.com lucid Release
Hit http://in.archive.ubuntu.com lucid-updates Release
Hit http://in.archive.ubuntu.com lucid/main Packages
Hit http://in.archive.ubuntu.com lucid/restricted Packages
Get:1 http://in.archive.ubuntu.com lucid/main Sources [508kB]
Get:2 http://in.archive.ubuntu.com lucid/main Sources [508kB]
Hit http://in.archive.ubuntu.com lucid/restricted Sources                                                                                                                        
Get:3 http://in.archive.ubuntu.com lucid/universe Packages [220kB]                                                                                                               
99% [3 Packages bzip2 0B] [Connecting to 172.29.32.9 (172.29.32.9)]
bzip2: Compressed file ends unexpectedly;
    perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://in.archive.ubuntu.com lucid/universe Packages           
  Sub-process /bin/bzip2 returned an error code (2)
Get:4 http://in.archive.ubuntu.com lucid/universe Sources [3,165kB]
Get:5 http://in.archive.ubuntu.com lucid/multiverse Packages [180kB]                                                                                                             
Get:6 http://in.archive.ubuntu.com lucid/multiverse Sources [5,061B]                                                                                                             
Get:7 http://in.archive.ubuntu.com lucid-updates/main Packages [508kB]                                                                                                           
Get:8 http://in.archive.ubuntu.com lucid-updates/restricted Packages [3,240B]                                                                                                    
Get:9 http://in.archive.ubuntu.com lucid-updates/main Sources [198kB]                                                                                                            
Get:10 http://in.archive.ubuntu.com lucid-updates/restricted Sources [1,443B]                                                                                                    
Get:11 http://in.archive.ubuntu.com lucid-updates/universe Packages [220kB]                                                                                                      
Get:12 http://in.archive.ubuntu.com lucid-updates/universe Sources [78.2kB]                                                                                                      
Get:13 http://in.archive.ubuntu.com lucid-updates/multiverse Packages [10.5kB]                                                                                                   
Get:14 http://in.archive.ubuntu.com lucid-updates/multiverse Sources [5,061B]                                                                                                    
Fetched 5,214kB in 5min 48s (14.9kB/s)
W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.
root@TME51:/etc/apt# 

```

---

### Post by mosaic2s on 2012-03-10
I am in the same boat.
karthik, did you get the work around?

---

