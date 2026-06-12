---
title: "OpenLDAP Nightmare ubuntu 10.04 and 10.10"
date: 2010-10-31
forum: General Help
---

### Post by jabes69 on 2010-10-31
Pardon me if this is not in the right place...noob here to this forum.

I have been trying without absolutely no luck whatsoever to install OpenLDAP on absolutely fresh installs of Ubuntu Server 10.04 and 10.10. I have followed every possible HOWTO that can be found on a google search and in the Ubuntu Community and Server Guide pages. Most HOWTO's outside of Ubuntu Community and Server Guides offer a moment to test your configurations and with each test using ssh to the localhost and ssh from clients back to the tld of the LDAP server I am getting permission denied.

Has anyone reading this successfully setup an OpenLDAP server on either 10.04 or 10.10? If so would you please send me some direction and details? Have been at this now for 3 weeks with no success and quite frankly I have not read of many successes out there in the various forums, here and elsewhere.

I am desperate for some success and any help from anyone would be greatly appreciated and come with free beer from the Avery Tap Room if ever you are in Colorado, heck - I don't care where you are a free case of your favorite brew to anyone who provides some real help.

Thanks!!

---

### Post by luvshines on 2010-10-31
> **jabes69 said:**
> Pardon me if this is not in the right place...noob here to this forum.

I have been trying without absolutely no luck whatsoever to install OpenLDAP on absolutely fresh installs of Ubuntu Server 10.04 and 10.10. I have followed every possible HOWTO that can be found on a google search and in the Ubuntu Community and Server Guide pages. Most HOWTO's outside of Ubuntu Community and Server Guides offer a moment to test your configurations and with each test using ssh to the localhost and ssh from clients back to the tld of the LDAP server I am getting permission denied.

Has anyone reading this successfully setup an OpenLDAP server on either 10.04 or 10.10? If so would you please send me some direction and details? Have been at this now for 3 weeks with no success and quite frankly I have not read of many successes out there in the various forums, here and elsewhere.

I am desperate for some success and any help from anyone would be greatly appreciated and come with free beer from the Avery Tap Room if ever you are in Colorado, heck - I don't care where you are a free case of your favorite brew to anyone who provides some real help.

Thanks!!

Dude!! You sound desperate :D

You are stuck at ssh login or the LDAP server setup itself ?

---

### Post by jabes69 on 2010-11-01
I am very desperate. Hate to say that but it is what it is after 3 weeks of trying to find something, anything that works.

I am just trying to get LDAP installed and tested. I have used the Community docs to install and create the backend and frontend ldif's. I have done the ldapsearch to insure info has populated correctly for the user added in the frontend and all returns well. From there nearly every doc says that you should be able to test the "basic" config by ssh'ing using the newly added user and at that point, whether done from the localhost or another machine to the tld of the LDAP server I get "Permission Denied" and cannot login.

There is no tracking in the logs to follow and at this point I have literally followed 143 different howto's on this item from fresh install of Ubuntu Server 10.04 and 10.10 and still nothing - same error no matter where I turn. I am pulling out my hair and this is really needed. I am about to dump Ubuntu all together without some direction cuz at this point its worthless even as a free server.

Peace - JB
303-586-1434

---

### Post by jabes69 on 2010-11-01
Sorry Luvshines - I never really answered your question.

I believe the installation is done correctly - at least there are no errors return during the basic setup and config of the frontend and backend. 

sudo apt-get install slapd ldap-utils

I just cannot login to the installation via ssh or GUI. In ssh the error is "Permission Denied" while at the GUI from a Ubuntu Desktop Client "Authentication Failure".

I am at a complete loss. Any help/advice/direction would be greatly appreciated.

Peace - JB 
303-586-1434

---

### Post by luvshines on 2010-11-01
Can you do this and paste the output:
```

## Check LDAP in nsswitch.conf
cat /ets/nsswitch.conf | egrep "^passwd|^shadow|^group"

## Check PAM LDAP presence
cd /etc/pam.d
grep pam_ldap.so *

```

