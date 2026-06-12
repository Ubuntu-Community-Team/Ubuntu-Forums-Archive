---
title: "LDAP users cannot log in unless they are local users as well"
date: 2009-08-18
forum: General Help
---

### Post by PatheticMoFo on 2009-08-18
Hi everyone. I wasn't sure where exactly this thread should go, so I thought I should just put it here in general help. I haven't had much success in finding a solid solution so I thought I'd ask everyone here.

I'm the system administrator for a lab at the college I attended. I set up a Fedora 11 Kerberos/LDAP/NFS4 server, a secondary KDC (which also acts as a backup LDAP server, also Fedora) and was tasked with migrating the current set up to one which would use the central NFS server to store all the user's files.

The servers took a while to get right, but I managed to get that working as well as I could. To test the setup, I sacrificed my laptop to be completely reconfigured as a test client. My laptop, as well as all of the computers which will be the clients, runs Ubuntu. Specifically, 8.10. I have had no problems at all with the configuration there: users are authenticated using Kerberos, passwd and group comes from the LDAP server, and the files for each user show up just fine with ID mapping working just as well.

Then I tried doing this on a machine running Jaunty. Only one user, my account, was able to log in with no issues, for it was the only account which was also a local account. All LDAP-only users were greeted with a blinking cursor if they tried to log in. I tried the exact same configuration on my laptop, followed guides from all over the internet, and that worked well. The ONLY way users could log in was if I added their entries to /etc/passwd (and group entries to /etc/group). So I ask you, could this be an issue specific to Jaunty? What else could be the problem? This is actually a new machine, so should I just install intrepid instead?

Please let me know any configuration files which may be useful to post.

I should also mention that logging in graphically as an LDAP-only user works, but is HORRIBLY slow, and if you try to open a terminal, it only shows a blinking cursor. If you log in through ssh like this:

```
ssh user@client bash
```

you get a bash shell with no prompt (took me a while to figure that out), and typing the tty command in it assures me that it is not a terminal (???).

Right now, I have had to resort to adding all the users to passwd and group just so that machine could be usable at least for a few days.

Thanks for any help, and again let me know anything I should post which may be of some help.

---

### Post by PatheticMoFo on 2009-08-19
I'd hate to bump, but I really need a response...bump.

---

### Post by PatheticMoFo on 2009-08-21
Ok, no one responded but that's fine as I have "solved" this issue myself. Or rather, I have come up with a workaround and am considering filing a bug, but I don't know if it is warranted.

In any case, I narrowed down the problem to the /etc/nsswitch.conf file.

On my laptop, which uses intrepid, my nsswitch.conf contains these two lines:
```

passwd:         files ldap [NOTFOUND=return] db
group:          files ldap [NOTFOUND=return] db
```

