---
title: "Limewire can find my installed JRE"
date: 2006-01-24
forum: General Help
---

### Post by k_smolka on 2006-01-24
i have java installed and i have been using java on other applications.

When i go to install lime wire i get the following message saying limewire can not find my jre.

OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com) [java = Error:]
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)


But my jre is installed and working

How do i go about letting limewire know where my jre is located

Thanks in advance

Karl

---

### Post by SSTwinrova on 2006-01-24
It appears to want the JRE in specific places, so possibly creaing symlinks could solve the issue?

---

### Post by njzillest on 2006-01-25
You can install JRE via automatix. Search the forums or a search engine for it. Automatix also installs if you wish frost wire, it is exacly the same as limewire and it connects to the gnutella network.

---

### Post by Pablo_Escobar on 2006-01-25
You can do
> sudo update-alternatives --config java

and select the java version you want.
(I'd recommend getting a sun 1.5 version from the PLF repos)

---

### Post by Who on 2006-01-25
[http://ubuntuguide.org/#limewire](http://ubuntuguide.org/#limewire) explains how to do this for Hoary - I used the same instructions for breezy and it worked OK.

Who

---