Also, amongst the 143 How-To's ;), did you ever hit this post ??
[http://ubuntuforums.org/showthread.php?t=1059297](http://ubuntuforums.org/showthread.php?t=1059297)

---

### Post by jabes69 on 2010-11-01
root@appm-ecot:/etc# cat /etc/nsswitch.conf | egrep "^passwd|^shadow|^group"
passwd:         files ldap
group:          files ldap
shadow:         files ldap
root@appm-ecot:/etc# 

root@appm-ecot:/etc# cd /etc/pam.d
root@appm-ecot:/etc/pam.d# grep pam_ldap.so *
root@appm-ecot:/etc/pam.d# 

Thanks Luvshines!

---

### Post by jabes69 on 2010-11-01
BTW - To get to a place to execute your requests a fresh install of ldap was done and this picks up with the config after its initial start.

Starting OpenLDAP: slapd.

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@appm-ecot:/home/flynt# ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=cosine,cn=schema,cn=config"

root@appm-ecot:/home/flynt# ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/inetorgperson.ldif
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=inetorgperson,cn=schema,cn=config"

root@appm-ecot:/home/flynt# ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/nis.ldif
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=nis,cn=schema,cn=config"

root@appm-ecot:/home/flynt# ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/misc.ldif
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=misc,cn=schema,cn=config"

root@appm-ecot:/home/flynt# ldapadd -Y EXTERNAL -H ldapi:/// -f backend.example.com.ldif
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=module,cn=config"

adding new entry "olcDatabase=hdb,cn=config"

root@appm-ecot:/home/flynt# sudo ldapadd -x -D cn=admin,dc=example,dc=com -W -f frontend.example.com.ldif
Enter LDAP Password: 
ldap_bind: Invalid credentials (49)
root@appm-ecot:/home/flynt# more backend.example.com.ldif
# Load dynamic backend modules
dn: cn=module,cn=config
objectClass: olcModuleList
cn: module
olcModulepath: /usr/lib/ldap
olcModuleload: back_hdb

# Database settings
dn: olcDatabase=hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcSuffix: dc=appm-ecot,dc=colorado,dc=edu
olcDbDirectory: /var/lib/ldap
olcRootDN: cn=admin,dc=appm-ecot,dc=colorado,dc=edu
olcRootPW: likeaflockofturtles
olcDbConfig: set_cachesize 0 2097152 0
olcDbConfig: set_lk_max_objects 1500
olcDbConfig: set_lk_max_locks 1500
olcDbConfig: set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcAccess: to attrs=userPassword by dn="cn=admin,dc=appm-ecot,dc=colorado,dc=edu" write by anonymous auth by self write by * non
e
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,dc=appm-ecot,dc=colorado,dc=edu" write by * read
root@appm-ecot:/home/flynt# sudo ldapadd -x -D cn=admin,dc=appm-ecot,dc=colorado,dc=edu -W -f frontend.example.com.ldif
Enter LDAP Password: 
adding new entry "dc=appm-ecot,dc=colorado,dc=edu"

adding new entry "cn=admin,dc=appm-ecot,dc=colorado,dc=edu"

adding new entry "ou=people,dc=appm-ecot,dc=colorado,dc=edu"

adding new entry "ou=groups,dc=appm-ecot,dc=colorado,dc=edu"

adding new entry "uid=jwolmer,ou=people,dc=appm-ecot,dc=colorado,dc=edu"

adding new entry "cn=staff,ou=groups,dc=appm-ecot,dc=colorado,dc=edu"

root@appm-ecot:/home/flynt#

---

### Post by luvshines on 2010-11-02
> **jabes69 said:**
> root@appm-ecot:/etc# cat /etc/nsswitch.conf | egrep "^passwd|^shadow|^group"
passwd:         files ldap
group:          files ldap
shadow:         files ldap
root@appm-ecot:/etc# 

root@appm-ecot:/etc# cd /etc/pam.d
root@appm-ecot:/etc/pam.d# grep pam_ldap.so *
root@appm-ecot:/etc/pam.d# 

Thanks Luvshines!

Since pam_ldap.so is missing completely, I doubt if it will work.
Did you have a look at #2 from the link I posted ? That explains what packages will provide the relevant modules and which pam files to modify

---

### Post by jabes69 on 2010-11-02
Yeah I've done all that "2nd Link" stuff and even that is upsetting because everywhere else I read that instead of libnss-ldap et. al. for 10.04 and 10.10 the recommended file end with 'ldapd'. Believe me, if I ever get this (and it looks like I have too cuz the client wont go to RHEL 5 with FedoraDS instead) I will write a very extensive HOWTO on this crape'! Right now though its just annoying as H*LL!!

Even after double checking all the common-* files your grep command still returns the same no output.

After yet another absolutely fresh install of Ubuntu 10.10 and following the Server Guide for OpenLDAP 10.10 - right after basic configuration and /etc/init.d/slapd restart - an ldapsearch -x  or ldapsearch -x -h <servername> returns this little nugget: ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

At this point I would love a recommendation on any version of Ubuntu KNOWN to actually run OpenLDAP. I am absolutely blown away by the immense quantity of horrible failing advice and HOWTO's out there on this topic. Its shameful!! Bug #1 is in full effect solely because of this kind of headache. If Ubuntu cant get this right it should just stop and take a long hard look at itself and maybe just stop offering a server build all together.

---

### Post by jabes69 on 2010-11-02
Sorry for sounding so darned negative but this goes far beyond ridiculous. The stack of Bugs and various other bits of misinformation on this whole OpenLDAP thing coming straight from Ubuntu Community Docs shows a complacent "cut and paste" attitude on the part of those responsible for testing and documentation.

---

### Post by jabes69 on 2010-11-02
And thanks Luvshine - you've been the one bright spot in all this darkness and I appreciate it!!

---

### Post by luvshines on 2010-11-02
> **jabes69 said:**
> Yeah I've done all that "2nd Link" stuff and even that is upsetting because everywhere else I read that instead of libnss-ldap et. al. for 10.04 and 10.10 the recommended file end with 'ldapd'. Believe me, if I ever get this (and it looks like I have too cuz the client wont go to RHEL 5 with FedoraDS instead) I will write a very extensive HOWTO on this crape'! Right now though its just annoying as H*LL!!

Even after double checking all the common-* files your grep command still returns the same no output.

After yet another absolutely fresh install of Ubuntu 10.10 and following the Server Guide for OpenLDAP 10.10 - right after basic configuration and /etc/init.d/slapd restart - an ldapsearch -x  or ldapsearch -x -h <servername> returns this little nugget: ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

At this point I would love a recommendation on any version of Ubuntu KNOWN to actually run OpenLDAP. I am absolutely blown away by the immense quantity of horrible failing advice and HOWTO's out there on this topic. Its shameful!! Bug #1 is in full effect solely because of this kind of headache. If Ubuntu cant get this right it should just stop and take a long hard look at itself and maybe just stop offering a server build all together.

Oops!! Back to square one ? Non working LDAP server ?
You wrote that after following #2, grep pam_ldap.so still doesn't return anything. How come ??:confused:
See if LDAP server is running:
```
ps aux | grep slapd 
```

---

### Post by jabes69 on 2010-11-02
Another day and yet another fresh build of Ubuntu Server 10.10. I will follow the 10.10 guide and the "2nd Link" for pam setup. But I should let you know that after following that "2nd Link" yesterday to setup pam.d I was unable to login from the GUI (which prompted this mornings rebuild) so something is wrong there too. I'll letcha know how it goes.

---

### Post by luvshines on 2010-11-02
> **jabes69 said:**
> Another day and yet another fresh build of Ubuntu Server 10.10. I will follow the 10.10 guide and the "2nd Link" for pam setup. But I should let you know that after following that "2nd Link" yesterday to setup pam.d I was unable to login from the GUI (which prompted this mornings rebuild) so something is wrong there too. I'll letcha know how it goes.

I should have warned you earlier, working with PAM comes with the [B]'Rule of Thumb':
Take backup of original PAM file which are modifying. Open a terminal, su to root and leave it as it is. This one will come handy if you commited any PAM mistakes. Don't restart the system or loose this terminal unless you are convinced that PAM configurations are fine[/B]

---

### Post by jabes69 on 2010-11-02
Yet another failure of LDAP install. Go figure - why aren't I surprised. The worst part of this is finding more and more people fighting the same damned issues. Why hasn't someone at Ubuntu woken up and realized there are problems with this and major problems at that.

This morning I followed this link and ldap_bind issues arise when trying to add people. This is really driving me nutz! Really wish my clients would follow my advice and not use Ubuntu for this. But because they will not budge on the Ubuntu thing forward we go into more billable hours. God I wish they'd just fire me already.

Anyways heres the link for the HOWTO I followed this morning that also fails to produce results: [http://ubuntuforums.org/showthread.php?p=8154148](http://ubuntuforums.org/showthread.php?p=8154148)

Thanks again luvshines!!

---

### Post by jabes69 on 2010-11-02
BTW - This thread is almost #1 in the search results for OpenLDAP Ubuntu Server 10.10 and 10.04 on Google - Congratulations to us for making this issue #1 relevancy on Google!! Less than 7 days to the top - a new record for me!

---

### Post by Gone fishing on 2010-11-02
I got ldap server working with devi1903 he used Ubuntu I used Opensuse he's better at ldap in Ubuntu than me so if you wish I get him to drop you a line and what how-tos he used. However we found that it wasn't very stable with nfs and both ended up using an Opensuse ldap nfs server.

I used this how-to on Opensuse [http://digiplan.eu.org/ldap-samba-howto-v4.html](http://digiplan.eu.org/ldap-samba-howto-v4.html)

Setting up ldap clients in Opensuse is so easy just a couple of clicks.

Oops wrote ntfs not nfs :oops:

---

### Post by jabes69 on 2010-11-02
OK - So following the Ubuntu Server Guide for 10.10 ( [https://help.ubuntu.com/10.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.10/serverguide/C/openldap-server.html) ) I can now ldapsearch -x and that returns:

flynt@appm-ecot:~$ sudo ldapsearch -x
# extended LDIF
#
# LDAPv3
# base <> (default) with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# search result
search: 2
result: 32 No such object

# numResponses: 1

_________________________________

Now what? I'm afraid to go forward. I know I'll try the search from a client to see if the OpenLDAP server is even seen on the network. 

Any ideas about next step very welcome...

---

### Post by jabes69 on 2010-11-02
Holy Moly - The client can see the server with ldapsearch -x -h <servername>.

Now I'm really sketched - what to do next? Time to do some documentation while I await a suggestion.

---

### Post by luvshines on 2010-11-02
Gud!! A working LDAP server :)

Have you added some users/groups ?
What does```
sudo slapcat
``` says ?

---

### Post by jabes69 on 2010-11-02
Yeah I added the John Doe user just to get something in the db. For S's & G's I tried logging in via ssh from the client and got the old Permission Denied. Here is the output from slapcat:


flynt@appm-ecot:~$ sudo slapcat
[sudo] password for flynt: 
dn: dc=appm-ecot,dc=colorado,dc=edu
objectClass: top
objectClass: dcObject
objectClass: organization
o: Applied Mathematics
dc: appm-ecot
description:: YXBwbS1lY290IExEQVAg
structuralObjectClass: organization
entryUUID: 489eeeee-7afa-102f-9228-4da1e8911bbf
creatorsName: cn=admin,dc=appm-ecot,dc=colorado,dc=edu
createTimestamp: 20101102182515Z
entryCSN: 20101102182515.918881Z#000000#000#000000
modifiersName: cn=admin,dc=appm-ecot,dc=colorado,dc=edu
modifyTimestamp: 20101102182515Z

dn: cn=admin,dc=appm-ecot,dc=colorado,dc=edu
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword:: xxxxxxxxxxxx
structuralObjectClass: organizationalRole
entryUUID: 48ac88ba-7afa-102f-9229-4da1e8911bbf
creatorsName: cn=admin,dc=appm-ecot,dc=colorado,dc=edu
createTimestamp: 20101102182516Z
entryCSN: 20101102182516.008015Z#000000#000#000000
modifiersName: cn=admin,dc=appm-ecot,dc=colorado,dc=edu
modifyTimestamp: 20101102182516Z

dn: ou=people,dc=appm-ecot,dc=colorado,dc=edu
objectClass: organizationalUnit
ou: people
structuralObjectClass: organizationalUnit
entryUUID: 48af34fc-7afa-102f-922a-4da1e8911bbf
creatorsName: cn=admin,dc=appm-ecot,dc=colorado,dc=edu
createTimestamp: 20101102182516Z
entryCSN: 20101102182516.025533Z#000000#000#000000
modifiersName: cn=admin,dc=appm-ecot,dc=colorado,dc=edu
modifyTimestamp: 20101102182516Z

dn: ou=groups,dc=appm-ecot,dc=colorado,dc=edu
objectClass: organizationalUnit
ou: groups
structuralObjectClass: organizationalUnit
entryUUID: 48b07560-7afa-102f-922b-4da1e8911bbf
creatorsName: cn=admin,dc=appm-ecot,dc=colorado,dc=edu
createTimestamp: 20101102182516Z
entryCSN: 20101102182516.033734Z#000000#000#000000
modifiersName: cn=admin,dc=appm-ecot,dc=colorado,dc=edu
modifyTimestamp: 20101102182516Z

dn: uid=john,ou=people,dc=appm-ecot,dc=colorado,dc=edu
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: john
sn: Doe
givenName: John
cn: John Doe
displayName: John Doe
uidNumber: 1000
gidNumber: 10000
userPassword:: xxxxxxxx
gecos: John Doe
loginShell: /bin/bash
homeDirectory: /home/john
shadowExpire: -1
shadowFlag: 0
shadowWarning: 7
shadowMin: 8
shadowMax: 999999
shadowLastChange: 10877
mail: [email]john.doe@example.com[/email]
postalCode: 31000
l: Toulouse
o: Example
mobile: +33 (0)6 xx xx xx xx
homePhone: +33 (0)5 xx xx xx xx
title: System Administrator
postalAddress:
initials: JD
structuralObjectClass: inetOrgPerson
entryUUID: 48b1c26c-7afa-102f-922c-4da1e8911bbf
creatorsName: cn=admin,dc=appm-ecot,dc=colorado,dc=edu
createTimestamp: 20101102182516Z
entryCSN: 20101102182516.042260Z#000000#000#000000
modifiersName: cn=admin,dc=appm-ecot,dc=colorado,dc=edu
modifyTimestamp: 20101102182516Z

dn: cn=example,ou=groups,dc=appm-ecot,dc=colorado,dc=edu
objectClass: posixGroup
cn: example
gidNumber: 10000
structuralObjectClass: posixGroup
entryUUID: 48b461ca-7afa-102f-922d-4da1e8911bbf
creatorsName: cn=admin,dc=appm-ecot,dc=colorado,dc=edu
createTimestamp: 20101102182516Z
entryCSN: 20101102182516.059449Z#000000#000#000000
modifiersName: cn=admin,dc=appm-ecot,dc=colorado,dc=edu
modifyTimestamp: 20101102182516Z

---

### Post by jabes69 on 2010-11-02
OK So now I have followed the guide to the letter (which includes many redundant steps) and have setup the server and the client accordingly.

At the client I cannot login to the LDAP server and it errors with Permission Denied. Not wanting to chase down the SSH error I assume I should be able to login at the GUI and that too fails with Authentication Error.

So either the LDAP server installation is a bust or...well I dunno. Anybody got any suggestions?

---

### Post by jabes69 on 2010-11-02
So while I wait for suggestions I have added a few users and none of them have worked to login from the client. This is very very sad and I am about to quit this all together if no one has any suggestions.

---

### Post by jabes69 on 2010-11-02
OK So the problem must be in this somewhere but I have no clue what to do about it. Anyone...?


flynt@appm-ecot:~$ ldapsearch -x
# extended LDIF
#
# LDAPv3
# base <> (default) with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# search result
search: 2
result: 32 No such object

# numResponses: 1


Thanks.

---

### Post by jabes69 on 2010-11-02
And now I get this on a restart of slapd (which has been working perfectly all day and now all of a sudden it will not)

flynt@appm-ecot:~$ /etc/init.d/slapd restart
No configuration directory was found for slapd at /etc/ldap/slapd.d/.
If you have moved the slapd configuration directory please modify
/etc/default/slapd to reflect this.  If you chose to not
configure slapd during installation then you need to do so
prior to attempting to start slapd.

---

### Post by jabes69 on 2010-11-02
OK so this is really strange at first an ldapsearch returned the above with result: 32 No Such Object and now its returning this for some reason and with no changes:

flynt@appm-ecot:/etc/default$ sudo ldapsearch -x
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

What the heck is going on...?

---

### Post by luvshines on 2010-11-03
> **jabes69 said:**
> OK so this is really strange at first an ldapsearch returned the above with result: 32 No Such Object and now its returning this for some reason and with no changes:

flynt@appm-ecot:/etc/default$ sudo ldapsearch -x
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

What the heck is going on...?

Maybe slapd is not running.
You'll have to sudo start/stop it, normal user don't have permissions to start/stop/restart services on a system

And for your earlier thing, I am also trying to configure my system with my locally setup LDAP server to check what has been bothering you for so long.
At present, I am able to list LDAP users(with id command) on my system but able to ssh through them :). I haven't tried login yet
If you can hang on, I'll try to figure out the solution

---

### Post by luvshines on 2010-11-03
Ok!! I have resolved it on my system :)
I am able to ssh using my LDAP users. Will try login and post back

Just followed the procedure under heading 'LDAP Authentication' in this link:
[https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html)

It did all nsswitch.conf and majority of PAM configurations for me. I did one additional change in common-auth and it started working

Try it and post back the results. I feel much more confident now since I have it working on my system :)

---

### Post by jabes69 on 2010-11-04
Thanks luvshine!!!

Got it on my own as well. Followed the links and installed TLS and that screwed it all up. TLS is broken. Researching a fix but I have enough logged to make a fairly decent howto and will. For now though we'll call this thread closed. Thanks for all your help and time. I cant believe you made the investment but I am glad you did!

---

### Post by luvshines on 2010-11-05
Superb !!

Finally it is resolved and that too on your own :), must be happy now

