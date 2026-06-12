---
title: "Clamav .88 help please"
date: 2006-02-02
forum: General Help
---

### Post by ahh_dee on 2006-02-02
Hi I just compiled Clamav but i have having trouble configuring "freshclam.conf" and "clamd.conf"  I dont know what I am doing wrong it just outputs ```
ERROR: Please edit the example config file /usr/local/etc/freshclam.conf.
ERROR: Please edit the example config file /usr/local/etc/clamd.conf.
ERROR: Can't parse the config file /usr/local/etc/clamd.conf

```

can someone lend me a copy of their config files or give me some hints here is what i did

```
##
## Example config file for freshclam
## Please read the freshclam.conf(5) manual before editing this file.
## This file may be optionally merged with clamd.conf.
##


# Comment or remove the line below.
Example

# Path to the database directory.
# WARNING: It must match clamd.conf's directive!
# Default: hardcoded (depends on installation options)
DatabaseDirectory /var/lib/clamav

# Path to the log file (make sure it has proper permissions)
 Default: disabled
#UpdateLogFile /var/log/freshclam.log

# Enable verbose logging.
 Default: disabled
#LogVerbose

# Use system logger (can work together with UpdateLogFile).
 Default: disabled
#LogSyslog

# Specify the type of syslog messages - please refer to 'man syslog'
# for facility names.
# Default: LOG_LOCAL6
#LogFacility LOG_MAIL

# This option allows you to save the process identifier of the daemon
# Default: disabled
PidFile /var/run/freshclam.pid

# By default when started freshclam drops privileges and switches to the
# "clamav" user. This directive allows you to change the database owner.
 Default: clamav (may depend on installation options)
#DatabaseOwner clamav

# Initialize supplementary group access (freshclam must be started by root).
 Default: disabled
#AllowSupplementaryGroups

# Use DNS to verify virus database version. Freshclam uses DNS TXT records
# to verify database and software versions. With this directive you can change
# the database verification domain.
 Default: enabled, pointing to current.cvd.clamav.net
#DNSDatabaseInfo current.cvd.clamav.net

# Uncomment the following line and replace XY with your country
# code. See http://www.iana.org/cctld/cctld-whois.htm for the full list.
# Default: There is no default, which results in an error when running freshclam
DatabaseMirror db.us.clamav.net

# database.clamav.net is a round-robin record which points to our most 
# reliable mirrors. It's used as a fall back in case db.XY.clamav.net is 
# not working. DO NOT TOUCH the following line unless you know what you
# are doing.
DatabaseMirror database.clamav.net

# How many attempts to make before giving up.
# Default: 3 (per mirror)
#MaxAttempts 5

# Number of database checks per day.
# Default: 12 (every two hours)
#Checks 24

# Proxy settings
# Default: disabled
#HTTPProxyServer myproxy.com
#HTTPProxyPort 1234
#HTTPProxyUsername myusername
#HTTPProxyPassword mypass

# Use aaa.bbb.ccc.ddd as client address for downloading databases. Useful for
# multi-homed systems.
# Default: Use OS'es default outgoing IP address.
#LocalIPAddress aaa.bbb.ccc.ddd

# Send the RELOAD command to clamd.
# Default: disabled
#NotifyClamd
# By default it uses the hardcoded configuration file but you can force an
# another one.
#NotifyClamd /config/file/path

# Run command after successful database update.
 Default: disabled
#OnUpdateExecute clamav

# Run command when database update process fails.
 Default: disabled
#OnErrorExecute command

# Run command when freshclam reports outdated version.
# In the command string %v will be replaced by the new version number.
# Default: disabled
#OnOutdatedExecute command

# Don't fork into background.
 Default: disabled
#Foreground

# Enable debug messages in libclamav.
# Default: disabled
#Debug

```

