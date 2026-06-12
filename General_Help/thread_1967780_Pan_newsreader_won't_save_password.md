---
title: "Pan newsreader won't save password"
date: 2012-04-28
forum: General Help
---

### Post by schmoken on 2012-04-28
Hi!
I'm running kubuntu 12.04 & Pan 0.136.

Pan will not remember passwords. 
Here is the event log:

> Sat Apr 28 11:16:24 2012 - Pan 0.136 started
Sat Apr 28 11:16:24 2012 - Loaded data backend in 0.0 seconds
Sat Apr 28 11:16:50 2012 - news20.forteinc.com requires a password, but none is set.
Sat Apr 28 11:16:50 2012 - Unable to connect to "news20.forteinc.com:119":
381 More authentication needed
 
Pan is now offline. Please see "File|Event Log" and correct the problem, then use "File|Work Online" to continue.


Back in the server settings I get this:

[IMG]http://img.photobucket.com/albums/v192/schmoken/forums/puter/snapshot1.png[/IMG]

I have tried with or without SSL.
On free servers that don't require a login, Pan works good.

---

### Post by schmoken on 2012-04-28
fixed!
Pan 0.136 stores passwords in gnome keyring. I did not have gnome-keyring installed.

---

### Post by oldrocker99 on 2012-04-29
I do have gnome-keyring installed, and looked at the .pan2/servers.xml file, it looked like this:
<username>fakeuser</username>
    <password></password> 

I entered the password between the >< thus:
<username>fakeuser</username>
    <password>fakepass</password>
(obviously, the username and password are, uh, fake).

And pan, which I have used for four years now, won't see my password, even though I edited the file to include the password:shock:.

This is one I've never seen before. I renamed the .pan2 directory so a new one could be created and it STILL won't remember or correctly read the servers.xml file](*,).

Any ideas? I'm no master, but hardly a n00b.

Solved: I reinstalled Mint 12.

---

### Post by notquitestr8t on 2012-05-14
I tried these fixes except for Mint 12 since I never installed it. I have gnome-keyring installed but pan failed immediately after the upgrade to 12.4. I don't know what Mint 12 is and I've never had to install it. Any other ideas?
The only thing that changed was the server ID parameter. I changed it back to "1" but it still fails.

Original

<?xml version="1.0" encoding="utf-8" ?>
<server-properties>
<server id="1">
<host>localhost</host>
<port>119</port>
<username>*****************</username>
<password>*****************</password>
<expire-articles-n-days-old>0</expire-articles-n-days-old>
<connection-limit>10</connection-limit>
<newsrc>/home/colson/.pan2/newsrc-1</newsrc>
<rank>1</rank>
</server>
</server-properties>

After upgrade

<?xml version="1.0" encoding="utf-8" ?>
<server-properties>
  <server id="2">
    <host>localhost</host>
    <port>119</port>
    <username>*********</username>
    <password>********</password>
    <expire-articles-n-days-old>93</expire-articles-n-days-old>
    <connection-limit>10</connection-limit>
    <newsrc>/home/colson/.pan2/newsrc-2</newsrc>
    <rank>1</rank>
  </server>
</server-properties>

Unable to connect to "localhost:119":
381 PASS required
localhost requires a password but none is set
 
Pan is now offline. Please see "File|Event Log" and correct the problem, then use "File|Work Online" to continue.

---

### Post by notquitestr8t on 2012-05-14
I solved my own problem. Interestingly, modifying the xml file via the command line did not take. When I opened the GUI there was no password listed. I added that and saved and all worked OK.

---

### Post by rich1842 on 2012-07-07
Thanks, I also did not have keyring installed - that worked for me!

---

