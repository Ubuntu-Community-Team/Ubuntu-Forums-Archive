---
title: "SADMS Active Directory cached logins: Samba  3.4.7 / Kubuntu 10.04.1"
date: 2010-10-13
forum: General Help
---

### Post by ubuntique on 2010-10-13
Hello

I've been banging my head on this for a week...:confused: I finally got AD login working, but I can't get cached logins working. 

I installed SADMS, let it configure everything, and though I can now login, I still cannot login as my AD username when my machine is not connected to the AD network. I need to be able to login at home, connect to the VPN (if I can ever get that working), then sign on to services at work using my AD username.

Also, I cannot login to *local *accounts when the system is not connected to the AD network.

Plus, home drive mapping is not working, our shares are \\*FILESERVER*\user\user\[I]username[I] so this does not work.

Any help would be much appreciated, thank you!

UPDATE: I installed likewise-open, and now I can't login unless I use the full domain name when logging in via ssh, but I cannot login on the desktop, which is not what I want, now my username doesn't match the previous UID mapping, and my home directory is mapped to /home/likewise-open/DOMAIN/user, instead of /home/DOMAIN/user, like it was before.

---

### Post by atworkwithjf on 2010-10-14
> **ubuntique said:**
> 
UPDATE: I installed likewise-open, and now I can't login unless I use the full domain name when logging in via ssh, but I cannot login on the desktop, which is not what I want, now my username doesn't match the previous UID mapping, and my home directory is mapped to /home/likewise-open/DOMAIN/user, instead of /home/DOMAIN/user, like it was before.

ubuntique,

Likewise-Open generates a UID for AD users that's based on the ID provided by AD.  If you want your OLD home directory to work you need to change the ownership on the contents of that director to reflect the AD user's UID.

Custom defined UID's is a feature of their Enterprise product so if you're just using open you have to stick with the UID generated on your DC.

If my suspicion is correct you are trying to use your old home directory with your new AD account and the previous files, including all those files used to initialize your environment are owned by the old UID.  You'll need to chown those files so that they are owned by the new user.

    > chown -R username:group /PATH/TO/DIRECTORY

There is also a setting in Likewise-Open that allows you to tell your clients to assume the default domain when logging in.  You will want to assume your /etc/passwd file does not have users of the same name if you do this.

The lwconfig tool that ships with likewise open can be used to set this value. [FONT=monospace]

[/FONT]> sudo lwconfig AssumeDefaultDomain true

You can find more detasails on installation, setup and troubleshooting here:

