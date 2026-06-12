---
title: "Ubuntu - active directory - ldap - cached user login is slow"
date: 2010-12-30
forum: General Help
---

### Post by skinnyquiver on 2010-12-30
Below are the steps that i used to get to the point where I currently am at. They all work but when i try to login after removing the network cable from the test computer it is able to login as a cached user but this process is slow as in it takes over 10 minutes to get from the username screen to the password screen slow.

The question is how can i get the cached users to be able to login without the system hanging

You will find that i put this in a very script like fashion because it is easier 

###############
#Time sync goes here

########################################
####add server hostname to host file####
########################################
echo "
#added by domain authencation script
192.168.11.100     testdomain testdomain.com" >> /etc/hosts

#######################
###Kerberos############
#######################

apt-get install krb5-admin-server krb5-kdc krb5-config krb5-user krb5-clients krb5-rsh-server -y

echo "[libdefaults]
default_realm = TESTDOMAIN.COM

# Here, we specify the kdc and admin server for the realm
# TESTDOMAIN.COM
[realms]
TESTDOMAIN.COM = {
  kdc = testdomain.com
  admin_server = testdomain.com
}

# This informs the kdc of which hosts it should consider part of the
# TESTDOMAIN.COM realm
[domain_realm]
testdomain.com = TESTDOMAIN.COM
.testdomain.com = TESTDOMAIN.COM

# I disable kerberos 4 compatibility altogether.  I understand it had
# some real security issues.  I don't know if this is important here,
# but, it doesn't hurt in my particular case (all clients on my network
# are kerberos 5 compatible).
[login]
krb4_convert = false
krb4_get_tickets = false" > /etc/krb5.conf

#kdb5_util create -s
#for script in /etc/init.d/krb5*; do $script restart; done

#################
####LDAP#########
#################
sudo apt-get install ldap-auth-client libpam-krb5 krb5-user libpam-foreground libsasl2-modules-gssapi-mit -y

#fill out the authencation options
#yes make root a domain admin
#yes it needs the extra auth

echo "host 192.168.11.100
base dc=TESTDOMAIN,dc=COM
uri ldap://testdomain.com/
rootbinddn [email]Administrator@testdomain.com[/email]
#binddn [email]binddnuser@testdomain.com[/email]
binddn cn=binddnuser,cn=users,dc=testdomain,dc=com
bindpw B\!nddnuser
scope sub
ssl no
nss_base_passwd dc=testdomain,dc=com?sub
nss_base_shadow dc=testdomain,dc=com?sub
nss_base_group dc=testdomain,dc=com?sub?&(objectCategory=group)(gidnumber=*)
nss_map_objectclass posixAccount user
nss_map_objectclass shadowAccount user
nss_map_objectclass posixGroup group
nss_map_attribute gecos cn
nss_map_attribute homeDirectory unixHomeDirectory
nss_map_attribute uniqueMember member
nss_initgroups_ignoreusers avahi,avahi-autoipd,backup,bin,couchdb,daemon,games,gdm,gnats,haldaemon,hplip,irc,kernoops,libuuid,list,lp,mail,man,messagebus,news,proxy,pulse,root,rtkit,saned,speech-dispatcher,sshd,statd,sync,sys,syslog,usbmux,uucp,vboxadd,www-data" > /etc/ldap.conf
cat /etc/ldap.conf | sed 's:\\::' > /etc/ldap.conf1
rm /etc/ldap.conf
mv /etc/ldap.conf1 /etc/ldap.conf

####################
####PAM#############
####################

mkdir /etc/auth-client-config/
mkdir /etc/auth-client-config/profile.d/
echo "[krb5ldap]
nss_passwd=passwd: files ldap
nss_group=group: files ldap
nss_shadow=shadow: files ldap
nss_netgroup=netgroup: files ldap
pam_auth=auth       sufficient   pam_krb5.so
         auth       required     pam_unix.so nullok_secure use_first_pass
pam_account=account    sufficient   pam_krb5.so
            account    required     pam_unix.so
