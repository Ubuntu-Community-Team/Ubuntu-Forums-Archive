---
title: "LottaNZB - Files Not Downloading"
date: 2009-08-27
forum: General Help
---

### Post by jonny1 on 2009-08-27
**EDIT: Solved. Login details were incorrect (oops - though I was expecting an authentication error in the log.)**

Hi,

For some reason I am unable to download files using LottaNZB. The progress bar stays at 0% and nothing happens.

[IMG]http://i32.tinypic.com/5ouy4k.png[/IMG]

The log is as follows:

```

19:44:21    LottaNZB    Starting LottaNZB 0.4.1...
19:44:21    LottaNZB    LottaNZB configuration file loaded.
19:44:21    LottaNZB    Starting backend thread...
19:44:21    LottaNZB    The HellaNZB configuration file /home/g/.lottanzb/hellanzb.conf has been loaded successfully.
19:44:21    LottaNZB    Launching GUI...
19:44:22    LottaNZB    Started HellaNZB daemon.
19:44:22    LottaNZB    Connected to the HellaNZB daemon at localhost:8760.
19:44:22    LottaNZB    Set usage mode to 'Stand-alone'.
19:44:22    LottaNZB    Added /tmp/ubuntu 9.04.nzb to the download queue.
19:44:22    HellaNZB    HellaNZB 0.13 (configuration: /home/g/.lottanzb/hellanzb.conf, daemonized, C yenc module)
19:44:22    HellaNZB    Opening 8 connections to Default Server...
19:44:22    HellaNZB    Now monitoring queue...
19:44:22    HellaNZB    Found new NZB : ubuntu 9.04
19:44:27    HellaNZB    Downloading: ubuntu 9.04
19:44:27    HellaNZB    Parsing: ubuntu 9.04.nzb...
19:44:27    HellaNZB    Parsed: 22 files (1991 posts), 751.1MB
19:44:27    HellaNZB    Queued: 751.1MB
19:52:58    LottaNZB    The HellaNZB configuration file /home/g/.lottanzb/hellanzb.conf has been loaded successfully.

```I have tried reinstalling LottaNZB and HellaNZB, but the problem remains. Can anybody help?

Thanks.

---

### Post by Lantash on 2009-08-27
Hi jonny1, this is a known problem. See [https://bugs.edge.launchpad.net/lottanzb/+bug/239491](https://bugs.edge.launchpad.net/lottanzb/+bug/239491) for more information.

The problem is that HellaNZB, the application that does the actual work for LottaNZB, just doesn't say a word if the login details aren't correct. We cannot change HellaNZB and will change the backend to SABnzbd starting with LottaNZB 0.6, which will also fix this particular problem (and a whole bunch of others).

---

### Post by Emanuele_Z on 2009-11-30
Hi, I'm facing the same issue (using 0.5.2 from their website).
Everything seems ok but then nothing happens.
Actually I'm using *British Telecom*... which username/password/server config should I input?
I'm asking because I can't find any official settings config on their website...

Will I have to wait for 0.6.0 to know if I'm inputting the right username/password or is there a better way to find it?

Cheers,

---

