---
title: "Multiple Instances of a Process - kill single instance"
date: 2012-09-19
forum: General Help
---

### Post by tek022 on 2012-09-19
I have a server transcoding multiple audio streams via VLC, each outputting on a different port, starting at 2001.  In the past, I have used 'killall vlc' then restarted the script to start all the streams back up.  I saw somewhere that you can use a combination of ps and grep to find the PID (that may be wrong).  Other than searching for the instance of VLC on my screen, how can I use the terminal to get this done?

---

### Post by Vaphell on 2012-09-19
do these vlc instances differ in *ps ux | grep vlc* output? It is required to pinpoint that one instance programmatically.

*ps ux | grep <keyword>* can be used to find the process(es) info, *kill <pid>* to terminate selected process.
there are also *pgrep* and *pkill* tools. *Pgrep* is like ps+grep combo, returns pid(s) (which can be used to feed *kill* command) while *pkill* works with the same options as *pgrep* but kills matched processes right off the bat.
[http://linux.die.net/man/1/pgrep](http://linux.die.net/man/1/pgrep)

---

### Post by tek022 on 2012-09-20
The ps ux | grep 2095 (for the vlc instance running on port 2095) brings up this, which is exactly what I need!
```

user       5168  3.7  0.3 1142492 53892 ?       Sl   Sep19  28:13 vlc udp://@:**2095** --sout-ts-dts-delay 400 :sout=#transcode{acodec=a52,ab=128,channels=1,samplerate=48000}:std{access=udp{ttl=1},mux=ts,dst=192.168.6.2:199}
```

Then I can just stop PID 5168.  Thanks!

---