```
##
## Example config file for the Clam AV daemon
## Please read the clamd.conf(5) manual before editing this file.
##


# Comment or remove the line below.
Example

# Uncomment this option to enable logging.
# LogFile must be writable for the user running daemon.
# A full path is required.
 Default: disabled
#LogFile /tmp/clamd.log

# By default the log file is locked for writing - the lock protects against
# running clamd multiple times (if want to run another clamd, please
# copy the configuration file, change the LogFile variable, and run
# the daemon with --config-file option).
# This option disables log file locking.
 Default: disabled
#LogFileUnlock

# Maximal size of the log file.
# Value of 0 disables the limit.
# You may use 'M' or 'm' for megabytes (1M = 1m = 1048576 bytes)
# and 'K' or 'k' for kilobytes (1K = 1k = 1024 bytes). To specify the size
# in bytes just don't use modifiers.
 Default: 1M
#LogFileMaxSize 2M

# Log time with each message.
 Default: disabled
#LogTime

# Also log clean files. Useful in debugging but drastically increases the
# log size.
 Default: disabled
#LogClean

# Use system logger (can work together with LogFile).
 Default: disabled
#LogSyslog

# Specify the type of syslog messages - please refer to 'man syslog'
# for facility names.
# Default: LOG_LOCAL6
#LogFacility LOG_MAIL

# Enable verbose logging.
 Default: disabled
#LogVerbose

# This option allows you to save a process identifier of the listening
# daemon (main thread).
 Default: disabled
#PidFile /var/run/clamd.pid

# Optional path to the global temporary directory.
 Default: system specific (usually /tmp or /var/tmp).
#TemporaryDirectory /var/tmp

# Path to the database directory.
# Default: hardcoded (depends on installation options)
DatabaseDirectory /var/lib/clamav

# The daemon works in a local OR a network mode. Due to security reasons we
# recommend the local mode.

# Path to a local socket file the daemon will listen on.
# Default: disabled
LocalSocket /tmp/clamd

# Remove stale socket after unclean shutdown.
# Default: disabled
FixStaleSocket

# TCP port address.
 Default: disabled
#TCPSocket 3310

# TCP address.
# By default we bind to INADDR_ANY, probably not wise.
# Enable the following to provide some degree of protection
# from the outside world.
 Default: disabled
#TCPAddr 127.0.0.1

# Maximum length the queue of pending connections may grow to.
 Default: 15
#MaxConnectionQueueLength 30

# Clamd uses FTP-like protocol to receive data from remote clients.
# If you are using clamav-milter to balance load between remote clamd daemons
# on firewall servers you may need to tune the options below.

# Close the connection when the data size limit is exceeded.
# The value should match your MTA's limit for a maximal attachment size.
 Default: 10M
#StreamMaxLength 20M

# Limit port range.
 Default: 1024
#StreamMinPort 30000
 Default: 2048
#StreamMaxPort 32000

# Maximal number of threads running at the same time.
 Default: 10
#MaxThreads 20

# Waiting for data from a client socket will timeout after this time (seconds).
# Value of 0 disables the timeout.
 Default: 120
#ReadTimeout 300

# Waiting for a new job will timeout after this time (seconds).
 Default: 30
#IdleTimeout 60

# Maximal depth directories are scanned at.
 Default: 15
#MaxDirectoryRecursion 20

# Follow directory symlinks.
 Default: disabled
#FollowDirectorySymlinks

# Follow regular file symlinks.
 Default: disabled
#FollowFileSymlinks

# Perform internal sanity check (database integrity and freshness).
 Default: 1800 (30 min)
#SelfCheck 600

# Execute a command when virus is found. In the command string %v will
# be replaced by a virus name.
# Default: disabled
VirusEvent /usr/local/bin/send_sms 123456789 "VIRUS ALERT: %v"

# Run as a selected user (clamd must be started by root).
 Default: disabled
#User clamav

# Initialize supplementary group access (clamd must be started by root).
 Default: disabled
#AllowSupplementaryGroups

# Stop daemon when libclamav reports out of memory condition.
ExitOnOOM

# Don't fork into background.
 Default: disabled
#Foreground

# Enable debug messages in libclamav.
 Default: disabled
#Debug

# Do not remove temporary files (for debug purposes).
 Default: disabled
#LeaveTemporaryFiles


# By default clamd uses scan options recommended by libclamav. This option
# disables recommended options and allows you to enable selected ones below.
# DO NOT TOUCH IT unless you know what you are doing.
# Default: disabled
#DisableDefaultScanOptions

##
## Executable files
##

# PE stands for Portable Executable - it's an executable file format used
# in all 32-bit versions of Windows operating systems. This option allows
# ClamAV to perform a deeper analysis of executable files and it's also
# required for decompression of popular executable packers such as UPX, FSG,
# and Petite.
# Default: enabled
#ScanPE

# With this option clamav will try to detect broken executables and mark
# them as Broken.Executable
# Default: disabled
#DetectBrokenExecutables


##
## Documents
##

# This option enables scanning of Microsoft Office document macros.
# Default: enabled
#ScanOLE2

##
## Mail files
##

# Enable internal e-mail scanner.
 Default: enabled
#ScanMail

# If an email contains URLs ClamAV can download and scan them.
# WARNING: This option may open your system to a DoS attack.
#	   Never use it on loaded servers.
# Default: disabled
#MailFollowURLs


##
## HTML
##

# Perform HTML normalisation and decryption of MS Script Encoder code.
# Default: enabled
#ScanHTML


##
## Archives
##

# ClamAV can scan within archives and compressed files.
# Default: enabled
#ScanArchive

# Due to license issues libclamav does not support RAR 3.0 archives (only the
# old 2.0 format is supported). Because some users report stability problems
# with unrarlib it's disabled by default and you must uncomment the directive
# below to enable RAR 2.0 support.
 Default: disabled
#ScanRAR

# The options below protect your system against Denial of Service attacks
# using archive bombs.

# Files in archives larger than this limit won't be scanned.
# Value of 0 disables the limit.
# Default: 10M
#ArchiveMaxFileSize 15M

# Nested archives are scanned recursively, e.g. if a Zip archive contains a RAR
# file, all files within it will also be scanned. This options specifies how
# deep the process should be continued.
# Value of 0 disables the limit.
# Default: 8
#ArchiveMaxRecursion 9

# Number of files to be scanned within an archive.
# Value of 0 disables the limit.
# Default: 1000
#ArchiveMaxFiles 1500

# If a file in an archive is compressed more than ArchiveMaxCompressionRatio
# times it will be marked as a virus (Oversized.ArchiveType, e.g. Oversized.Zip)
# Value of 0 disables the limit.
# Default: 250
#ArchiveMaxCompressionRatio 300

# Use slower but memory efficient decompression algorithm.
# only affects the bzip2 decompressor.
# Default: disabled
#ArchiveLimitMemoryUsage

# Mark encrypted archives as viruses (Encrypted.Zip, Encrypted.RAR).
 Default: disabled
#ArchiveBlockEncrypted

# Mark archives as viruses (e.g. RAR.ExceededFileSize, Zip.ExceededFilesLimit)
# if ArchiveMaxFiles, ArchiveMaxFileSize, or ArchiveMaxRecursion limit is
# reached.
 Default: disabled
#ArchiveBlockMax


##
## Clamuko settings
## WARNING: This is experimental software. It is very likely it will hang
##	    up your system!!!
##

# Enable Clamuko. Dazuko (/dev/dazuko) must be configured and running.
# Default: disabled
#ClamukoScanOnAccess

# Set access mask for Clamuko.
# Default: disabled
#ClamukoScanOnOpen
#ClamukoScanOnClose
#ClamukoScanOnExec

# Set the include paths (all files in them will be scanned). You can have
# multiple ClamukoIncludePath directives but each directory must be added
# in a seperate line.
# Default: disabled
#ClamukoIncludePath /home
#ClamukoIncludePath /students

# Set the exclude paths. All subdirectories are also excluded.
# Default: disabled
#ClamukoExcludePath /home/guru

# Don't scan files larger than ClamukoMaxFileSize
# Value of 0 disables the limit.
# Default: 5M
#ClamukoMaxFileSize 10M

```

