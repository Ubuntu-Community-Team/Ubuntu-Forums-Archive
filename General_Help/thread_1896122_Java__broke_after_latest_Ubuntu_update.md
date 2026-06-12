---
title: "Java  broke after latest Ubuntu update"
date: 2011-12-16
forum: General Help
---

### Post by captain_rob on 2011-12-16
Today Ubuntu updated Sun Java on my lucid 10.04, but there is something wrong.

java -version gives:
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) Client VM (build 20.1-b02, mixed mode, sharing)

However when I test Java on ://java.com/en/download/testjava.jsp I get "Something is wrong. Java is not working". Besides when I check about : plugins the Java plugin is now not installed anymore in Firefox 8.0. 

What happened and what can I do?

---

### Post by kamaji792 on 2011-12-16
Running 10.04 Desktop - I looked at the link you posted.  My Firefox 8.0 is told it is working fine but then I am using **Java SE 6 Update 20** (it does tell me an update is available).

Looking in the Firefox **addons** there is no Java addon in Extensions or Plugins, so I don't think that is your problem.

I'd be tempted to remove Java and re-install.  Not sure how else you might track the problem.

atb k

---

### Post by Lampi on 2011-12-16
confirmed in kubuntu lucid 32bit and

- firefox 3.6.24
- chrome 16.0.912.63
- opera 11.60 Build 1185

None of them does list java in about:plugins anymore

I guess one of those 3 packages messed it up:
```
sun-java6-bin_6.26-2lucid1_i386.deb
sun-java6-jre_6.26-2lucid1_all.deb
sun-java6-plugin_6.26-2lucid1_i386.deb
```

Edit: Bugreport: [https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/905026](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/905026)

Bug is confirmed, workaround is the jre binary from the oracle site, or the usual java ubuntu ppas ...

I prefer to wait until they fix it @canonical

---

### Post by ubto66 on 2011-12-16
After updating to java 6 update 30 it does not work.
Is there a way I can get java 6 update 29 back?
Thanks.

---

### Post by Lampi on 2011-12-16
@ubto66: here's how I downgraded to the last working version @canoncial, now java is working again

**Will only work on Lucid and Canonical packages**
[COLOR="Red"]Edit 2: canonical removed last working version, so this won't work anymore, sorry[/COLOR]

```
sudo aptitude install sun-java6-bin=6.26-1lucid1 sun-java6-plugin=6.26-1lucid1
apt-cache policy sun-java6-bin
```

```

sun-java6-bin:
  Installed: 6.26-1lucid1
  Candidate: 6.26-2lucid1
  Version table:
     6.26-2lucid1 0
        500 http://archive.canonical.com/ lucid/partner Packages
 *** 6.26-1lucid1 0
        100 /var/lib/dpkg/status
```

Edit: Optional: Set java packages on hold until they fix it:

```
sudo aptitude hold sun-java6-bin sun-java6-jre sun-java6-plugin
```

once they fixed it it's aptitude unhold ...

---

### Post by ubto66 on 2011-12-16
Thank you lampi.
I'm not that skilled on ubuntu, so all this
#!/bin/bash

OLDPWD=$PWD

mkdir /tmp/revert-java
cd /tmp/revert-java

