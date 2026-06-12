---
title: "Need Oracle Java for School"
date: 2012-02-27
forum: General Help
---

### Post by allan.w.macdonald on 2012-02-27
Hello Ubuntu Community,

I am using Ubuntu 10.04 LTS and firefox 10.0.2.  I need Oracle (Sun) Java (not OpenJDK) for my school assignments.  It is not working and I am so desperate that I may need to borrow a dreaded W@!#$ws machine!

I tried to install the latest Oracle Java by following the instructions here:

[http://sites.google.com/site/easylinuxtipsproject/java]("http://sites.google.com/site/easylinuxtipsproject/java")

Unfortunately, my browser does not seem to be detecting the existence of the plugin.  Here is the contents of my plugins directory:

```

myname@my_computer:~/.mozilla/plugins$ ls -al
total 8
drwxr-xr-x 2 myname myname 4096 2012-02-27 20:04 .
drwxr-x--- 6 myname myname 4096 2012-01-14 09:44 ..
lrwxrwxrwx 1 myname myname   45 2012-02-27 20:04 libnpjp2.so -> /opt/java/32/jre1.6.0_31/lib/i386/libnpjp2.so
myname@my_computer:~/.mozilla/plugins$

```

I even tried copying this link (using sudo of course) everywhere that I thought Firefox would look to find the plugin:

```

/usr/lib/firefox/plugins
/usr/lib/firefox-addons/plugins
/usr/lib/mozilla/plugins
/usr/lib/mozilla-firefox/plugins

```

This was working before but Oracle posted a Java update and ever since I installed the update, it no longer worked.  Can anyone help me?  I will be eternally grateful.

Best regards,

Allan Macdonald

p.s. Why are there so many places for keeping Firefox plugins?  Why is it that I cannot make Firefox only use one location to keep plugins?

---

### Post by Disabled20240622 on 2012-02-27
I've not tried it myself, but this PPA looks promising: [https://launchpad.net/~webupd8team/+archive/java](https://launchpad.net/~webupd8team/+archive/java)

Hopefully the installer includes the forefox plugin setup like the sun ones used to.

---

### Post by sammiev on 2012-02-27
I prefer [this]("http://sites.google.com/site/easylinuxtipsproject/java") one myself. :)

---

### Post by Disabled20240622 on 2012-02-27
Off topic a bit: The retraction of sun java from the repos has largely passed me by.

I don't use any java apps on my own machine, that I know of.

I do use quite a few at work, but there we have our own JVM (they make it one floor up from me).