per this guide on using pamccreds and libnss-db: [https://help.ubuntu.com/community/PamCcredsHowto](https://help.ubuntu.com/community/PamCcredsHowto)

That works with no problems at all on intrepid. However, the same configuration fails on jaunty with all the appropriate packages installed. Users MUST be present in the /etc/passwd file (and groups in /etc/group) in order for a login shell to come up when logging in. My workaround was to change the lines to read

```

passwd:         db files ldap
group:          db files ldap
```

files MUST be before ldap, else the root user disappears (when trying to run commands, you get the message "You don't exist, go away!"). Of course, libnss-ldap must be running, and you had to have run nss_updatedb ldap first to actually create the database.

So I'm wondering if this is a bug in pam or libnss-ldap or something somewhere, but I don't know if I should file it or under what package. Thanks anyway!

---

### Post by apalacheno on 2009-08-28
Re-check at your PAM config. The NSS config

```
passwd:		files ldap [NOTFOUND=return] db 
group:		files ldap [NOTFOUND=return] db
```

is correct and works flawlesly here using both Jaunty Server and Jaunty Clients.

Cheers,
Robert

---

### Post by PatheticMoFo on 2009-09-01
Thanks for your response, and sorry for my late response. What exactly should I check for in it? Here is the relevant part of my auth-client-config profile that I am using on these machines:

```
pam_auth=auth       required      pam_env.so
        auth        sufficient    pam_unix.so nullok try_first_pass
        auth        requisite     pam_succeed_if.so uid >= 500 quiet
#the following line (containing pam_group.so) must be placed before pam_ldap.so
#for ldap users to be placed in local groups such as fuse, plugdev, scanner, etc ...
        auth        required      pam_group.so use_first_pass
        auth        sufficient    pam_krb5.so use_first_pass
        auth        required      pam_deny.so
pam_account=account    required      pam_unix.so broken_shadow
        account     sufficient    pam_localuser.so
        account     sufficient    pam_succeed_if.so uid < 500 quiet
        account     [default=bad success=ok user_unknown=ignore] pam_krb5.so
        account     required      pam_permit.so
pam_password=password   requisite     pam_cracklib.so retry=3
        password    sufficient    pam_unix.so sha512 shadow nullok try_first_pass use_authtok
        password    sufficient    pam_krb5.so use_authtok
        password    required      pam_deny.so
pam_session=session    optional      pam_keyinit.so revoke
        session     required      pam_limits.so
        session     [success=1 default=ignore] pam_succeed_if.so service in crond quiet use_uid
        session     required      pam_unix.so
        session     optional      pam_krb5.so
```

I came up with this by following guides on help.ubuntu.com/community and from looking at Fedora's PAM configuration when it is set up to authenticate using Kerberos and get accounts from LDAP. Since the server is using UID's starting at 500, I decided to use that in the PAM configuration as well.

Thanks,
Yözen

---

### Post by apalacheno on 2009-09-02
Try the following PAM config (which is a copy&paste of my working config). Be aware though that I use Cached Credentials:

**/etc/pam.d/common-auth:**
```
auth		sufficient	pam_unix.so 
auth		[authinfo_unavail=ignore success=1 default=die]	pam_krb5.so use_first_pass 
auth		[default=done]	pam_ccreds.so action=validate use_first_pass 
auth		[default=done]	pam_ccreds.so action=store use_first_pass 
auth		[default=done]	pam_ccreds.so action=update use_first_pass 
auth		requisite	pam_deny.so
```

**/etc/pam.d/common-account:**
```
account		sufficient	pam_unix.so nullok_secure 
account		sufficient	pam_krb5.so 
account		required	pam_permit.so
```

**/etc/pam.d/common-password:**
```
password	requisite	pam_krb5.so 
password	[success=2 default=ignore]	pam_unix.so obscure use_authtok try_first_pass sha512 
password	[success=1 user_unknown=ignore default=die]	pam_ldap.so use_authtok try_first_pass 
password	requisite	pam_deny.so 
password	required	pam_permit.so
```

**/etc/pam.d/common-session:**
```
session		required	pam_mkhomedir.so skel=/etc/skel/ umask=0022 
session		[default=1]	pam_permit.so 
session		requisite	pam_deny.so 
session		required	pam_permit.so 
session		optional	pam_krb5.so 
session		required	pam_unix.so 
session		optional	pam_ldap.so 
session		optional	pam_ck_connector.so nox11
```

Let me know if it helps or not.

Cheers,
Robert

---

### Post by PatheticMoFo on 2009-09-02
Thanks, Robert. I'll try that out as soon as I get a chance to this Friday and will let you know how it works out. I already have three machines up using my workaround and am pretty eager to get this resolved before I have to roll the rest out. I have libpam-ccreds installed already so its fine (and probably better for me) to use cached credentials.

Quick side question though, your setup allows users to change their password with passwd, right? I've had mixed success with this as well: some users were able to use passwd, but the last two had to use kpasswd. In those cases, I got a "passwd : Authentication token manipulation" error.


Thanks,
Yözen

---

### Post by apalacheno on 2009-09-03
Hey Yözen,
the password change using *passwd* works just fine here. However, I have no empirical values on larger environments as currently I use the whole thing in a test environment only.

Good luck!

Cheers,
Robert

---

### Post by PatheticMoFo on 2009-09-08
Hi Robert,

You, sir, are amazing. I need to really look at what I might have been doing wrong, but I basically copy pasted your configuration (with 2 minor adjustments for my setup), changed the passwd and group lines to what you said should work, and it.just.worked.

Amazing. Thank you very much. I need to buy you a beer/beverage-of-your-choice.

I haven't tested out *passwd*, but I'm sure its gotta work by now.


Thanks, again
Yözen

Edit:
Actually, I *STILL* need to put "db" at the start of the passwd and group lines in /etc/nsswitch.conf
passwd: db files ldap [NOTFOUND=return]
group: db files ldap [NOTFOUND=return]
It looks like Fedora recommends this too...so maybe that's right now? If I don't do that, it takes forever for user's sessions to log in, and for the terminal emulator to display a prompt.

---

### Post by apalacheno on 2009-09-09
Hi Yözen,
no wonder it is faster this way, because the line

```
passwd:		db files ldap [NOTFOUND=return]
```

translates to:

*"First, look in the local LDAP cache, if the user can be found there. If not, look in the local passwd files. If still not found, query the LDAP server."*

So usually, the LDAP server will never be queried, thus the short logon time.

This is fine, but brings along some caveats you have to be aware of. First, it's always recommended to put "files" first. Because if the local db cache gets corrupt, nobody can log in, not even the local root. If "files" is first, at least local users (and root) can log in.

Second, if "db" is put before "ldap", the clients always work with potentially aged data. If a user changes his password or an existing user is deleted (i.e. because he is leaving the company), this change isn't reflected on the clients until they update their local db. This is a potential security risk.
If you can live with that, make sure that the clients fetch up-to-date data from the LDAP server every 30 or (maximum) 60 minutes. I can help you with a script that does that automatically.

However, if the clients take forever to log in, something isn't right. Usually you shouldn't notice any differences between local and LDAP authentication.

Is the LDAP server at the same site as your clients, or do LDAP queries have to travel over a WAN? How much time do manual LDAP queries need? Is there any noticeable delay? How do the clients connect to the LDAP server? Via IP address or is a name resolution at a DNS server necessary? This could be a bottleneck if the DNS server isn't configured correctly. Do you use LDAP with TLS (which is always recommended)? Try to temporarily disable any encryption and check if logon is faster.

If all of the above is without usable results, you could set a timelimit in the client's ldap.conf to avoid too long delays (you can experiment with the timelimit values; 5 seconds should be reasonable in most cases).
If the LDAP query takes longer than the time set in the timelimit option, the client falls back to the local "db". This way you may have both - short logon times and up-to-date user information, if time permits.

Cheers,
Robert

---

### Post by PatheticMoFo on 2009-09-09
> **apalacheno said:**
> Second, if "db" is put before "ldap", the clients always work with potentially aged data. If a user changes his password or an existing user is deleted (i.e. because he is leaving the company), this change isn't reflected on the clients until they update their local db. This is a potential security risk.
If you can live with that, make sure that the clients fetch up-to-date data from the LDAP server every 30 or (maximum) 60 minutes. I can help you with a script that does that automatically.


Is this still a problem if the Kerberos server still needs to be contacted for password authentication? I thought only the list of users/groups is what gets cached if I am using Kerberos for authentication and the password field in the LDAP entry is unused.

I've written a simple crontab for updating the database every 30 minutes. Database corruption, however, is a problem. One I hadn't thought of...

> **apalacheno said:**
> Is the LDAP server at the same site as your clients, or do LDAP queries have to travel over a WAN? How much time do manual LDAP queries need? Is there any noticeable delay? How do the clients connect to the LDAP server? Via IP address or is a name resolution at a DNS server necessary? This could be a bottleneck if the DNS server isn't configured correctly. Do you use LDAP with TLS (which is always recommended)? Try to temporarily disable any encryption and check if logon is faster.


The LDAP server is at the same site, just a few doors away. Manual LDAP queries seem to take nearly no time at all, which is why I am confused about the lag issue. I *do* use the FQDN as the ldap uri, and that isn't necessary: the servers' IP addresses aren't likely to take too long. I'll try with one machine today, time permitting, with the IP address in the LDAP uri. I do use LDAP with TLS -- I can just tell the client not to use it when querying, that should work since I can run ldapsearch without TLS as well. Again, I'll see if I can actually test these configurations today.

> **apalacheno said:**
> If all of the above is without usable results, you could set a timelimit in the client's ldap.conf to avoid too long delays (you can experiment with the timelimit values; 5 seconds should be reasonable in most cases).
If the LDAP query takes longer than the time set in the timelimit option, the client falls back to the local "db". This way you may have both - short logon times and up-to-date user information, if time permits.

Cheers,
Robert

That's a really good idea: my timelimit, and bind_timelimit, parameters are currently set at 120 so that's probably a tad high. These are the same setting as on the backup KDC/LDAP server, but I have seen none of these problems on that machine (it runs Fedora). That can probably be attributed to the fact that it can just consult itself for the needed information, however.


Thanks,
Yözen

---

### Post by apalacheno on 2009-09-09
AFAIK all credentials needed for login get cached. You can test that by booting your machine with the network cable unplugged. Using cached credentials, you still can login (that's the point of cached credentials), but you don't get a Kerberos ticket.

Let me know how your tests turn out!

---

### Post by PatheticMoFo on 2009-09-09
RE: cached login credentials -> Got it, that makes perfect sense.

OK, so thanks to your help, I have narrowed down the problem to libnss-ldap and OpenSSL.

Here's the run-down. If I have ssl start_tls enabled in /etc/ldap.conf, I get messages on the client side saying that nss_ldap could not connect to the ldap server. On the server side, I get messages saying "unable to get TLS client DN". Looks like that last message is a pretty heavily searched term, and there's even a thread in the ubuntu forums asking about it which went unanswered. (Doesn't look too good for me).

*However*, using ldapsearch with the -ZZ option works just fine: no error messages like the above on either client, nor server. Something must be going wrong with how nss_ldap uses the certificate file, and I don't know what, or how to go about fixing that.

Until I figure out what might be wrong there, I'll have to stick to my old, potentially insecure, configuration for the time being.

Any ideas, Robert?

Thanks,
Yözen

Edit:
Forgot to mention: running nss_updatedb works fine, but I get the error message on the server side only. Logging in with the same configurations causes the error messages on both sides as explained above.

---

### Post by apalacheno on 2009-09-10
Hi Yözen,
that may be a shot right out into the blue, but do you have the option *TLS_REQCERT* in /etc/ldap/ldap.conf set to "demand"|"hard" or to "allow"? Try "allow" for instance. I remember vaguely having read something about hiccups with gnutls and self-signed certificates.

Concerning the login delay, it crossed my mind that you should have "*bind_policy*" set to "soft" in /etc/ldap.conf. But I don't expect that will help much in your case anyway.

Would you mind posting your /etc/ldap.conf and /etc/ldap/ldap.conf? I'd like to reconstruct your settings (as time permits) and test it here locally.

Cheers,
Robert

---

### Post by PatheticMoFo on 2009-09-10
Hey Robert,

Nope, I haven't defined TLS_REQCERT, so it must be on the default "demand". Sure, I'll try using "allow", but this would probably only get rid of the client side-issues, so if there really is something going on in the server side that is preventing the setup from working properly, it might not fix it. Of course, I will try it anyway in case I'm wrong.

Oh, bind_policy is set to "soft" already. I've read about "hard" causing some pretty bad issues.

You got it, I'll post both files. If you don't mind, I'll remove the references to the server hostnames :wink:

Thanks,
Yözen

Attachments Note:
ldap.conf.txt -> /etc/ldap.conf
ldap_ldap.conf.txt -> /etc/ldap/ldap.conf
In this file, have not yet added TLS_REQCERT "allow"

---

### Post by apalacheno on 2009-09-11
Thanks Yözen. Gimme some time to implement a test environment with your settings. It may take a few days. I'll reply as soon as I'm done.

Have a nice weekend meanwhile!

---

### Post by PatheticMoFo on 2009-09-11
> **apalacheno said:**
> Thanks Yözen. Gimme some time to implement a test environment with your settings. It may take a few days. I'll reply as soon as I'm done.

Have a nice weekend meanwhile!

Sure, no rush. Thanks a lot for the help!

You have a nice weekend too!

---

### Post by apalacheno on 2009-09-24
Hey,
sorry for the long delay, it was a busy week.

Looking at your */etc/ldap.conf* I see that the following lines are missing:

```
nss_base_passwd			ou=users,dc=removed,dc=com?one
nss_base_group			ou=groups,dc=removed,dc=com?one
```

They should point to the actual ou of your users and groups. What I also noticed is your use of the *use_sasl* and *rootuse_sasl* options. Adding these to my config, the login took significantly longer. I'm not using them though, and to be honest I have no idea what they actually do. It works nevertheless.

Also, check your *TLS_CACERT* and *TLS_CACERTDIR* options in */etc/ldap/ldap.conf*. I'm not sure about this, but I think you have to decide for one, not use both. And since you use a backup server, you'd likely want to go for TLS_CACERTDIR.

Here's my config that works without problems:

*/etc/ldap.conf*:

```
# Pre-configured values
base				dc=removed,dc=com
uri				ldap://masterldap.removed.com
ldap_version			3
pam_password			md5

# Own settings
ssl				start_tls
tls_checkpeer			yes
bind_policy			soft
nss_base_passwd			ou=users,dc=removed,dc=com?one
nss_base_group			ou=groups,dc=removed,dc=com?one
nss_initgroups_ignoreusers	avahi,avahi-autoipd,backup,bin,daemon,games,gdm,gnats,haldaemon,hplip,irc,klog,libuuid,list,lp,mail,man,messagebus,news,polkituser,proxy,pulse,root,saned,sync,sys,syslog,uucp,vboxadd,www-data
```

*/etc/ldap/ldap.conf*:

```
BASE		dc=removed,dc=com
URI		ldap://masterldap.removed.com
TLS_REQCERT	demand
TLS_CACERT      /usr/share/ca-certificates/cacert_home.crt
```

If you still have problems, I'd guess there's something wrong with the certificates. How did you add your certs to your LDAP server? And does the LDAP server cert's *common name* match exactly your LDAP URI, in this case *masterldap.removed.com*? You'd need a separate certificate for your LDAP backup server as well.

Hm, that's all that comes to my mind for now. Hope it is of some use for you!

Cheers,
Robert

---

### Post by CarlosAF on 2009-09-25
Please,

Have a look at

[http://www.linux-mag.com/id/4738](http://www.linux-mag.com/id/4738)

and

[http://www.linux-mag.com/id/4765](http://www.linux-mag.com/id/4765)

I've followed the instructions described there and sso ldap authentication worked fine width ssh.

My server and clients are ubuntu 9.04.


Carlos

---

### Post by PatheticMoFo on 2009-09-28
Thanks for your responses, guys. I will try out Robert's suggestions first, but I will look at the two articles you've posted Carlos, thanks.

@ Robert,
The use_sasl and rootuse_sasl options came from this page:
[https://www-s.acm.uiuc.edu/wiki/space/Setting+up+Kerberized+LDAP+NSS+on+Fedora+Core+6](https://www-s.acm.uiuc.edu/wiki/space/Setting+up+Kerberized+LDAP+NSS+on+Fedora+Core+6)
I just used them to try them out, but if you say log in time went up, I should really get rid of them! TLS_CACERTDIR was actually added automatically for me, I never added it myself! I was only using TLC_CACERT, but everytime I remove TLS_CACERTDIR it seems to spontaneously reappear.

Also, in regards to having a separate certificate for my backup LDAP server, according to this page:
[http://www-theorie.physik.unizh.ch/~dpotter/howto/kerberos#ssl_certificate](http://www-theorie.physik.unizh.ch/~dpotter/howto/kerberos#ssl_certificate)
I just have to tweak a setting in my openssl.conf file, subjectAltName, so that I can use just one certificate.


Thanks, all. I'll let you know how it goes.

---

### Post by PatheticMoFo on 2009-09-28
Good news, guys! After following Robert's suggestion to add nss_base_passwd and nss_base_group to /etc/ldap.conf, and then modifying /etc/nsswitch.conf to the correct configuration, everything seems to be working just fine! Hard to believe all of this trouble was caused by two little lines! And that those lines weren't really touched upon in anything I read.

Of course, I'll be testing to see if I still get any issues, but so far, everything on my testing computer appears fine: no delays, no lag, users can be LDAP-only!

@ Carlos,
Sorry, I still haven't read the links you sent me as they require registration so I haven't gotten around to that yet. But thanks, since those might prove to be helpful in the future.

I'll keep you posted,
Yözen

---

### Post by apalacheno on 2009-09-29
> **PatheticMoFo said:**
> Also, in regards to having a separate certificate for my backup LDAP server, according to this page:
[http://www-theorie.physik.unizh.ch/~dpotter/howto/kerberos#ssl_certificate](http://www-theorie.physik.unizh.ch/~dpotter/howto/kerberos#ssl_certificate)
I just have to tweak a setting in my openssl.conf file, subjectAltName, so that I can use just one certificate.
Yep, that's correct.

It's amusing that you use the exact same tutorials that I started out with :)

Good luck!

---

### Post by PatheticMoFo on 2009-09-29
Well no problems so far, so it seems to have worked just fine, thanks! By the way, is it ok to set idle_timelimit in /etc/ldap.conf to 5 as well? (Instead of 3600). It might be just me, but it seems like using sudo takes a lot longer when this setting is at its default.

@Robert
Yeah, I think that tutorial and a few select others are probably like the "gold standard" in how to set this stuff up!

I'm thinking about writing yet another tutorial myself in case others experienced similar troubles, so thanks again for all of your help!

Marking this thread as "solved".

---

### Post by apalacheno on 2009-09-29
Hey Yözen!

Great to hear that it works for you! And to motivate you... I think good tutorials that cover these topics are badly needed as there still is a bit of voodoo involved, and I haven't found any single tutorial so far that really covered everything from ground up (not even the Ubuntu official or community docs)... I always had to put bits and pieces together from many tutorials and mailing lists and loooots of sweating later I somehow figured it out finally (just like you). So if you've got a free minute or so - I'm sure it will be greatly appreciated!

And regarding *idle_limit* - I have no experience with that, but if it is better with 5 seconds and nothing breaks - sure, why not?

Cheers,
Robert

---