---

### Post by dcstar on 2006-02-02
[QUOTE=ahh_dee]Hi I just compiled Clamav but i have having trouble configuring "freshclam.conf" and "clamd.conf"  I dont know what I am doing wrong it just outputs ......[/QUOTE]
Try:

sudo dpkg-reconfigure clamav-base

My config files are in /etc/clamav

---

### Post by lotusleaf on 2006-02-02
Your problem is easily solved. Just sudo gedit both files and save them with the following modifications:

Change:

```
# Comment or remove the line below.
Example
```

to:

```
# Comment or remove the line below.
#Example
```

Following this try sudo freshclam and you should be set.

---

### Post by ahh_dee on 2006-02-06
[QUOTE=lotusleaf]Your problem is easily solved. Just sudo gedit both files and save them with the following modifications:

Change:

```
# Comment or remove the line below.
Example
```

to:

```
# Comment or remove the line below.
#Example
```

Following this try sudo freshclam and you should be set.[/QUOTE]












Thanks i just rebuilt the source and it worked fine =)

---

### Post by DirtDawg on 2008-06-26
> **lotusleaf said:**
> Your problem is easily solved. Just sudo gedit both files and save them with the following modifications:

Change:

```
# Comment or remove the line below.
Example
```

to:

```
# Comment or remove the line below.
#Example
```

Following this try sudo freshclam and you should be set.

Wow, worked great. Thanks! Kind of a silly bug.

---

