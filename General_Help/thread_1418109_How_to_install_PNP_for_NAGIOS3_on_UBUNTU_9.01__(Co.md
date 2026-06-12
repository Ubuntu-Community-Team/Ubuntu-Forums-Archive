---
title: "How to install PNP for NAGIOS3 on UBUNTU 9.01 ? (Coming tuto)"
date: 2010-02-28
forum: General Help
---

### Post by emma_peel on 2010-02-28
Hello dear forum.

I'm currently trying to install PNP for NAGIOS3. The NAGIOS3 installation has been done easily through the package manager. Nothing has been change in the configurations files.

I now want to have the graphs. There is no package for PNP, so I decided to install it from the source.

I did the following  commands :

```
root@box:~# git clone git://pnp4nagios.git.sourceforge.net/gitroot/pnp4nagios/pnp4nagios
```

And then :

```
root@box:~/pnp4nagios# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
…
*** Configuration summary for pnp4nagios-0.6.2 12-23-2009 ***

  General Options:
  -------------------------         -------------------
  Nagios user/group:                nagios nagios
  Install directory:                /usr/local/pnp4nagios
  HTML Dir:                         /usr/local/pnp4nagios/share
  Config Dir:                       /usr/local/pnp4nagios/etc
  Location of rrdtool binary:       /usr/bin/rrdtool Version 1.3.1
  RRDs Perl Modules:                FOUND (Version 1.3001)
  RRD Files stored in:              /usr/local/pnp4nagios/var/perfdata
  process_perfdata.pl Logfile:      /usr/local/pnp4nagios/var/perfdata.log
  Perfdata files (NPCD) stored in:  /usr/local/pnp4nagios/var/spool

  Web Interface Options:  -------------------------         -------------------
  HTML URL:                         http://localhost/pnp4nagios/
  Apache Config File:               /etc/apache2/conf.d/pnp4nagios.conf


  Review the options above for accuracy.  If they look okay,
  type 'make all' to compile.


```

At this step, there is something that is still unclear. What do they mean by accurate ? Accurate against the NAGIOS installation, or do they just ask if the default directories are  OK for the user ?

Next step :

```
root@box:~/pnp4nagios# make all
root@box:~/pnp4nagios# make install-config
root@box:~/pnp4nagios# make install-init
```

Then, I have activated the process performance functionality in nagios.cfg :

```
process_performance_data=1


service_perfdata_file=/usr/local/pnp4nagios/var/service-perfdata
service_perfdata_file_template=DATATYPE::SERVICEPERFDATA\tTIMET::$TIMET$\tHOSTNAME::$HOSTNAME$\tSERVICEDESC::$SERVICEDESC$\tSERVICEPERFDATA::$SERVICEPERFDATA$\tSERVICECHECKCOMMAND::$SERVICECHECKCOMMAND$\tHOSTSTATE::$HOSTSTATE$\tHOSTSTATETYPE::$HOSTSTATETYPE$\tSERVICESTATE::$SERVICESTATE$\tSERVICESTATETYPE::$SERVICESTATETYPE$
service_perfdata_file_mode=a
service_perfdata_file_processing_interval=15
service_perfdata_file_processing_command=process-service-perfdata-file
```

In the commands.cfg, I have defined the process-service-perfdata-file :

```
# 'process-host-perfdata-file' command definition
define command{
        command_name    process-service-perfdata-file
        command_line    $USER1$/process_perfdata.pl --bulk=/usr/local/pnp4nagios/var/host-perfdata
        }

```

It is important to restart NAGIOS before launching the check script :

```
emma@box:/usr/local/pnp4nagios/libexec$ sudo /etc/init.d/nagios3 restart
emma@box:/usr/local/pnp4nagios/libexec$ sudo ./verify_pnp_config.pl -m bulk -b /usr/lib/nagios -c /etc/nagios3/nagios.cfg -B nagios3
```

And now the error log :

```
Check Nagios/Icinga/PNP integration, v0.1.18

[I] OS: Ubuntu 9.10  
[I] Perl: 5.010000
[I] Package Manager: /usr/bin/dpkg
[I] Package: "php5 5.2.10.dfsg.1-2ubuntu6.4"
[I] Package: "ttf-dejavu 2.29-2"
[I] install_opts: -o nagios -g nagios
[I] PNP-version: 0.6.2
[I] using Nagios basedir "/usr/lib/nagios"
[I] using Nagios config "/etc/nagios3/nagios.cfg"
[E] (Nagios-Binary) file "/usr/lib/nagios/bin/nagios3" is missing
[I] using Nagios binary "/usr/lib/nagios/bin/nagios3"
[I] PNP mode: "bulk"
sh: /usr/lib/nagios/bin/nagios3: not found
[I] Nagios info: 
[A] verifying Nagios config
sh: /usr/lib/nagios/bin/nagios3: not found
[A] processing "/etc/nagios3/nagios.cfg"
[I] nagios_user=nagios
[I] nagios_group=nagios
[A] checking RRDtool (/usr/bin/rrdtool)
[I] RRDtool: RRDtool 1.3.1 
[I] RRDs perl module installed
[A] processing "/etc/nagios3/resource.cfg"
[I] using "/var/cache/nagios3/objects.cache" entries
[E] (process-service-perfdata-file) file "/usr/lib/nagios/plugins/process_perfdata.pl" is missing
[E] (pgm) file "$USER1$/process_perfdata.pl" is missing
Use of uninitialized value $NagiosVer in numeric ge (>=) at ./verify_pnp_config.pl line 382.
[A] checking template "service_perfdata_file_template"
[A] processing "/usr/local/pnp4nagios/etc/process_perfdata.cfg-sample"
[I] (rra_cfg) file "/usr/local/pnp4nagios/etc/rra.cfg" doesn't exist (yet)
[I] (log_file) file "/usr/local/pnp4nagios/var/perfdata.log" doesn't exist (yet)
[E] "stats_dir" is not a valid option
[A] processing "/usr/local/pnp4nagios/etc/config.php"
[A] checking of RRDpath "/usr/local/pnp4nagios/var/perfdata"
[E] 0 dir(s) but NO rrd files => NO graphs!

Errors found. Please check the settings and have a look at the documentation.

```

First error (Nagios-Binary). This script doest not look for the binary at the right place.

Next error, the process-service-perfdata-file is not found. I do not see at this step how to configure NAGIOS to help it to found the perl script.

I'm still working on it, but any help would be appreciated.

Once working, I will write a tutorial, the ones googled are not complete.

---

