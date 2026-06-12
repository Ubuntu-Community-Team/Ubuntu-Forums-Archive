---
title: "Problem running Firefox 3.6 - script runs 3.5.7"
date: 2010-02-01
forum: General Help
---

### Post by t0p on 2010-02-01
I downloaded firefox-3.6.tar.bz2 from [here]("http://www.mozilla-europe.org/en/firefox/")  and extracted it to my Desktop.  I had a look in the resulting "firefox" folder, and deduced I run the script called "firefox" to start Firefox 3.6.  Problem is, when I run ~/Desktop/firefox/firefox, it starts another instance of Firefox 3.5.7 (my current browser).

What on earth is going on here?  How do I get Firefox 3.6 to run?

---

### Post by DeMus on 2010-02-01
> **t0p said:**
> I downloaded firefox-3.6.tar.bz2 from [here]("http://www.mozilla-europe.org/en/firefox/")  and extracted it to my Desktop.  I had a look in the resulting "firefox" folder, and deduced I run the script called "firefox" to start Firefox 3.6.  Problem is, when I run ~/Desktop/firefox/firefox, it starts another instance of Firefox 3.5.7 (my current browser).

What on earth is going on here?  How do I get Firefox 3.6 to run?

Can you tell us what is written in the script you start? Does it simply start firefox &u or really ~/Desktop/firefox/firefox?
If it is the first then yes, the old version will be started since that one is known to the system. The new one is probably not installed, is it? You placed the folder on tour desktop and tried to start it from there.
Change the link, every link you want to use to  ~/Desktop/firefox/firefox %u and it'll work.

---

### Post by t0p on 2010-02-01
Okay, here is the script I've got at ~/Desktop/firefox/firefox:

```

#!/bin/sh
#
# ***** BEGIN LICENSE BLOCK *****
# Version: MPL 1.1/GPL 2.0/LGPL 2.1
#
# The contents of this file are subject to the Mozilla Public License Version
# 1.1 (the "License"); you may not use this file except in compliance with
# the License. You may obtain a copy of the License at
# http://www.mozilla.org/MPL/
#
# Software distributed under the License is distributed on an "AS IS" basis,
# WITHOUT WARRANTY OF ANY KIND, either express or implied. See the License
# for the specific language governing rights and limitations under the
# License.
#
# The Original Code is mozilla.org code.
#
# The Initial Developer of the Original Code is
# Netscape Communications Corporation.
# Portions created by the Initial Developer are Copyright (C) 1998
# the Initial Developer. All Rights Reserved.
#
# Contributor(s):
#
# Alternatively, the contents of this file may be used under the terms of
# either the GNU General Public License Version 2 or later (the "GPL"), or
# the GNU Lesser General Public License Version 2.1 or later (the "LGPL"),
# in which case the provisions of the GPL or the LGPL are applicable instead
# of those above. If you wish to allow use of your version of this file only
# under the terms of either the GPL or the LGPL, and not to allow others to
# use your version of this file under the terms of the MPL, indicate your
# decision by deleting the provisions above and replace them with the notice
# and other provisions required by the GPL or the LGPL. If you do not delete
# the provisions above, a recipient may use your version of this file under
# the terms of any one of the MPL, the GPL or the LGPL.
#
# ***** END LICENSE BLOCK *****

## 
## Usage:
##
## $ mozilla [args]
##
## This script is meant to run the application binary from mozilla/dist/bin.
##
## The script will setup all the environment voodoo needed to make
## the application binary to work.
##

#uncomment for debugging
#set -x

moz_libdir=/usr/local/lib/firefox-3.6

# Use run-mozilla.sh in the current dir if it exists
# If not, then start resolving symlinks until we find run-mozilla.sh
found=0
progname="$0"
curdir=`dirname "$progname"`
progbase=`basename "$progname"`
run_moz="$curdir/run-mozilla.sh"
if test -x "$run_moz"; then
  dist_bin="$curdir"
  found=1
else
  here=`/bin/pwd`
  while [ -h "$progname" ]; do
    bn=`basename "$progname"`
    cd `dirname "$progname"`
    # Resolve symlink of dirname
    cd `/bin/pwd`
    progname=`/bin/ls -l "$bn" | sed -e 's/^.* -> //' `
    progbase=`basename "$progname"`
    if [ ! -x "$progname" ]; then
      break
    fi
    curdir=`dirname "$progname"`
    run_moz="$curdir/run-mozilla.sh"
    if [ -x "$run_moz" ]; then
      cd "$curdir"
      dist_bin=`/bin/pwd`
      run_moz="$dist_bin/run-mozilla.sh"
      found=1
      break
    fi
  done
  cd "$here"
fi
if [ $found = 0 ]; then
  # Check default compile-time libdir
  if [ -x "$moz_libdir/run-mozilla.sh" ]; then
    dist_bin="$moz_libdir"
    run_moz="$moz_libdir/run-mozilla.sh"
  else
    echo "Cannot find Firefox runtime directory. Exiting."
    exit 1
  fi
fi

script_args=""
debugging=0
MOZILLA_BIN="${progbase}-bin"

if [ "$OSTYPE" = "beos" ]; then
  mimeset -F "$MOZILLA_BIN"
fi

pass_arg_count=0
while [ $# -gt $pass_arg_count ]
do
  case "$1" in
    -p | --pure | -pure)
      MOZILLA_BIN="${MOZILLA_BIN}.pure"
      shift
      ;;
    -g | --debug)
      script_args="$script_args -g"
      debugging=1to my Desktop
      shift
      ;;
    -d | --debugger)
      script_args="$script_args -d $2"
      shift 2
      ;;
    *)
      # Move the unrecognized argument to the end of the list.
      arg="$1"
      shift
      set -- "$@" "$arg"
      pass_arg_count=`expr $pass_arg_count + 1`
      ;;
  esac
done

if [ $debugging = 1 ]
then
  echo $dist_bin/run-mozilla.sh $script_args $dist_bin/$MOZILLA_BIN "$@"
fi
"$dist_bin/run-mozilla.sh" $script_args "$dist_bin/$MOZILLA_BIN" "$@"
exitcode=$?

exit $exitcode
# EOF.

```Yes, I put the "firefox" folder on my Desktop and I'm trying to run it from there.  I haven't *installed* Firefox 3.6 because I don't see any way to install it.  It appears to me that I'm supposed to run it from my home directory.  That's how I've run Firefox 3.5 for some months now , and it seems fine working that way.  Can someone tell me how I'm supposed to install 3.6?

