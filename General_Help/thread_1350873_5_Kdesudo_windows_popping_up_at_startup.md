---
title: "5 Kdesudo windows popping up at startup"
date: 2009-12-09
forum: General Help
---

### Post by dh003i on 2009-12-09
To better work with LUT-loading and monitor-calibration, I switched to the ATI Catalyst drivers. This went fine. However, I now have 5 Kdesudo windows popping up when I login, asking for the administrator password to do who-knows-what. I just cancel out of all of them. But does anyone have any idea what he deal would be here, or how to debug it?

I'm in Kubuntu 9.04.

---

### Post by Sin@Sin-Sacrifice on 2009-12-09
Personally I would be suspicious and run chkrootkit just in case. I have no idea otherwise. Sorry if this is no help.

---

### Post by dh003i on 2009-12-10
chkrootkit didn't detect anything:

```
$ sudo chkrootkit                                                                                                                                                                  
ROOTDIR is `/'                                                                                                                                                                                             
Checking `amd'...                                           not found                                                                                                                                      
Checking `basename'...                                      not infected                                                                                                                                   
Checking `biff'...                                          not found                                                                                                                                      
Checking `chfn'...                                          not infected                                                                                                                                   
Checking `chsh'...                                          not infected                                                                                                                                   
Checking `cron'...                                          not infected                                                                                                                                   
Checking `crontab'...                                       not infected                                                                                                                                   
Checking `date'...                                          not infected                                                                                                                                   
Checking `du'...                                            not infected                                                                                                                                   
Checking `dirname'...                                       not infected                                                                                                                                   
Checking `echo'...                                          not infected                                                                                                                                   
Checking `egrep'...                                         not infected                                                                                                                                   
Checking `env'...                                           not infected                                                                                                                                   
Checking `find'...                                          not infected                                                                                                                                   
Checking `fingerd'...                                       not found                                                                                                                                      
Checking `gpm'...                                           not found                                                                                                                                      
Checking `grep'...                                          not infected                                                                                                                                   
Checking `hdparm'...                                        not infected                                                                                                                                   
Checking `su'...                                            not infected                                                                                                                                   
Checking `ifconfig'...                                      not infected                                                                                                                                   
Checking `inetd'...                                         not infected                                                                                                                                   
Checking `inetdconf'...                                     not infected                                                                                                                                   
Checking `identd'...                                        not found                                                                                                                                      
Checking `init'...                                          not infected                                                                                                                                   
Checking `killall'...                                       not infected                                                                                                                                   
Checking `ldsopreload'...                                   not infected                                                                                                                                   
Checking `login'...                                         not infected                                                                                                                                   
Checking `ls'...                                            not infected                                                                                                                                   
Checking `lsof'...                                          not infected                                                                                                                                   
Checking `mail'...                                          not infected                                                                                                                                   
Checking `mingetty'...                                      not found                                                                                                                                      
Checking `netstat'...                                       not infected                                                                                                                                   
Checking `named'...                                         not found                                                                                                                                      
Checking `passwd'...                                        not infected                                                                                                                                   
Checking `pidof'...                                         not infected                                                                                                                                   
Checking `pop2'...                                          not found                                                                                                                                      
Checking `pop3'...                                          not found                                                                                                                                      
Checking `ps'...                                            not infected                                                                                                                                   
Checking `pstree'...                                        not infected                                                                                                                                   
Checking `rpcinfo'...                                       not infected                                                                                                                                   
Checking `rlogind'...                                       not found                                                                                                                                      
Checking `rshd'...                                          not found                                                                                                                                      
Checking `slogin'...                                        not infected                                                                                                                                   
Checking `sendmail'...                                      not infected
Checking `sshd'...                                          not found
Checking `syslogd'...                                       not infected
Checking `tar'...                                           not infected
Checking `tcpd'...                                          not infected
Checking `tcpdump'...                                       not infected
Checking `top'...                                           not infected
Checking `telnetd'...                                       not found
Checking `timed'...                                         not found
Checking `traceroute'...                                    not found
Checking `vdir'...                                          not infected
Checking `w'...                                             not infected
Checking `write'...                                         not infected
Checking `aliens'...                                        no suspect files
Searching for sniffer's logs, it may take a while...        nothing found
Searching for rootkit HiDrootkit's default files...         nothing found
Searching for rootkit t0rn's default files...               nothing found
Searching for t0rn's v8 defaults...                         nothing found
Searching for rootkit Lion's default files...               nothing found
Searching for rootkit RSHA's default files...               nothing found
Searching for rootkit RH-Sharpe's default files...          nothing found
Searching for Ambient's rootkit (ark) default files and dirs... nothing found
Searching for suspicious files and dirs, it may take a while...
/usr/lib/jvm/java-6-sun-1.6.0.16/.systemPrefs /usr/lib/jvm/.java-6-sun.jinfo /usr/lib/firefox-3.5.5/.autoreg /usr/lib/firefox-3.0.15/.autoreg /usr/lib/xulrunner-1.9.1.5/.autoreg /usr/lib/xulrunner-1.9.0.15/.autoreg /lib/init/rw/.ramfs /lib/modules/2.6.28-11-generic/volatile/.mounted

Searching for LPD Worm files and dirs...                    nothing found
Searching for Ramen Worm files and dirs...                  nothing found
Searching for Maniac files and dirs...                      nothing found
Searching for RK17 files and dirs...                        nothing found
Searching for Ducoci rootkit...                             nothing found
Searching for Adore Worm...                                 nothing found
Searching for ShitC Worm...                                 nothing found
Searching for Omega Worm...                                 nothing found
Searching for Sadmind/IIS Worm...                           nothing found
Searching for MonKit...                                     nothing found
Searching for Showtee...                                    nothing found
Searching for OpticKit...                                   nothing found
Searching for T.R.K...                                      nothing found
Searching for Mithra...                                     nothing found
Searching for LOC rootkit...                                nothing found
Searching for Romanian rootkit...                           nothing found
Searching for Suckit rootkit...                             nothing found
Searching for Volc rootkit...                               nothing found
Searching for Gold2 rootkit...                              nothing found
Searching for TC2 Worm default files and dirs...            nothing found
Searching for Anonoying rootkit default files and dirs...   nothing found
Searching for ZK rootkit default files and dirs...          nothing found
Searching for ShKit rootkit default files and dirs...       nothing found
Searching for AjaKit rootkit default files and dirs...      nothing found
Searching for zaRwT rootkit default files and dirs...       nothing found
Searching for Madalin rootkit default files...              nothing found
Searching for Fu rootkit default files...                   nothing found
Searching for ESRK rootkit default files...                 nothing found
Searching for rootedoor...                                  nothing found
Searching for ENYELKM rootkit default files...              nothing found
Searching for common ssh-scanners default files...          nothing found
Searching for anomalies in shell history files...           nothing found
Checking `asp'...                                           not infected
Checking `bindshell'...                                     not infected
Checking `lkm'...                                           chkproc: nothing detected
chkdirs: nothing detected
Checking `rexedcs'...                                       not found
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[3458])
Checking `w55808'...                                        not infected
Checking `wted'...                                          chkwtmp: nothing deleted
Checking `scalper'...                                       not infected
Checking `slapper'...                                       not infected
Checking `z2'...                                            user root deleted or never logged from lastlog!
```

---

### Post by Sin@Sin-Sacrifice on 2009-12-10
I just started using Backtrack 4 yesterday and the same thing happens. Not sure... sorry I'm no help but if I find anything I will let you know.

---

### Post by jbrown96 on 2009-12-10
I'm guessing that you didn't close out the admin-level ATI Catalyst manager, and KDE is trying to restore it, but needs permission to do it.

In System Settings-->Advanced (tab)-->Session Manager. Choose "start with an empty session" then try logging again. If that doesn't work then check Autostart in the advanced section of system settings.

If you get rid of the kdesudo dialogs, then you can change it back to restore your session if you want. KDE has had a strange bug for a long time like this. If I exit a session with a window open, then it restores it like it should next time. The problem is that it will restore the app every time I login, even if I don't leave it open on subsequent logins. Apps seem to get stuck on the "restore" list.

---

