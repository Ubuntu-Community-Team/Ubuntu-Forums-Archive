---
title: "Help installing Firefox and Thunderbird from &quot;.tar.bz2&quot; files"
date: 2010-03-24
forum: General Help
---

### Post by Deer Hunter on 2010-03-24
Hello all,

I'm actually currently using the Firefox version that came on my Ubuntu 9.10, and the Thunderbird version available from the Software Center; and I don't have any complaints with them, except that I'd like to upgrade to the latest versions.  I've downloaded the latest versions from Mozilla, but when I open these ".tar.bz2" files, I don't know where to go to install them.  Can someone help me on this?  Thanks in advance.

Deer Hunter

---

### Post by pennacook on 2010-03-24
At least with the firefox one, there is a run-mozilla.sh script that runs the browser.

---

### Post by aysiu on 2010-03-24
UbuntuZilla will help.

Simple copy and paste terminal instructions:
[http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

More involved point and click with mouse instructions:
[http://www.psychocats.net/ubuntu/ubuntuzilla](http://www.psychocats.net/ubuntu/ubuntuzilla)

---

### Post by kamaji792 on 2010-03-24
Hi,

For what it is worth.  Here is what I do to run the latest version (from memory).  Assume you have the mozilla download file in folder of your home directory called **Download**, off your home directory.

**Extract the files**
```
cd ~/Download
tar xvjf mozilla-file.tar.bz2
```

**Move the files**
```
sudo mv firefox /opt
```

**Test all is OK**
Open a terminal and enter the following:
```
/opt/firefox/firefox &
```

If it fires up your in business.  Now add a launcher to a Panel or Menu with the **command** set to: **/opt/firefox/firefox %u**

*Don't try and copy the original launcher if you want to use both.  If you copy the launchers they stay linked and when you edit one the other changes :shock:*

Thunderbird only needs **command** set to **/opt/thunderbird/thunderbird**

Not sure what the disadvantages of this are but it seems to work fine for me.  I have several ad-ons running, in fact it seem to happily pick up the ad-ons I had running in the original.

All the best

---

### Post by aysiu on 2010-03-24
> **kamaji792 said:**
> 
Not sure what the disadvantages of this are It's a perfectly legitimate method.

The only advantages UbuntuZilla has over the method you described are: [list][*]Once you've added the UbuntuZilla repository, you can easily install and uninstall the Mozilla builds of Firefox or Thunderbird using Synaptic Package Manager.[*]If a new version of Firefox or Thunderbird comes out later, you can just upgrade via the package manager.[*]Not as much manually linking of files and launchers.[/list]

---

### Post by Deer Hunter on 2010-03-24
> **aysiu said:**
> UbuntuZilla will help.

Simple copy and paste terminal instructions:
[http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

More involved point and click with mouse instructions:
[http://www.psychocats.net/ubuntu/ubuntuzilla](http://www.psychocats.net/ubuntu/ubuntuzilla)


Thank you very much Sir!!

I followed the second link you provided, and everything went great.

Deer Hunter

---

### Post by Easy Limits on 2010-03-24
Worked like a champ for me!  Thanks guys.

---

