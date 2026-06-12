---
title: "Evolution Exchange Connector Problems"
date: 2005-03-02
forum: General Help
---

### Post by ahannemann on 2005-03-02
I'm having issues with trying to connect to my MS Small Business Server (running Exchange 2003 Server) with Evolution and the Exchange Connector.  I'm very much a Linux Newb, but I've tried apt-get, done a re-install from Synaptic, about every username combo that I could think of, searched pretty much everywhere I have the patience to search and I'm stumped.  I'm running Evolution 2.0.2.

The problem is that it fails to find my account on the Exchange 2003 server. I can log in quite happily with my username/password over the web interface, but evolution claims there is no mailbox with my username.

Then if I change my username, I then get an error message saying:

Could not connect to Evolution Exchange backend process:
No such file or directory

The reason I might change my username is to set it to something like username or domain\username or domain/username (I can never remeber which way round the slashes go...) although the plain username works fine under web access.

I'm a long time Windows user, and the connection to my Exchange Server is an absolute must if I want to seriously give Linux a shot.  My server runs OWA beautifully, and I'm able to log in using Firefox although it's nasty without ActiveX helping out.

Thanks to anyone who has ideas for me to try.

Adam

---

### Post by yqyq22 on 2005-03-02
[QUOTE=ahannemann]I'm having issues with trying to connect to my MS Small Business Server (running Exchange 2003 Server) with Evolution and the Exchange Connector.  I'm very much a Linux Newb, but I've tried apt-get, done a re-install from Synaptic, about every username combo that I could think of, searched pretty much everywhere I have the patience to search and I'm stumped.  I'm running Evolution 2.0.2.

The problem is that it fails to find my account on the Exchange 2003 server. I can log in quite happily with my username/password over the web interface, but evolution claims there is no mailbox with my username.

Then if I change my username, I then get an error message saying:

Could not connect to Evolution Exchange backend process:
No such file or directory

The reason I might change my username is to set it to something like username or domain\username or domain/username (I can never remeber which way round the slashes go...) although the plain username works fine under web access.

I'm a long time Windows user, and the connection to my Exchange Server is an absolute must if I want to seriously give Linux a shot.  My server runs OWA beautifully, and I'm able to log in using Firefox although it's nasty without ActiveX helping out.

Thanks to anyone who has ideas for me to try.

Adam[/QUOTE]

I have the same problem, could someone help us!!!!!!!1
thank you.
yqyq22

---

### Post by ahannemann on 2005-03-02
Rats... I thought someone had an idea for me.  I'm glad to see that I'm not the only person with this issue though.  Was beginning to think it was just me.

---

### Post by ahannemann on 2005-03-03
Bump.

---

### Post by ahannemann on 2005-03-09
Bump again.

---

### Post by elias4444 on 2005-03-09
I haven't tried it on Ubuntu yet, but on Debian, it has to do with a bug in Evolution (or, at least, in my case it does). There's a somewhat complicated fix that requires manual editing of some gconf files, but it has a tendency to revert back (and hence, repeatedly doing the manual editing thing). Good news though:

The problem seems to be fixed in the latest version of Evolution. And since it now comes with Gnome (2.10), you'll probably be good to go with the next release of Ubuntu.

If you're in a hurry, Suse runs a newer version that works flawlessly as far as I can tell.

---

### Post by ahannemann on 2005-03-09
Thanks for the info.  I can hold on.  I'm just working on learning it more than anything else.  It's just tough to try to work full time in Linux if I can't check my email.

---

### Post by WirelessMike on 2005-03-10
I'm on Hoary running Evolution 2.2 and I can tell you from personal experience that you are MORE likely to connect to an exchange server with the previous version (2.0) than this one.

The previous version had enough config to allow you to identify not just your login to connect, but also your directory/folder name, which on my company's server is different from your login.  The latest version for Ubuntu does NOT include that config, so if your directory on exchange is different from your login, as is my case, evolution 2.2 is actually a downgrade.

My suggestion is to find out if your login is not your folder name.  If it isn't, you'll need to identify different "logins" on the Recieving Email and Recieving Options tabs.

---

### Post by shakudu on 2005-03-15
Anyone knows how to fix this? Running Ubuntu 5.03 with Evolution 2.2 and i get that same error message... I read in some post that an apt-get upgrade should fix it but it cant fint any new packages....

---

### Post by ahannemann on 2005-03-17
What Gnome does Ubuntu 5.04 run?  I don't have time to test it this week, and if someone knows offhand it'd be cool.

---

