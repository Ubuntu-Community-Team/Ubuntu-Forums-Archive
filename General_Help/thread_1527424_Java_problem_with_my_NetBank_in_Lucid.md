---
title: "Java problem with my NetBank in Lucid"
date: 2010-07-09
forum: General Help
---

### Post by Prognatus on 2010-07-09
Hello all,

Sorry if this issue already has been answered elsewhere.  If so, please guide me to the topic.

I have problems with Java towards several web sites, and most importantly my NetBank - which is a showstopper, forcing me to use Google Chrome instead of Firefox.  So I think this may be a Firefox plugin problem, since it works in Chrome?

The [NetBank verification site (norwegian)]("https://www.bankid.no/Hjelp-og-nyttige-verktoy/Nyttige-verktoy/Test-din-datamaskin/?check=1") gives me two problems:

1. It says my Java version is not 1.6
2. It says my browser is old (I'm using Firefox 3.6.6)

The latter isn't critical, or even important, but the first is. (see attached image "bankid.png" for my result of this compatibility test)

What I've already done to remedy this, is:

[LIST]
[*]Verified that the default Open Source version of Java didn't work.
[*]Checked that "http://archive.canonical.com/ubuntu lucid partner" is enabled i Software Sources
[*]Installed Sun Java 6 and plugin with the help from [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
[*]Set the Sun Java version as system default, with the command: [COLOR="Green"]sudo update-java-alternatives -s java-6-sun[/COLOR]
[*]Verified that Sun Java is the default, with the command: [COLOR="Green"]java -version[/COLOR] (see attached image "java_version.png" for the result)
[/LIST]

So everything looks just fine in Ubuntu, as far as I can tell, but something must still be wrong, because the same errors persist.  Any ideas where to look in Firefox to check the plugin?  Other ideas?

I'm kind of stuck here, so thanks for any input you may have!

---

### Post by gordintoronto on 2010-07-09
To test my Java, I Google: cool shisen
The first result should be a game on "cool math for kids" If you can play the game, your Java is OK.

In Firefox, Tools, Add-ons, Plugins should show you what Java it is using.

---

### Post by Prognatus on 2010-07-09
Thanks for the reply.  The game works and the plugin says version 1.6.0_20 (see attached image "add-ons_plugins.png").

But still the net bank compatibility test isn't satisfied ... :-(

In addition, the test now reports one more thing than an hour ago (see attached image "cookies.png")!  It now also complains about that I have to allow cookies.  But I do allow cookies ... and I haven't changed any setting in Firefox since my first post, except trying to disable/enable some other plugins to see if any of them influenced the Java test in any way.

---

### Post by gordintoronto on 2010-07-09
It looks like your end is set up properly, but their end is not.

---

### Post by Prognatus on 2010-07-09
Yes, well, I agree with you, but it's not that easy to do something about it.

The "BankID" organization is a national service provider for all banks here.  So they have banks as their customers.  It's no use for me to contact the BankID organization, I must contact my bank.  And my bank just refers to the general requirements ...

This worked before I started to use Lucid and FF 3.6.  That's what so strange - it worked before!  And Chrome works with this, on the same PC.  Just not Firefox ...

---

### Post by Prognatus on 2010-07-10
Actually, it suddenly works now!  I don't know why or how, but maybe restart of Firefox is the key.  I certainly didn't restart Ubuntu.  The compatibility test page still looks exactly as I reported in msg #3 in this thread, but it works anyway.

So, case solved and closed.  :)

---

### Post by ankit singh on 2010-07-10
[http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

Test ur java at this page.

---

### Post by dheym on 2010-07-23
I have the same problem. BankID works perfectly on Google Chrome, but it causes my firefox to chrash permanently. When I uninstall BankID, firefox works again. I get the same results on the testpage posted in the first post.

---

### Post by dheym on 2010-08-21
I found the solution! 

Do this and it works:
```
sudo rm /usr/local/lib/personal/libP11.so && sudo apt-get install libp11-1
```

From[ here]("http://ubuntu-se.org/phpBB3/viewtopic.php?f=19&t=49532") (in swedish).

---

### Post by lykeion on 2010-08-21
> **dheym said:**
> I found the solution! 

Do this and it works:
```
sudo rm /usr/local/lib/personal/libP11.so && sudo apt-get install libp11-1
```

From[ here]("http://ubuntu-se.org/phpBB3/viewtopic.php?f=19&t=49532") (in swedish).

I'm using FF 3.6.8 and previously had problems with freezing after login to my bank with BankID/Nexus. 
I used to solve this by removing secmod.db in my FF user profile,
but with this solution the problem does not seem to exist anymore.
THANK YOU

---

### Post by rikubu on 2010-08-27
The libp11-1 installation worked for me too, although I had no /usr/local/lib version to deinstall, e.g. only 

sudo apt-get install libp11-1

was the solution. I had been resigned to rebooting into Windows to do banking, as I have had problems for years keeping Java (and Flash) working with Firefox in 64bit ubuntu. (I remain dedicated to open source, and look forward to the era of open source plugins...)

---