[http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-guide.html#quick-start](http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-guide.html#quick-start)

---

### Post by ubuntique on 2010-10-14
Thanks, I would have tried lwconfig, except it does not exist. I read the documentation and couldn't find anything on how to fix these problems.

Also, my system is running E-X-T-R-E-M-E-L-Y S-L-O-W since I installed Likewise.

---

### Post by atworkwithjf on 2010-10-14
> **ubuntique said:**
> Thanks, I would have tried lwconfig, except it does not exist. I read the documentation and couldn't find anything on how to fix these problems.

Also, my system is running E-X-T-R-E-M-E-L-Y S-L-O-W since I installed Likewise.

Which version are you running?

The version from the Likewise Open site is now up to version 6.  I'd absolutely suggest you update to that.  I have not done an upgrade so I'd uninstall the old repo version and then use the likewise installer.

I'd also make sure your DNS is working as it should, that can cause all sorts of issues.  Use the usual tools (nslookup and dig) to insure your host resolution (forward and reverse) is as it should be.

If it's not there's certainly going to be issues.

Just be aware that if you're using the version form Likewise's site it will install into /opt/likewise/ (as it's not in the base distro) as per the usual standards.

Let me know if your dns is working and if you continue to have issues I'll be happy to help.

---

### Post by ubuntique on 2010-10-15
I installed the version listed in kpackagekit, 5.4. I am trying to login now, but the system is acting very strange and won't display the desktop. The DNS is working, I didn't have any problem logging in with AD before I installed likewise. I will try uninstalling it and installing the latest version, but I think I may just install fedora 13. I will let you know how that works.

Thanks!

---

### Post by atworkwithjf on 2010-10-15
ubuntique,

I'd strongly suggest upgrading to the newest version 6.0.8269 from the Likewise Website.  There are some fixes in there you'll probably want.

It's odd that you're having UI issues, that's generally indicative of permissions  on the home dir.

Can you better describe your machine configuration scenario?  Is the account you are working with on a network mounted home directory?  Is the user ID in AD the same as some previous user ID in the local passwd file?

Cheers

---

### Post by ubuntique on 2010-10-15
I decided to try fedora 13... My kubuntu system became so unstable that I couldn't login to the desktop at all. 

I had created a different username for local login. The AD account name was the same, I didn't have any local entries for it.

Thanks for your responses.

---

### Post by atworkwithjf on 2010-10-15
That's too bad, although I have a Fedora 13 system here running LWO without issue and numerous Ubuntu machines from 9.04 to 10.04, all joined to my 2008r2 Domain Controller and all are quite happy and very stable.  I am however running the current release, 6.0-8269 from their website, not the downrev version from the repo.

Hard to say what's causing the issues on kubuntu, I have no experience with KDE since the 3.4 days, so perhaps there's something there that's causing the issues.  Hopefully you'll have better luck with F13.

---

### Post by ubuntique on 2010-10-19
> **atworkwithjf said:**
> That's too bad, although I have a Fedora 13 system here running LWO without issue and numerous Ubuntu machines from 9.04 to 10.04, all joined to my 2008r2 Domain Controller and all are quite happy and very stable.  I am however running the current release, 6.0-8269 from their website, not the downrev version from the repo.

Hard to say what's causing the issues on kubuntu, I have no experience with KDE since the 3.4 days, so perhaps there's something there that's causing the issues.  Hopefully you'll have better luck with F13.

Thanks again for your help. I did install F13, and I followed the prompts to enable AD authentication when I first logged in. First off, that didn't work at all, then, there is no way to set the root password, so now I have to boot to a rescue system to edit the passwd file... so frustrating. I could try lwo, but I'm afraid it will just screw everything up like it did on Kubuntu.

---

### Post by atworkwithjf on 2010-10-19
Ubuntique,

That's truly remarkable.  

I installed a Fedora 13 machine, ran the updates with yum (as root), configured my network and pointed my dns to my DC and then installed the software following the instructions and was able to join both my Win2000 DC and my Win2008r2 DC after unjoining the older one without any issue.

I just can't imagine why you're having issues.

Perhaps you can be a bit more specific about the exact steps you took when setting up your machine.  You really aren't giving anyone anything to work with here other than saying it doesn't work.

---

### Post by joefish63 on 2010-10-19
It sounds like he has not followed the docs and disabled SELinux to start with.

What's confusing me in his posts is Fedora's installer asks users for local user/password info during firstboot.  Fedora prompts for a root password during anaconda installation.  Why you would edit the password file?

If ubuntique configurd the machine properly, has properly resolving DNS after installing the distribution (regardless of whether it's Fedora or Ubuntu), correctly disabled SELinux as it says in the docs, this should be a very simple process.

I personally installed Likewise on a rack of Fedora 12 servers and all I did was:

1. configure my network properly (I'm using DHCP with static addresses and providing my domain controller's IP for the DNS entry and the domain name for my search domain all via DHCP, others may just do this using static addresses, whatever)

2. updated my box (you don't have to but I figured I should make sure all my packages were up to date while I was at it ( > yum update ) )

3. disable SELinux (I actually set it to disabled though I have used permissive with success)

4. after that I pinged my dc ( > ping mydomain.com ) to be sure it resolved and my network was functioning as expected. NOTE: as with all such projects, be it NIS config, LDAP or binding to AD, if you can't get this going then nothing you do with other software is going to work.

5. Installed Likewise using the installer from their website

6. ran the domainjoin-cli command to join my domain

7. Now I rebooted the machine and had no problems since then logging in using network accounts.

One other thing I did which you may want to do it to set the Likewise software to use the default domain prefix

# /opt/likewise/bin/lwconfig AssumeDefaultDomain true

A couple things you may want to consider.

SELinux needs to be disabled or configured in permissive mode.  If you just use the setenforce command you need to remember that that is only going to disable selinux for the session.

You can't use the same user names for network and local accounts if you are using the assume default domain.  If you just think about it you'll realize why this might cause issues.

---

### Post by atworkwithjf on 2010-10-19
Today I came in and set up a new vanilla Kubuntu 10.04.1 box and set up a single local user account.  As mentioned by other users, I configured networking, picked up my address, dns and search domain from the dhcp server without any issue using the defaults.

I didn't have to do anything at all to the local machine.  I simply checked that I was able to correctly resolve the domain controller using nslookup:

> nslookup mydomain.net

Next I downloaded the 6.0.8269 deb installer from likewise's website and ran the installer as a privileged user with sudo.  It installed without any problem.

Next I did a domainjoin with the command line tool (again with sudo) and successfully joined the domain.

I rebooted the machine and then logged in with a number of my domain user accounts and all of them logged in without any problem.

Without knowing what ubuntique is specifically doing it's pretty difficult to make any suggestions as to how to resolve the issue.  Even the most basic install seems to work and work well.

Just to satisfy my curiosity I decided to try this with some manual tweaks to my resolv.conf and interfaces files and despite having to uninstall network-manager to keep it from stomping on my changes, it also worked without any issue or effort.  As long as my networking was functioning properly Likewise just worked.

I have unplugged my network cable and logged out, and then logged back in with cached credentials and it all worked just fine both with the static IP and the dhcp assigned IP address.

---

### Post by ubuntique on 2010-10-20
> **atworkwithjf said:**
> Today I came in and set up a new vanilla Kubuntu 10.04.1 box and set up a single local user account.  As mentioned by other users, I configured networking, picked up my address, dns and search domain from the dhcp server without any issue using the defaults.

I didn't have to do anything at all to the local machine.  I simply checked that I was able to correctly resolve the domain controller using nslookup:

> nslookup mydomain.net

Next I downloaded the 6.0.8269 deb installer from likewise's website and ran the installer as a privileged user with sudo.  It installed without any problem.

Next I did a domainjoin with the command line tool (again with sudo) and successfully joined the domain.

I rebooted the machine and then logged in with a number of my domain user accounts and all of them logged in without any problem.

Without knowing what ubuntique is specifically doing it's pretty difficult to make any suggestions as to how to resolve the issue.  Even the most basic install seems to work and work well.

Just to satisfy my curiosity I decided to try this with some manual tweaks to my resolv.conf and interfaces files and despite having to uninstall network-manager to keep it from stomping on my changes, it also worked without any issue or effort.  As long as my networking was functioning properly Likewise just worked.

I have unplugged my network cable and logged out, and then logged back in with cached credentials and it all worked just fine both with the static IP and the dhcp assigned IP address.

Sorry, my last post was sort of a public groan. I rebooted the machine to single-user and got my root password reset. **Apparently other fedora 13 users have had this problem as well, where they were never prompted to enter a root password during setup.** I did get AD authentication set up on my machine, without installing Likewise.

I'm using fedora 13 now, so I apologize that this is technically off-topic (though I have another machine running Ubuntu 10.04 and AD authentication, but it is an always-connected server :)) 

HOWEVER, I do have cached logins working now !!

I've disabled selinux because we don't use it in our environment, it was one of the first things I did when I installed.

I appreciate all the input on this thread, thanks. The last thing stumping me is iptables rules for privoxy & oident - I gave up trying to configure it and just disabled it, we don't use it here anyway.

---

### Post by atworkwithjf on 2010-10-20
So is your AD config just using the bare bones LDAP authentication?

---