I looked for a .deb to install, but all I could find was stuff for 9.04 and 9.10.  I've got 8.04 on this computer, and I haven't seen a .deb for this version.  Does anyone know of one?

---

### Post by sarin_cv on 2010-02-01
1. copy the extracted folder to /opt. 
2. change ownership of the firefox folder to ur user id using chown -R
3. give execute permission to firefox script and execute in command line
4. You can also create a shorcut to the menu using edit menus..

---

### Post by t0p on 2010-02-01
> **sarin_cv said:**
> 1. copy the extracted folder to /opt. 
2. change ownership of the firefox folder to ur user id using chown -R
3. give execute permission to firefox script and execute in command line
4. You can also create a shorcut to the menu using edit menus..

Thanks for that.  I did as you suggested - copied "firefox" folder to /opt, changed ownership to t0p, marked "firefox" script as executable, then ran it from terminal with command

```

/opt/firefox/firefox
```

...and it still runs 3.5.7!

This is getting real weird now.  Why on earth is it still running 3.5.7?  What am I doing wrong?

:confused:

---

### Post by sarin_cv on 2010-02-01
no way...it should work this way coz it is woking fine for me...i also had firefox 3.5.8beta with me when i installed 3.6.. try removing the 3.5.7 version using synaptic and do the steps again... 

check [scouser73]("http://ubuntuforums.org/member.php?u=536148")'s reply in this thread for exact commands... 
[http://ubuntuforums.org/showthread.php?t=1392171&page=2](http://ubuntuforums.org/showthread.php?t=1392171&page=2)

---

### Post by HiImTye on 2010-02-01
[LIST=1]
[*]preferences > preferred applications
[*]under 'web browser' (first panel) choose 'custom'
[*]inside the text box labelled 'command' enter 'firefox-3.6'
[/LIST]
hope this helps

---

### Post by t0p on 2010-02-01
I can't remove Firefox-3.5.7 through Synaptic or apt-get because I I don't have Firefox-3.5.7 *installed* - when I got Firefox-3.5, I got it in a similar way to 3.6 - I run it by running a script in a "firefox" directory in my home directory, I start it with a launcher that points at ~/firefox/firefox.

I moved the "firefox" directory for Firefox-3.5 so it shouldn't run anymore.  I made a launcher pointing to /opt/firefox/firefox to launch Firefox-3.6.  And I changed the preferred browser in System > Preferences > Preferred Applications to /opt/firefox/firefox.  And now, when I click on the launcher, it does *nothing*.  Same if I type /oopt/firefox/firefox in the terminal.  It creates an application tab called "Firefox" on the bottom panel, but Firefox-3.6 doesn't open.

I don't know what I've done to make this happen.  Any ideas?

---

### Post by lovinglinux on 2010-02-01
For future reference, see Installing Other Versions from [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by t0p on 2010-02-01
Never mind, I've got it working now.

The problem was, I was trying to open Firefox-3.6 while I still had 3.5.7 open.  When I closed 3.5.7, 3.6 opened.

Thanks everyone who helped!

---

### Post by HiImTye on 2010-02-01
open up synaptic, search for firefox right click it and choose 'reinstall'

install your firefox 3.6

change your application preference to 'firefox-3.6'

edit: or it's working now
lol

---

### Post by lovinglinux on 2010-02-01
> **t0p said:**
> I can't remove Firefox-3.5.7 through Synaptic or apt-get because I I don't have Firefox-3.5.7 *installed* - when I got Firefox-3.5, I got it in a similar way to 3.6 - I run it by running a script in a "firefox" directory in my home directory, I start it with a launcher that points at ~/firefox/firefox.

I moved the "firefox" directory for Firefox-3.5 so it shouldn't run anymore.  I made a launcher pointing to /opt/firefox/firefox to launch Firefox-3.6.  And I changed the preferred browser in System > Preferences > Preferred Applications to /opt/firefox/firefox.  And now, when I click on the launcher, it does *nothing*.  Same if I type /oopt/firefox/firefox in the terminal.  It creates an application tab called "Firefox" on the bottom panel, but Firefox-3.6 doesn't open.

I don't know what I've done to make this happen.  Any ideas?

Can you run it with this?

```
/opt/firefox/firefox -P -no-remote
```

BTW, there is no need to change the ownership of anything. All you had to do was to extract it to /opt and run the command /opt/firefox/firefox.

---

