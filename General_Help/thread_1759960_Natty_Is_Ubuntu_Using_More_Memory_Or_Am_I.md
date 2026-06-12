---
title: "Natty: Is Ubuntu Using More Memory Or Am I???"
date: 2011-05-16
forum: General Help
---

### Post by coljohnhannibalsmith on 2011-05-16
Well,

When I first started using Ubuntu (Gutsy Gibon),  I installed Conky shortly afterwards; and was always able to see RAM & SWAP usage.  I almost never used SWAP; and under normal circumstances RAM usage 'never' exceeded 22%. **I have 4GB installed.**  Even under 'extreme' load, RAM usage 'never' exceeded 35%, unless I had a runaway process situation.  In this case, I just killed the process or rebooted; no harm no foul.

Now, with just a couple of apps running, I'm hiiting 66% RAM usage and above; and my system starts running ***realllll slowww*** at about 64% RAM.  It's not unusual for me to hit 80% during a session.  I have swapiness set to about 4; and this still isn't helping...

I suppose it could be the way I'm using the system; since I'm running ***both*** APACHE & TOMCAT; but, I should still see their memory usage reflected in Conky. And, as long as I'm ***not*** hitting SWAP; I don't think I should be experiencing such drastic performance degradation. During a normal session, I might have four Firefox tabs open, VUZE; and I might be watching a movie.  Even this quickly becomes way too much for my system to handle.  [COLOR=Blue]***It never used to be...***[/COLOR]

**I've also noticed that when I close applications, [COLOR=Red]especially Firefox;[/COLOR] that memory isn't released right away...**

Could this be a memory leak:confused: 

If so, I suspect this is a[COLOR=Blue]*** Linux***[/COLOR] kernel issue and 'not' an ***[COLOR=Red]Ubuntu[/COLOR]*** issue per se...


[B]Comments???


[IMG]http://www.suburbandomains.com.au/user_website/images/cms/plumbing_2.jpg[/IMG]




[COLOR=Blue]Thanks Hannibal[/COLOR]
[/B]

---

### Post by coljohnhannibalsmith on 2011-05-17
**[COLOR=Red]bump[/COLOR]**.

---

### Post by stinkeye on 2011-05-17
I've been monitoring memory with conky since karmic and natty for me uses 
the least of the lot.
At the moment I'm running a browser(10 tabs) and 4 conkys for 360mb of 2gig mem.

I've set my swappiness to 10.

As a test ran rhtyhmbox, opera (14 tabs), movie player,shutter,software centre,gpodder, synaptic.
650mb

---

### Post by coljohnhannibalsmith on 2011-05-17
Well,

It's certainly looking like I have some kind of memory issue.  What can I do about it???




Thanks, Hannibal

---

### Post by gangsterkb on 2011-05-17
I have also conky installed and i use now 21% with also 4 GB i have now Chrome running with 9 tabs and LibreOffice. 

Chrome is using by far the most 200MB + or so. The only memory leak i have encountered is the screen saver gltext.

---

### Post by mc4man on 2011-05-17
> **coljohnhannibalsmith said:**
> Well,

It's certainly looking like I have some kind of memory issue.  What can I do about it???

You may want to post how you're determining mem use (if using system monitor keep in mind it's one of the worst  abusers of mem use around

I'd do a fresh boot, wait about 30 sec's or so and then run these 2 commands, this will record where you are at start up and what's running, ect.
```
free -m >> base_mem.log && \
ps -A u >> base_mem.log

```

Then go ahead and do some things, ect. and re-run the commands - then open the log file and see what's doing what, compare the first records with the 2nd set
As far as mem the RSS column matters more than the VSZ column