pam_password=password   sufficient   pam_krb5.so
             password   required     pam_unix.so nullok obscure min=4 max=8 md5
pam_session=session    required     pam_unix.so
            session    required     pam_mkhomedir.so skel=/etc/skel/
            session    optional     pam_krb5.so
            session    optional     pam_foreground.so

[krb5ldap.cached]
nss_passwd=passwd: files ldap [NOTFOUND=return] db
nss_group=group: files ldap [NOTFOUND=return] db
nss_shadow=shadow: files ldap
nss_netgroup=netgroup: files ldap
pam_auth=auth   required       pam_env.so
         auth   sufficient     pam_unix.so likeauth nullok
         auth   [default=ignore success=1 service_err=reset] pam_krb5.so use_first_pass
         auth   [default=die success=done] pam_ccreds.so action=validate use_first_pass
         auth   sufficient pam_ccreds.so action=store use_first_pass
         auth   required        pam_deny.so
pam_account=account    sufficient   pam_krb5.so
            account    required     pam_unix.so
pam_password=password   sufficient   pam_krb5.so
             password   required     pam_unix.so nullok obscure min=4 max=8 md5
pam_session=session    required     pam_unix.so
            session    required     pam_mkhomedir.so skel=/etc/skel/
            session    optional     pam_krb5.so
            session    optional     pam_foreground.so" > /etc/auth-client-config/profile.d/krb-auth-config

#sudo auth-client-config -a -p krb5ldap

############################
###PAM Cached credentials###
############################

apt-get install nss-updatedb libnss-db libpam-cracklib libpam-ccreds -y
nss_updatedb ldap
auth-client-config -a -p krb5ldap.cached

#echo "account     [user_unknown=ignore authinfo_unavail=ignore default=done] pa$
#account     [user_unknown=ignore authinfo_unavail=ignore default=done] pam_ldap$
#account     required       pam_permit.so" >> /etc/pam.d/common-account

#cat /etc/pam.d/common-session | sed 's:session.*fore:#session    optional     pam_fore:' > /etc/pam.d/common-sessiontmp
#rm /etc/pam.d/common-session
#mv /etc/pam.d/common-sessiontmp /etc/pam.d/common-session

#echo "

#timelimit 5
#bind_timelimit 5
#bind_policy soft" >> /etc/ldap.conf

###################################
###create cron job to sync users###
###################################
echo '#!/bin/sh'               | sudo tee    /etc/cron.daily/upd-local-nss-db
echo `which nss_updatedb` ldap | sudo tee -a /etc/cron.daily/upd-local-nss-db
sudo chmod +x /etc/cron.daily/upd-local-nss-db

---

### Post by luvshines on 2011-01-02
Are you talking about 'nscd' cache ?
Though I haven't used AD + LDAP but you can try using 'bind policy soft' option in /etc/ldap.conf so that nss returns quickly instead of going in for exponential sleep trying to connect to LDAP server

---

### Post by skinnyquiver on 2011-01-03
no i do not think that this is using nscd because i am using kerberos 
but it is whatever module libpam-ccreds uses

I tried setting bind_policy soft in /etc/ldap.conf and there was no change here is the output of the auth log