Does anyone know if the new oracle java (which I'm told is openJDK based) will have such horrid license restrictions?

---

### Post by QIII on 2012-02-27
Use sammiev's suggestion.  I have been recommending it for years.

Off topic answer:  OpenJDK is an open source implementation. 

It is supposed to become the reference implementation for Oracle, but not to become Oracle's intellectual propery (to my knowledge).

---

### Post by Miljet on 2012-02-27
You did remove the IcedTea browser plugin, didn't you? It will often preempt the new plugin if not removed.

---

### Post by allan.w.macdonald on 2012-02-27
Thanks to sammiev and QIII.  Unfortunately, that is the exact procedure that I tried, unsuccessfully.  I am not sure what I am doing wrong.  Any help in that regard would be most appreciated.

Miljet, I believe I did do so.  I will go back and check that again - maybe it is lurking in one of the many possible places plugins are kept.

I also have not tried the PPA route; I have read some advice to the effect that PPA's can be risky.  If I have to, I will try that as a last resort but I would rather try to find out why the recommended procedure is not working.

Many thanks to all who responded.

Cheers,

Allan

---

### Post by allan.w.macdonald on 2012-02-27
Update - I just looked through the directories I listed in my original post; no iced-tea plugin.  I also checked Ubuntu Software Center and the Icedtea plugin is showing as not installed (Synaptic agrees).

Sigh.  I guess I'll keep using the Evil Empire's box until I can solve this.  I am not yet 100% Linux although I am striving to be!

Cheers,

Allan

---

### Post by QIII on 2012-02-28
If you were not successful the first time with the tutorial, try again.  Cut and paste the commands if necessary.  You may have inadvertently mistyped or skipped a step.  Unless you have something pretty unusual in your installation, those instructions should work.  Be very careful to create the symbolic link exactly as described.  If it does not work, you would be the first person for whom it did not work since I started recommending that tutorial years ago.

It would be helpful for others if we could figure out why it didn't work.

---

### Post by sammiev on 2012-02-28
You may also want to start at the bottom where it has you removing other packages first.

---

### Post by Bobhuber on 2012-02-28
Remove only the IcedTea Java-plug-in. Leave OpenJDK itself on your hard disk or the plugin will not work. Also make sure the symlinks are made for all users if more than one. 
The link you have looks correct however.

---

### Post by Gremlinzzz on 2012-02-28
Go tools on your firefox browser choose add ons click plugins and see how many  java plugins you have,if more than one disable the older one

later you can remove it using synaptic

---

### Post by allan.w.macdonald on 2012-03-01
Thanks to all who responded... I'll go over the procedure again with extreme care and report back.

Cheers,

Allan

---

### Post by allan.w.macdonald on 2012-03-01
Update:

Following the instructions in the howto, I did the following:

1. As root (using sudo), I removed the java directory from /opt
2. I removed any and all symbolic links to the plugin, including the one in my home directory (~/.mozilla/plugins).
3. Repeated the install instructions, to the letter.
4. Restarted my browser.

There are no java plugins at all showing up in the list of plugins displayed when I type ```
about:plugins
``` in my browser.

My browser is just not picking it up.  What did I break?

Here are the commands I used:

```

sudo rm ~/.mozilla/plugins/libnpjp2.so
sudo rm -rf /opt/java
sudo mkdir /opt/java
sudo mkdir /opt/java/32
sudo cp ~/downloads/installers/java/jre-6u31-linux-i586.bin /opt/java/32
sudo chmod 755 /opt/java/32/jre-6u31-linux-i586.bin
cd /opt/java/32
sudo /opt/java/32/jre-6u31-linux-i586.bin
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32/jre1.6.0_31/bin/java" 1
sudo update-alternatives --set java /opt/java/32/jre1.6.0_31/bin/java
ln -s /opt/java/32/jre1.6.0_31/lib/i386/libnpjp2.so ~/.mozilla/plugins/

```

Aside from the fact that java is not working, there were no error messages resulting from the above commands.  Everything seemed to go OK.

Suggestions anyone?  Questions?  Did I miss anything?  Is there anything else I can post that might help someone identify the issue?

Allan

---

### Post by QIII on 2012-03-01
There's a difference between Java not working and the plugin not working.  Let's see if we got the Java part OK.

Would you post the results of 

```
java -version
```

---

### Post by allan.w.macdonald on 2012-03-01
```

java version "1.6.0_31"
Java(TM) SE Runtime Environment (build 1.6.0_31-b04)
Java HotSpot(TM) Server VM (build 20.6-b01, mixed mode)

```

---

### Post by allan.w.macdonald on 2012-03-01
Folks,

By the way, my version of Ubuntu is 10.04 LTS Lucid Lynx, not 8.04.  For some reason, I can't edit my own profile details.  Strange.

Allan

---

### Post by sammiev on 2012-03-01
Here's mine.

java version "1.6.0_31"
Java(TM) SE Runtime Environment (build 1.6.0_31-b04)
Java HotSpot(TM) 64-Bit Server VM (build 20.6-b01, mixed mode)

[Verified]("http://java.com/en/") Java Version
Congratulations!
You have the recommended Java installed (Version 6 Update 31).

---

### Post by allan.w.macdonald on 2012-03-01
Cool!  Now all I need to do is find out why my browser does not detect the presence of the plugin.

---

### Post by allan.w.macdonald on 2012-03-01
...but I don't know how.

---

### Post by inf1nity on 2012-03-02
I want to install JDK and BlueJ along with it. I looked at the tutorial, it seems like it has insructions for installing only JRE.  How do i install JDK? I tried to install openjdk-7 through synaptic, but it failed to download some packages (they were called icedtea-something). Then it told me to check my internet connection, which was working perfectly.. Please help.


P.S.
I already have the bluej.deb package file. I just need JDK.
Mine is 11.10 Oneiric Oncelot.

---

### Post by QIII on 2012-03-02
Allan --

Sorry I didn't get back to you.  Dinner with the wife, my son came over, my daughter called, one thing led to another and then one of my BOINC machines decided to to "Tango Uniform" on me (old military term, definition not for polite company.)  Fortunately is was just an hdd that was there as a network storage device that was, even more fortunately, empty.  But it kept the mobo from POSTing.

Anyway.

I'll review this tomorrow and see what's up.  There is something wrong about the symbolic link to the plugin.  You probably have a perfectly good plugin, but your browser can't find it.  At the very worst we can put that symlink in another spot where it can live happily with all the other symlinks to plugins.

I don't think we're far off.  If I can get you there, I'll explain what is going on.

---

### Post by allan.w.macdonald on 2012-03-02
Thanks QIII!  It is nice to see that you have priorities; I respect that.  I also get the phonetic alphabet reference.  Situation normal...  Nevertheless, I am looking forward to your next reply.

Cheers,

Allan

---

### Post by QIII on 2012-03-02
Ah.  Good thing you raised this, so I could see it.

Could you confirm two things?

Could you check to see if check to see that /opt/java/32/jre1.6.0_31/lib/i386/libnpjp2.so exists and if there is an unbroken link to it in ~/.mozilla/plugins?

Depending on your file manager, the icon indicating the link is broken may differ, but you can right-click and click properties to see if it's broken or not.

---

### Post by allan.w.macdonald on 2012-03-03
Hi QIII,

Hopefully, this will answer your question:

```
myname@mycomputer:~$ ls -al /opt/java/32/jre1.6.0_31/lib/i386/libnpjp2.so 
-rwxr-xr-x 1 root root 74038 2012-01-20 14:55 /opt/java/32/jre1.6.0_31/lib/i386/libnpjp2.so
myname@mycomputer:~$ ls -al .mozilla/plugins/total 8
drwxr-xr-x 2 myname myname 4096 2012-03-01 21:32 .
drwxr-x--- 6 myname myname 4096 2012-01-14 09:44 ..
lrwxrwxrwx 1 myname myname   45 2012-03-01 21:32 libnpjp2.so -> /opt/java/32/jre1.6.0_31/lib/i386/libnpjp2.so
myname@mycomputer:~$ 
```

Cheers,
Allan

---

### Post by allan.w.macdonald on 2012-03-03
In addition, under Nautilus, the link's icon in ~/.mozilla/plugins looks like a sheet of lined paper with a heavy curved arrow on the bottom right corner and a closed padlock on the upper right corner.  Before, I have seen a broken link show up with a big X over the arrow but that is not the case this time.

---

### Post by allan.w.macdonald on 2012-03-04
Is this thread still alive?

---

### Post by cryptotheslow on 2012-03-04
The closed padlock on the icon in Nautilus makes me think it is a permissions problem - although from your earlier posting of the file listings they appear to be fine.

Does the padlock disappear if you start Nautilus with gksu ?

```
gksu nautilus
```

** Caution - at that point you are running Nautilus with elevated privilege so take care!

---

### Post by allan.w.macdonald on 2012-03-04
Hi cryptotheslow,

Thanks for your question.

Yes, the padlock disappears when I view the icon from a root session.  That's no surprise since the file is owned by root and the file's world permissions are set to execute only.  I am not sure how the plugin file works, whether it is a purely executable file or whether or not the file should also have world read permission as well.  Nevertheless, I followed the directions in the howto which said to set the permissions of the binary installer (world execute) but it did not instruct me to change the permissions of any of the individual files in the extracted directory heirarchy.

Should I be changing the permissions of the link target?  What should the permissions be?  If this step was required, one would think that it would have been included in the howto.

Cheers,

Allan

---

### Post by cryptotheslow on 2012-03-04
The file has world read permission already as the last three letters of the alphabet soup are r_x

I've never setup this particular plugin but if you let me know what Ubuntu version and Firefox version you're running I'll see if I can replicate the problem (I have a gadzillion different version installs in various vm's for breaking.. umm I mean testing things in).

I can't see you should need to change the permissions of the target file for the link - all that could be done is to add group and world write permissions - which for a shared library file wouldn't be sane.

As an aside - you haven't by any chance got an AppArmor profile in force for Firefox have you?

This command will show what AppArmor is currently configured to enforce:
```
sudo /etc/init.d/apparmor status
```Look for profiles in "enforce mode" that mention firefox. Just a long shot on that but AppArmor restricts file access.

***edit - ***re-read the original post and have Ubuntu and FF version, going to tinker.

---

### Post by allan.w.macdonald on 2012-03-04
Thanks Cryptotheslow,

AppArmor?  I have never heard of it before.  I just googled it and the first result was a wikipedia article full of gobbledegook.  I hope I do not have to try to sort out what this might be doing to prevent the java plugin from working!

Here's the status:

