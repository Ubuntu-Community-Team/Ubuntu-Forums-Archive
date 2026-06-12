---
title: "ftp://site bookmarked under places, opens in firefox instead of nautilus"
date: 2011-09-10
forum: General Help
---

### Post by xecure on 2011-09-10
Hi guys,

This should be a simple fix but I'm not sure how to change the default program to open a ftp:// link. I've added my web server under places and was expecting a nautilus window to pop open showing my files on the server but instead the file opens on firefox. I read somewhere to edit my ~\.gconf\desktop\gnome\url-handlers\ftp\%gconf.xml file but on my machine the \ftp\ directory doesn't exist at all. So I created a ftp directory with this in my %gconf.xml file:

```
<?xml version="1.0"?>
<gconf>
        <entry name="needs_terminal" mtime="1264151220" type="bool" value="false"/>
        <entry name="enabled" mtime="1264151220" type="bool" value="true"/>
        <entry name="command" mtime="1264151220" type="string">
                <stringvalue>/usr/bin/nautilus</stringvalue>
        </entry>
</gconf>
```

Still no luck, any ideas?

---

### Post by haqking on 2011-09-10
> **xecure said:**
> Hi guys,

This should be a simple fix but I'm not sure how to change the default program to open a ftp:// link. I've added my web server under places and was expecting a nautilus window to pop open showing my files on the server but instead the file opens on firefox. I read somewhere to edit my ~\.gconf\desktop\gnome\url-handlers\ftp\%gconf.xml file but on my machine the \ftp\ directory doesn't exist at all. So I created a ftp directory with this in my %gconf.xml file:

```
<?xml version="1.0"?>
<gconf>
        <entry name="needs_terminal" mtime="1264151220" type="bool" value="false"/>
        <entry name="enabled" mtime="1264151220" type="bool" value="true"/>
        <entry name="command" mtime="1264151220" type="string">
                <stringvalue>/usr/bin/nautilus</stringvalue>
        </entry>
</gconf>
```Still no luck, any ideas?

alt+f2

gconf-editor

desktop -> gnome -> url-handlers and find the entry for FTP and change firefox to nautilus

---

### Post by xecure on 2011-09-11
Hmm, Nautilus is already set as my default program to open ftp:// links. But my server still initially opens in firefox (when I click on my server from places, but if I click it from an already opened nautilus window it opens in a nautilus window)


Any other ideas?

---

### Post by xecure on 2011-09-17
bump

---

### Post by haqking on 2011-09-17
> **xecure said:**
> bump

it appears it may be a bug, you will have to do a little more research on it though.

[https://bugs.archlinux.org/task/23564](https://bugs.archlinux.org/task/23564)

this is from arch, but still the same issue you are having

and an old launchpad bug for Ubuntu [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/196202](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/196202)

edi: try this maybe ? [http://radu.cotescu.com/how-to-set-nautilus-as-default-ftp-application/ ]("http://radu.cotescu.com/how-to-set-nautilus-as-default-ftp-application/")

[s]i think its the same as i orginally said with gconf-editor but there is a section at bottom about with 11.04 and i dont know what verions you are using[/s] i guess thats the same as your OP

---