Jan  3 09:28:54 adaptive-desktop gdm-simple-slave[888]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:28:54 adaptive-desktop gdm-simple-slave[888]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100/: Can't contact LDAP server
Jan  3 09:28:54 adaptive-desktop gdm-simple-slave[888]: nss_ldap: could not search LDAP server - Server is unavailable
Jan  3 09:28:59 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:28:59 adaptive-desktop gdm-session-worker[1360]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100: Can't contact LDAP server
Jan  3 09:29:04 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:29:04 adaptive-desktop gdm-session-worker[1360]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100/: Can't contact LDAP server
Jan  3 09:29:04 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not search LDAP server - Server is unavailable
Jan  3 09:29:09 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:29:09 adaptive-desktop gdm-session-worker[1360]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100: Can't contact LDAP server
Jan  3 09:29:14 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:29:14 adaptive-desktop gdm-session-worker[1360]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100/: Can't contact LDAP server
Jan  3 09:29:14 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not search LDAP server - Server is unavailable
Jan  3 09:29:19 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:29:19 adaptive-desktop gdm-session-worker[1360]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100: Can't contact LDAP server
Jan  3 09:29:24 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:29:24 adaptive-desktop gdm-session-worker[1360]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100/: Can't contact LDAP server
Jan  3 09:29:24 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not search LDAP server - Server is unavailable
Jan  3 09:29:29 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:29:29 adaptive-desktop gdm-session-worker[1360]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100: Can't contact LDAP server
Jan  3 09:29:34 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:29:34 adaptive-desktop gdm-session-worker[1360]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100/: Can't contact LDAP server
Jan  3 09:29:34 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not search LDAP server - Server is unavailable
Jan  3 09:29:34 adaptive-desktop gdm-session-worker[1360]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "rhardy"
Jan  3 09:29:39 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:29:39 adaptive-desktop gdm-session-worker[1360]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100: Can't contact LDAP server
Jan  3 09:29:44 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:29:44 adaptive-desktop gdm-session-worker[1360]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100/: Can't contact LDAP server
Jan  3 09:29:44 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not search LDAP server - Server is unavailable
Jan  3 09:30:26 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:30:26 adaptive-desktop gdm-session-worker[1360]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100: Can't contact LDAP server
Jan  3 09:30:31 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:30:31 adaptive-desktop gdm-session-worker[1360]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100/: Can't contact LDAP server
Jan  3 09:30:31 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not search LDAP server - Server is unavailable
Jan  3 09:30:36 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:30:36 adaptive-desktop gdm-session-worker[1360]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100: Can't contact LDAP server
Jan  3 09:30:41 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:30:41 adaptive-desktop gdm-session-worker[1360]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100/: Can't contact LDAP server
Jan  3 09:30:41 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not search LDAP server - Server is unavailable
Jan  3 09:30:41 adaptive-desktop gdm-session-worker[1360]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=rhardy
Jan  3 09:31:02 adaptive-desktop gdm-session-worker[1360]: pam_krb5(gdm:auth): authentication failure; logname=rhardy uid=0 euid=0 tty=:0 ruser= rhost=
Jan  3 09:31:07 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:31:07 adaptive-desktop gdm-session-worker[1360]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100: Can't contact LDAP server
Jan  3 09:31:12 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:31:12 adaptive-desktop gdm-session-worker[1360]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100/: Can't contact LDAP server
Jan  3 09:31:12 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not search LDAP server - Server is unavailable
Jan  3 09:31:17 adaptive-desktop gdm-simple-slave[888]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:31:17 adaptive-desktop gdm-simple-slave[888]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100: Can't contact LDAP server
Jan  3 09:31:22 adaptive-desktop gdm-simple-slave[888]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:31:22 adaptive-desktop gdm-simple-slave[888]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100/: Can't contact LDAP server
Jan  3 09:31:22 adaptive-desktop gdm-simple-slave[888]: nss_ldap: could not search LDAP server - Server is unavailable
Jan  3 09:31:27 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:31:27 adaptive-desktop gdm-session-worker[1360]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100: Can't contact LDAP server
Jan  3 09:31:32 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:31:32 adaptive-desktop gdm-session-worker[1360]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100/: Can't contact LDAP server
Jan  3 09:31:32 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not search LDAP server - Server is unavailable
Jan  3 09:31:37 adaptive-desktop gdm-session-worker[1360]: nss_ldap: could not connect to any LDAP server as [email]Administrator@testdomain.com[/email] - Can't contact LDAP server
Jan  3 09:31:37 adaptive-desktop gdm-session-worker[1360]: nss_ldap: failed to bind to LDAP server ldap://192.168.11.100: Can't contact LDAP server

after this it says logged in with cached credentials

---

### Post by skinnyquiver on 2011-01-05
I got another set of eyes to look at this.

We have narrowed the problem down to just the nsswitch.conf file. The problem is that when ever it wants to lookup a group or a user the system tries to connect to the ldap server that is disconnected this is what causes the hang.

