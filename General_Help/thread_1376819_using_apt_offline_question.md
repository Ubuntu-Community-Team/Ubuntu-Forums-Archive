---
title: "using apt offline question"
date: 2010-01-09
forum: General Help
---

### Post by budr on 2010-01-09
Not sure what section this goes in.

I'm currently running kubuntu jaunty, but I have lucid installed on another partition.  Keeping it up to date is kind of a hassle because my isp imposes bandwidth restrictions during regular hours.  If I want to download anything very big I have to do it at night.

What I've been doing is, boot into lucid, do an apt-get update and upgrade --print-uris to get a list of files to download later with cron.  One problem with that, aside from two extra reboots every time, is there is always a time lag between the update and the downloads.  Occasionally something gets updated in the repositories in the meantime, which means I don't get everything in sync.

Yesterday I stumbled onto the Using APT Offline howto.

[http://www.fifi.org/doc/apt/offline.html/ch2.html](http://www.fifi.org/doc/apt/offline.html/ch2.html)

The howto describes how to use a custom apt.conf to update and download packages for another machine, possibly a different distro, to portable media.  The most obvious case is to update a machine that doesn't have net access.

In my case, the "portable media" is another partition on this machine.  Since the /var/cache/apt directory structure already exists on the lucid partition, my idea was to use a custom apt.conf to point to that existing directory structure and let apt update the lucid installation using the existing lucid status file and sources.list on that partition.

Assuming the lucid partition is mounted at /lucid, it would look something like this:

```
APT
      {
        /* This is not necessary if the two machines are the same arch, it tells
           the remote APT what architecture the Debian machine is */
        Architecture "i386";
       
        Get::Download-Only "true";
      };
     
      Dir
      {
        /* Use the disc for state information and redirect the status file from
           the /var/lib/dpkg default */
        State "/lucid/var/lib/dpkg/";
        State::status "status";
     
        // Binary caches will be stored locally
        Cache::archives "/lucid/var/cache/apt/archives/";
        Cache "/lucid/tmp/";
       
        // Location of the source list.
        Etc "/lucid/etc/";
      };

```
That may not be exactly right, but maybe you can see what I have in mind.  Then I could run a version of the script a little further down the howto from cron to keep my lucid install current.  Does that make sense?

---