```

apparmor module is loaded.
15 profiles are loaded.
14 profiles are in enforce mode.
   /sbin/dhclient3
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/bin/freshclam
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/firefox-10.0.2/firefox{,*[^s][^h]}
   /usr/lib/firefox-10.0.2/firefox{,*[^s][^h]}//firefox_java
   /usr/lib/firefox-10.0.2/firefox{,*[^s][^h]}//firefox_openjdk
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
   /usr/share/gdm/guest-session/Xsession
1 profiles are in complain mode.
   /usr/sbin/ntpd
6 processes have profiles defined.
5 processes are in enforce mode :
   /sbin/dhclient3 (8270) 
   /usr/bin/freshclam (2585) 
   /usr/lib/firefox-10.0.2/firefox{,*[^s][^h]} (3522) 
   /usr/lib/firefox-10.0.2/firefox{,*[^s][^h]} (4210) 
   /usr/sbin/cupsd (2701) 
1 processes are in complain mode.
   /usr/sbin/ntpd (8385) 
0 processes are unconfined but have a profile defined.

```

Gulp!  I see "java" listed under the heading "enforce mode".  Is this my problem?

---

### Post by cryptotheslow on 2012-03-04
Hi Allan,

Well knock me over with a feather!!! That was just a stab in the dark as I tripped myself up with AppArmor the other week on a totally unrelated application.

By default AppArmor is not active for Firefox but there is an Ubuntu provided profile for it that can be activated.

Don't be too alarmed by the gobbledegook - essentially what AppArmor does is enforce what files or directories a given application can access. It basically confines things to only the files they should be accessing - it is a very powerful security tool in the right hands (my hands are not those hands by a mile or more sadly).

Looking at the enforced profiles you list I can see firefox java and openjdk mentioned so it is reasonable to assume AppArmor is denying access to your newly installed java plugin.