### Post by eroux on 2005-04-01
[QUOTE=WirelessMike]My suggestion is to find out if your login is not your folder name.  If it isn't, you'll need to identify different "logins" on the Recieving Email and Recieving Options tabs.[/QUOTE]

Which I would dearly love to do, since I'm in the same boat, but I'm stumped as how to go about it.

My version of Evolution 2.2 has no spot for a username or login in the "Receiving Options" tab. I'm stumped.

Fortunately my FC3 box is still on Evolution 2.0.4 so I'm still able to read my corporate email.

If anyone has a workaround or know of a version of Evolution that will "Fix" this deficiency, I'll be glad to hear about it.

Regards,
Eugéne

---

### Post by greebo on 2005-04-05
Hi,

I thought I'd post to say that the Exchange connector in Hoary is _HEAPS_ better than in Warty. In warty I found my CPU usage sat on 100% within minutes and my entire machine wasn't usable, but not my exchange stuff "just worked". I didn't have to do any wierd fiddling with settings, and we use Exchange 2003  :-D 

Rock on! Now my enforced work mail isn't nearly so painful ;)

---

### Post by eroux on 2005-04-11
[QUOTE=eroux]Which I would dearly love to do, since I'm in the same boat, but I'm stumped as how to go about it.

My version of Evolution 2.2 has no spot for a username or login in the "Receiving Options" tab. I'm stumped.[/QUOTE]

I am *very*  pleased to report that this has been fixed in the connector released to the APT repositories from CVS on 2005-04-05...

It still does not have a seperate entry for mailbox, but it seems to autodetect the mailbox name on connection.

All seems to work fine now.

Regards,
Eugéne

---

### Post by Paco Rodriguez on 2005-04-17
execute this in command line:

/usr/sbin/bonobo-activation-sysconf --add-directory=/usr/local/lib/bonobo/servers

---

### Post by chard on 2005-04-18
[QUOTE=eroux]I am *very*  pleased to report that this has been fixed in the connector released to the APT repositories from CVS on 2005-04-05...

It still does not have a seperate entry for mailbox, but it seems to autodetect the mailbox name on connection.

All seems to work fine now.

Regards,
Eugéne[/QUOTE]
 Unable to authenticate correctly...Evolution 2.2.1.1

Was able to work around issues in Warty, but Hoary has combined some fields.

Is there a gconf file that can be manually edited rather than relying on the dialog boxes?

---

### Post by damber on 2006-08-14
I'm having the same problem.  Running kubuntu 6.0.6 and evolution 2.6.1 with exchange connector. 

