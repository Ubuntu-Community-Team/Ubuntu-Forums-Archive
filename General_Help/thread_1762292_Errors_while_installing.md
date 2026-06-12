---
title: "Errors while installing??"
date: 2011-05-19
forum: General Help
---

### Post by ambdeep on 2011-05-19
Every time i try and install anything, i keep getting this error.
I have already tried:
```
sudo apt-get install -f
sudo dpkg --configure -a
```
Please help.
```
ambdeep@Amber:~$ sudo dpkg --configure -a
sudo: unable to resolve host Amber
Setting up gconf2 (2.32.2-0ubuntu2) ...
/usr/share/gconf/schemas/bin-rm_thumb.schemas:53: parser error : Premature end of data in tag schemalist line 2

^
/usr/share/gconf/schemas/bin-rm_thumb.schemas:53: parser error : Premature end of data in tag gconfschemafile line 1

^
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gconf-editor:
 gconf-editor depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gconf-editor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gecko-mediaplayer:
 gecko-mediaplayer depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gecko-mediaplayer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgweather-common:
 libgweather-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgweather-common (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gconf2
 gconf-editor
 apturl
 gecko-mediaplayer
 libgweather-common

```

---

### Post by lmarmisa on 2011-05-19
I read this warning:
```

sudo: unable to resolve host Amber

```

Try to change the Ubuntu software source. Select System -> Admin -> Synaptic -> Settings -> Repositories -> Download from. After that, try Reload.

---

### Post by ambdeep on 2011-05-19
the warning was there ever since i upgraded to 11.04. but the installation error is new.

---

### Post by wildmanne39 on 2011-05-19
> **ambdeep said:**
> Every time i try and install anything, i keep getting this error.
I have already tried:
```
sudo apt-get install -f
sudo dpkg --configure -a
```
Please help.
```
ambdeep@Amber:~$ sudo dpkg --configure -a
sudo: unable to resolve host Amber
Setting up gconf2 (2.32.2-0ubuntu2) ...
/usr/share/gconf/schemas/bin-rm_thumb.schemas:53: parser error : Premature end of data in tag schemalist line 2

^
/usr/share/gconf/schemas/bin-rm_thumb.schemas:53: parser error : Premature end of data in tag gconfschemafile line 1

^
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gconf-editor:
 gconf-editor depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gconf-editor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gecko-mediaplayer:
 gecko-mediaplayer depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gecko-mediaplayer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgweather-common:
 libgweather-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgweather-common (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gconf2
 gconf-editor
 apturl
 gecko-mediaplayer
 libgweather-common

```
Hi, the command should be
sudo apt-get -f install

---

### Post by ambdeep on 2011-05-19
> **wildmanne39 said:**
> Hi, the command should be
sudo apt-get -f install
still no change. someone please help.

---

### Post by ambdeep on 2011-05-19
Ok...I found the solution. The following line was giving a problem:
```
/usr/share/gconf/schemas/bin-rm_thumb.schemas:53: parser error : Premature end of data in tag schemalist line 2

```
So i just removed it by typing:
```
sudo rm /usr/share/gconf/schemas/bin-rm_thumb.schemas
```
Then I reinstalled gconf2.

---