If i remove ldap from the nsswitch.conf file it works to authenticate the cached user.

But then no-longer goes to ldap for user information so i i try to login with a user that is not in the cache already the login fails.

---

### Post by luvshines on 2011-01-07
Well I think it should have worked with bind_policy soft
Did you also set bind_timelimit 5 along with bind_policy ?

---

### Post by skinnyquiver on 2011-01-10
Yes i tried both of those. In my tests i decided to try it without libpam-ccreds and use nscd. I am having a few other issues with nscd but I will be working those out. I will post my final script as a script for those who want an easy way to install this.

---

### Post by skinnyquiver on 2011-01-11
Below is my script to add krb5/ldap to your system with cached user accounts

There are 2 known issues with this that i am working out
1.) when not connected to ldap the gnome screen saver locks
2.) ldap.secret is in plain text

Any help on these would be nice.

Please if you improve this script post it back here so i can utilize it.

Thanks,


#! /bin/bash

# This script has been created after looking into several sites 
# and not seeing a effective way to authenticate with cashing and uid/gid
# being pulled from the server 
#
# This script was setup to work with ubuntu 10.04 and win server 2008
# In order for this script to work you need to install the nix schema on
# your windows server.
#
# on this script only change settings on the set variables section
#
# Created by Raymond Hardy

########################
##### set variables ####
########################
dmserverip="192.168.11.100"
dmservernm="testdomain"
dmserverpx="com"
rootbinduser="Administrator"
guestbinduser="binddnuser"
guestbindcontainer="users"
guestbindpw="B\!nddnuser"
ntpserver="pool.ntp.org"

#################################################
###set case all upper on servernm and serverpx###
#################################################

dmservernmcase=$(echo $dmservernm|tr '[:lower:]' '[:upper:]')
dmserverpxcase=$(echo $dmserverpx|tr '[:lower:]' '[:upper:]')

##########################
###Check for root user####
##########################

if [[ $EUID -ne 0 ]]; then
        echo "This script must be run as root" 1>&2
        exit 1
fi

##################
####Time sync ####
##################
apt-get install ntpdate
ntpdate $ntpserver

########################################
####add server hostname to host file####
########################################
echo "
#added by domain authencation script
$dmserverip     $dmservernm $dmservernm.$dmserverpx" >> /etc/hosts

#######################
###Kerberos############
#######################
apt-get install krb5-admin-server krb5-kdc krb5-config krb5-user krb5-clients krb5-rsh-server -y

echo "[libdefaults]
default_realm = $dmservernmcase.$dmserverpxcase
[realms]
$dmservernmcase.$dmserverpxcase = {
  kdc = $dmservernm.$dmserverpx
  admin_server = $dmservernm.$dmserverpx
}
[domain_realm]
$dmservernm.$dmserverpx = $dmservernmcase.$dmserverpxcase
.$dmservernm.$dmserverpx = $dmservernmcase.$dmserverpxcase
[login]
krb4_convert = false
krb4_get_tickets = false" > /etc/krb5.conf

#kdb5_util create -s
#for script in /etc/init.d/krb5*; do $script restart; done

#################
####LDAP#########
#################
sudo apt-get install ldap-auth-client libpam-krb5 krb5-user libpam-foreground libsasl2-modules-gssapi-mit -y

