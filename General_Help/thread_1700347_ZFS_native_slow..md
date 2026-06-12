---
title: "ZFS native slow."
date: 2011-03-04
forum: General Help
---

### Post by bomix on 2011-03-04
I'm trying the native ZFS module on my home fileserver.  So far with pretty disappointing results.
Writing degrades quickly to 5-10 MB/s, and reading is just plain ridiculous at 300 KB/s. I need som help tuning this thing. Please?

Some details:

[LIST]
[*]Ubuntu 10.04.2 LTS 64bit, 8GB RAM.
[*]Installed ubuntu-zfs metapackage version "3~lucid (ubuntu-zfs)" (0.6.0.1rc1)
[*]zpool: 4 x 2TB Samsung spinpoint F4 disks in a RAIDZ1:
```

    tank        ONLINE       0     0     0
      raidz1-0  ONLINE       0     0     0
        sda     ONLINE       0     0     0
        sdb     ONLINE       0     0     0
        sdc     ONLINE       0     0     0
        sdd     ONLINE       0     0     0

```
[/LIST]
When I start copying files into the zpool, things start out great, but then degrades quickly. When the zfs kernel module has aloocated all system memory, kswapd0 steps into action and performance of the whole system grinds to a near-halt.

Example output of iostat of a file-copy on a freshly booted system:

```

# zpool iostat 5
               capacity     operations    bandwidth
pool        alloc   free   read  write   read  write
----------  -----  -----  -----  -----  -----  -----
tank        1,34T  5,91T  2,13K     18  1,46M  1,86M
tank        1,34T  5,91T  3,65K    438  2,48M  51,9M
tank        1,34T  5,91T  3,53K    635  2,39M  73,0M
tank        1,34T  5,91T  3,34K    784  2,27M  90,6M
tank        1,34T  5,91T  3,68K    379  2,48M  44,9M
tank        1,34T  5,91T  3,56K    800  2,41M  94,8M
tank        1,34T  5,91T  3,08K    412  2,09M  49,0M
tank        1,34T  5,91T  2,75K  1,02K  1,86M  81,0M
tank        1,34T  5,91T  2,47K  13,8K  1,66M  24,5M
tank        1,34T  5,91T  1,65K  61,4K  1,12M  35,5M
tank        1,34T  5,91T  2,73K  50,1K  1,85M  29,1M
tank        1,34T  5,91T  2,67K  34,8K  1,81M  20,4M
tank        1,34T  5,91T  2,80K  50,0K  1,90M  29,1M
tank        1,34T  5,91T  2,62K  31,8K  1,78M  18,7M
tank        1,34T  5,91T  2,27K  18,3K  1,55M  10,9M
tank        1,34T  5,91T  2,51K  16,4K  1,70M  9,59M

```I would expect write performance to be 50+ MB/s or something. 

I tried to limit the memory consumption by setting the zfs_arc_max to 5.000.000.000 (5GB, right?) with this:

```

# echo "5000000000" > /sys/module/zfs/parameters/zfs_arc_max

```That doesn't seem to do anything. After rebooting it is reset to zero. So I guess I'm not doing this right? How do I tell ZFS to limit memory usage? And how do I make it stick?

Also, somewhere it was suggested to disable primarycache:

```

# zfs set primarycache=none tank

```That seems to make kswapd0 slightly less active. General performance is pretty much the same...

Please help :-)

---

### Post by ben8472 on 2011-03-05
i am just starting to test out the native ZFS Module on my own ubuntu installation.

i think you have to enter the size of the cache in hexdezimal

for me, 512MB was 

```
echo "0x20000000" > /sys/module/zfs/parameters/zfs_arc_max
```

to be safe i'd rather check it with an editor directly

i used this as a reference:

[http://www.okboot.org/2008/02/limiting-ram-used-by-zfs-limiting-arc.html]("http://www.okboot.org/2008/02/limiting-ram-used-by-zfs-limiting-arc.html")

---

### Post by RobbieCrash on 2011-09-30
Have you made any progress on this?

I'm having the same issues, write speeds peak at about 30MB/sec and then quickly degrade to 10MB/sec at max, usually down around 7.

I'm running a RAIDZ2 pool with five WD Caviar Blacks on a Promise controller. If I switch things around and run an mdadm array off the same card, with the same model drives in RAID5 I get 70MB/sec at least.

Additionally, unless I periodically reset zfs_arc_max to some limit I my system locks up when the RAM usage spikes on large IO operations.

I've tried adding a fast SSD as a log drive, and it had seemingly no effect on the transfer rates. Read rates also did not improve if I added a cache drive.

Edit: premature post

---

### Post by Alvinator9000 on 2013-03-05
> **RobbieCrash said:**
> 
I'm having the same issues, write speeds peak at about 30MB/sec and then quickly degrade to 10MB/sec at max, usually down around 7.
I've tried adding a fast SSD as a log drive, and it had seemingly no effect on the transfer rates. Read rates also did not improve if I added a cache drive.

 
Same here unfortunately :/
I've got 6 drives running that each have a tested IOSTAT speed of minimum 70MB/s all in a Z1, I've added SLOG and 40GB cache both to no avail.

It seems to work fine for transfers up to the first 10GB (Ram limit) after a restart of the PC at about 200MB/s, then drops down to about 3-4 MB/s, even if I stop the transfer and transfer something else it has the slow speed.

I use "**[COLOR=#222222][FONT=Courier New]zpool iostat -v -T d 1"[/FONT][/COLOR]** [FONT=Courier New]to see what each drive in my pool is doing at any given time including the SLOG and Cache, this updates new info every second, to kill run "killall iostat" as root ("sudo -i").[/FONT]

---

### Post by wildmanne39 on 2013-03-05
Old thread closed! please start a new thread if you need to you can link to this thread. Thanks

---