Much wisdom on AppArmor here from bodhi.zazen:
[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

Close Firefox, open a Terminal and execute:
```
tail -F /var/log/messages
```

Then open Firefox again while watching the Terminal window - I expect you will see all manner of [AUDIT] entries appearing there.

Who administers your PC for you? You do not have a default / generic security setup, so this may be best to refer to them to address.

Let's confirm it is AppArmor that is confining you :)

---

### Post by allan.w.macdonald on 2012-03-04
Thanks again, cryptotheslow

For one thing, I am both the administrator and sole user of said computer  (albeit not a particularly competent one) so, unfortunately for me, I cannot slough this off to someone else.

Just one entry in messages appears when I start firefox:

```

Mar  4 22:25:02 (none) kernel: [56244.713976] type=1503 audit(1330914302.497:42):  operation="open" pid=9020 parent=1 profile="/usr/lib/firefox-10.0.2/firefox{,*[^s][^h]}" requested_mask="::r" denied_mask="::r" fsuid=1001 ouid=0 name="/etc/apt/sources.list"

```

I am not quite sure what this means.  I certainly do not see any mention of java or jdk in the messages, but what do I know anyway. I will have a look at that other thread you mentioned.  More questions are sure to come.

Cheers,

Allan

---

### Post by allan.w.macdonald on 2012-03-04
Hi cryptotheslow,

Wow.  It will take me all night to read up on this and actually understand it so I need a shortcut:

1. Do the lines in an AppArmor profile allow or prevent whatever the line has in it?

2. Is the problem the fact that the path to the java plugin isn't shown in the AppArmor profile?

3. Can I just find the AppArmour profile pertaining to firefox and add a line specifying the path to the file pointed to by the symbolic link in my ~/.mozilla/plugins directory?

Cheers,
Allan

---

### Post by cryptotheslow on 2012-03-04
Hi Allan,

As the sole admin and user of the PC you should know how the firefox AppArmor profiles became enforced. They aren't enforced in a default installation.

The messages you quoted show AppArmor denying Firefox reading /etc/apt/sources.list - doesn't seem sane to me why a browser would be going there.

Try putting AppArmor into complain mode rather than enforce for firefox and monitor messages. That will allow firefox to do what it wants while you can monitor it.

Without seeing your AppArmor profile files, questions 1 2 and 3 can't be answered with certainty.

~crypto~

---

### Post by allan.w.macdonald on 2012-03-05
Thanks cryptotheslow!

I've attached a copy of my firefox profile.

I also found a wiki here which is a bit more my style of documentation:

[http://wiki.apparmor.net/index.php/Main_Page]("http://wiki.apparmor.net/index.php/Main_Page")

I will have to read up a bit to understand what's going on but any quick pointers will be greatly appreciated.

Gotta go to work now.  Later,

Cheers
Allan

---

### Post by cryptotheslow on 2012-03-05
Firstly I'd put the firefox apparmor profile into complain rather than enforce mode (in complain mode it will just log transgressions rather than stop them dead).

Be sure to have all instances of firefox closed, put the profile into complain mode then start up firefox and see if it picks up the plugin.

If it does - then look at /var/log/messages for apparmor complaints and alter the apparmor firefox profile to suit before putting it back into enforce mode.

From your previous post about what apparmor logged on starting firefox I think it may well be a red herring I've thrown you - there's no complaints there about the plugin file (or link to it) and your apparmor firefox profile appears to allow reading anything in your home dir .mozilla folder so the link should be unimpeded. However, apparmor also enforces based on the destination of the link, I've not had a chance to study your profile file to see if that is excluded - I expect not as you seem to have no logs suggesting it is being blocked.

---

### Post by allan.w.macdonald on 2012-03-05
Hello everyone,

Thanks to all who posted so far.

Here is an update:

I closed my browser, opened a terminal, ran the command "sudo complain firefox" and got the following response: "Setting /etc/apparmor.d/usr.bin.firefox to complain mode."

This didn't seem to help.  When I restarted the browser and typed ```
about:plugins
```" in the address bar, no java plugin was listed.

I am still at a loss.  Besides, I did mention in my original post that the java plugin worked once but when I followed the remove and update instructions, it stopped working.

I am not a developer so my comprehension of script languages is limited at best; nevertheless, at line 225 of the profile file I posted, it appears that the java plugin is given cx permission under a child profile called "firefox_java".  However, the path of this line doesn't seem to match any of the paths mentioned in this Howto: [http://sites.google.com/site/easylinuxtipsproject/java]("http://sites.google.com/site/easylinuxtipsproject/java").  Is this my problem?  I am confused by this.  Do I have to edit the profile paths to allow firefox to find the files in /opt/java?

Otherwise, am I barking up the wrong tree here?

br,
Allan

---

### Post by sammiev on 2012-03-05
> **allan.w.macdonald said:**
> Hello everyone,

Thanks to all who posted so far.

Here is an update:

I closed my browser, opened a terminal, ran the command "sudo complain firefox" and got the following response: "Setting /etc/apparmor.d/usr.bin.firefox to complain mode."

This didn't seem to help.  When I restarted the browser and typed ```
about:plugins
```" in the address bar, no java plugin was listed.

I am still at a loss.  Besides, I did mention in my original post that the java plugin worked once but when I followed the remove and update instructions, it stopped working.

I am not a developer so my comprehension of script languages is limited at best; nevertheless, at line 225 of the profile file I posted, it appears that the java plugin is given cx permission under a child profile called "firefox_java".  However, the path of this line doesn't seem to match any of the paths mentioned in this Howto: [http://sites.google.com/site/easylinuxtipsproject/java]("http://sites.google.com/site/easylinuxtipsproject/java").  Is this my problem?  I am confused by this.  Do I have to edit the profile paths to allow firefox to find the files in /opt/java?

Otherwise, am I barking up the wrong tree here?

br,
Allan

Try [step #9]("http://sites.google.com/site/easylinuxtipsproject/java") and close your browser. Goto [Java.com]("http://java.com/en/") and test your install.

---

### Post by allan.w.macdonald on 2012-03-05
Hi, cryptotheslow,

I am sorry I missed your post.  I was in the middle of writing my post when you posted your message.  I think you are right about the red herring although I am not sure why myself.  Nevertheless, the plugin is still broken and setting the firefox profile to complain mode did not help.

I have to get back to studying; I am getting way too deep here.

I will check back tomorrow.

Cheers,

Allan

---

### Post by allan.w.macdonald on 2012-03-05
> **sammiev said:**
> Try [step #9]("http://sites.google.com/site/easylinuxtipsproject/java") and close your browser. Goto [Java.com]("http://java.com/en/") and test your install.

Thanks but I tried that already (several times, I might add) to no avail.  java is installed; I can run the Java control panel and can get the java version from the command line.  I also tried the install command with the Apparmor profile set to complain mode and still it didn't work.  When I open the browser, go to the Java test page and click on the Verify Java Version button, it just sits there spinning for a long time.

When I access this page, Firefox does suggest installing the missing iced-tea plugin.  Unfortunately, for the course I am taking, the on-line learning software works badly with the iced-tea plugin.  I need the Oracle Java plugin to access the course material.

I was using 6u30 and it seemed to work OK but when I tried to upgrade to 6u31, it didn't work.  I even tried downgrading to 6u30 again and that didn't work either.  I should have left well enough alone.

---

### Post by allan.w.macdonald on 2012-03-10
Hello folks,

It's me again.  I would still like to solve this.

I wrote a script that performs all the steps automatically (I got tired of typing commands).  I wonder if someone would like to review it for me to see if there are any mistakes.

Many thanks in advance.

Allan

---

### Post by allan.w.macdonald on 2012-03-12
Hi,

I am still hoping to fix this problem.  Unfortunately, my last couple of posts have gone unanswered.  Does the silence mean there is no solution to this problem?

Is there a way to escalate this, somehow?

Thanks in advance

Allan

---

### Post by allan.w.macdonald on 2012-03-14
Hello everybody,

I am going to assume that, due to the lack of replies, then

1. No one has identified a problem with the script I posted.

2. No one has indentified any other problem that may explain the behaviour.

3. The installation procedure I am using is correct.

4. My system is not broken.

5. Since I am doing everything right, the only logical conclusion is that the software has a bug preventing it from working.

I will look for a place to report this bug.  If anyone can help me find a place to report the bug, please let me know.  Nevertheless, I will be going to the Mozilla bug tracker and Ubuntu bug tracker.  I haven't decided yet whether to try to report a bug through the Oracle bug database.  I will try that too if the others do not pan out.

My thanks to all who replied with comments and suggestions.

Best Regards to all,

Allan

---

### Post by sammiev on 2012-03-14
I suggest you read [this]("http://sites.google.com/site/easylinuxtipsproject/java") from top to bottom. Then start where you need to start and move back to the top and start there after wards. It works for the rest of us. Please post back after you have given it a real try. GL :)

---

### Post by allan.w.macdonald on 2012-03-15
Thanks, sammiev,

The heart of the matter is that *have* gone through the web page to which you refer, repeatedly, making sure every step was performed correctly.  Unfortunately, the Java plugin still does not work (i.e. it is not picked up by Firefox).  I made sure my system was up to date and repeated the entire process, to no avail.  I reinstalled the IcedTea plugin (to make sure any dependencies were corrected) and then repeated the entire process again.  Firefox does not pick up the Java plugin.

However, I still could be missing something (sometimes one can be blind to what is plainly visible to others).

I posted that script because it contains a summary of all the commands I used in the above-referenced web page (I took out the extra 32 directory but including it did not make a difference).  If I am missing something, that would be in the script.  Perhaps someone could briefly have a look and confirm whether or not there is a missing or erroneous command or step.  If someone looked at that and said "You missed doing xxx" or "that path is wrong", maybe my problem would be solved.

Nevertheless, I am giving up for now.  I will stick with the borrowed proporietary system for my school work since I need the performance now.  I can debug my Unbuntu system after exams.

Thanks to all who responded.

By for now.

Allan

---

### Post by zero2xiii on 2012-03-15
Hay,

I have read through the entire thread and it seems there is more wrong than right. But non the less.

Try running firefox in gksudo mode ```
gksudo firefox
``` and see if it picks up your java plug-in.. Might be a permission error.

Cherz

---

### Post by sammiev on 2012-03-15
> **zero2xiii said:**
> Hay,

I have read through the entire thread and it seems there is more wrong than right. But non the less.

Try running firefox in gksudo mode ```
gksudo firefox
``` and see if it picks up your java plug-in.. Might be a permission error.

Cherz

You have a good point there zero2xiii. Sure is worth the try. Thanks for adding to this thread.

---

### Post by allan.w.macdonald on 2012-03-15
Thanks!  I'll let you know what happens!

---

### Post by allan.w.macdonald on 2012-03-15
Ah hah!  You are going to like this one!  Here is what happened:

When I first tried the command "gksudo firefox", it complained about configuration being funny (Sorry, I didn't capture the complaint).  I then exited Firefox. 

I then thought, "what about the plugin?"  So, I copied the link to the plugin from my own home directory into /root/.mozilla/plugins and repeated the "gksudo firefox" command.  Here's what appeared in terminal:

```

myname@mycomputer:~$ gksudo firefox
LoadPlugin: failed to initialize shared library /opt/java/jre1.6.0_31/lib/i386/libnpjp2.so [/opt/java/jre1.6.0_31/lib/i386/libnpjp2.so: cannot open shared object file: Permission denied]

```

Hmmm.  When I typed about:plugins in the browser address bar, the IcedTea plugin appeared in the list.  I think the reason that this happened is that I had re-installed the IcedYea plugin after my last failed attempt to install the Oracle Java Plugin. (Well, I need to have *some* sort of java plugin!)

Anyway, realizing the error, I removed the IcedTea Plugin:

```

myname@mycomputer:~$ sudo apt-get remove icedtea6-plugin 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  icedtea6-plugin
0 upgraded, 0 newly installed, 1 to remove and 5 not upgraded.
After this operation, 274kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 742376 files and directories currently installed.)
Removing icedtea6-plugin ...

```

Now, when I run "gksudo firefox", there is no error message but, also, _***no plugin!***_

```

myname@mycomputer:~$ gksudo firefox
myname@mycomputer:~$ 

```

Very strange!

All ideas welcome!

Cheers,

Allan

---

### Post by sammiev on 2012-03-15
Now attach Oracle Java to FF and close browser and restart FF.

---

### Post by allan.w.macdonald on 2012-03-15
> **sammiev said:**
> Now attach Oracle Java to FF and close browser and restart FF.

???

What do you mean?  I am not familiar with the phrase "attach Oracle Java to FF".  What is "attach"?  Is this a command?  Please define.  Perhaps this is the step I am missing.

Assuming you meant that I needed to "install" Oracle Java again, I entered the following commands:

```

sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/jre1.6.0_31/bin/java" 1

```

No messages were returned (assume success).

and

```

sudo update-alternatives --set java /opt/java/jre1.6.0_31/bin/java

```

Again, no messages were returned (assume success).

Here are the contents of my /root/.mozilla/plugins directory

```

 ls -al /root/.mozilla/plugins/
total 140
drwxr-xr-x 2 root root   4096 2012-03-15 18:53 .
drwxr-xr-x 5 root root   4096 2012-03-15 18:51 ..
lrwxrwxrwx 1 root root     42 2012-03-15 18:53 libnpjp2.so -> /opt/java/jre1.6.0_31/lib/i386/libnpjp2.so
-rwxr-xr-x 1 root root 127260 2009-02-14 10:28 nppdf.so

```

Here is the result of the java -version command:
```

java version "1.6.0_31"
Java(TM) SE Runtime Environment (build 1.6.0_31-b04)
Java HotSpot(TM) Server VM (build 20.6-b01, mixed mode)

```

Everything seems OK but, when I run firefox as root, and type "about:plugins" in the browser, no java plugin is listed.  If I go to java.com and test my installation, no java is detected.

If the above actions equate to the term "attach", then the "attach" was not successful.

We seem to be going in circles here.  The discussion always boils down to someone asking me to repeat the same actions over and over again.  Doing the same thing over and over will only yield the same results.  Someone needs to ask me to do something different, something that will help to troubleshoot the problem.

---

### Post by allan.w.macdonald on 2012-03-15
](*,)

---

### Post by sammiev on 2012-03-15
[HTML][/HTML]> **allan.w.macdonald said:**
> ???

What do you mean?  I am not familiar with the phrase "attach Oracle Java to FF".  What is "attach"?  Is this a command?  Please define.  Perhaps this is the step I am missing.

Assuming you meant that I needed to "install" Oracle Java again, I entered the following commands:

```

[HTML]sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/jre1.6.0_31/bin/java" 1[/HTML]

```

No messages were returned (assume success).

and

```

sudo update-alternatives --set java /opt/java/jre1.6.0_31/bin/java

```

Again, no messages were returned (assume success).

Here are the contents of my /root/.mozilla/plugins directory

```

 ls -al /root/.mozilla/plugins/
total 140
drwxr-xr-x 2 root root   4096 2012-03-15 18:53 .
drwxr-xr-x 5 root root   4096 2012-03-15 18:51 ..
lrwxrwxrwx 1 root root     42 2012-03-15 18:53 libnpjp2.so -> /opt/java/jre1.6.0_31/lib/i386/libnpjp2.so
-rwxr-xr-x 1 root root 127260 2009-02-14 10:28 nppdf.so

```

Here is the result of the java -version command:
```

java version "1.6.0_31"
Java(TM) SE Runtime Environment (build 1.6.0_31-b04)
Java HotSpot(TM) Server VM (build 20.6-b01, mixed mode)

```

Everything seems OK but, when I run firefox as root, and type "about:plugins" in the browser, no java plugin is listed.  If I go to java.com and test my installation, no java is detected.

If the above actions equate to the term "attach", then the "attach" was not successful.

We seem to be going in circles here.  The discussion always boils down to someone asking me to repeat the same actions over and over again.  Doing the same thing over and over will only yield the same results.  Someone needs to ask me to do something different, something that will help to troubleshoot the problem.

[HTML][/HTML]ln -s /opt/java/64/jre1.6.0_31/lib/amd64/libnpjp2.so ~/.mozilla/plugins/[HTML][/HTML]

this is for 64 bit systems only

---

### Post by allan.w.macdonald on 2012-03-16
> **sammiev said:**
> [HTML][/HTML]

[HTML][/HTML]ln -s /opt/java/64/jre1.6.0_31/lib/amd64/libnpjp2.so ~/.mozilla/plugins/[HTML][/HTML]

this is for 64 bit systems only

If you had actually read my previous postings in this thread, you would have realized that I have done that already, repeatedly.  As a matter of fact, that is the last line in the script I posted.  It did not work the multitude of times I already tried it, so it certainly can not work now.  Nevertheless, I will waste my time, follow your advice and repeat the command, yet again. Maybe, because the gods have decreed so, the command shall succeed.  I will get back with the results.

I will do the same thing with the root account to see if it works there too.

Wish me luck (that's the only thing that will make this work!)

Cheers,

Allan

---

### Post by allan.w.macdonald on 2012-03-16
sammiev,

Here is the command I sent:

```

ln -s /opt/java/jre1.6.0_31/lib/i386/libnpjp2.so ~/.mozilla/plugins/

```

Guess what happened?


...


Nothing!

Just as I expected.  That is what happens when you do the same thing over and over again.  Still no java plugin in the browser.  I did this in both my own account and the root account.

So, do you have any other suggestions, especially helpful ones? I am all ears (or actually eyes in this case).  If not, I am willing to entertain suggestions from other forum members.

Allan

p.s. I am starting to feel like a sucker.

---

### Post by sammiev on 2012-03-16
After all you have done and after the last try you did before running that command I thought that would polish it off. This is by me and I feel bad for you. I will follow the out come of this thread and read on so I maybe able to help the next folk with the same problem. GL

---

### Post by allan.w.macdonald on 2012-03-16
> **sammiev said:**
> After all you have done and after the last try you did before running that command I thought that would polish it off. This is by me and I feel bad for you. I will follow the out come of this thread and read on so I maybe able to help the next folk with the same problem. GL

Sorry sammiev for coming down on you like that but, as you can obviously gather, I am very frustrated.

I need the Oracle java plugin because the IcedTea plugin crashes my browser when I log in to my university's online learning web site.  Consequently, I am forced to use a borrowed computer running the horrid M$$@#%@# W#$%$@$ operating system.

What is more annoying is that I did have an earlier version of Oracle java that actually worked (6u30) but when I learned of the new version of Java, I thought I was doing the right thing and followed all the instructions [here]("http://sites.google.com/site/easylinuxtipsproject/java") to remove the old version and install the new one.  That is when all my troubles began.

I am not even able to downgrade to the earlier version.  I tried installing the older version using the newer instructions but it did not work.  Plus, the howto has been updated to the new version so I do I am not sure the instructions are even valid for the earlier version anymore.

I still have the installer for the earlier version.  Perhaps if someone still has the correct instructions for 6u30 he or she can kindly post them so that I can try to see if I am doing the downgrade process correctly.

Allan

---

### Post by sammiev on 2012-03-16
I always update my java before the instructions are correct. In your case if you want to try 30 instead of 31 just change the 31 to 30 and your good to go. Make sure you download version 6.30 first. GL

---

### Post by zero2xiii on 2012-03-17
> **allan.w.macdonald said:**
> 
What is more annoying is that I did have an earlier version of Oracle java that actually worked (6u30) but when I learned of the new version of Java, I thought I was doing the right thing and followed all the instructions [here]("http://sites.google.com/site/easylinuxtipsproject/java") to remove the old version and install the new one.  That is when all my troubles began.

As a general rule, "If it aint broke, dont fix it"... Esp on computers you need in a constant working condition. And always update when you have TIME to troubleshoot, and only to a mainstreem release (Not a beta, or dev version).

I have followed all the steps in the earlier posts, and it works for me. I have a strong suspicion that the upgrade left some residual config files. Start there, re-uninstall the previous version. And make sure to manualy delete all the files that needs to be.

Cherz

---

### Post by allan.w.macdonald on 2012-03-17
> **zero2xiii said:**
> As a general rule, "If it aint broke, dont fix it"... Esp on computers you need in a constant working condition. And always update when you have TIME to troubleshoot, and only to a mainstreem release (Not a beta, or dev version).

I have followed all the steps in the earlier posts, and it works for me. I have a strong suspicion that the upgrade left some residual config files. Start there, re-uninstall the previous version. And make sure to manualy delete all the files that needs to be.

Cherz

Thanks Cherz,

OK, I have uninstalled the Oracle Java per the instructions in the howto.  I have deleted the /opt/java directory and removed the symbolic link from the plugins directory.  But what else should I do?  You mentioned to "manually delete all the files that need to be."  Any hints as to what this would entail?  How do I confirm that the system is clean of any residual configuration?

What about the other versions of Java that appear to be on my machine?  Should I remove all of them and start from scratch?  How should they be configured?

Here is the output of the command, "update-alternatives --config java":

```

There are 4 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                      Priority   Status
------------------------------------------------------------
* 0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1            /usr/bin/gij-4.2                           42        manual mode
  2            /usr/bin/gij-4.4                           1044      manual mode
  3            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
  4            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode

Press enter to keep the current choice[*], or type selection number: 


```

Does this look right?  I do not really understand the alternatives system that well.  Do I see multiple versions of java installed or are these just aliases to a single version.  Also, why is there a java-6-sun entry in the update-alternatives table (or whatever you call that)?  Is that a source of conflict?  Should I remove that entry?  Should I delete the directory as well?  What is the difference between Auto and Manual modes?

Where else should I look to ensure I am starting from a clean slate?

Thanks in advance

---

### Post by allan.w.macdonald on 2012-03-17
Another question: I am trying to learn about the alternatives system but it is pretty confusing.  Nevertheless, I will attempt to ask intelligent questions about this:

Firstly, under "/etc/alternatives", I see a link called "firefox-javaplugin.so" which links to "/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so".  Should I remove this link?  Should I nuke the entire "/usr/lib/jvm/java-6-sun" heirarchy?  Why is it there in the first place?

There is also a "/usr/lib/jvm/java-6-openjdk/" herarchy.  Are these two heirarchies supposed to co-exist?  Any explanation here would be greatly appreciated.

---

### Post by dino99 on 2012-03-17
open synaptic and purge everything related to java and likes, then reinstall what you need (oracle)

---

### Post by allan.w.macdonald on 2012-03-17
> **dino99 said:**
> open synaptic and purge everything related to java and likes, then reinstall what you need (oracle)

Hi dino99,

Thanks for the suggestion.  I have thought of that but that is advised against in the [howto]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-Remove-the-browser-plug-in-of-the-o")

So, after I remove everything, should I install openJDK before re-installing the Oracle java stuff or will my machine work with only Oracle java on the machine?

---

### Post by zero2xiii on 2012-03-17
Wow, 

hehe I am no ubuntu expert by any means... But I have had issues do to "updates" before. Due to residual config files... 

Lets see now,

The tutorial points to:
/opt/jave
~/.mozilla/plugins/libnpjp2.so

Nothing else. But I also suggest using synaptic and purging ALL java related installs (not just un-install). And start from as close to scratch as you can.

As far as if your system will function purely running oracle concerns, I have no idea, if it does not work, you can always add the aditional Java installation. I run all the availible systems open JDK, and sun Java system. Don't have any issues. 

So I suggest you start purgeing ALL java related files... However, I also recommend getting opera (the webbrowser) as a second reference. I use opera. Some websites load beter on opera, some on firefox. So if a site gives me issues (esp Java and Flash related) I switch to the other one, I have yet to find a website failing on both....)


After opera is installed, check for java. (this is a very small stone into a very large bush...) If it also states no java is installed. Then continue with purging the Java and all related installs.

THEN please give the output of: (in code tags please as these outputs might give a LOT of output)
```
ls /proc/ -a -R
ls $HOME/.mozilla/
```

If these outputs generate to much text, you can save it to a file by appending a > file_name.txt to your command eg:
```
ls /proc/ -a -R > proc_ls.txt
ls $HOME/.mozilla/ > mozzilla_ls.txt
```

and then pastebin that text.

Once we can gather that NO java or broken links exist, we can continue from there with a fresh install, monitoring and checking each and every step to see from where the expected results is not shown.

Cherz

---

### Post by allan.w.macdonald on 2012-03-17
Thanks Cherz,

I will decline the suggestion to install Opera for the time being; to me, that just seems to be yet another variable to worry about.  I would like to keep things as simple as possible.  

Nevertheless, I will try all the other things you suggested and get back to you.

Here goes!  Wish me luck!

Cheers,

Allan

---

### Post by zero2xiii on 2012-03-17
haha No worries about the opera thing. Just a suggestion.

I will be online for the next 2 hours for active support (as far as I can). 
sammiev truely tried his/her best. But I have had previous issues with residual config files (as stated earlier) so lets give it another shot.

Cherz again

---

### Post by allan.w.macdonald on 2012-03-17
Hi Cherz,

So, I opened synaptic and searched for "java" in the name only.  I then found a package called "java-common" and selected that for removal.  A bunch of other packages got selected as well.

There are a bunch of other packages with the "java" in the name (things like libcomons-xxx-java and libdbn.n-java and such) but I think that those are not important for this experiment so I didn't select anything else.

Then, I clicked apply and waited.  Then an alarming thing happened:  During the removal process, my entire desktop appearance changed to what appears to be an older look!  Although worrying, I did not see any other side-effects.

Anyway, attached are the results of two commands: 

ls /proc/ -a -R > ls_proc.txt
ls -R $HOME/.mozilla/ > ls_mozilla.txt

The second command differs slightly from yours in that I added the Recursive option (the original command didn't show anything useful).

I had to zip them up since one of the files is too big.

I am looking forward to your analysis, Cherz.

Cheers,

Allan

---

### Post by allan.w.macdonald on 2012-03-17
In addition, I repeated the update-alternatives --config java and here is the output:
```

There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path              Priority   Status
------------------------------------------------------------
* 0            /usr/bin/gij-4.4   1044      auto mode
  1            /usr/bin/gij-4.2   42        manual mode
  2            /usr/bin/gij-4.4   1044      manual mode

Press enter to keep the current choice[*], or type selection number: 

```

What is gij?  Should I remove that too?

---

### Post by allan.w.macdonald on 2012-03-17
My desktop is back to normal: I brought up the system->preferences->appearance applet and suddenly, I am back to normal again.  Whew!

---

### Post by zero2xiii on 2012-03-17
Hay,

I have no idea what gij is? But a quick google didnt show anything that can interfere, its only an interpreter for java byte code.

Seems like your firefox has crashed numerous times. But that shouldnt be an issue, unless it is directly connected to anything regarding the java issue?

Plugins folder is empty, so no plugins should be present to hinder the Java oracle installation.


/proc also seems clean from any java clutter. And no strange kernel mods or other strange simlinks that I saw... 


Soooo let us get a terminal session preped so I can follow the process with precise detail. We will do everything from the terminal now, as to monitor everything that goes on under the hood:

```
script -a -f java_setup.txt
```

Now this will create a file in your ~/ (home) directory, echoing EVERYTHING that is echoed to the terminal (including everything that is typed).

So let us go forth:
```
sudo mkdir /opt/java
sudo mkdir /opt/java/32

```
Creates the install directory, now copy your downloaded install file her using cp for example:
```
sudo cp ./my_download.bin ./opt/java/32
```
good lets go on (so far everything sould be smooth)
```
sudo chmod +x install_file.bin
```

Oka now we have everything setup. Im posting this so you can get to this point solong...

---

### Post by zero2xiii on 2012-03-17
oka, up to this point nothing CAN go wrong really... 

Here is where we need to pay special attention to everything:

```
cd /opt/java/32
sudo ./jre-6u31-linux-i586.bin #I am using the same name here as my installer since I am guessing we are installing the same version of the program...

```
oka follow the onscreen jargon untill the installation is finished.

Now before we setup all the things and all that, please post the file "Java_setup.txt" so that I can see if the installation went smooth (do not close the terminal. Just copy paste the file)

If the installation was successful we shall continue

---

### Post by allan.w.macdonald on 2012-03-17
Sorry, had to step a way for a few minutes.

I will do the above and get back to you shortly.

---

### Post by zero2xiii on 2012-03-17
haha no worries, I just know the feeling of waiting hours for "oka and the next step" responses that drive a person up the wall.

---

### Post by allan.w.macdonald on 2012-03-17
Here is the script file.

---

### Post by zero2xiii on 2012-03-17
Oka awsum, 

Setup seems successful and all things working as it should I assume (you can check running "Java -version" as before.

Now lets get the links going.. Most toturials only say to put one link in a folder, we are going to put 3... 

```
sudo mkdir ~/mozilla/plugins
ln -s /opt/java/32/jre1.6.0_31/lib/i386/libnpjp2.so ~/.mozilla/plugins/
ln -s /opt/java/32/jre1.6.0_31/lib/i386/libnpjp2.so /usr/lib/firefox/plugins/
ln -s /opt/java/32/jre1.6.0_31/lib/i386/libnpjp2.so /usr/lib/firefox-addons/plugins
```

**_EDIT - had a syntax error, please recheck you made 3 links_**
We are not doing the alternative version setup (yet atleast)...

Oka that should be it. now start firefox (from terminal)

```
firefox
```

and test your java as you did previously...

Lets keep thumbs crossed, if any of the above give errors, please post the file again..

---

### Post by allan.w.macdonald on 2012-03-17
What about update-alternatives?

---

### Post by zero2xiii on 2012-03-17
I am skipping that step cause it caused issues for me. Maybe that is also your problem. Just create the links. It SHOULD work only with links..

---

### Post by allan.w.macdonald on 2012-03-17
> **zero2xiii said:**
> I am skipping that step cause it caused issues for me. Maybe that is also your problem. Just create the links. It SHOULD work only with links..

OK but, when I enter the command "java -version", I get the same version that is listed when I enter the command "update-alternatives --config java".  Will that be a problem?

---

### Post by zero2xiii on 2012-03-17
No,

See your problem is not the java version, or installation, it is firefox fails to detect and use it. all the other checks i perform inbetween is just to make SURE that everything is moving along as planned..

---

### Post by allan.w.macdonald on 2012-03-17
Here are the results of the "java -version" and "update-alternatives --config java" commands:

result of java -version:

```

java version "1.5.0"
gij (GNU libgcj) version 4.4.3

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

Result of "update-alternatives --config java":

```

There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path              Priority   Status
------------------------------------------------------------
* 0            /usr/bin/gij-4.4   1044      auto mode
  1            /usr/bin/gij-4.2   42        manual mode
  2            /usr/bin/gij-4.4   1044      manual mode

Press enter to keep the current choice[*], or type selection number: 

```

---

### Post by allan.w.macdonald on 2012-03-17
Should the ln commands going in /usr/lib/... be under sudo?

---

### Post by zero2xiii on 2012-03-17
Yep oka,

still, please create the 3 links so we can check if firefox is atleast finding the java installation.. 

```
sudo mkdir ~/mozilla/plugins
ln -s /opt/java/32/jre1.6.0_31/lib/i386/libnpjp2.so ~/.mozilla/plugins/
ln -s /opt/java/32/jre1.6.0_31/lib/i386/libnpjp2.so /usr/lib/firefox/plugins/
ln -s /opt/java/32/jre1.6.0_31/lib/i386/libnpjp2.so /usr/lib/firefox-addons/plugins
```

EDIT- 
yes if it gives permission errors, add sudo:

```
sudo mkdir ~/mozilla/plugins
sudo ln -s /opt/java/32/jre1.6.0_31/lib/i386/libnpjp2.so ~/.mozilla/plugins/
sudo ln -s /opt/java/32/jre1.6.0_31/lib/i386/libnpjp2.so /usr/lib/firefox/plugins/
sudo ln -s /opt/java/32/jre1.6.0_31/lib/i386/libnpjp2.so /usr/lib/firefox-addons/plugins
```

---

### Post by allan.w.macdonald on 2012-03-17
OK bye for now (back shortly)

---

### Post by zero2xiii on 2012-03-17
Hay,

I will not be able to continue to assist you further tonigh. After the links are created in all 3 locations that firefox checks for plugins and it still fails to find the java version. We can continue tomorow. I am usualy on the forums every day this time for aprox 2 hours. We can then continue.

As for now,
Cherz again hahaha):P

