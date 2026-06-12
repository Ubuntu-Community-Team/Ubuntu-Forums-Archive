---
title: "likewise-open versions and CIFS support"
date: 2012-07-05
forum: General Help
---

### Post by bandken on 2012-07-05
Hi all,

I'm trying to get the CIFS server working in likewise-open.  I've found this set of instructions and everything seems to work until I try to connect ([http://www.likewise.com/resources/documentation_library/manuals/cifs/likewise-cifs-smb-file-server-guide.html#id2765992):](http://www.likewise.com/resources/documentation_library/manuals/cifs/likewise-cifs-smb-file-server-guide.html#id2765992):)

```
1.6. Build and Configure a Standalone Likewise-CIFS Server

This section demonstrates how to build and configure a standalone instance of Likewise-CIFS from the command line. The following procedure assumes that you want to set up Likewise-CIFS on a Linux server to share files with Windows computers in a network without Active Directory. This procedure also assumes you know how to build Linux applications from their source code and then install them.

Download Likewise-CIFS from its open source git location:

$ git clone git://git.likewiseopen.org/

Download, build, and install the following tools. The tools listed are known to work, but earlier or later versions might work as well. Also, instead of downloading the tools, you might be able to install them on your platform with apt-get or some other means.

    http://ftp.gnu.org/gnu/autoconf/autoconf-2.65.tar.gz
    http://ftp.gnu.org/gnu/automake/automake-1.9.6.tar.gz
    http://ftp.gnu.org/gnu/libtool/libtool-2.2.6a.tar.gz
    http://pkgconfig.freedesktop.org/releases/pkg-config-0.23.tar.gz
    gcc --version 3.x or greater
Build Likewise-CIFS:

    $ cd likewise-open
    $ build/mkcomp --debug all
Install Likewise-CIFS:

    $ sudo su
    $ cd staging/install-root
    $ tar cf - . | (cd / && tar xvf -)
Make sure Samba is not running:

$ /etc/init.d/smb stop

Make sure SELinux is either disabled or set to permissive.

Make sure the ports required by Likewise are open. For a list of ports that Likewise uses, see the Likewise Open Installation and Administration Guide.

Configure Likewise Open:

    $ /etc/init.d/lwsmd start
    $ for i in /etc/likewise/*.reg; do /opt/likewise/bin/lwregshell upgrade $i; done
    $ /etc/init.d/lwsmd stop
    $ /etc/init.d/lwsmd start
    $ /opt/likewise/bin/lwsm start srvsvc
    $ /opt/likewise/bin/domainjoin-cli configure --enable nsswitch
Add a user account to the local Likewise provider database. In the following example, substitute the account name that you want for newuser.

    $ /opt/likewise/bin/lw-add-user --home /home/newuser --shell /bin/bash newuser
    Successfully added user newuser
Enable the user and set the password:

    $ /opt/likewise/bin/lw-mod-user --enable-user --set-password newuser
    New Password: **********
    Successfully modified user newuser
Look up new user's identity as follows. Substitute the value from the command hostname -s for the hostname. Keep in mind that Likewise truncates a hostname longer than 15 characters to the first 15 characters of the string.

    % id hostname\\newuser
    uid=2000(HOSTNAME\newuser) gid=1800(HOSTNAME\Likewise Users)   
    groups=1800(HOSTNAME\Likewise Users) 
    context=system_u:system_r:unconfined_t:s0
Make a CIFS directory for the user:

    mkdir /lwcifs/newuser
    chown 2000:1800 /lwcifs/newuser
From a Windows computer, map the Likewise-CIFS drive share:

     Computer->Map Network Drive...
     Folder: \\IP_hostname\c$
     Click "Finish"
     Username: hostname\newuser
     Password: user_password

```

The last step fails when I try to connect.  I've tried with Windows XP Pro and Windows 7 Pro.  The rest of the directions only appear to work for version 5.4 (the one that shipped with 10.04).  For 12.04, version 6.1 is the only one available and it doesn't appear to have the srvsvc module mentioned in these instructions.  Is CIFS support dropped in the 6.1 version of likewise-open?

---