The issue is that several of the fields for entering the configuration information is missing - this link shows screenshots of what the configuration screens should look like in the exchange section: [http://www.gnome.org/projects/evolution/doc/evolution26.pdf](http://www.gnome.org/projects/evolution/doc/evolution26.pdf) 

However, the screens do not have these fields, and there is an entire (exchange specific) tab missing.

From things I've read so far, Evolutions exchange connector has become worse and worse since v2.0 .....

Has anyone found any resolution to this ?  an apt-get returns the version I'm currently using - should I be looking around for any other versioned packages ?  if so, which ?  

Thanks in advance for any help you can provide..

---

### Post by simd on 2006-08-21
Just to add my voice to this. I'm using a brand new install of Ubuntu 6.06 and Evo 2.6.1. From the start I've been getting the "Could not connect to Evolution Exchange backend process" error. 

I've tried various fixes I've found on the net - nothing works. I'm assuming there's simply a path wrong somewhere. 

Help! It's certainly a barrier for the many corporates who use Exchange to find that Evolution doesn't connect to Exchange "out of the box" on the most popular distribution, despite suggestions to the contrary.

---

### Post by DaveBrink on 2006-09-01
I was having the same error about exchange backend process. I was able to correct the issue by pointing the OWA URL to an HTTPS adress instead of the HTTP as follows [HTTPS://servername.domain.com/exchange](HTTPS://servername.domain.com/exchange) and also changing the password to secure instead of plaintext. Hope this helps somebody.

---

### Post by TheRunningBoard on 2006-09-27
> **damber said:**
> I'm having the same problem.  Running kubuntu 6.0.6 and evolution 2.6.1 with exchange connector. 

The issue is that several of the fields for entering the configuration information is missing - this link shows screenshots of what the configuration screens should look like in the exchange section: [http://www.gnome.org/projects/evolution/doc/evolution26.pdf](http://www.gnome.org/projects/evolution/doc/evolution26.pdf) 

However, the screens do not have these fields, and there is an entire (exchange specific) tab missing.

From things I've read so far, Evolutions exchange connector has become worse and worse since v2.0 .....

Has anyone found any resolution to this ?  an apt-get returns the version I'm currently using - should I be looking around for any other versioned packages ?  if so, which ?  

Thanks in advance for any help you can provide..

I have this EXACT same problem.  This is a real road block to corporate adoption.  If anyone has any fixes for this, please post them.  Sorry I am of no use.

---

### Post by TheRunningBoard on 2006-10-13
Bump.

Still getting the error "Could not connect to Evolution Exchange backend process: No such file or directory".

Any one find a fix for this yet?

---

### Post by kasulstyls on 2006-11-01
similar issue here also but I am seeing &#8211; Unable to refresh folder, lost connection to Evolution Exchange backend process.    I have tired the for mentioned idea above but no joy!:confused:

---

### Post by simd on 2006-11-01
I've upgraded to Edgy, and can report that Evolution is now working fine with our Exchange server, after all the problems in Dapper.

---

### Post by pdabel on 2006-11-15
I am having the same problems, I am running Edgy with the default Evolution install.  All was working fine for 2 weeks after the initial install, then these errors started.  There were no changes/updates made.

Is anybody else having the same problem on Edgy?

---

### Post by tubadanm on 2006-11-15
I'm having general issues with evolution in ubuntu 6.10 -- I have both imap (via thunderbird) and exchange connections to my mail server.  Thunderbird sees new email right away and I can read, etc.  If I click on send-receive on evolution, there's no change.  I created a meeting in MS's webmail system and it took 15 minutes for this meeting to appear in evolution.  And meeting alarms are not working.  plus evolution has crashed a few times -- I submit the bugs but then bug-buddy tells me that stack trace is not enough and that I should try to reproduce the error.  why is evolution (exchange server connector?) so buggy after being out for so many years?

---

### Post by maheshjagadeesan on 2006-11-27
Hey, I had changed my username too (don't ask me why though! ;-) ), and I am happy to say that I was able to resolve almost the same set of issues faced by "ahannemann" by simply creating a symbolic link for the name of the previous home directory. E.g., in my case, my home directory was earlier /home/maheshj. Now, I have a sym-link called maheshj under /home.

Check it out!

---

### Post by popeyelin on 2006-11-27
I solved the problem in my Ubuntu 6.06.
Although when I upgraded to Ubuntu 6.10, Evolution 2.8 works well. But Ubuntu 6.10 itself cannot work well in my Dell Dimension 3000. So I have to go back to Ubuntu 6.06.](*,) 
The Ubuntu 5.10's evolution works well in my computer, but once I upgraded to Ubuntu 6.06, it couldn't work. 
Today I just have a careful look at the manual and found one thing.
When inputing the exchange's user name, the manual's screenshot doesn't contain the domain name. 
For an example, your email is [email]blablabla@lalala.com[/email], you can only fill blablabla.(But in Ubuntu 5.10, domain name is must).
When I remove the domain name, it works.
Thanks god, I can use that three years now.:mrgreen:

---

### Post by bedge on 2006-12-18
I'm on edgy due to the connector problems in dapper. It worked fine for a while, now it never starts up. It just says "Scanning folders in..." forever.

I had to change my exchange pw, which I did through the exchange web UI, but now I can't change it in evolution.

There's a PW prompt that vanishes after .5 seconds, and going into tools->accounts->edit makes it crash. Grrr.

-Bruce

---

### Post by theToolman on 2007-02-08
using dapper, I have had the exchange link going fine until my password expired.  I have reset my password, but am having diffuiculty getting it to talk again.   One trick is to start in offline mode:

```
evolution --offline
```

this stopped my crash on load due to it trying to send/recieve.. now got to figure out how to get them talkin nice again :|

---

### Post by n2000 on 2007-04-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/52800](https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/52800) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Im am running Evolution 2.8.1 from Edgy 6.10.
I also have problems with the exchange connector.
I read this bug-report [Bug #52800 Evolution cannot connect to Exchange backend process]("https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/52800").

Try this:
```
export LD_LIBRARY_PATH=/usr/lib/evolution/2.8/
/usr/lib/evolution/2.8/evolution-exchange-storage &
evolution
```

On my system evolution and exchange connector are running now.

Instead of typing *export LD_LIBRARY_PATH=/usr/lib/evolution/2.8/* you can also add */usr/lib/evolution/2.8/* to */etc/ld.so.conf* and run *sudo ldconfig* afterwards.

Good luck!

---