---

### Post by allan.w.macdonald on 2012-03-17
> **zero2xiii said:**
> Hay,

I will not be able to continue to assist you further tonigh. After the links are created in all 3 locations that firefox checks for plugins and it still fails to find the java version. We can continue tomorow. I am usualy on the forums every day this time for aprox 2 hours. We can then continue.

As for now,
Cherz again hahaha):P

OK but I will post my results anyway.

For one thing, I could not create the links in two of the three places you mentioned without running them under sudo.

But then, when I run Firefox, it seems to try to pick up something and complains:

```

Script started on Sat 17 Mar 2012 05:02:15 PM ADT
]0;myname@mycomputer: ~myname@mycomputer:~$ sudo mkdir ~/.mozilla/plugins
[sudo] password for myname: 
mkdir: cannot create directory `/home/myname/.mozilla/plugins': File exists
]0;myname@mycomputer: ~myname@mycomputer:~$ ln -s /opt/java/32/jre1.6.0_31/lib/i386/libnpjp2 
.so ~/.mozilla/plugins/
]0;myname@mycomputer: ~myname@mycomputer:~$ sudo ln -s /opt/java/32/jre1.6.0_31/lib/i386/lib 
npjp2.so /usr/lib/firefox/plugins/
]0;myname@mycomputer: ~myname@mycomputer:~$ sudo ln -s /opt/java/32/jre1.6.0_31/lib/i386/lib 
npjp2.so /usr/lib/firefox-addons/plugins
]0;myname@mycomputer: ~myname@mycomputer:~$ firefox
LoadPlugin: failed to initialize shared library /opt/java/32/jre1.6.0_31/lib/i386/libnpjp2.so [/opt/java/32/jre1.6.0_31/lib/i386/libnpjp2.so: cannot open shared object file: Permission denied]
]0;myname@mycomputer: ~myname@mycomputer:~$ exit
exit

