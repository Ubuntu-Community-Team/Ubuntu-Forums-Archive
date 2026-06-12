---
title: "Majorly weird problem"
date: 2010-06-01
forum: General Help
---

### Post by Kurtosis on 2010-06-01
The past couple days I've started having really weird problems in Ubuntu.  They all started around the same time, and all involve not being able to connect to website login pages and other authentication services.  In no particular order:

- Ubuntu Software Center won't install anything.  It appears to work normally until I click the Install button.  It depresses for a second or two, then pops back up and the installation doesn't start.  No error or anything.

- Some website login/authentication links are unreachable:
 > Gmail
 > Blogger Authentication
 > Mozy.com login page
 > Borders.com login page
 > us.battle.net login page 
 > random others
 
- Running Warcraft in Wine and can't login, get disconnected during login attempt, no successful logins.

There are other web login sites that work fine - Posterous, Tumblr, Twitter, Identi.ca, Yahoo Mail, etc.  Just some that don't.

I restarted Ubuntu, and that seemed to fix Gmail, Borders, and Ubuntu Software Center installation, but not battle.net and Warcraft (I assume Warcraft is authenticating at [https://us.battle.net/etc](https://us.battle.net/etc) too).  Haven't tested the others yet.

I added several things to the system around the time this started happening:

1.  GetDeb apps repository and signing key
2.  GetDeb games repository and signing key
3.  IPblock application (I've tested the above problems with this disabled, but that doesn't seem to have any effect)

I tried removing the GetDeb repositories, but strangely even though I deleted them from the Software Sources control panel, GetDeb still shows up in the Ubuntu Software Center left column menu.  Shouldn't it disappear after the sources were deleted?

I've got no idea what's going on.  Any suggestions/pointers/advice appreciated.

---

### Post by prshah on 2010-06-01
> **Kurtosis said:**
> all involve not being able to connect to website login pages and other authentication services.

- Some website login/authentication links are unreachable:
 > Gmail
 > Blogger Authentication
 
There are other web login sites that work fine - Posterous, Tumblr, Twitter, Identi.ca, Yahoo Mail, etc.  

[GetDeb]even though I deleted them from the Software Sources control panel, GetDeb still shows up in the Ubuntu Software Center left column menu.  Shouldn't it disappear after the sources were deleted?

I suspect that https (secure) login pages are giving you a problem. To confirm this, find a problem page, and check if it has an option to log in without https. Or find a working page (such as yahoo) and choose the option to log in securely. If it stops working, then it is probably an SSL problem, please post back for further instructions.

After deleting the GetDeb entries, the repositories need refreshing; you can use ```
sudo apt-get update
``` from a terminal (Applications-Accessories-Terminal) to do this; you will need an active Internet connection.

Please post back with results and further information as applicable.

---

### Post by Kurtosis on 2010-06-01
Thanks PRShah.  
> **prshah said:**
> I suspect that https (secure) login pages are giving you a problem.
Agreed, that's what it seems, though it's inconsistent.  Some https pages work, some don't.
> **prshah said:**
> To confirm this, find a problem page, and check if it has an option to log in without https. Or find a working page (such as yahoo) and choose the option to log in securely.
Ok, tried with Yahoo Mail, and can successfully log into their https site.  However, Facebook's https login gives the following error:

```
This webpage is not available.

The webpage at https://login.facebook.com/login.php?login_attempt=1 might be temporarily down or it may have moved permanently to a new web address.

[-] More information on this error
Below is the original error message

Error 101 (net::ERR_CONNECTION_RESET): Unknown error.
```

> **prshah said:**
> After deleting the GetDeb entries, the repositories need refreshing; you can use ```
sudo apt-get update
``` from a terminal (Applications-Accessories-Terminal) to do this; you will need an active Internet connection.

I ran sudo apt-get update and restarted the computer, but the Ubuntu Software Center still shows GetDeb in the sources list and can display both the games and apps in the GetDeb repo.

cat /etc/apt/sources.list shows no 'getdeb' lines the sources file either, so not sure where Ubuntu Software Center is finding that repository link.

Baffling.

Edit:  [Livejournal's login page]("http://www.livejournal.com/login.bml") provides an easy way to switch between http and https.  However, both work.  It just seems some sites are afflicted with this problem.  I wish I had more of an idea how to troubleshoot it and what I should be looking for.

---

### Post by Kurtosis on 2010-06-02
Everything seems to be magically working again now, except [Battle.net]("http://us.battle.net/").  When I click the Manage Battle.net Account button I get the following error, a little different than the previous one:

```
This webpage is not available.

The webpage at https://us.battle.net/account/index.xml might be temporarily down or it may have moved permanently to a new web address.

[-] More information on this error
Below is the original error message

Error 102 (net::**ERR_CONNECTION_REFUSED**): Unknown error.
```

What about my computer could possibly be causing secure sites to reject my http requests to them?  Never heard of this before.

---

### Post by Kurtosis on 2010-06-06
Here's a more informative error from Gmail:

```
SSL connection error.

Unable to make a secure connection to the server. This may be a problem with the server, or it may be requiring a client authentication certificate that you don't have.

[-] More information on this error
Below is the original error message

Error 107 (net::ERR_SSL_PROTOCOL_ERROR): SSL protocol error.
```

Any idea what could be preventing authentication from working normally on my machine?  Or, how to troubleshoot that?  Any advice appreciated.

---

### Post by ankspo71 on 2010-06-06
> **Kurtosis said:**
> 

I ran sudo apt-get update and restarted the computer, but the Ubuntu Software Center still shows GetDeb in the sources list and can display both the games and apps in the GetDeb repo.

cat /etc/apt/sources.list shows no 'getdeb' lines the sources file either, so not sure where Ubuntu Software Center is finding that repository link.

Baffling.


Hi,
Do you have any repositories in the folder /etc/apt/sources.list.d? That is a secondary location to add more sources. If so delete the one for GetDeb then run the command 'sudo apt-get update' again. Those GetDeb repositories aren't working for me either.

If you would like to try a mirror repository for GetDeb and PlayDeb, go to this page:
[http://www.webupd8.org/2010/05/getdeb-playdeb-repositories-down-what.html](http://www.webupd8.org/2010/05/getdeb-playdeb-repositories-down-what.html)
Hope this helps.

---

### Post by zobcat on 2010-07-24
I was having the same problem, although I knew it to only be affecting logging into gmail. Disabling IPblock seems to have corrected it.

Open terminal and enter:
```
sudo ipblock -d
```

When I started ipblock back up (sudo ipblock -s) Chromium immediately started behaving the same way as before. However, Firefox had no trouble with gmail for at least a minute or two.

---

### Post by linux18 on 2010-07-24
this might be a good place for my " fix 90% of all synaptic errors " shell script: 

```
 #!/bin/bash
####   Fix 90% of synaptic errors   ###

sudo rm /var/lib/apt/lists/partial/* || echo "ERROR 1: no partial packages - harmless error"
sudo rm /var/cache/apt/*.bin || echo "ERROR 2"
sudo apt-get clean || echo "ERROR 3"
apt-get autoclean || echo "ERROR 4"
sudo apt-get autoremove || echo "ERROR 5"
sudo apt-get update || echo "ERROR 6"
sudo apt-get upgrade || echo "ERROR 7"
echo "100% DONE"  

```

---

### Post by Kurtosis on 2010-07-25
> **zobcat said:**
> I was having the same problem, although I knew it to only be affecting logging into gmail. Disabling IPblock seems to have corrected it.

Open terminal and enter:
```
sudo ipblock -d
```

When I started ipblock back up (sudo ipblock -s) Chromium immediately started behaving the same way as before. However, Firefox had no trouble with gmail for at least a minute or two.
Thanks zob, I did have ipblock installed back then, but not sure if it was running every time or not.  Haven't had the problem for a while now, but will remember this if it pops up again.

---

### Post by Kurtosis on 2010-07-25
> **linux18 said:**
> this might be a good place for my " fix 90% of all synaptic errors " shell script: 

```
 #!/bin/bash
####   Fix 90% of synaptic errors   ###

sudo rm /var/lib/apt/lists/partial/* || echo "ERROR 1: no partial packages - harmless error"
sudo rm /var/cache/apt/*.bin || echo "ERROR 2"
sudo apt-get clean || echo "ERROR 3"
apt-get autoclean || echo "ERROR 4"
sudo apt-get autoremove || echo "ERROR 5"
sudo apt-get update || echo "ERROR 6"
sudo apt-get upgrade || echo "ERROR 7"
echo "100% DONE"

```
Thanks linux, saved.

---

