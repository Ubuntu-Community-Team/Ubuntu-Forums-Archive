---
title: "OpenBravo ppa for 12.04"
date: 2012-05-14
forum: General Help
---

### Post by Yumi on 2012-05-14
I am looking for the ppa to install Openbravo 3.0 on Ubuntu 12.04

Thanks
Michael

---

### Post by PhantomTurtle on 2012-05-14
From the openbravo download page:
> Ubuntu installation
Openbravo is included in the Ubuntu partner repository, so that you can add the software quickly and easily to your Ubuntu server. Follow this installation guide. (source: [http://wiki.openbravo.com/wiki/Installation/Ubuntu]("http://wiki.openbravo.com/wiki/Installation/Ubuntu"))

The guide is at - [http://wiki.openbravo.com/wiki/Installation/Ubuntu]("http://wiki.openbravo.com/wiki/Installation/Ubuntu")

EDIT: Oh it seems the guide uses a ppa made by them, even though the install site says its in the partner repo's. Well then here are the instructions:
```
sudo add-apt-repository ppa:openbravo-isv/ppa
sudo apt-get update
sudo apt-get install openbravo-3
```

---

### Post by Yumi on 2012-05-14
Thanks for the quick reply. But "sudo add-apt-repository ppa:openbravo-isv/ppa" returns "Supported releases for Openbravo 3: Lucid, Natty, Oneiric
".

Means that I have to wait until ....

Michael

---

### Post by PhantomTurtle on 2012-05-14
You can still and the ppa and see if it will install on precise. To do this you have to open your sources.list file with root privileges(sudo) and add these two lines to it,
```
deb http://ppa.launchpad.net/openbravo-isv/ppa/ubuntu oneiric main 
deb-src http://ppa.launchpad.net/openbravo-isv/ppa/ubuntu oneiric main 
```
This will of course install the oneric version which shouldn't cause a problem, but I could be wrong. I have done this before(with a different ppa) and it worked fine so you could try that. After that you just run,
```
sudo apt-get update
sudo apt-get install openbravo-3
```
And that should work. If it doesn't just remove it and wait for the precise release.

---

### Post by Yumi on 2012-05-19
Still no precise ppa

Oneiric version does not work under 12.04 as described in this threat: [URL="http://ubuntuforums.org/showthread.php?t=1969973"/URL]

---

### Post by PhantomTurtle on 2012-05-19
> **Yumi said:**
> Still no precise ppa

Oneiric version does not work under 12.04 as described in this threat: [URL="http://ubuntuforums.org/showthread.php?t=1969973"/URL]

Openbravo 3 is available as a vmachine for virtualbox if it is urgent for you. You could try it if you really really need it right now(its on the downloads page).

---

### Post by Yumi on 2012-05-31
Disregard this post. I mistook oneiric for precise. Precise is still not available


Openbravo ppa for 12.04 precise is now available
sudo add-apt-repository ppa:openbravo-isv/ppa

Hope it works. I will report.

---

### Post by Yumi on 2012-06-04
Does anybody know if OpenBravo will be available under Precise 12.04?

Michael

---

### Post by PhantomTurtle on 2012-06-05
> **Yumi said:**
> Does anybody know if OpenBravo will be available under Precise 12.04?

Michael

I was looking at the ppa, there was no precise verion available. However since this is a Long term support release, therefore it will most likely be supported. I'm sure that soon they will have a precise version in their ppa.

---

### Post by Yumi on 2012-06-06
How do people cope who use OpenBravo and upgraded to 12.04 Precise? Are they left with a unusable ERP?

I installed OpenBrave in 11.04 but found it too complex to set up at the time. Now I regred it and want to have another go.

Michael

---

### Post by mastablasta on 2012-06-06
they would use LTS and not upgrade until .1 LTS is out (which is a bit later in the year)
10.04 LTS is still supported until 2013.
adidtionally if one uses 11.04 or 11.10 they too are still supported. 11.04 until Oct 2012 and 11.10 until april 2013.

---

### Post by dmezentsev on 2012-10-03
Hello All,

I would like to give official Openbravo summary to this post.

1. Here is the list of Ubuntu releases Openbravo supports
Ubuntu version 10.04 (Lucid Lynx)
Ubuntu version 11.04 (Natty Narwhal)
Ubuntu version 11.10 (Oneiric Ocelot)
[http://wiki.openbravo.com/wiki/Installation/Ubuntu#Software](http://wiki.openbravo.com/wiki/Installation/Ubuntu#Software)

2. >10.04 LTS is still supported until 2013.
10.04 is indeed LTS but as we are talking about server side application so we need to refer to Ubuntu Server LTS which has 5 years of support so will be supported till the 04.15.
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)
So 10.04 LTS and Openbravo package for it is the recommended configuration for Ubuntu productions installation.

3. We are working on the 12.04 support. Our current plan is to have it in the middle of October.
[http://wiki.openbravo.com/wiki/Openbravo_ERP_roadmap#Usability_and_Platform](http://wiki.openbravo.com/wiki/Openbravo_ERP_roadmap#Usability_and_Platform), see Deployment Options.
But maybe we would delay it a month or so if we decide this package to be based on PostgreSQL 9.1 instead of 8.4

Hope it helps.
We will update this thread when Openbravo package for 12.04 is released.

---

### Post by hennotaht on 2012-10-17
How is the precise version coming along?

---

### Post by accumbare on 2012-11-23
Any news about a version of openbravo for ubuntu 12.04? I would really like to test it, but I do not want to downgrade my server..

---

### Post by PhantomTurtle on 2012-11-23
> **accumbare said:**
> Any news about a version of openbravo for ubuntu 12.04? I would really like to test it, but I do not want to downgrade my server..

The OpenBravo PPA has still not updated for a Precise(12.04) or Quantal(12.10) and their Wiki has not been updated either. That means that so far, no OpenBravo for 12.04 or higher users.

---

### Post by hotdancing on 2013-02-19
yeah. I've installed successfully at 12.04.
so thanks.

---

### Post by sangramanand on 2013-04-04
Adding to sources.list works.  One question i have is, does it install tomcat, postgressql, etc., along with  openbravo-3 installation?

> **PhantomTurtle said:**
> From the openbravo download page:
 (source: [http://wiki.openbravo.com/wiki/Installation/Ubuntu](http://wiki.openbravo.com/wiki/Installation/Ubuntu))

The guide is at - [http://wiki.openbravo.com/wiki/Installation/Ubuntu](http://wiki.openbravo.com/wiki/Installation/Ubuntu)

EDIT: Oh it seems the guide uses a ppa made by them, even though the install site says its in the partner repo's. Well then here are the instructions:
```
sudo add-apt-repository ppa:openbravo-isv/ppa
sudo apt-get update
sudo apt-get install openbravo-3
```

---