Script done on Sat 17 Mar 2012 05:05:06 PM ADT
```

---

### Post by allan.w.macdonald on 2012-03-17
So, it looks like we might have a permissions problem.

To me, Linux permissions have always been a royal pain in the you-know-what.

```
lrwxrwxrwx 1 root root 45 2012-03-17 17:02 /usr/lib/firefox/plugins/libnpjp2.so -> /opt/java/32/jre1.6.0_31/lib/i386/libnpjp2.so
lrwxrwxrwx 1 root root 45 2012-03-17 17:02 /usr/lib/firefox-addons/plugins/libnpjp2.so -> /opt/java/32/jre1.6.0_31/lib/i386/libnpjp2.so
lrwxrwxrwx 1 myname myname 45 2012-03-17 17:02 .mozilla/plugins/libnpjp2.so -> /opt/java/32/jre1.6.0_31/lib/i386/libnpjp2.so

```

So, what is the solution?  Is the problem the location of the symbolic link?  Do I have to chmod or chown the links in /usr/lib...?  Why does firefox not pick up the symbolic link in ~/.mozilla/plugins?  Does firefox not look there anymore?  Should I delete two out of the three links to see which one works and which one doesn't?

---

### Post by allan.w.macdonald on 2012-03-17
I also noticed this in one of the plugin directories:

```