If you find some suspect process's than switch over to pidstat to ck. them
You shouldn't be using anymore then 300MB (RSS) or so from the fresh boot (2nd row in free -m ) 
I average around 250MB here across several unity machines, Classic logins are a bit less, nouveau considerably less than nvidia-current (170MB on unity @ start up

---

### Post by coljohnhannibalsmith on 2011-05-17
Thanks for the reply,

I'm using conky to display memory usage; and I'm at 40% at startup with no apps running.

I'll run the code you gave and get back to you.  I have some questions about your other suggestions; because I don't know how to do all of those things...




Thanks Hannibal

---

### Post by coljohnhannibalsmith on 2011-05-17
Wow,

This file has lots of entries; and it's not very clear what they mean.  I was able to figure the top part out and it doesn't look good.

**Immediately After Boot:**

                   total       used       free     shared    buffers     cached
Mem:          **3709      2541     1167 **         0        234        919
-/+ buffers/cache:     1386       2322
Swap:         8539            0       8539

**After Opening 4 Firefox Tabs Lauching VUZE & Miro (To Watch a Movie):**

                   total       used       free     shared    buffers     cached
Mem:          **3709      3502      206    **      0        244       1211
-/+ buffers/cache:      2046     1662
Swap:         8539            0      8539

[COLOR=Blue]***This is kind of not looking good.***[/COLOR]

I can recognize most of the processes; but I can't really tell if they're supposed to be  running or not; and how much memory they're supposed to be using.  I have LAMP installed on my unit; and there are **six** entries for this.  There always have been.  This doesn't look right to me; but then again, I'm not really sure:

[B]root      2847  0.0  0.3 283104 13472 ?        Ss   20:08   0:00 /usr/sbin/apache2 -k start
www-data  2895  0.0  0.1 283104  6684 ?        S    20:08   0:00 /usr/sbin/apache2 -k start
www-data  2896  0.0  0.1 283104  6684 ?        S    20:08   0:00 /usr/sbin/apache2 -k start
www-data  2898  0.0  0.1 283104  6684 ?        S    20:08   0:00 /usr/sbin/apache2 -k start
www-data  2900  0.0  0.1 283104  6684 ?        S    20:08   0:00 /usr/sbin/apache2 -k start
www-data  2901  0.0  0.1 283104  6684 ?        S    20:08   0:00 /usr/sbin/apache2 -k start[/B]

It turns out that I had 5 apache processes running; so I killed 4 of them and my apache and tomcat servers still worked; but I didn't notice any reduction in memory.  The servers seemed to run a little faster though.

[COLOR=Blue]***Why is this process starting so many times; and how do I get it to load only once???***[/COLOR]

I'm going to include the contents of the two files here; but they're big; and I really can't grok them:[B]

Immediately After Boot:

[/B]            total       used       free     shared    buffers     cached
Mem:          3709       2541       1167          0        234        919
-/+ buffers/cache:       1386       2322
Swap:         8539          0       8539
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.4  0.0  24144  2272 ?        Ss   20:07   0:00 /sbin/init
root       385  0.1  0.0  17052   640 ?        S    20:07   0:00 upstart-udev-bridge --daemon
root       396  0.0  0.0  21656  1172 ?        S<s  20:07   0:00 udevd --daemon
root       474  0.0  0.0  21532  1052 ?        S<   20:07   0:00 udevd --daemon
root       477  0.0  0.0  21532  1020 ?        S<   20:07   0:00 udevd --daemon
102        599  0.4  0.0  24628  2104 ?        Ss   20:07   0:00 dbus-daemon --system --fork --activation=upstart
avahi      622  0.0  0.0  32128  1688 ?        S    20:07   0:00 avahi-daemon: running [sophie-laptop.local]
avahi      625  0.0  0.0  32008   468 ?        S    20:07   0:00 avahi-daemon: chroot helper
root       627  0.1  0.1  92692  4944 ?        Ssl  20:07   0:00 NetworkManager
root       633  0.0  0.0  64656  2732 ?        S    20:07   0:00 /usr/sbin/modem-manager
root       661  0.2  0.1 129604  4104 ?        Sl   20:07   0:00 /usr/lib/policykit-1/polkitd
root       721  0.0  0.0  28812  2768 ?        S    20:07   0:00 /sbin/wpa_supplicant -u -s
root       821  0.0  0.0  15004   400 ?        S    20:07   0:00 upstart-socket-bridge --daemon
root       833  0.0  0.0      0     0 ?        S    20:07   0:00 [pccardd]
root       967  0.0  0.0   6196   636 tty4     Ss+  20:08   0:00 /sbin/getty -8 38400 tty4
root       974  0.0  0.0   6196   628 tty5     Ss+  20:08   0:00 /sbin/getty -8 38400 tty5
root       995  0.0  0.0   6196   636 tty2     Ss+  20:08   0:00 /sbin/getty -8 38400 tty2
root       996  0.0  0.0   6196   628 tty3     Ss+  20:08   0:00 /sbin/getty -8 38400 tty3
root       998  0.0  0.0   6196   632 tty6     Ss+  20:08   0:00 /sbin/getty -8 38400 tty6
root      1018  0.0  0.0   4284   820 ?        Ss   20:08   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      1021  0.0  0.0  18928  1012 ?        Ss   20:08   0:00 cron
daemon    1022  0.0  0.0  16728   380 ?        Ss   20:08   0:00 atd
root      1024  0.0  0.1 159728  3972 ?        Ssl  20:08   0:00 gdm-binary
proxy     1040  0.0  0.1  24828  5052 ?        Ss   20:08   0:00 /usr/sbin/squid -N -D
mysql     1041  0.7  0.8 174204 33152 ?        Ssl  20:08   0:00 /usr/sbin/mysqld
root      1045  0.0  0.0  15780   656 ?        Ss   20:08   0:00 /usr/sbin/irqbalance
root      1047  0.0  0.0      0     0 ?        S<   20:08   0:00 [kvm-irqfd-clean]
root      1051  0.1  0.1  59768  3884 ?        Sl   20:08   0:00 /usr/sbin/console-kit-daemon --no-daemon
proxy     1072  0.0  0.0   3980   332 ?        Ss   20:08   0:00 (unlinkd)
syslog    1141  0.0  0.0  12576   784 ?        Ss   20:08   0:00 /sbin/syslogd -u syslog
root      1185  0.0  0.0   8408   632 ?        S    20:08   0:00 /bin/dd bs=1 if=/proc/kmsg of=/var/run/klogd/kmsg
klog      1186  0.1  0.1   8328  4736 ?        Ss   20:08   0:00 /sbin/klogd -P /var/run/klogd/kmsg
root      1188  0.0  0.1 174360  4584 ?        Sl   20:08   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root      1191  0.0  0.0      0     0 ?        S    20:08   0:00 [irq/22-b43]
root      1203  0.0  0.0      0     0 ?        S<   20:08   0:00 [hd-audio0]
root      1205  3.0  0.5 136124 22036 tty7     Ss+  20:08   0:03 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-BIcW1y/database -nolisten tcp vt7
root      1282  0.0  0.0  19736  3128 ?        Ss   20:08   0:00 /usr/sbin/argus -w /var/log/argus/argus.log -n /var/run/argus.pid
root      1285  0.0  0.0  12744   168 ?        S    20:08   0:00 /usr/sbin/ax25spyd 2
root      1286  0.0  0.0  75512  3108 ?        Ss   20:08   0:00 /usr/sbin/cupsd -F
root      1334  0.0  0.0  19220  2576 ?        S    20:08   0:00 /usr/sbin/argus -w /var/log/argus/argus.log -n /var/run/argus.pid
root      1335  0.0  0.0  19412  2672 ?        S    20:08   0:00 /usr/sbin/argus -w /var/log/argus/argus.log -n /var/run/argus.pid
root      1613  0.0  0.1 219992  4672 ?        Sl   20:08   0:00 /usr/lib/gdm/gdm-session-worker
root      1619  0.1  0.1  77712  4364 ?        Sl   20:08   0:00 /usr/lib/upower/upowerd
rtkit     1624  0.0  0.0  37628  1284 ?        SNl  20:08   0:00 /usr/lib/rtkit/rtkit-daemon
clamav    1852  0.0  3.2 181004 122564 ?       Ssl  20:08   0:00 /usr/sbin/clamd
clamav    2029  0.0  0.0  51748  1852 ?        Ss   20:08   0:00 /usr/bin/freshclam -d --quiet
clamav    2182  0.0  0.0 125556   892 ?        Ssl  20:08   0:00 /usr/sbin/clamav-milter
root      2223  0.0  0.1  52768  7300 ?        S    20:08   0:00 python /usr/sbin/denyhosts --daemon --purge --config=/etc/denyhosts.conf
root      2240  0.1  0.1  49816  5772 ?        Ssl  20:08   0:00 /usr/sbin/fprobe -ieth0 -fip localhost:555
root      2245  0.1  0.0  45492  3360 ?        Ssl  20:08   0:00 /usr/sbin/fprobe-ulog -Xeth0:100,ppp0:200 localhost:555
gnugk     2255  0.0  0.3 230420 13880 ?        Sl   20:08   0:00 /usr/sbin/gnugk --config /etc/gatekeeper.ini --output /var/log/gnugk/gnugk.log --pid /var/run/gnugk/gnugk.pid
gnunet    2267  1.7  0.1 353184  5000 ?        SNsl 20:08   0:02 /usr/bin/gnunetd -c /etc/gnunetd.conf
root      2327  0.0  0.0   4400   764 ?        S    20:08   0:00 /usr/sbin/hddtemp -d -l 127.0.0.1 -p 7634 -s | /dev/sda
ntop      2352  0.0  0.7 222608 28560 ?        Ssl  20:08   0:00 /usr/sbin/ntop -d -L -u ntop -P /var/lib/ntop --access-log-file /var/log/ntop/access.log -i eth0 -p /etc/ntop/protocol.list -O /var/log/ntop -n 0
proxy     2367  0.0  0.0   4572   348 ?        Ss   20:08   0:00 /usr/bin/polipo -c /etc/polipo/config pidFile=/var/run/polipo/polipo.pid daemonise=true logFile=/var/log/polipo/polipo.log forbiddenFile=/etc/polipo/forbidden
root      2454  0.0  0.0  37364  2272 ?        Ss   20:08   0:00 /usr/lib/postfix/master
rtpproxy  2470  0.0  0.0  27096   524 ?        Ssl  20:08   0:00 /usr/sbin/rtpproxy -s unix:/var/run/rtpproxy/rtpproxy.sock -u rtpproxy rtpproxy -p /var/run/rtpproxy/rtpproxy.pid
snmp      2486  0.0  0.1  47612  4868 ?        S    20:08   0:00 /usr/sbin/snmpd -Lsd -Lf /dev/null -u snmp -g snmp -I -smux -p /var/run/snmpd.pid
snort     2503  0.8  1.4 131936 53848 ?        Ss   20:08   0:01 /usr/sbin/snort -m 027 -D -d -l /var/log/snort -u snort -g snort -c /etc/snort/snort.conf -S HOME_NET=[192.168.0.0/16] -i eth0
root      2524  0.0  0.0  65800  1712 ?        Ss   20:08   0:00 /usr/sbin/winbindd
root      2527  0.0  0.0  65800  1280 ?        S    20:08   0:00 /usr/sbin/winbindd
yacy      2549  6.5  2.8 664528 106424 ?       SNl  20:08   0:07 /usr/bin/java -Xms180m -Xmx180m -server -XX:+UseConcMarkSweepGC -XX:+CMSIncrementalMode -XX:-UseGCOverheadLimit -XX:+UseAdaptiveSizePolicy -Djava.net.preferIPv4Stack=true -Djava.awt.headless=true -Dfile.encoding=UTF-8 -classpath /usr/share/java/yacy.jar:/usr/share/yacy/htroot:/usr/share/java/yacy/J7Zip-modified.jar:/usr/share/java/yacy/activation.jar:/usr/share/java/yacy/apache-mime4j-0.6.jar:/usr/share/java/yacy/apache-solr-solrj-3.1.0.jar:/usr/share/java/yacy/bcmail-jdk15-145.jar:/usr/share/java/yacy/bcprov-jdk15-145.jar:/usr/share/java/yacy/bzip2.jar:/usr/share/java/yacy/commons-codec-1.4.jar:/usr/share/java/yacy/commons-fileupload-1.2.2.jar:/usr/share/java/yacy/commons-io-1.4.jar:/usr/share/java/yacy/commons-jxpath-1.3.jar:/usr/share/java/yacy/commons-logging-1.1.1.jar:/usr/share/java/yacy/fontbox-1.2.1.jar:/usr/share/java/yacy/httpclient-4.1.jar:/usr/share/java/yacy/httpcore-4.1.jar:/usr/share/java/yacy/httpmime-4.1.jar:/usr/share/java/yacy/icu4j-core.jar:/usr/share/java/yacy/jakarta-oro-2.0.8.jar:/usr/share/java/yacy/jcifs-1.3.15.jar:/usr/share/java/yacy/jsch-0.1.42.jar:/usr/share/java/yacy/json-simple-1.1.jar:/usr/share/java/yacy/log4j-1.2.16.jar:/usr/share/java/yacy/metadata-extractor-2.4.0-beta-1.jar:/usr/share/java/yacy/mysql-connector-java-5.1.12-bin.jar:/usr/share/java/yacy/pdfbox-1.2.1.jar:/usr/share/java/yacy/poi-3.6-20091214.jar:/usr/share/java/yacy/poi-scratchpad-3.6-20091214.jar:/usr/share/java/yacy/servlet-api.jar:/usr/share/java/yacy/slf4j-api-1.5.5.jar:/usr/share/java/yacy/slf4j-jdk14-1.5.5.jar:/usr/share/java/yacy/webcat-0.1-swf.jar:/usr/share/java/yacy/xerces.jar:/usr/share/java/yacy/yacycore.jar:/usr/share/java/javatar.jar:/usr/share/java/commons-httpclient.jar:/usr/share/java/commons-fileupload.jar:/usr/share/java/commons-logging.jar:/usr/share/java/commons-codec.jar:/usr/share/java/commons-discovery.jar:/usr/share/java/commons-io.jar:/usr/share/java/pdfbox.jar:/usr/share/java/bcprov.jar:/usr/share/java/bcmail.jar:/usr/share/java/jakarta-poi.jar:/usr/share/java/jakarta-poi-scratchpad.jar:/usr/share/java/oro.jar:/usr/share/java/xerces.jar:/usr/share/java/jsch.jar:/usr/share/java/ant.jar:/usr/share/java/jmimemagic.jar:/usr/share/java/log4j-1.2.jar:/usr/share/java/odfutils.jar:/usr/share/java/jrpm.jar:/usr/share/java/tmextractors.jar:/usr/share/java/servlet-api.jar:/usr/share/java/j7zip.jar net.yacy.yacy
root      2573  0.0  0.0  42748  2052 ?        Ssl  20:08   0:00 /usr/local/bin/zfoned
ser       2581  0.0  0.1  71932  4372 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2584  0.0  0.0  71932   560 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2585  0.0  0.0  71932   364 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2586  0.0  0.0  71932   364 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2587  0.0  0.0  71932   364 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2588  0.0  0.0  71932   364 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2589  0.0  0.0  71932   364 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2590  0.0  0.0  71932   364 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2591  0.0  0.0  71932   364 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2592  0.0  0.0  71932   552 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2593  0.0  0.0  71932   556 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2594  0.0  0.0  71932   556 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2595  0.0  0.0  71932   544 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2596  0.0  0.0  71932   544 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2597  0.0  0.0  71932   544 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2598  0.0  0.0  71932   544 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2599  0.0  0.0  71932   544 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2600  0.0  0.0  71932   544 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2605  0.0  0.0  71932   544 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2606  0.0  0.0  71932   544 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2607  0.0  0.0  71932   536 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
sophie    2618  0.0  0.0 219108  1260 ?        S    20:08   0:00 /usr/lib/gdm/gdm-session-worker
nobody    2639  0.0  0.0  35868  1272 ?        S<s  20:08   0:00 /usr/sbin/gpsd -F /var/run/gpsd.sock -P /var/run/gpsd.pid
mpd       2665  0.0  0.1 235184  5088 ?        Ssl  20:08   0:00 /usr/bin/mpd /etc/mpd.conf
sophie    2677  0.0  0.0 234396  3384 ?        Sl   20:08   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
sophie    2710  0.3  0.2 256404  8448 ?        Ssl  20:08   0:00 gnome-session --session=classic-gnome
freerad   2722  0.0  0.1 126700  4136 ?        Ssl  20:08   0:00 /usr/sbin/freeradius
nobody    2742  0.2  0.0  19248  1336 ?        S    20:08   0:00 /usr/sbin/LCDd -s 1 -f -c /etc/LCDd.conf
sophie    2831  0.0  0.0  12092   284 ?        Ss   20:08   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session --session=classic-gnome
sophie    2834  0.0  0.0  26400   608 ?        S    20:08   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session --session=classic-gnome
sophie    2835  0.5  0.0  26164  2400 ?        Ss   20:08   0:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
sophie    2844  7.0  6.1 367196 235016 ?       S    20:08   0:07 /usr/lib/libgconf2-4/gconfd-2
root      2847  0.0  0.3 283104 13472 ?        Ss   20:08   0:00 /usr/sbin/apache2 -k start
www-data  2895  0.0  0.1 283104  6684 ?        S    20:08   0:00 /usr/sbin/apache2 -k start
www-data  2896  0.0  0.1 283104  6684 ?        S    20:08   0:00 /usr/sbin/apache2 -k start
www-data  2898  0.0  0.1 283104  6684 ?        S    20:08   0:00 /usr/sbin/apache2 -k start
www-data  2900  0.0  0.1 283104  6684 ?        S    20:08   0:00 /usr/sbin/apache2 -k start
www-data  2901  0.0  0.1 283104  6684 ?        S    20:08   0:00 /usr/sbin/apache2 -k start
129       2922  0.0  0.5 137188 21444 ?        Ss   20:08   0:00 /usr/sbin/smokeping [FPing]
tomcat6   2956 21.7  4.1 722196 155964 ?       Sl   20:08   0:23 /usr/lib/jvm/java-6-openjdk/bin/java -Djava.util.logging.config.file=/var/lib/tomcat6/conf/logging.properties -Djava.awt.headless=true -Xmx128m -XX:+UseConcMarkSweepGC -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.endorsed.dirs=/usr/share/tomcat6/endorsed -classpath /usr/share/tomcat6/bin/bootstrap.jar -Dcatalina.base=/var/lib/tomcat6 -Dcatalina.home=/usr/share/tomcat6 -Djava.io.tmpdir=/tmp/tomcat6-tmp org.apache.catalina.startup.Bootstrap start
root      3004  0.0  0.0      0     0 ?        S    20:08   0:00 [flush-ecryptfs-]
timidity  3064  0.0  0.1 111712  7364 ?        S    20:08   0:00 /usr/bin/timidity -Os -iAD
root      3068  0.0  0.0   6196   636 tty1     Ss+  20:08   0:00 /sbin/getty -8 38400 tty1
sophie    3103  0.4  0.3 473140 13748 ?        Ssl  20:08   0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
sophie    3110  0.0  0.0 132520  2436 ?        S    20:08   0:00 /usr/lib/gvfs/gvfsd
sophie    3115  0.0  0.0  81008  2660 ?        Ssl  20:08   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/sophie/.gvfs
sophie    3122  1.1  0.5 339656 21064 ?        Sl   20:08   0:01 /usr/bin/compiz
sophie    3125  0.3  0.1 324392  6176 ?        S<sl 20:08   0:00 /usr/bin/pulseaudio --start --log-target=syslog
sophie    3138  0.0  0.1 181372  3900 ?        Sl   20:08   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
sophie    3142  0.0  0.0  24680  1120 ?        S    20:08   0:00 syndaemon -i 0.5 -k -R
sophie    3144  0.0  0.0 148324  3684 ?        S    20:08   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      3146  0.1  0.1  62092  3916 ?        Sl   20:08   0:00 /usr/lib/udisks/udisks-daemon
root      3147  0.0  0.0  45168   800 ?        S    20:08   0:00 udisks-daemon: polling /dev/sr1 /dev/sr0
sophie    3150  0.0  0.0 153916  2608 ?        Sl   20:08   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
sophie    3153  0.0  0.0 140120  2588 ?        S    20:08   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
sophie    3154  8.6  4.3 907216 166160 ?       Sl   20:08   0:08 nautilus
sophie    3155  0.8  0.7 434912 29984 ?        Sl   20:08   0:00 /usr/bin/python /usr/bin/blueman-applet
sophie    3156  0.1  0.3 360088 11664 ?        Sl   20:08   0:00 /usr/lib/evolution/2.32/evolution-alarm-notify
sophie    3158  0.0  0.1 245060  6900 ?        Sl   20:08   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
sophie    3160  0.3  0.1 158260  6964 ?        Sl   20:08   0:00 zeitgeist-datahub
sophie    3162  0.0  0.2 276412  8636 ?        Sl   20:08   0:00 bluetooth-applet
sophie    3164  0.4  0.4 490268 16308 ?        Sl   20:08   0:00 nm-applet --sm-disable
sophie    3165  0.0  0.1  96432  3836 ?        Sl   20:08   0:00 /usr/lib/deja-dup/deja-dup-monitor
sophie    3169  2.2  0.8 482864 32468 ?        Sl   20:08   0:02 /usr/bin/python /usr/bin/caffeine
sophie    3171  2.5  0.5 466004 21932 ?        Sl   20:08   0:02 gnome-panel
sophie    3174  0.5  0.4 262148 18912 ?        Sl   20:08   0:00 /usr/bin/python /usr/bin/zeitgeist-daemon
sophie    3175  0.1  0.2 349336  9296 ?        Sl   20:08   0:00 gnome-power-manager
sophie    3193  0.0  0.0  87412   584 ?        S    20:08   0:00 /bin/cat
sophie    3195  0.0  0.0      0     0 ?        Z    20:08   0:00 [zeitgeist-datah] <defunct>
sophie    3204  0.3  0.3 332652 15132 ?        Sl   20:08   0:00 /usr/lib/notify-osd/notify-osd
sophie    3206  0.1  0.2 407032  9156 ?        Sl   20:08   0:00 /usr/lib/evolution/e-calendar-factory
sophie    3221  0.0  0.0 137292  3236 ?        S    20:08   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.10 /org/gtk/gvfs/exec_spaw/0
sophie    3233  0.0  0.0 130976  2152 ?        S    20:08   0:00 /usr/bin/obex-data-server --no-daemon 
sophie    3245  0.0  0.2 336928  9408 ?        Sl   20:08   0:00 /usr/lib/evolution/e-addressbook-factory
sophie    3254  0.0  0.1 258796  7312 ?        S    20:08   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
sophie    3255  0.0  0.0 258404  3092 ?        Ss   20:08   0:00 gnome-screensaver
root      3259  0.0  0.0   7084  1504 ?        S    20:08   0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp/dhclient-df1bbd02-693f-4f28-8dfb-30f52b6d1090-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
sophie    3269  0.0  0.0   4220   580 ?        Ss   20:08   0:00 /bin/sh -c /usr/bin/compiz-decorator
sophie    3270  0.3  0.3 263304 12288 ?        Sl   20:08   0:00 /usr/bin/unity-window-decorator
sophie    3308  0.0  0.1 237836  4140 ?        Ssl  20:08   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=23
sophie    3346  0.3  0.3 342828 15044 ?        Sl   20:08   0:00 /usr/lib/gnome-panel/wnck-applet
postfix   3356  0.0  0.0  39428  2260 ?        S    20:08   0:00 pickup -l -t fifo -u -c
postfix   3357  0.0  0.0  39480  2164 ?        S    20:08   0:00 qmgr -l -t fifo -u
sophie    3372  0.2  0.2 316812  9716 ?        Sl   20:08   0:00 /usr/lib/gnome-applets/multiload-applet-2
sophie    3374  0.1  0.3 321508 11692 ?        Sl   20:08   0:00 /usr/lib/gnome-applets/drivemount_applet2
sophie    3376  0.3  0.3 408248 14664 ?        Sl   20:08   0:00 /usr/lib/indicator-applet/indicator-applet-session
sophie    3378  0.6  0.7 621832 28084 ?        Sl   20:08   0:00 /usr/lib/gnome-panel/clock-applet
sophie    3380  0.4  0.3 430684 14496 ?        Sl   20:08   0:00 /usr/lib/indicator-applet/indicator-applet
sophie    3382  0.1  0.2 363416  9624 ?        Sl   20:08   0:00 /usr/lib/gnome-panel/notification-area-applet
sophie    3401  0.0  0.0 132784  2752 ?        S    20:08   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.10 /org/gtk/gvfs/exec_spaw/1
sophie    3424  0.0  0.0 127164  3064 ?        S    20:09   0:00 /usr/lib/gvfs/gvfsd-metadata
sophie    3429  0.5  0.6 315712 23164 ?        S    20:09   0:00 /usr/bin/python /usr/share/system-config-printer/applet.py
sophie    3444  6.8  1.2 381264 47388 ?        Sl   20:09   0:03 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
sophie    3466  0.1  0.1 407948  6336 ?        Sl   20:09   0:00 /usr/lib/indicator-sound/indicator-sound-service
sophie    3469  0.1  0.1 256484  5704 ?        Sl   20:09   0:00 /usr/lib/indicator-me/indicator-me-service
sophie    3470  0.1  0.1 207376  4856 ?        Sl   20:09   0:00 /usr/lib/indicator-application/indicator-application-service
sophie    3471  0.1  0.1 381984  5976 ?        Sl   20:09   0:00 /usr/lib/indicator-session/indicator-session-service
sophie    3473  0.1  0.1 311772  5060 ?        Sl   20:09   0:00 /usr/lib/indicator-messages/indicator-messages-service
sophie    3516  1.0  0.3 410244 14704 ?        Sl   20:09   0:00 update-notifier
sophie    3524  8.2  0.8 469416 31508 ?        Sl   20:09   0:02 gedit /home/sophie/Desktop/htop
sophie    3526  1.9  0.2 256484 10396 ?        S    20:09   0:00 /usr/lib/bamf/bamfdaemon
sophie    3576  0.0  0.0   4220   584 ?        Ss   20:09   0:00 /bin/sh -c gnome-terminal
sophie    3577  8.3  0.4 418776 16824 ?        Sl   20:09   0:00 gnome-terminal
sophie    3580  0.0  0.0  14612   808 ?        S    20:09   0:00 gnome-pty-helper
sophie    3581 10.3  0.1 105260  6116 pts/0    Ss   20:09   0:01 bash
postfix   3767  0.0  0.0  39532  2364 ?        S    20:10   0:00 cleanup -z -t unix -u -c
postfix   3768  0.0  0.0  39440  2156 ?        S    20:10   0:00 trivial-rewrite -n rewrite -t unix -u -c
postfix   3769  0.1  0.0  39672  2872 ?        S    20:10   0:00 local -t unix
sophie    3771  0.0  0.0  98496  1356 pts/0    R+   20:10   0:00 ps -A u

**After Launching 3 Applications:**

           total       used       free     shared    buffers     cached
Mem:          3709       3502        206          0        244       1211
-/+ buffers/cache:       2046       1662
Swap:         8539          0       8539
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  24144  2272 ?        Ss   20:07   0:00 /sbin/init
root       385  0.0  0.0  17052   640 ?        S    20:07   0:00 upstart-udev-bridge --daemon
root       396  0.0  0.0  21656  1172 ?        S<s  20:07   0:00 udevd --daemon
root       474  0.0  0.0  21532  1052 ?        S<   20:07   0:00 udevd --daemon
root       477  0.0  0.0  21532  1020 ?        S<   20:07   0:00 udevd --daemon
102        599  0.0  0.0  24628  2104 ?        Ss   20:07   0:00 dbus-daemon --system --fork --activation=upstart
avahi      622  0.0  0.0  32128  1688 ?        S    20:07   0:00 avahi-daemon: running [sophie-laptop.local]
avahi      625  0.0  0.0  32008   468 ?        S    20:07   0:00 avahi-daemon: chroot helper
root       627  0.0  0.1  92692  4944 ?        Ssl  20:07   0:00 NetworkManager
root       633  0.0  0.0  64656  2732 ?        S    20:07   0:00 /usr/sbin/modem-manager
root       661  0.0  0.1 129604  4104 ?        Sl   20:07   0:00 /usr/lib/policykit-1/polkitd
root       721  0.0  0.0  28812  2768 ?        S    20:07   0:00 /sbin/wpa_supplicant -u -s
root       821  0.0  0.0  15004   400 ?        S    20:07   0:00 upstart-socket-bridge --daemon
root       833  0.0  0.0      0     0 ?        S    20:07   0:00 [pccardd]
root       967  0.0  0.0   6196   636 tty4     Ss+  20:08   0:00 /sbin/getty -8 38400 tty4
root       974  0.0  0.0   6196   628 tty5     Ss+  20:08   0:00 /sbin/getty -8 38400 tty5
root       995  0.0  0.0   6196   636 tty2     Ss+  20:08   0:00 /sbin/getty -8 38400 tty2
root       996  0.0  0.0   6196   628 tty3     Ss+  20:08   0:00 /sbin/getty -8 38400 tty3
root       998  0.0  0.0   6196   632 tty6     Ss+  20:08   0:00 /sbin/getty -8 38400 tty6
root      1018  0.0  0.0   4284   820 ?        Ss   20:08   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      1021  0.0  0.0  18928  1032 ?        Ss   20:08   0:00 cron
daemon    1022  0.0  0.0  16728   380 ?        Ss   20:08   0:00 atd
root      1024  0.0  0.1 159728  3972 ?        Ssl  20:08   0:00 gdm-binary
proxy     1040  0.0  0.1  24828  5052 ?        Ss   20:08   0:00 /usr/sbin/squid -N -D
mysql     1041  0.2  0.9 175856 34732 ?        Ssl  20:08   0:02 /usr/sbin/mysqld
root      1045  0.0  0.0  15780   656 ?        Ss   20:08   0:00 /usr/sbin/irqbalance
root      1047  0.0  0.0      0     0 ?        S<   20:08   0:00 [kvm-irqfd-clean]
root      1051  0.0  0.1  59768  3884 ?        Sl   20:08   0:00 /usr/sbin/console-kit-daemon --no-daemon
proxy     1072  0.0  0.0   3980   332 ?        Ss   20:08   0:00 (unlinkd)
syslog    1141  0.0  0.0  12576   784 ?        Ss   20:08   0:00 /sbin/syslogd -u syslog
root      1185  0.0  0.0   8408   632 ?        S    20:08   0:00 /bin/dd bs=1 if=/proc/kmsg of=/var/run/klogd/kmsg
klog      1186  0.0  0.1   8328  4736 ?        Ss   20:08   0:00 /sbin/klogd -P /var/run/klogd/kmsg
root      1188  0.0  0.1 174360  4584 ?        Sl   20:08   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root      1191  0.0  0.0      0     0 ?        S    20:08   0:00 [irq/22-b43]
root      1203  0.0  0.0      0     0 ?        S<   20:08   0:00 [hd-audio0]
root      1205  7.9  1.3 167036 50368 tty7     Ss+  20:08   1:03 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-BIcW1y/database -nolisten tcp vt7
root      1282  0.1  0.1  20528  4336 ?        Rs   20:08   0:00 /usr/sbin/argus -w /var/log/argus/argus.log -n /var/run/argus.pid
root      1285  0.1  0.0  12744   168 ?        R    20:08   0:00 /usr/sbin/ax25spyd 2
root      1286  0.0  0.0  75512  3108 ?        Ss   20:08   0:00 /usr/sbin/cupsd -F
root      1334  0.0  0.0  19220  2576 ?        S    20:08   0:00 /usr/sbin/argus -w /var/log/argus/argus.log -n /var/run/argus.pid
root      1335  0.0  0.0  19412  2672 ?        S    20:08   0:00 /usr/sbin/argus -w /var/log/argus/argus.log -n /var/run/argus.pid
root      1613  0.0  0.1 219992  4672 ?        Sl   20:08   0:00 /usr/lib/gdm/gdm-session-worker
root      1619  0.0  0.1  77712  4368 ?        Sl   20:08   0:00 /usr/lib/upower/upowerd
rtkit     1624  0.0  0.0  37628  1284 ?        SNl  20:08   0:00 /usr/lib/rtkit/rtkit-daemon
clamav    1852  0.0  3.2 181004 122564 ?       Ssl  20:08   0:00 /usr/sbin/clamd
clamav    2029  0.0  0.0  51748  1852 ?        Ss   20:08   0:00 /usr/bin/freshclam -d --quiet
clamav    2182  0.0  0.0 125556   892 ?        Ssl  20:08   0:00 /usr/sbin/clamav-milter
root      2223  0.0  0.1  52768  7300 ?        S    20:08   0:00 python /usr/sbin/denyhosts --daemon --purge --config=/etc/denyhosts.conf
root      2240  0.3  0.1  49816  6296 ?        Ssl  20:08   0:02 /usr/sbin/fprobe -ieth0 -fip localhost:555
root      2245  0.1  0.0  45492  3360 ?        Ssl  20:08   0:01 /usr/sbin/fprobe-ulog -Xeth0:100,ppp0:200 localhost:555
gnugk     2255  0.0  0.3 295956 13880 ?        Sl   20:08   0:00 /usr/sbin/gnugk --config /etc/gatekeeper.ini --output /var/log/gnugk/gnugk.log --pid /var/run/gnugk/gnugk.pid
gnunet    2267  2.2  0.2 360280  8652 ?        SNsl 20:08   0:17 /usr/bin/gnunetd -c /etc/gnunetd.conf
root      2327  0.0  0.0   4400   764 ?        S    20:08   0:00 /usr/sbin/hddtemp -d -l 127.0.0.1 -p 7634 -s | /dev/sda
ntop      2352  0.2  1.0 295272 40176 ?        Ssl  20:08   0:01 /usr/sbin/ntop -d -L -u ntop -P /var/lib/ntop --access-log-file /var/log/ntop/access.log -i eth0 -p /etc/ntop/protocol.list -O /var/log/ntop -n 0
proxy     2367  0.0  0.0   4572   348 ?        Ss   20:08   0:00 /usr/bin/polipo -c /etc/polipo/config pidFile=/var/run/polipo/polipo.pid daemonise=true logFile=/var/log/polipo/polipo.log forbiddenFile=/etc/polipo/forbidden
root      2454  0.0  0.0  37364  2272 ?        Ss   20:08   0:00 /usr/lib/postfix/master
rtpproxy  2470  0.0  0.0  27096   524 ?        Ssl  20:08   0:00 /usr/sbin/rtpproxy -s unix:/var/run/rtpproxy/rtpproxy.sock -u rtpproxy rtpproxy -p /var/run/rtpproxy/rtpproxy.pid
snmp      2486  0.0  0.1  47612  4872 ?        S    20:08   0:00 /usr/sbin/snmpd -Lsd -Lf /dev/null -u snmp -g snmp -I -smux -p /var/run/snmpd.pid
snort     2503  0.3  1.4 132728 54828 ?        Ss   20:08   0:02 /usr/sbin/snort -m 027 -D -d -l /var/log/snort -u snort -g snort -c /etc/snort/snort.conf -S HOME_NET=[192.168.0.0/16] -i eth0
root      2524  0.0  0.0  65800  1712 ?        Ss   20:08   0:00 /usr/sbin/winbindd
root      2527  0.0  0.0  65800  1280 ?        S    20:08   0:00 /usr/sbin/winbindd
yacy      2549  1.4  4.1 686864 156084 ?       SNl  20:08   0:11 /usr/bin/java -Xms180m -Xmx180m -server -XX:+UseConcMarkSweepGC -XX:+CMSIncrementalMode -XX:-UseGCOverheadLimit -XX:+UseAdaptiveSizePolicy -Djava.net.preferIPv4Stack=true -Djava.awt.headless=true -Dfile.encoding=UTF-8 -classpath /usr/share/java/yacy.jar:/usr/share/yacy/htroot:/usr/share/java/yacy/J7Zip-modified.jar:/usr/share/java/yacy/activation.jar:/usr/share/java/yacy/apache-mime4j-0.6.jar:/usr/share/java/yacy/apache-solr-solrj-3.1.0.jar:/usr/share/java/yacy/bcmail-jdk15-145.jar:/usr/share/java/yacy/bcprov-jdk15-145.jar:/usr/share/java/yacy/bzip2.jar:/usr/share/java/yacy/commons-codec-1.4.jar:/usr/share/java/yacy/commons-fileupload-1.2.2.jar:/usr/share/java/yacy/commons-io-1.4.jar:/usr/share/java/yacy/commons-jxpath-1.3.jar:/usr/share/java/yacy/commons-logging-1.1.1.jar:/usr/share/java/yacy/fontbox-1.2.1.jar:/usr/share/java/yacy/httpclient-4.1.jar:/usr/share/java/yacy/httpcore-4.1.jar:/usr/share/java/yacy/httpmime-4.1.jar:/usr/share/java/yacy/icu4j-core.jar:/usr/share/java/yacy/jakarta-oro-2.0.8.jar:/usr/share/java/yacy/jcifs-1.3.15.jar:/usr/share/java/yacy/jsch-0.1.42.jar:/usr/share/java/yacy/json-simple-1.1.jar:/usr/share/java/yacy/log4j-1.2.16.jar:/usr/share/java/yacy/metadata-extractor-2.4.0-beta-1.jar:/usr/share/java/yacy/mysql-connector-java-5.1.12-bin.jar:/usr/share/java/yacy/pdfbox-1.2.1.jar:/usr/share/java/yacy/poi-3.6-20091214.jar:/usr/share/java/yacy/poi-scratchpad-3.6-20091214.jar:/usr/share/java/yacy/servlet-api.jar:/usr/share/java/yacy/slf4j-api-1.5.5.jar:/usr/share/java/yacy/slf4j-jdk14-1.5.5.jar:/usr/share/java/yacy/webcat-0.1-swf.jar:/usr/share/java/yacy/xerces.jar:/usr/share/java/yacy/yacycore.jar:/usr/share/java/javatar.jar:/usr/share/java/commons-httpclient.jar:/usr/share/java/commons-fileupload.jar:/usr/share/java/commons-logging.jar:/usr/share/java/commons-codec.jar:/usr/share/java/commons-discovery.jar:/usr/share/java/commons-io.jar:/usr/share/java/pdfbox.jar:/usr/share/java/bcprov.jar:/usr/share/java/bcmail.jar:/usr/share/java/jakarta-poi.jar:/usr/share/java/jakarta-poi-scratchpad.jar:/usr/share/java/oro.jar:/usr/share/java/xerces.jar:/usr/share/java/jsch.jar:/usr/share/java/ant.jar:/usr/share/java/jmimemagic.jar:/usr/share/java/log4j-1.2.jar:/usr/share/java/odfutils.jar:/usr/share/java/jrpm.jar:/usr/share/java/tmextractors.jar:/usr/share/java/servlet-api.jar:/usr/share/java/j7zip.jar net.yacy.yacy
root      2573  0.5  0.0  42748  2052 ?        Ssl  20:08   0:04 /usr/local/bin/zfoned
ser       2581  0.0  0.1  71932  4372 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2584  0.0  0.0  71932   560 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2585  0.0  0.0  71932   364 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2586  0.0  0.0  71932   364 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2587  0.0  0.0  71932   364 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2588  0.0  0.0  71932   364 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2589  0.0  0.0  71932   364 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2590  0.0  0.0  71932   364 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2591  0.0  0.0  71932   364 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2592  0.0  0.0  71932   552 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2593  0.0  0.0  71932   556 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2594  0.0  0.0  71932   556 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2595  0.0  0.0  71932   544 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2596  0.0  0.0  71932   544 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2597  0.0  0.0  71932   544 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2598  0.0  0.0  71932   544 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2599  0.0  0.0  71932   544 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2600  0.0  0.0  71932   544 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2605  0.0  0.0  71932   544 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2606  0.0  0.0  71932   544 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
ser       2607  0.0  0.0  71932   536 ?        S    20:08   0:00 /usr/sbin/ser -P /var/run/ser/ser.pid -u ser -g ser
nobody    2639  0.0  0.0  35868  1272 ?        S<s  20:08   0:00 /usr/sbin/gpsd -F /var/run/gpsd.sock -P /var/run/gpsd.pid
mpd       2665  0.0  0.1 235184  5088 ?        Ssl  20:08   0:00 /usr/bin/mpd /etc/mpd.conf
sophie    2677  0.0  0.0 234396  3384 ?        Sl   20:08   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
sophie    2710  0.0  0.2 256404  8448 ?        Ssl  20:08   0:00 gnome-session --session=classic-gnome
freerad   2722  0.0  0.1 126700  4136 ?        Ssl  20:08   0:00 /usr/sbin/freeradius
nobody    2742  0.3  0.0  19248  1336 ?        S    20:08   0:02 /usr/sbin/LCDd -s 1 -f -c /etc/LCDd.conf
sophie    2831  0.0  0.0  12092   284 ?        Ss   20:08   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session --session=classic-gnome
sophie    2834  0.0  0.0  26400   608 ?        S    20:08   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session --session=classic-gnome
sophie    2835  0.1  0.0  26292  2536 ?        Ss   20:08   0:01 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
sophie    2844  1.0  6.1 367200 235024 ?       S    20:08   0:08 /usr/lib/libgconf2-4/gconfd-2
root      2847  0.0  0.3 283104 13524 ?        Ss   20:08   0:00 /usr/sbin/apache2 -k start
www-data  2895  0.0  0.4 292456 18972 ?        S    20:08   0:00 /usr/sbin/apache2 -k start
www-data  2896  0.1  0.8 305348 32416 ?        S    20:08   0:01 /usr/sbin/apache2 -k start
www-data  2898  0.0  0.2 283456  7676 ?        S    20:08   0:00 /usr/sbin/apache2 -k start
www-data  2900  0.0  0.2 283456  7676 ?        S    20:08   0:00 /usr/sbin/apache2 -k start
www-data  2901  0.0  0.2 283456  7676 ?        S    20:08   0:00 /usr/sbin/apache2 -k start
129       2922  0.0  0.5 137188 22248 ?        Ss   20:08   0:00 /usr/sbin/smokeping [FPing]
tomcat6   2956  6.1  4.8 754540 185796 ?       Sl   20:08   0:47 /usr/lib/jvm/java-6-openjdk/bin/java -Djava.util.logging.config.file=/var/lib/tomcat6/conf/logging.properties -Djava.awt.headless=true -Xmx128m -XX:+UseConcMarkSweepGC -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.endorsed.dirs=/usr/share/tomcat6/endorsed -classpath /usr/share/tomcat6/bin/bootstrap.jar -Dcatalina.base=/var/lib/tomcat6 -Dcatalina.home=/usr/share/tomcat6 -Djava.io.tmpdir=/tmp/tomcat6-tmp org.apache.catalina.startup.Bootstrap start
root      3004  0.0  0.0      0     0 ?        S    20:08   0:00 [flush-ecryptfs-]
timidity  3064  0.0  0.1 111712  7364 ?        S    20:08   0:00 /usr/bin/timidity -Os -iAD
root      3068  0.0  0.0   6196   636 tty1     Ss+  20:08   0:00 /sbin/getty -8 38400 tty1
sophie    3103  0.5  0.3 473928 14596 ?        Ssl  20:08   0:04 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
sophie    3110  0.0  0.0 132520  2436 ?        S    20:08   0:00 /usr/lib/gvfs/gvfsd
sophie    3115  0.0  0.0  81008  2660 ?        Ssl  20:08   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/sophie/.gvfs
sophie    3122  2.2  0.5 340120 21696 ?        Sl   20:08   0:16 /usr/bin/compiz
sophie    3125  0.3  0.1 455468  7464 ?        S<sl 20:08   0:02 /usr/bin/pulseaudio --start --log-target=syslog
sophie    3138  0.0  0.1 181372  3900 ?        Sl   20:08   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
sophie    3142  0.0  0.0  24680  1120 ?        S    20:08   0:00 syndaemon -i 0.5 -k -R
sophie    3144  0.0  0.0 148324  3684 ?        S    20:08   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      3146  0.0  0.1  62092  3916 ?        Sl   20:08   0:00 /usr/lib/udisks/udisks-daemon
root      3147  0.0  0.0  45168   800 ?        S    20:08   0:00 udisks-daemon: polling /dev/sr1 /dev/sr0
sophie    3150  0.0  0.0 153916  2608 ?        Sl   20:08   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
sophie    3153  0.0  0.0 140120  2588 ?        S    20:08   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
sophie    3154  4.0  4.9 925640 189504 ?       Rl   20:08   0:30 nautilus
sophie    3155  0.1  0.7 434912 29984 ?        Sl   20:08   0:00 /usr/bin/python /usr/bin/blueman-applet
sophie    3156  0.0  0.3 360088 11664 ?        Sl   20:08   0:00 /usr/lib/evolution/2.32/evolution-alarm-notify
sophie    3158  0.0  0.1 245060  6900 ?        Sl   20:08   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
sophie    3160  0.1  0.1 158260  6964 ?        Sl   20:08   0:01 zeitgeist-datahub
sophie    3162  0.0  0.2 276412  8636 ?        Sl   20:08   0:00 bluetooth-applet
sophie    3164  0.0  0.4 490268 16308 ?        Sl   20:08   0:00 nm-applet --sm-disable
sophie    3165  0.0  0.1 161968  3960 ?        Sl   20:08   0:00 /usr/lib/deja-dup/deja-dup-monitor
sophie    3169  2.0  0.8 482864 32588 ?        Sl   20:08   0:15 /usr/bin/python /usr/bin/caffeine
sophie    3171  0.6  0.5 468328 22492 ?        Sl   20:08   0:04 gnome-panel
sophie    3174  0.1  0.5 262148 19008 ?        Sl   20:08   0:00 /usr/bin/python /usr/bin/zeitgeist-daemon
sophie    3175  0.0  0.2 349336  9296 ?        Sl   20:08   0:00 gnome-power-manager
sophie    3193  0.0  0.0  87412   584 ?        S    20:08   0:00 /bin/cat
sophie    3195  0.0  0.0      0     0 ?        Z    20:08   0:00 [zeitgeist-datah] <defunct>
sophie    3204  0.0  0.3 332652 15132 ?        Sl   20:08   0:00 /usr/lib/notify-osd/notify-osd
sophie    3206  0.0  0.2 407032  9156 ?        Sl   20:08   0:00 /usr/lib/evolution/e-calendar-factory
sophie    3221  0.0  0.0 137292  3236 ?        S    20:08   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.10 /org/gtk/gvfs/exec_spaw/0
sophie    3233  0.0  0.0 130976  2152 ?        S    20:08   0:00 /usr/bin/obex-data-server --no-daemon 
sophie    3245  0.0  0.2 336928  9408 ?        Sl   20:08   0:00 /usr/lib/evolution/e-addressbook-factory
sophie    3254  0.0  0.1 258796  7312 ?        S    20:08   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
sophie    3255  0.0  0.0 258404  3296 ?        Ss   20:08   0:00 gnome-screensaver
root      3259  0.0  0.0   7084  1504 ?        S    20:08   0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp/dhclient-df1bbd02-693f-4f28-8dfb-30f52b6d1090-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
sophie    3269  0.0  0.0   4220   580 ?        Ss   20:08   0:00 /bin/sh -c /usr/bin/compiz-decorator
sophie    3270  0.2  0.3 263456 12552 ?        Sl   20:08   0:01 /usr/bin/unity-window-decorator
sophie    3308  0.0  0.1 237836  4140 ?        Ssl  20:08   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=23
sophie    3346  0.3  0.4 342992 15844 ?        Sl   20:08   0:02 /usr/lib/gnome-panel/wnck-applet
postfix   3356  0.0  0.0  39428  2260 ?        S    20:08   0:00 pickup -l -t fifo -u -c
postfix   3357  0.0  0.0  39588  2376 ?        S    20:08   0:00 qmgr -l -t fifo -u
sophie    3372  0.1  0.2 316812  9716 ?        Sl   20:08   0:01 /usr/lib/gnome-applets/multiload-applet-2
sophie    3374  0.0  0.3 321508 11692 ?        Sl   20:08   0:00 /usr/lib/gnome-applets/drivemount_applet2
sophie    3376  0.0  0.3 408248 14752 ?        Sl   20:08   0:00 /usr/lib/indicator-applet/indicator-applet-session
sophie    3378  0.1  0.7 621832 28148 ?        Sl   20:08   0:00 /usr/lib/gnome-panel/clock-applet
sophie    3380  0.0  0.3 430684 14496 ?        Sl   20:08   0:00 /usr/lib/indicator-applet/indicator-applet
sophie    3382  0.0  0.2 363416  9672 ?        Sl   20:08   0:00 /usr/lib/gnome-panel/notification-area-applet
sophie    3401  0.0  0.0 132784  2752 ?        S    20:08   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.10 /org/gtk/gvfs/exec_spaw/1
sophie    3424  0.0  0.0 127188  3108 ?        S    20:09   0:00 /usr/lib/gvfs/gvfsd-metadata
sophie    3429  0.0  0.6 315712 23164 ?        S    20:09   0:00 /usr/bin/python /usr/share/system-config-printer/applet.py
sophie    3444  0.7  1.2 381264 47388 ?        Sl   20:09   0:05 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
sophie    3466  0.0  0.1 407948  6336 ?        Sl   20:09   0:00 /usr/lib/indicator-sound/indicator-sound-service
sophie    3469  0.0  0.1 256484  5704 ?        Sl   20:09   0:00 /usr/lib/indicator-me/indicator-me-service
sophie    3470  0.0  0.1 207376  4856 ?        Sl   20:09   0:00 /usr/lib/indicator-application/indicator-application-service
sophie    3471  0.0  0.1 381984  5976 ?        Sl   20:09   0:00 /usr/lib/indicator-session/indicator-session-service
sophie    3473  0.0  0.1 311772  5060 ?        Sl   20:09   0:00 /usr/lib/indicator-messages/indicator-messages-service
sophie    3516  0.0  0.3 410244 14704 ?        Sl   20:09   0:00 update-notifier
sophie    3526  0.1  0.3 310980 11724 ?        S    20:09   0:00 /usr/lib/bamf/bamfdaemon
root      3865  0.0  0.0      0     0 ?        S    20:13   0:00 [kworker/0:0]
root      3866  0.0  0.0      0     0 ?        S    20:13   0:00 [kworker/1:0]
sophie    3994  1.3  1.0 484756 39260 ?        Sl   20:16   0:03 gedit /home/sophie/base_mem.log
sophie    4010 12.5  3.0 881704 115848 ?       Sl   20:17   0:32 /usr/lib/firefox-4.0.1/firefox-bin
www-data  4099  0.0  0.2 283456  7676 ?        S    20:17   0:00 /usr/sbin/apache2 -k start
root      4105  0.1  0.0      0     0 ?        S    20:18   0:00 [kworker/0:3]
root      4108  0.0  0.0      0     0 ?        S    20:18   0:00 [kworker/1:3]
www-data  4109  0.0  0.2 283456  7676 ?        S    20:18   0:00 /usr/sbin/apache2 -k start
www-data  4121  0.0  0.2 283600  7680 ?        S    20:18   0:00 /usr/sbin/apache2 -k start
www-data  4122  0.0  0.2 283600  7680 ?        S    20:18   0:00 /usr/sbin/apache2 -k start
www-data  4123  0.0  0.2 283456  7680 ?        S    20:18   0:00 /usr/sbin/apache2 -k start
root      4126  0.0  0.0      0     0 ?        S    20:18   0:00 [kworker/u:0]
sophie    4133  2.9  0.1 307792  5720 ?        Sl   20:18   0:05 /usr/bin/conky
sophie    4150 40.2  7.0 1874732 269304 ?      Sl   20:18   1:04 /usr/lib/jvm/java-6-openjdk/bin/java -classpath /usr/lib/jni:/usr/lib/java:/usr/share/java/Azureus2.jar:/usr/share/java/log4j-1.2.jar:/usr/share/java/commons-cli.jar:/usr/share/java/swt.jar -Dazureus.install.path=/home/sophie/.azureus org.gudy.azureus2.ui.common.Main
postfix   4359  0.0  0.0  39532  2360 ?        S    20:20   0:00 cleanup -z -t unix -u -c
postfix   4360  0.0  0.0  39440  2152 ?        S    20:20   0:00 trivial-rewrite -n rewrite -t unix -u -c
postfix   4361  0.0  0.0  39672  2876 ?        S    20:20   0:00 local -t unix
sophie    4384  0.0  0.0   4220   588 ?        S    20:20   0:00 /bin/sh /usr/bin/miro /home/sophie/Videos/Movies/EndGame-Blueprint_For_Global_Enslavement.avi
sophie    4385 30.4  3.2 1159300 124224 ?      RLl  20:20   0:12 /usr/bin/python2.7 /usr/bin/miro.real /home/sophie/Videos/Movies/EndGame-Blueprint_For_Global_Enslavement.avi
sophie    4414  3.5  0.5 373952 21216 ?        Sl   20:20   0:01 /usr/bin/python2.7 /usr/lib/pymodules/python2.7/miro/dl_daemon/Democracy_Downloader.py
sophie    4447  0.0  0.0   4220   580 ?        Ss   20:21   0:00 /bin/sh -c gnome-terminal
sophie    4448  9.1  0.4 418772 16812 ?        Sl   20:21   0:00 gnome-terminal
sophie    4451  0.0  0.0  14612   808 ?        S    20:21   0:00 gnome-pty-helper
sophie    4452  6.5  0.1 105260  6116 pts/0    Ss   20:21   0:00 bash
sophie    4626  0.0  0.0  98496  1352 pts/0    R+   20:21   0:00 ps -A u

[COLOR=Blue]***Can someone take a look at these and tell me if they see anything strange???***[/COLOR]





**Thanks Hannibal**

---

### Post by NormanFLinux on 2011-05-17
Install more RAM or upgrade the kernel.

Upgrade the kernel first and see if it addresses the memory leak issue.

Running 2.6.39.0 here.

---

### Post by coljohnhannibalsmith on 2011-05-17
> **NormanFLinux said:**
> Install more RAM or upgrade the kernel.

Upgrade the kernel first and see if it addresses the memory leak issue.

Running 2.6.39.0 here.

I've got 4GB RAM installed.  That's max...

Also, .39's not available in the repository yet.  I'm on x64.

---

### Post by mc4man on 2011-05-17
Well you have quite a lot running at start up but still a fair amount of memory available. (blue
(looking at all this when not in a orig. txt file or code box is a little hard (and the ps wouldn't be too good in code box either - 
lining up a bit for easier reading -  

 ```
             total    used    free    shared     buffers     cached

 Mem:         3709    2541    1167         0         234        919

 -/+ buffers/cache:   1386    [COLOR="Blue"]2322[/COLOR]

 Swap:        8539       0    8539


```

Then you start 3+ things and meanwhile many of your orig. processes also have gone up, a couple fairly significantly (_yacy has increased 50%_, all your [www..](www..)., several  others,  whether they should can't quite say yet.

But you still have a fair amount avail. (blue) and no swap
 ```
             total     used    free   shared     buffers     cached

 Mem:         3709     3502     206        0         244       1211

 -/+ buffers/cache:    2046    [COLOR="#0000ff"]1662[/COLOR]

 Swap:        8539        0    8539

```

So you don't currently seem memory starved and aren't using the cache. ( And while the mem use does add up, some do seem high (libgconf2-4/gconfd-2 is one), many i don't know because i don't use.
If some of these current processes from your start up keep increasing then that may be an issue sooner than later...

If at this point, (the 2nd report), you're already "running realllll slowww" then you need someone more knowledgeable than me. ( maybe your set up and what's running can't be moved from cached to use and back in a timely fashion.
( I do wonder if you really need all this running at once..

Have attached a  basic diff, if you wish to look thru you can see which processes have altered mem. use.( < 1st report, > 2nd, the 2nd mem # matters the most
(many do stay static or relatively so, but a lot of small increases, if they continue, do add up quickly.
If your problems occur after the 2nd report then I'd look at logging some of those that have increased to see if they continue rising

---

### Post by coljohnhannibalsmith on 2011-05-18
Thanks for the diff.  The resulting file still looks a little too complicated to sort out.

What I'd like to do is eliminate as many unecessary processes as possible; and then try to look at the results again.

Can you give me an opinion as to what you think is unecessary; and I'll try to remove some packages?




**Thanks Hannibal**

---

### Post by coljohnhannibalsmith on 2011-05-18
Here's something I just noticed...

Whenever I have Miro running Python 2.7 starts eating-up a lot of processor bandwidth; over 20%.

It creeps up real slowly; but gets real big real fast...

---