Yeah, I have seen TLS mentioned on the HOW TO's, which can create trouble for a person who is setting up an LDAP server for the first time

And I too am happy that I was able to configure Ubuntu with LDAP, since for the past one year(at my job) I have been doing only RHEL/Fedora(about 4-5 of them everyday)

---

### Post by aflores3 on 2010-11-10
Jabes, 
I found your post by doing some preliminary research before setting up an LDAP on an existing Ubuntu server running 10.04. Should I even attempt it, or should I go a different route? Also, please comment back in this post when you post your comprehensive how-to. Finally, I read the entire thread, but I think I might have overlooked the part where you ask luvshines what type of beer he/she prefers :)

---

### Post by byb3 on 2010-11-15
I read this with a similar feeling of anger and disillusion, after only spending 3 hours, never mind 3 weeks.

After many searches on google, I however came up with this Gem which just works (for me anyway)

[http://albanianwizard.org/ubuntu-10-0-4-lucid-lynx-ldap-configuration-the-working-how-to.albanianwizard](http://albanianwizard.org/ubuntu-10-0-4-lucid-lynx-ldap-configuration-the-working-how-to.albanianwizard)

Make sure you edit the first few lines of the script, and you're good to go.  I can't believe I've just fixed this in 5 minutes!  Congrats to the guy who made that blog post because it's saved me loads of time.  I'm installing it on Ubunutu 10.10 if that makes any difference.

Regards

---

### Post by luvshines on 2010-11-16
Haven't tried the new style configuration, but this is what I did to stick to the old style slapd.conf configuration, which was as easy as breathing
```

# My /etc/default/slapd contents
cat /etc/default/slapd | egrep -v "^#|^$"
SLAPD_CONF="/etc/ldap/slapd.conf"
SLAPD_USER="openldap"
SLAPD_GROUP="openldap"
SLAPD_PIDFILE="/var/run/slapd/slapd.pid"
SLAPD_SERVICES="ldap:///"
SLAPD_SENTINEL_FILE=/etc/ldap/noslapd
SLAPD_OPTIONS=""

# I think I also did
mkdir -p /var/run/slapd

# Added these to /etc/init.d/slapd (because of a bug)

# At the end of start_slapd {} function
pidof /usr/sbin/slapd > "$SLAPD_PIDFILE"

# At the end of stop_slapd {} function
rm -f $SLAPD_PIDFILE

# Copied samba.schema (comes with samba package) in /etc/ldap/schema

# /etc/ldap/slapd.conf contents
cat /etc/ldap/slapd.conf | egrep -v "^#|^$"
include		/etc/ldap/schema/core.schema
include		/etc/ldap/schema/cosine.schema
include		/etc/ldap/schema/inetorgperson.schema
include		/etc/ldap/schema/nis.schema
include	        /etc/ldap/schema/samba.schema

allow bind_v2

moduleload back_bdb
database	bdb

suffix		dc=luvshines,dc=com
rootdn		cn=manager,dc=luvshines,dc=com

rootpw		secret

index objectClass                       eq,pres
index ou,cn,mail,surname,givenname      eq,pres,sub
index uidNumber,gidNumber,loginShell    eq,pres
index uid,memberUid                     eq,pres,sub
index nisMapName,nisMapEntry            eq,pres,sub

```

And that was it, got a working LDAP server

Then you'll have to add some users and basic configuration(you can change this as per your need)

First defined some basic tree structure
```

# Create a file manager.ldif
dn: dc=luvshines,dc=com
objectclass: dcObject
objectclass: organization
o: ExampleCo
dc: luvshines

dn: cn=Manager,dc=luvshines,dc=com
cn: Manager
objectclass: organizationalRole

dn: ou=People,dc=luvshines,dc=com
ou: People
objectClass: top
objectClass: organizationalUnit

dn: ou=Group,dc=luvshines,dc=com
ou: Group
objectClass: top
objectClass: organizationalUnit

```

Issued the command```

ldapadd -x -D cn=manager,dc=luvshines,dc=com -w secret -f manager.ldif
```

Then added some users, created another file, testuser.ldif```

dn: cn=testgroup,ou=Group,dc=luvshines,dc=com
objectClass: posixGroup
objectClass: top
cn: testgroup
userPassword: testgroup
gidNumber: 1000

dn: uid=testuser,ou=People,dc=luvshines,dc=com
cn: Test User
uid: testuser
objectClass: account
objectClass: posixAccount
objectClass: top
objectClass: shadowAccount
objectClass: sambaSamAccount
userpassword: testpassword
uidNumber: 1100
gidNumber: 1000
homeDirectory: /home
sambaSID: S-1-0-1100
sambaNTPassword: 82E6D500C194BA5B9716495691FB7DD6
loginShell: /bin/bash
sambaPasswordHistory: 00000000000000000000000000000000000000000000000000000000
 00000000
sambaAcctFlags: [U          ]
sambaPwdLastSet: 1263386096

```

Again issued the command```

ldapadd -x -D cn=manager,dc=luvshines,dc=com -w secret -f testuser.ldif

```

I generated the Samba stuff from script given here. I put in some fake SID, you can configure it as per your need
[http://search.cpan.org/~bjkuit/Crypt-SmbHash-0.12/SmbHash.pm](http://search.cpan.org/~bjkuit/Crypt-SmbHash-0.12/SmbHash.pm)

The above ldif created a group testgroup and a user testuser with Samba password as 'test01' and userpassword as 'testpassword'

Don't know if this helps neone or not, but I find it real simple to configure and use :)
This doesn't have any ACL stuff nor includes any SSL/TLS stuff. You can add it as you proceed/learn. Also, I see no point in running into security considerations unless you really know what you are doing and why you are doing it. So learn it and then use it :D

---

### Post by revzalot on 2010-12-13
Has anyone got filtering aka host based authentication to work after the install?  

Here's my link:[http://ubuntuforums.org/showthread.php?p=10212707#post10212707](http://ubuntuforums.org/showthread.php?p=10212707#post10212707)

---