ls -al /usr/lib/firefox/plugins/
total 188
drwxr-xr-x 2 root root   4096 2012-03-17 17:39 .
drwxr-xr-x 3 root root   4096 2011-04-17 15:22 ..
lrwxrwxrwx 1 root root     37 2012-03-06 21:14 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root     39 2012-03-15 21:52 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 root root     35 2011-11-30 21:09 mozplugger.so -> ../../mozilla/plugins/mozplugger.so
-rwxr-xr-x 1 root root 179552 2011-08-29 22:56 nppdf.so

ls -al /usr/lib/firefox-addons/plugins/
total 188
drwxr-xr-x 2 root root   4096 2012-03-17 17:39 .
drwxr-xr-x 5 root root   4096 2010-07-11 11:01 ..
-rwxr-xr-x 1 root root 179552 2011-08-29 22:56 nppdf.so


```

Notice the libjavaplugin.so link in /user/lib/firefox/plugins?  Is that the problem?  What is that link for?  Should I nuke that link and retry the original link in that location?

---

### Post by zero2xiii on 2012-03-18
Hay,

I had a few minutes to come on and so I saw your post.

I have a feeling it might be a permission thing then. So lets test, and then fix that. Try running firefox with superuser privs (this is STRONGLY discouraged but for testing purposes it should be fine):

```
gksudo firefox
```

Check to see if it still complains about permissions. If it doesn't, see if the java is detected.

As far as all the rest of your concerns go, do not "nuke" anything just yet. As we can safely assume this is a CLEAN install, all of the links and such have been created by the installer. I think it is a permission issue.

Looking at the official Java site, it says to install java to your home directory, creating links from there. Since you own your home directory, permissions wont be a problem. Further also note this remark:

> Note about root access: To install Java in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the Java in your home directory or a subdirectory for which you have write permissions.
Even though it does not state that you then require root access to use java, your firefox gives an error...

> Notice the libjavaplugin.so link in /user/lib/firefox/plugins? Is that the problem? What is that link for? Should I nuke that link and retry the original link in that location?
No, not yet atleast. The installer might have created it.



However, after re-examining the error I see that firefox complains about the java path, not the link to it. So lets chown it anyway, No harm can come from it:

```
sudo chwon -chR $(whoami) /opt/java/32/jre1.6.0_31/
```

This should generate some (or a lot of) output. If you do this wile under "script", no need to redirect the ouput. However, if you are NOT under "Script" please redirect your output to a file to examine it for all the changes made:

```
sudo chwon -chR $(whoami) /opt/java/32/jre1.6.0_31/ > chown_Java.txt
```

Let us keep all the good luck charms we have at hand so as to this being the problem and the chown the cure of the disease...[-o<

Cherz again

---

