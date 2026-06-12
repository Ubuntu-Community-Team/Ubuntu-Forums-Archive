---
title: "Processes hangups: futex_wait &amp; poll_schedule"
date: 2011-03-21
forum: General Help
---

### Post by paul_gc on 2011-03-21
Hello everyone, this is a very new forum account but I can assure you I am a very real person with a very serious problem.

I have been using Ubuntu on/off for years now, recently I decided to buy a new machine and use only Ubuntu on it for work (web developer / php programmer here). However after a few weeks this still doesn't work consistently.

**The machine:**

Hardwarre: high specs: Intel i7 2600 sandy bridge, 16GB DDR3-1333, a 64GB crucial SSD, Asus P8P67-M Pro, etc.(an overkill really to edit code that doesn't even need to be compiled)

Im running: Ubuntu 10.10 2.6.35-28-generic x86_64 with all updates and patches.

**Some screenshots:**

sysmonitor: [http://img215.imageshack.us/img215/4206/processes.png](http://img215.imageshack.us/img215/4206/processes.png)
dmesg: [http://img141.imageshack.us/img141/6349/dmesg1.png](http://img141.imageshack.us/img141/6349/dmesg1.png)

**The problem:**

Zend Studio (a php code editor) will only run for 10 minutes before freezing hard. I have tried many other code editors (Quanta, BlueFish, gPHPEdit, you name it) but they all need Ubuntu to provide a local path to a remote FTP folder via "Connect to Server" on the top menu. This (again) works at first but will hang/freeze after a few minutes of use.

I have to close/kill programs and that server connection to make things work again... for another 10 minutes. I have already loose small amount of work here and there (not to mention blanked files that I needed to pull from backup)

**The Symptoms:**

1. Right after system start, all (but 1 or 2) processes show in System Monitor a waiting channel of "poll_schedule_timeout". 

2. gvfs-fuse-daemon goes straight into "futex_wait_queue_me" after bootup.

3. Right after opening Zend Studio, Java (process called "java") goes into "futex_wait_queue_me".

4. After a bit of FTP / file opening / file editing Zend Studio (and any other code editor) will freeze and needs to be ended and sometimes killed.

5. Browsing a local folder made with the "connect to a server" will work for 10 minutes or less and then freeze will a blank folder trying to load.

**Help needed:**

I have booted from a pendrive, with a live ubuntu (10.10 again) and I experience the same problems.

I can run a lot of other programs flawless for hours / days (this machine is on 24/7): Opera, Firefox, virtualbox, skype, gimp, remote desktop, mysql tools, filezilla. 

Note: that filezilla is an FTP client and it works fine, FTPing with Zend Studio or "Connect to server" from ubuntu doesnt seem to work consistently.

Also note: none of those programs are programmed in java, Zend Studio runs on Eclipse which runs on java, this could be a hint. Then again, "Connect to server" from Ubuntu.. does that use java??? I dont think so, but still it will hang after a few minutes.

The ZendStudio process has a waiting channel of "do_wait"

Any help is much much much appreciated.

If you need any extra info, screnshots, file/command output just ask I will provided ASAP.

---

### Post by woolyg on 2011-04-17
Hi paul_gc,

I'm seeing exactly the same issue - I wanted to evaluate Zend studio, so I reinstalled my system and installed the demo version. It worked fine for 2 days, then out of nowhere, whenever I tried to download files from remote server, it appeared to connect, display the files available, and after that - nothing. I checked the resource monitor, and the network connection seemed to go dead.

Most of the active processes changed to poll_scheduled_timeout, with a few do_waits in the mix as well.

The only thing I'm really noticing is that I'm using the laptop's wireless connection, rather than a wired connection.

If you do find an answer to your problem, I'd be very interested in hearing of it - Zend studio really suits me, and I was (up to this point) considering buying it.

Sorry I couldn't have better news for you!

- WoolyG

---

### Post by woolyg on 2011-04-17
Hey paul_gc,

I went ahead and deleted all of the projects held in the application, and recreated them, and then re-downloaded the files from the project server, and it appeared to begin working again - something to try perhaps?

WoolyG

---

### Post by Andrew_P on 2011-05-06
I'm seeing a similar problem with SeaMonkey browser, and it seems to be getting progressively worse over the last 5-6 days.  The browser hangs spontaneously, sometimes while viewing certain Web pages, sometimes just idling on a fully-loaded page at sites that have never caused problems before. I just installed an upgrade to SeaMonkey yesterday that was pushed out via Update manager, but it didn't seem to make any difference.  Whenever it happens, the browser window dims and the browser becomes unresponsive, but I can still kill it instantly by right-clicking its button on the Gnome panel.  System Monitor shows it sleeping with futex_wait_queue_me in the Wait Channel column.  I'm also seeing the problem with Firefox 3.6, which I don't use as frequently.  Restarting the system doesn't make any difference.  Flushing the browser cache doesn't make any difference.

This is getting rather frustrating, as I can only use the browser for random times, varying from 5-15 minutes, before it hangs.  (I had to restart it once just to post this comment.) I used to be able to run the browser for hours on end without a hitch as recently as last week.  The worsening of the situation may be related to some patch that Ubuntu pushed out in the last 5-6 days, but which one, I haven't a clue.

I'm currently running Ubuntu 10.04.1 LTS on an AMD Athlon 3 GHz machine, 4GB of RAM.

---

### Post by nick7076 on 2011-06-12
I've just installed google chrome and now have this same issue with chrome.

I am a complete novice so don't even know what the waiting channel list is for!

10.04
kernel 2.6.32-32
gnome 2.30.2

Laptop
2 GB ram
Intel core2 duo 2Ghz

---