echo "host $dmserverip
base dc=$dmservernmcase,dc=$dmserverpxcase
uri ldaps://$dmservernm.$dmserverpx/
rootbinddn $rootbinduser@$dmservernm.$dmserverpx
binddn "cn=$guestbinduser,cn=$guestbindcontainer,dc=$dmservernm,dc=$dmserverpx"
bindpw $guestbindpw
scope sub
ssl no
nss_base_passwd dc=$dmservernm,dc=$dmserverpx?sub
nss_base_shadow dc=$dmservernm,dc=$dmserverpx?sub
nss_base_group dc=$dmservernm,dc=$dmserverpx?sub?&(objectCategory=group)(gidnumber=*)
nss_map_objectclass posixAccount user
nss_map_objectclass shadowAccount user
nss_map_objectclass posixGroup group
nss_map_attribute gecos cn
nss_map_attribute homeDirectory unixHomeDirectory
nss_map_attribute uniqueMember member
nss_initgroups_ignoreusers avahi,avahi-autoipd,backup,bin,couchdb,daemon,games,gdm,gnats,haldaemon,hplip,irc,kernoops,libuuid,list,lp,mail,man,messagebus,news,proxy,pulse,root,rtkit,saned,speech-dispatcher,sshd,statd,sync,sys,syslog,usbmux,uucp,vboxadd,www-data
bind_policy soft
bind_timelimit 5" > /etc/ldap.conf
cat /etc/ldap.conf | sed 's:\\::' > /etc/ldap.conf1
rm /etc/ldap.conf
mv /etc/ldap.conf1 /etc/ldap.conf

####################
####PAM#############
####################

mkdir /etc/auth-client-config/
mkdir /etc/auth-client-config/profile.d/
echo "[krb5ldap.cached]
nss_passwd=passwd: files ldap
nss_group=group: files ldap
nss_shadow=shadow: files ldap
nss_netgroup=netgroup: files ldap
pam_auth=auth   required       pam_env.so
         auth   sufficient     pam_unix.so likeauth nullok
         auth   [default=ignore success=1 service_err=reset] pam_krb5.so use_first_pass
         auth   [default=die success=done] pam_ccreds.so action=validate use_first_pass
         auth   sufficient pam_ccreds.so action=store use_first_pass
         auth   required        pam_deny.so
pam_account=account    sufficient   pam_krb5.so
            account    required     pam_unix.so
pam_password=password   sufficient   pam_krb5.so
             password   required     pam_unix.so nullok obscure min=4 max=8 md5
pam_session=session    required     pam_unix.so
            session    required     pam_mkhomedir.so skel=/etc/skel/
            session    optional     pam_krb5.so
            session    optional     pam_foreground.so" > /etc/auth-client-config/profile.d/krb-auth-config

############################
###PAM Cached credentials###
############################

apt-get install nss-updatedb libnss-db libpam-cracklib libpam-ccreds nscd -y
nss_updatedb ldap
auth-client-config -a -p krb5ldap.cached

###################################
###create cron job to sync users###
###################################

echo '#!/bin/sh'               | sudo tee    /etc/cron.daily/upd-local-nss-db
echo `which nss_updatedb` ldap | sudo tee -a /etc/cron.daily/upd-local-nss-db
sudo chmod +x /etc/cron.daily/upd-local-nss-db

---

