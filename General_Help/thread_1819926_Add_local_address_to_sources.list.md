---
title: "Add local address to sources.list"
date: 2011-08-07
forum: General Help
---

### Post by progammer on 2011-08-07
Hi,

In my sources.list all I can see is online addresses but there is another directory in my pc which has all the sofwares but I don't know how to add its address to sources.list. I need to know the format of how to add it.

local directory is:
/var/www/debian/pool/main

---

### Post by bodhi.zazen on 2011-08-07
You need to create a local mirror

[http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)

You do understand it is not a good idea to mix debian and ubuntu packages unless you know what you are doing or if it is one or two minor packages I trust.

---

### Post by progammer on 2011-08-07
I already have a local repository its in:
**/var/www/debian/pool**

so I need its main files and contrib fiels to appear in the software center for this purpose I have added this line to my sources.list

[B]deb file:///var/www/debian/pool maverick main contrib
deb-src file:///var/www/debian/pool maverick main contrib[/B]

In past it was already setup and there was only one line in my sources.list but as I am new with ubuntu I delete it accidently and now I want my software center to install the softwares offline from the above mentioned folder.

But now when I click on "Reload" of "Synaptic Package Manager" I get following error message:

[COLOR=Red]**Could not download all repository indexes**
**the repository may no longer be available or could not be contacted because of network problems. if available an older version of failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct**.[/COLOR]

and after clicking close button I get another error message:
[B]
[COLOR=Red]E:could not get lock /var/lib/apt/lists/lock-open(11:Resource temporarily unavailable)
E:Unable to lock the list directory[/COLOR][/B]

my ubuntu pc does not have internet access and its sources.list does not contain anyother lines except what that is mentioned and that is entered by me as I deleted the old data accidently and I remember that there was only one line at that time in my sources.list.

---

### Post by progammer on 2011-08-07
Problem solved

The packages were in "/var/www/debian" and then found "lenny"(SuiteCodename) from my dist folder of "/var/ww/debian"

and in lenny there were two other folders "main" and "contrib"

then I added these lines to my sources.list

deb file:///var/www/debian lenny main contrib
deb-src file:///var/www/debian lenny main contrib

save it and restart your computer. Then go to System->Administration->Synaptic Package Manager

Once the window appear click on reload button. Now go to your Software Center and you have all your softwares offline.

---