wget [http://archive.canonical.com/pool/partner/s/sun-java6/sun-java6-bin_6.26-1lucid1_i386.deb](http://archive.canonical.com/pool/partner/s/sun-java6/sun-java6-bin_6.26-1lucid1_i386.deb)
wget [http://archive.canonical.com/pool/partner/s/sun-java6/sun-java6-jre_6.26-1lucid1_all.deb](http://archive.canonical.com/pool/partner/s/sun-java6/sun-java6-jre_6.26-1lucid1_all.deb)
wget [http://archive.canonical.com/pool/partner/s/sun-java6/sun-java6-plugin_6.26-1lucid1_i386.deb](http://archive.canonical.com/pool/partner/s/sun-java6/sun-java6-plugin_6.26-1lucid1_i386.deb)

dpkg -i sun-java6-bin_6.26-1lucid1_i386.deb sun-java6-jre_6.26-1lucid1_all.deb sun-java6-plugin_6.26-1lucid1_i386.deb

apt-cache policy sun-java6-bin

cd $OLDPWD


~$ apt-cache policy sun-java6-bin
sun-java6-bin:
  Installed: 6.26-1lucid1
  Candiate: 6.26-2lucid1
  History:
     6.26-2lucid1 0
        500 [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Packages
 *** 6.26-1lucid1 0
        100 /var/lib/dpkg/status
is to be run in terminal?

---

### Post by Lampi on 2011-12-16
@ubto66: found an easier way - try the aptitude line from terminal

btw: if you are not using lucid this will not work for you -> you'll have to change the line to natty or whatever ubuntu you are using

---

### Post by yndesai on 2011-12-16
> **captain_rob said:**
> Today Ubuntu updated Sun Java on my lucid 10.04, but there is something wrong.

java -version gives:
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) Client VM (build 20.1-b02, mixed mode, sharing)

However when I test Java on ://java.com/en/download/testjava.jsp I get "Something is wrong. Java is not working". Besides when I check about : plugins the Java plugin is now not installed anymore in Firefox 8.0. 

What happened and what can I do?

Once you upgrade the firefox to firefox 8.0 there is one issue. The plugins location
is change to /usr/lib/firefox-8.0/plugins/ from /usr/lib/firefox/plugins/ 

and hence you need to move files from /usr/lib/firefox/plugins/  to   /usr/lib/firefox-8.0/plugins/  especially your link to libnpjp2.so

You can also create a new link in the /usr/lib/firefox-8.0/plugins/

To understand the above you may also refer:

[http://www.java.com/en/download/help/linux_install.xml](http://www.java.com/en/download/help/linux_install.xml)

I could solve my issue in this way hope you can too.

---

### Post by captain_rob on 2011-12-16
Thanks Yndesal, you pointed me in the right direction.

However my firefox plugins are in:
cd /usr/lib/mozilla/plugins
and my Java (from canonical partners repositories) in:
/usr/lib/jvm/java-6-sun/jre/lib/i386

So I could solve my problem with:

cd /usr/lib/mozilla/plugins
sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so

---

### Post by captain_rob on 2011-12-16
Thanks Yndesai, you pointed me in the right direction.

However my firefox plugins are in:
cd /usr/lib/mozilla/plugins
and java (from canonical partners repositories) in:
/usr/lib/jvm/java-6-sun/jre/lib/i386

So I could solve my problem with:

cd /usr/lib/mozilla/plugins
sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so

:)

---

### Post by yndesai on 2011-12-17
I am happy that I could help you & am able to share with a community
which has produced such a marvellous Free Software.

Do mark the thread as "Solved"

---

### Post by ubto66 on 2011-12-18
To Lampi.
I tried
sudo aptitude install sun-java6-bin=6.26-1lucid1 sun-java6-plugin=6.26-1lucid1
apt-cache policy sun-java6-bin
after first removing java in 'softwarecenter'.
A lot of installation took place.

Didn't work.
I also tried to download java 6 update 26 from oracle's homepage.
And install the binfile.  Again installation
took place.  But java didn't work.  If I look in the folders, it appears that
java 6 update30 is still around, and side by side to a java update 26 folder.
So maybe ubuntu still tries to use the java 6 update 30 folder.  I don't
know.
Thanks again.

---

### Post by coulan on 2011-12-19
On 64 bit Ubuntu 10.10, Firefox 3.6.24, the following fix worked for me (as per an earlier posting for 32 bit).  

1. shut down all firefox instances
2. cd /usr/lib/mozilla/plugins
3. create a symbolic link to the java plugin libnpjp2.so, eg:
    sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so .
4. restart firefox; check tools addons - your should see Java Plug-in 

The instructions on Oracle's Java site make reference to a different path for the firefox plugin directory, placing the link in that path did not work for me:
[http://www.oracle.com/technetwork/java/javase/manual-plugin-install-linux-136395.html](http://www.oracle.com/technetwork/java/javase/manual-plugin-install-linux-136395.html)

I did not try to roll back the JDK/JVM update.

Andy

---

### Post by Lampi on 2011-12-19
Rollback makes no sense, since Marc the ubuntu maintainer mentioned there won't be a fix: Oracle announced last august they will revoke all third party license for sun-java. This obviously was the last release before the debian package will be disabled, then removed.

---

### Post by ubto66 on 2011-12-19
Are the commands to be run in terminal?
cd /usr/lib/mozilla/plugins
sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so
Thanks.

---

### Post by Castania on 2011-12-19
The symbolic link (last quoted line) worked for me -- Thanks, Captain Rob!

Ken

> **captain_rob said:**
> Thanks Yndesal, you pointed me in the right direction.

However my firefox plugins are in:
cd /usr/lib/mozilla/plugins
and my Java (from canonical partners repositories) in:
/usr/lib/jvm/java-6-sun/jre/lib/i386

So I could solve my problem with:

cd /usr/lib/mozilla/plugins
sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so

---

### Post by ubto66 on 2011-12-20
You don't have to repeat the post.  I have read it. I'm not skilled on ubuntu, and ask for
detailed instruction.

---

### Post by coulan on 2011-12-20
> **ubto66 said:**
> Are the commands to be run in terminal?
cd /usr/lib/mozilla/plugins
sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so
Thanks.

Yes run these in terminal.  If you are unfamiliar with the command line it may be best to practice a little first and/or read up in one of the on line bash guides.

---

### Post by ubto66 on 2011-12-20
Coulan
 Thank you.
 I ran the commands in terminal, and java works.
 

 Java is a key feature on my computer. I didn't want to make an
 error, that's why I asked to verify that commands must be run in terminal.
 

 If you please, I have some questions.
 When I run commands in
 terminal I often don't know what I write.
 About this subject, that's the case.
 

 I understand   cd /usr/lib/mozilla/plugins.
 I don't understand   sudo ln -s in the second command.
 Can you explain what it does?
 And why does the commands not have to be run again, after
 restarting the computer?
 And does the second command, if another update should arrive, make any  
 trouble in terms of installing an update?
 

 I'm confused, when Lampi writes, that there will be no java updates.
 What then, can you then not run java on ubuntu?

---

### Post by MartijnNL on 2011-12-20
You may want to look at this thread: [http://ubuntuforums.org/showthread.php?t=1897885](http://ubuntuforums.org/showthread.php?t=1897885)

You can use OpenJDK instead, or download Java from the Oracle site.

---

### Post by coulan on 2011-12-20
ln -s creates a symbolic link to the long path name for plugin library.

sudo allows you to run the command as a super user (root) which is common practice for administrative tasks like this.

The symbolic link will remain on the system after you shut down so you do not need to run this command every time you restart your computer.

For more details see : [http://www.thelinuxlink.net/lvlinux/resources/commands/ln.html](http://www.thelinuxlink.net/lvlinux/resources/commands/ln.html)

---

### Post by ubto66 on 2011-12-20
Coulan:
Thank you for the answer.

Martijn:
I used the link [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes/Java6Transition](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes/Java6Transition),
and installed openjdk.
It seems to work, I don't know if all features are supported.
Thank you.

---

### Post by John Wiersba on 2011-12-21
> **Lampi said:**
> @ubto66: here's how I downgraded to the last working version @canoncial, now java is working again

**Will only work on Lucid and Canonical packages**

```
sudo aptitude install sun-java6-bin=6.26-1lucid1 sun-java6-plugin=6.26-1lucid1
apt-cache policy sun-java6-bin
```


Sounds like this is what I want.  However, I'm on Maverick and: 
```

$ sudo aptitude install sun-java6-bin=6.29-1maverick1 
Unable to find a version "6.29-1maverick1" for the package "sun-java6-bin"

```

Neither can I find the Lucid versions you mention.  Any idea what I'm doing wrong?  I have all the Canonical package sources enabled.

---

### Post by MartijnNL on 2011-12-21
> **John Wiersba said:**
> Neither can I find the Lucid versions you mention.  Any idea what I'm doing wrong?  I have all the Canonical package sources enabled.

Are you on a desktop ubuntu? In that case you could try searching in synaptic for the right package (name).

Apart from this: the sun java packages in the ubuntu repositories will be empty (if they aren't already). Check out the link I posted above.

---

### Post by John Wiersba on 2011-12-21
Well, I got things working by manually loading the Oracle JRE tar.gz, but I'd prefer the Canonical packages, if I could get that to work.  My understanding is that the commands given by Lampi should pull in particular version of the packages (the previously released version).  But I'm not sure how to locate a repository that has them.

---

### Post by MartijnNL on 2011-12-21
Well I'm not sure, but as the license has Sun Java has expired, it is very well possible that all the older versions have been removed. (After all, it has expired for older versions as well.

---

### Post by John Wiersba on 2011-12-21
But if the older packages have been removed, then how does Lampi's post (#5 above) work?

---

### Post by MartijnNL on 2011-12-21
This change regarding Java happened yesterday I believe. Lampi's post was 4 days ago.

---

### Post by Lampi on 2011-12-21
yep, canonical removed the previous version from the repository, so post #5 no longer works.

So, thanks to oracle, we are down to one of these options:

- use open-jdk
- use the sun-java binary from the oracle website
- find an ubuntu ppa that still updates sun-java packages

again: thanks oracle ... needless to say I still see rpm and solaris packages on the java website but nothing for debian

---

### Post by John Wiersba on 2011-12-21
Thanks, Lampi!  I figured something like that was going on.  BTW, how did you figure out the exact package name to use in your commands?  Also, do you know of any way to take a checkpoint before installing updates, so that you can rollback if the update fails?

BTW, a bug was filed for this whole issue at [bugs.launchpad]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/906388").  Also, see this [OMGUbuntu]("http://www.omgubuntu.co.uk/2011/12/java-to-be-removed-from-ubuntu-uninstalled-from-user-machines/") post.

In my case, I'm all set now, since I installed the binaries from the oracle website and it wasn't too painful getting the plugin linked to firefox (although I had to guess at where to create the symlinks).  But what about the poor masses who were expecting an update to **fix** problems, not **create** them?!?

---

### Post by suresnjain on 2011-12-21
Right your are Mr John, i am one of the poor masses who never expected a problem after this update.Now, using older sun java version as iced tea plugin is not good for some websites.

---

### Post by paxxus on 2011-12-21
Firefox crashes for me with icedtea.

---

### Post by paxxus on 2011-12-21
Tried the Oracle binary and the instructions for the symbolic link. My Firefox freezes when I go to the Java test site :(

---

### Post by kauboy on 2011-12-21
This is how I fixed my Firefox 9.0 missing Java plugin on Ubuntu 10.04 LTS 32bit.

Two things happened almost simultaneously.

1. Sun Java 1.6.0_26-b03 update.
2. Firefox 9.0 update.

Turned out that my real issue was the Firefox 9.0 update, not the Java update.

Firefox 9.0 creates its own plugins directory at /usr/lib/firefox-9.0/plugins and this does not have a link to the Java plugin.

Try the following:

```
sudo updatedb
locate libnpjp #This returns your_path_to_libnpjp2.so, /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libnpjp2.so on my box.

cd /usr/lib/firefox-9.0/plugins
sudo ln -s your_path_to_libnpjp2.so #My case, /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libnpjp2.so
```

Restart Firefox and check Tools-->Add-ons-->Plugins. You should see Java plugin show up there now. :)

---

### Post by John Wiersba on 2011-12-21
If you've set things up properly, you should be able to remove the symlink, restart firefox, and get a failure message from the test site.  Then, stop firefox, restore the symlink, restart firefox, and get a success message from the test site.

In my case, because of having noscript installed, I had to click through to allow the site to run.

---

### Post by paxxus on 2011-12-29
Thanks kauboy, you saved my day! My banking and VPN client is now running again, the only thing that doesn't work is the Java test site. Oh well.

---

### Post by skywalk on 2012-01-01
kauboy, thanks:
Your instructions work fine for me. I only need to change my version of Firefox 9.0.1.
After that the java plugin appears on the Add-ons and java is runnig fine.

---

### Post by yndesai on 2012-01-05
> **ubto66 said:**
> Coulan
 I understand   cd /usr/lib/mozilla/plugins.
 I don't understand   sudo ln -s in the second command.
 Can you explain what it does?

 And why does the commands not have to be run again, after
 restarting the computer?

I recommend you to read the man pages (ie user manual for linux)
well for knowing what happens with the command on terminal
you can type 
```
ln --help
```
once the link is created in the required folder you will not need to 
do the same again till the time you change your setup ie firefox or java

---