### Post by skinnyquiver on 2011-01-19
My final script
if you wish to join the domain using winbind for samba authencations just use this script modify your smb.conf according to [http://www.onnoot.com/wiki/how_to_join_ubuntu_samba_to_a_windows_2003_active_directory_domain](http://www.onnoot.com/wiki/how_to_join_ubuntu_samba_to_a_windows_2003_active_directory_domain)
then run the net ads join -U administrator command

Hope this script helps others as much as it has helped me.

This will allow you to have the UIDs and GIDs set server side

I am using windows server 2008 for this setup with the unix schema installed


#! /bin/bash

# This script has been created after looking into several sites
# and not seeing a effective way to authenticate with cashing and uid/gid
# being pulled from the server
#
# This script was setup to work with ubuntu 10.04 and win server 2008
# In order for this script to work you need to install the nix schema on
# your windows server.
#
# on this script only change settings on the set variables section
#
# Created by Raymond Hardy

########################
##### set variables ####
########################
dmserverip="192.168.11.100"
dmservernm="testdomain"
dmserverpx="com"
dcname="DC1"
rootbinduser="binddnuser"
guestbinduser="binddnuser"
guestbindcontainer="users"
guestbindpw="B\!nddnuser"
rootbindpw="B\!nddnuser"
ntpserver="pool.ntp.org"


#################################################
###set case all upper on servernm and serverpx###
#################################################

dmservernmcase=$(echo $dmservernm|tr '[:lower:]' '[:upper:]')
dmserverpxcase=$(echo $dmserverpx|tr '[:lower:]' '[:upper:]')

##########################
###Check for root user####
##########################

if [[ $EUID -ne 0 ]]; then
        echo "This script must be run as root" 1>&2
        exit 1
fi

#####################
### update system ###
#####################
apt-get update -y

##################
####Time sync ####
##################
apt-get install ntpdate
ntpdate $ntpserver

########################################
####add server hostname to host file####
########################################
echo "
#added by domain authencation script
$dmserverip     $dmservernm $dmservernm.$dmserverpx" >> /etc/hosts

#######################
###Kerberos############
#######################
apt-get install krb5-admin-server krb5-kdc krb5-config krb5-user krb5-clients krb5-rsh-server -y

echo "[libdefaults]
default_realm = $dmservernmcase.$dmserverpxcase
[realms]
$dmservernmcase.$dmserverpxcase = {
  kdc = $dcname.$dmservernm.$dmserverpx
  admin_server = $dcname.$dmservernm.$dmserverpx
}
[domain_realm]
$dmservernm.$dmserverpx = $dcname.$dmservernmcase.$dmserverpxcase
.$dmservernm.$dmserverpx = $dcname.$dmservernmcase.$dmserverpxcase
[login]
krb4_convert = false
krb4_get_tickets = false" > /etc/krb5.conf

#################
####LDAP#########
#################
sudo apt-get install ldap-auth-client libpam-krb5 krb5-user libpam-foreground libsasl2-modules-gssapi-mit -y

echo "host $dmserverip
base dc=$dmservernmcase,dc=$dmserverpxcase
uri ldaps://$dmservernm.$dmserverpx/
rootbinddn $rootbinduser@$dmservernm.$dmserverpx
binddn "cn=$guestbinduser,cn=$guestbindcontainer,dc=$dmservernm,dc=$dmserverpx"
bindpw $guestbindpw
scope sub
ssl no
nss_base_passwd dc=$dmservernm,dc=$dmserverpx?sub
nss_base_shadow dc=$dmservernm,dc=$dmserverpx?sub
nss_base_group dc=$dmservernm,dc=$dmserverpx?sub?&(objectCategory=group)(gidnumber=*)
nss_map_objectclass posixAccount user
nss_map_objectclass shadowAccount user
nss_map_objectclass posixGroup group
nss_map_attribute gecos cn
nss_map_attribute homeDirectory unixHomeDirectory
nss_map_attribute uniqueMember member
nss_initgroups_ignoreusers avahi,avahi-autoipd,backup,bin,couchdb,daemon,games,gdm,gnats,haldaemon,hplip,irc,kernoops,libuuid,list,lp,mail,man,messagebus,news,proxy,pulse,root,rtkit,saned,speech-dispatcher,sshd,statd,sync,sys,syslog,usbmux,uucp,vboxadd,www-data
bind_policy soft
bind_timelimit 5" > /etc/ldap.conf
cat /etc/ldap.conf | sed 's:\\::' > /etc/ldap.conf1
rm /etc/ldap.conf
mv /etc/ldap.conf1 /etc/ldap.conf
echo "$rootbindpw" > /etc/ldap.secret
cat /etc/ldap.secret | sed 's:\\::' > /etc/ldap.secret1
rm /etc/ldap.secret
mv /etc/ldap.secret1 /etc/ldap.secret

####################
####PAM#############
####################

mkdir /etc/auth-client-config/
mkdir /etc/auth-client-config/profile.d/
echo "[krb5ldap.cached]
nss_passwd=passwd: files ldap
nss_group=group: files ldap
nss_shadow=shadow: files ldap
nss_netgroup=netgroup: files ldap
pam_auth=auth   required       pam_env.so
         auth   sufficient     pam_unix.so likeauth nullok
         auth   [default=ignore success=1 service_err=reset] pam_krb5.so use_first_pass
         auth   [default=die success=done] pam_ccreds.so action=validate use_first_pass
         auth   sufficient pam_ccreds.so action=store use_first_pass
         auth   required        pam_deny.so
pam_account=account    sufficient   pam_krb5.so
            account    required     pam_unix.so
pam_password=password   sufficient   pam_krb5.so
             password   required     pam_unix.so nullok obscure min=4 max=8 md5
pam_session=session    required     pam_unix.so
            session    required     pam_mkhomedir.so skel=/etc/skel/
            session    optional     pam_krb5.so
            session    optional     pam_foreground.so" > /etc/auth-client-config/profile.d/krb-auth-config

############################
###PAM Cached credentials###
############################

apt-get install nss-updatedb libnss-db libpam-cracklib libpam-ccreds nscd -y
nss_updatedb ldap
auth-client-config -a -p krb5ldap.cached

###################################
###create cron job to sync users###
###################################

echo '#!/bin/sh'               | sudo tee    /etc/cron.daily/upd-local-nss-db
echo `which nss_updatedb` ldap | sudo tee -a /etc/cron.daily/upd-local-nss-db
sudo chmod +x /etc/cron.daily/upd-local-nss-db

apt-get install nscd -y

---

### Post by skinnyquiver on 2011-01-19
My final script
if you wish to join the domain using winbind for samba authencations just use this script modify your smb.conf according to [http://www.onnoot.com/wiki/how_to_join_ubuntu_samba_to_a_windows_2003_active_directory_domain](http://www.onnoot.com/wiki/how_to_join_ubuntu_samba_to_a_windows_2003_active_directory_domain)
then run the net ads join -U administrator command

Hope this script helps others as much as it has helped me.

This will allow you to have the UIDs and GIDs set server side

I am using windows server 2008 for this setup with the unix schema installed


#! /bin/bash

# This script has been created after looking into several sites
# and not seeing a effective way to authenticate with cashing and uid/gid
# being pulled from the server
#
# This script was setup to work with ubuntu 10.04 and win server 2008
# In order for this script to work you need to install the nix schema on
# your windows server.
#
# on this script only change settings on the set variables section
#
# Created by Raymond Hardy

########################
##### set variables ####
########################
dmserverip="192.168.11.100"
dmservernm="testdomain"
dmserverpx="com"
dcname="DC1"
rootbinduser="binddnuser"
guestbinduser="binddnuser"
guestbindcontainer="users"
guestbindpw="B\!nddnuser"
rootbindpw="B\!nddnuser"
ntpserver="pool.ntp.org"


#################################################
###set case all upper on servernm and serverpx###
#################################################

dmservernmcase=$(echo $dmservernm|tr '[:lower:]' '[:upper:]')
dmserverpxcase=$(echo $dmserverpx|tr '[:lower:]' '[:upper:]')

##########################
###Check for root user####
##########################

if [[ $EUID -ne 0 ]]; then
        echo "This script must be run as root" 1>&2
        exit 1
fi

#####################
### update system ###
#####################
apt-get update -y

##################
####Time sync ####
##################
apt-get install ntpdate
ntpdate $ntpserver

########################################
####add server hostname to host file####
########################################
echo "
#added by domain authencation script
$dmserverip     $dmservernm $dmservernm.$dmserverpx" >> /etc/hosts

#######################
###Kerberos############
#######################
apt-get install krb5-admin-server krb5-kdc krb5-config krb5-user krb5-clients krb5-rsh-server -y

echo "[libdefaults]
default_realm = $dmservernmcase.$dmserverpxcase
[realms]
$dmservernmcase.$dmserverpxcase = {
  kdc = $dcname.$dmservernm.$dmserverpx
  admin_server = $dcname.$dmservernm.$dmserverpx
}
[domain_realm]
$dmservernm.$dmserverpx = $dcname.$dmservernmcase.$dmserverpxcase
.$dmservernm.$dmserverpx = $dcname.$dmservernmcase.$dmserverpxcase
[login]
krb4_convert = false
krb4_get_tickets = false" > /etc/krb5.conf

#################
####LDAP#########
#################
sudo apt-get install ldap-auth-client libpam-krb5 krb5-user libpam-foreground libsasl2-modules-gssapi-mit -y

echo "host $dmserverip
base dc=$dmservernmcase,dc=$dmserverpxcase
uri ldaps://$dmservernm.$dmserverpx/
rootbinddn $rootbinduser@$dmservernm.$dmserverpx
binddn "cn=$guestbinduser,cn=$guestbindcontainer,dc=$dmservernm,dc=$dmserverpx"
bindpw $guestbindpw
scope sub
ssl no
nss_base_passwd dc=$dmservernm,dc=$dmserverpx?sub
nss_base_shadow dc=$dmservernm,dc=$dmserverpx?sub
nss_base_group dc=$dmservernm,dc=$dmserverpx?sub?&(objectCategory=group)(gidnumber=*)
nss_map_objectclass posixAccount user
nss_map_objectclass shadowAccount user
nss_map_objectclass posixGroup group
nss_map_attribute gecos cn
nss_map_attribute homeDirectory unixHomeDirectory
nss_map_attribute uniqueMember member
nss_initgroups_ignoreusers avahi,avahi-autoipd,backup,bin,couchdb,daemon,games,gdm,gnats,haldaemon,hplip,irc,kernoops,libuuid,list,lp,mail,man,messagebus,news,proxy,pulse,root,rtkit,saned,speech-dispatcher,sshd,statd,sync,sys,syslog,usbmux,uucp,vboxadd,www-data
bind_policy soft
bind_timelimit 5" > /etc/ldap.conf
cat /etc/ldap.conf | sed 's:\\::' > /etc/ldap.conf1
rm /etc/ldap.conf
mv /etc/ldap.conf1 /etc/ldap.conf
echo "$rootbindpw" > /etc/ldap.secret
cat /etc/ldap.secret | sed 's:\\::' > /etc/ldap.secret1
rm /etc/ldap.secret
mv /etc/ldap.secret1 /etc/ldap.secret

####################
####PAM#############
####################

mkdir /etc/auth-client-config/
mkdir /etc/auth-client-config/profile.d/
echo "[krb5ldap.cached]
nss_passwd=passwd: files ldap
nss_group=group: files ldap
nss_shadow=shadow: files ldap
nss_netgroup=netgroup: files ldap
pam_auth=auth   required       pam_env.so
         auth   sufficient     pam_unix.so likeauth nullok
         auth   [default=ignore success=1 service_err=reset] pam_krb5.so use_first_pass
         auth   [default=die success=done] pam_ccreds.so action=validate use_first_pass
         auth   sufficient pam_ccreds.so action=store use_first_pass
         auth   required        pam_deny.so
pam_account=account    sufficient   pam_krb5.so
            account    required     pam_unix.so
pam_password=password   sufficient   pam_krb5.so
             password   required     pam_unix.so nullok obscure min=4 max=8 md5
pam_session=session    required     pam_unix.so
            session    required     pam_mkhomedir.so skel=/etc/skel/
            session    optional     pam_krb5.so
            session    optional     pam_foreground.so" > /etc/auth-client-config/profile.d/krb-auth-config

############################
###PAM Cached credentials###
############################

apt-get install nss-updatedb libnss-db libpam-cracklib libpam-ccreds nscd -y
nss_updatedb ldap
auth-client-config -a -p krb5ldap.cached

###################################
###create cron job to sync users###
###################################

echo '#!/bin/sh'               | sudo tee    /etc/cron.daily/upd-local-nss-db
echo `which nss_updatedb` ldap | sudo tee -a /etc/cron.daily/upd-local-nss-db
sudo chmod +x /etc/cron.daily/upd-local-nss-db

apt-get install nscd -y

---

### Post by luvshines on 2011-01-21
A suggestion for the rootbindpw:```

echo $rootbindpw > /etc/ldap.secret
sed -i 's:\\::g' /etc/ldap.secret # Avoid making ldap.secret1, an extra file
chmod 0600 /etc/ldap.secret # To make it secure from world :)
```

---

