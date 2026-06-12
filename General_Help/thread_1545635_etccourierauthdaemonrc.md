---
title: "/etc/courier/authdaemonrc"
date: 2010-08-04
forum: General Help
---

### Post by yui72o on 2010-08-04
Hello, salam alaykoum
 
 I was installing courier-imap when I deleted this file by error
 > /etc/courier/authdaemonrc Can someone give me a copy ?
 
 reinstalling don't make the file reappear
 
 
 I have courier imap version 4.6.0-2.1ubuntu1
 and courier-authdaemon version 0.62.4-1
 but I think any version will work
 
 thanks in advance
 
------------------------------------------------------
[COLOR=DimGray]hum : The message you have entered is too short. Please lengthen your message to at least 1 characters. 
boring .... -_-
apparently blocking yahooapis make the forum bug xD
okay fixed[/COLOR]

---

### Post by yui72o on 2010-08-04
> 
##VERSION: $Id: authdaemonrc.in,v 1.8 2001/10/07 02:16:22 mrsam Exp $
#
# Copyright 2000-2001 Double Precision, Inc.  See COPYING for
# distribution information.
#
# authdaemonrc created from authdaemonrc.dist by sysconftool
#
# Do not alter lines that begin with ##, they are used when upgrading
# this configuration.
#
# This file configures authdaemond, the resident authentication daemon.
#
# Comments in this file are ignored.  Although this file is intended to
# be sourced as a shell script, authdaemond parses it manually, so
# the acceptable syntax is a bit limited.  Multiline variable contents,
# with the \ continuation character, are not allowed.  Everything must
# fit on one line.  Do not use any additional whitespace for indentation,
# or anything else.

##NAME: authmodulelist:0
#
# The authentication modules that are linked into authdaemond.  The
# default list is installed.  You may selectively disable modules simply
# by removing them from the following list.  The available modules you
# can use are: authcustom authcram authuserdb authldap authpgsql authmysql authpam

authmodulelist="authpam"

##NAME: authmodulelistorig:1
#
# This setting is used by Courier's webadmin module, and should be left
# alone

authmodulelistorig="authcustom authcram authuserdb authldap authpgsql authmysql authpam"

##NAME: daemons:0
#
# The number of daemon processes that are started.  authdaemon is typically
# installed where authentication modules are relatively expensive: such
# as authldap, or authmysql, so it's better to have a number of them running.
# PLEASE NOTE:  Some platforms may experience a problem if there's more than
# one daemon.  Specifically, SystemV derived platforms that use TLI with
# socket emulation.  I'm suspicious of TLI's ability to handle multiple
# processes accepting connections on the same filesystem domain socket.
#
# You may need to increase daemons if as your system load increases.  Symptoms
# include sporadic authentication failures.  If you start getting
# authentication failures, increase daemons.  However, the default of 5
# SHOULD be sufficient.  Bumping up daemon count is only a short-term
# solution.  The permanent solution is to add more resources: RAM, faster
# disks, faster CPUs...

daemons=5

##NAME: version:0
#
# When you have multiple versions of authdaemond.* installed, authdaemond
# just picks the first one it finds.  Set "version" to override that.
# For example:  version=authdaemond.plain

version=""

##NAME: authdaemonvar:0
#
# authdaemonvar is here, but is not used directly by authdaemond.  It's
# used by various configuration and build scripts, so don't touch it!

authdaemonvar=/var/run/courier/authdaemon

:popcorn:

---

