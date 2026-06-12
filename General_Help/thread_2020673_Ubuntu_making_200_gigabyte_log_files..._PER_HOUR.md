---
title: "Ubuntu making 200 gigabyte log files... PER HOUR"
date: 2012-07-08
forum: General Help
---

### Post by JigglyWiggly_ on 2012-07-08
.xsession errros are becoming so insanely huge so quickly

so i used gnome-schedule to do this 
truncate the file to 0 kilobytes every minute now.

However, this madness makes vnc stop working for some reason, it's like killing my server.

Server still working, but it's going to kill the main HD if this keeps up.

How can I stop these HUGE .xsession errors in my home folder? I tried putting the file to read only but the insane developers thought it would be a good idea to make new files with the same name but with random ending letters. 

What are these people smoking? Can someone help me?

[http://ubuntuforums.org/showthread.php?t=1517991](http://ubuntuforums.org/showthread.php?t=1517991)

same issues

on ubuntu 10.04

i don't want to go to 12.04 LTS,  because I am afraid it might break some of my apcupsd settings... and it probably won't even fix the issue.



edit: I think this fixed it
[http://marc.waeckerlin.org/computer/blog/get_rid_of_xsession-error_that_s_filling_up_the_home_directory](http://marc.waeckerlin.org/computer/blog/get_rid_of_xsession-error_that_s_filling_up_the_home_directory)


incase his website website ever goes down i will just quote 

> The file .xsession-error gets extremely huge, several giga bytes with nonsense contents. It does not contain real errors or problems, but millions of bytes of absolutely useless nonsense debugging ********. See Example Snipppets of the Contents ath the end for some snippets.

It is very difficult to get rid of this useless ****, because if you delete the file, the contents is not freed before you log off. If you create the file as link to /dev/null, it will be recreated as normal file on next login. Even if you take away the write access (chomod ugo= ~/.xsession-errors) and even if you give it to user root (chown root.root ~/.xsession-errors), it does not help. After next reboot, the file will be restored with read-/write-access for the user.

The file /etc/X11/Xsession is responsible for this bad behavior. You need to edit that file as root (e.g. sudo xemacs /etc/X11/Xsession and to remove all that ********. I commented it out (it's on top) and replaced exec >>"$ERRFILE" 2>&1 by exec >> /dev/null 2>&1:

[...]
USERXSESSIONRC=$HOME/.xsessionrc
ALTUSERXSESSION=$HOME/.Xsession

# Get rid of this damned ******** ERRFILE filling up the whole home directory

# ERRFILE=$HOME/.xsession-errors

# # attempt to create an error file; abort if we cannot
# if (umask 077 && touch "$ERRFILE") 2> /dev/null && [ -w "$ERRFILE" ] &&
#   [ ! -L "$ERRFILE" ]; then
#   chmod 600 "$ERRFILE"
# elif ERRFILE=$(tempfile 2> /dev/null); then
#   if ! ln -sf "$ERRFILE" "${TMPDIR:=/tmp}/xsession-$USER"; then
#     message "warning: unable to symlink \"$TMPDIR/xsession-$USER\" to" \
#              "\"$ERRFILE\"; look for session log/errors in" \
#              "\"$TMPDIR/xsession-$USER\"."
#   fi
# else
#   errormsg "unable to create X session log/error file; aborting."
# fi

# # truncate ERRFILE if it is too big to avoid disk usage DoS
# if [ "`stat -c%s \"$ERRFILE\"`" -gt 500000 ]; then
#   T=`mktemp -p "$HOME"`
#   tail -c 500000 "$ERRFILE" > "$T" && mv -f "$T" "$ERRFILE" || rm -f "$T"
# fi

#exec >>"$ERRFILE" 2>&1
exec >> /dev/null 2>&1

[...]

---

### Post by Habitual on 2012-07-08
My bad.

Edit:
Well, poop.
Just read "It is very difficult to get rid of this useless ****, because if you  delete the file, the contents is not freed before you log off. If you  create the file as link to /dev/null, it will be recreated as normal file on next login. Even if you take away the write access (chomod ugo= ~/.xsession-errors) and even if you give it to user root  (chown root.root ~/.xsession-errors), it does not help. After next reboot, the file will be restored with read-/write-access for the user" at [http://marc.waeckerlin.org/computer/blog/get_rid_of_xsession-error_that_s_filling_up_the_home_directory](http://marc.waeckerlin.org/computer/blog/get_rid_of_xsession-error_that_s_filling_up_the_home_directory) so my hack is useless in this situation, sorry about that.

---

