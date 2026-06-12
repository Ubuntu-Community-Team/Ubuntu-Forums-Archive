---
title: "Someone please help"
date: 2006-06-24
forum: General Help
---

### Post by souteneur3190 on 2006-06-24
Adept isnt working for me.  This is the error I always get for anything im trying to get.  I just switched from gnome to kde, and all of gnome is deleted.

There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages.

And this is the output of the follwoing command

sudo apt-get -f install

 (Reading database ... 95680 files and directories currently installed.)
 Removing scim-gtk2-immodule ...
 /var/lib/dpkg/info/scim-gtk2-immodule.postrm: line 8: /usr/sbin/update-gtk-immodules: No such file or directory
 dpkg: error processing scim-gtk2-immodule (--remove):
 subprocess post-removal script returned error exit status 1
 Errors were encountered while processing:
 scim-gtk2-immodule
 E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by souteneur3190 on 2006-06-24
shall i just reinstall ubuntu?

---

### Post by digby on 2006-06-24
Try sudo apt-get --fix-missing

---

### Post by souteneur3190 on 2006-06-24
that doesnt do anything, i dont have synaptic installed

---

### Post by gatekeeper on 2006-06-24
If you want a GUI interface for your package management, I personally would use Synaptic. If you have got a broken package, it will tell you, you can then uninstall it, or add the additional dependencies if you know what they are, then reinstall your package.

---

### Post by digby on 2006-06-24
Does that mean you tried that command and it did nothing?  The presence of synaptic is really irrelevant at this point.

What was the output when you ran it?

---

### Post by souteneur3190 on 2006-06-24
apt 0.6.43.3ubuntu2 for linux i386 compiled on Apr 18 2006 19:46:38
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to continue if the integrity check fails
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
malubankudi@DellDesktop:~$

---

### Post by souteneur3190 on 2006-06-24
scim-gtk2-immodule

that is the brocken package...and i dont kno what to do now...

---

### Post by souteneur3190 on 2006-06-24
im going to try to delete this manually...

---

### Post by souteneur3190 on 2006-06-24
wow to make this even more complicated it has no installed files.

---

### Post by souteneur3190 on 2006-06-24
i found the solution thanks guys.

---

### Post by pihl on 2006-10-06
Care to share your solution? I have the same problem as you.

---

