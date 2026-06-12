---
title: "More on Charset encoding - Dapper"
date: 2006-05-31
forum: General Help
---

### Post by viz_e on 2006-05-31
After having updated Breezy to Dapper (and also after a fresh install), some people had troubles with the charset and locale stuff. Here I would like to summarize my experience and call for help... Indeed this is a *major* trouble for non-english users.

During the installation I chose a English setup and "swiss-residence". locale on bash reports all the settings to en_US utf8. If I use special characters as accents, dieresis and so on, everything seems to work fine.

* If I try to mount a Windows partition via Samba (using all suggestions found on this board), the special characters are not correctly displayed (a ?-mark within a box). Here it is an example of the tried fstab line:
```

//txxx/user /home/xxx/directory smbfs credentials=/home/xxx/.smbpasswd,users,noauto,iocharset=iso-8859-1 0 0

```
Opening a file with kate and setting ISO-8859-1 encoding the file is properly displayed. Same problem with files imported via subversion.

* Playing a bit with locale stuff and setting either de_CH.ISO-8859-1 or en_US.ISO-8859-1 (making sure they are generated) I get the famous error:
```

locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US
LANGUAGE=en_US:en_GB:en
LC_CTYPE="en_US"
LC_NUMERIC="en_US"
LC_TIME="en_US"
LC_COLLATE="en_US"
LC_MONETARY="en_US"
LC_MESSAGES="en_US"
LC_PAPER="en_US"
LC_NAME="en_US"
LC_ADDRESS="en_US"
LC_TELEPHONE="en_US"
LC_MEASUREMENT="en_US"
LC_IDENTIFICATION="en_US"
LC_ALL=

```

Note also that the .ISO-8859-1 tag is not present. After a reboot the special characters are displayed in a very fancy way, like "erklï¿½e". Here kate recognizes that the encoding is ISO-8859-1.

The questions are now:
* How can I avoid the "locale" errors?
* More important: how do I get the special characters displayed properly (pdflatex and so on does not work otherwise)?
* Is this going to be fixed before the final release?

Dapper has a lot of nice features, but it did a lot of steps backwards since breezy, like encoding support, codec support and so on. That is sad, because I am a kubuntu-fan ;)

---

### Post by uantuzri on 2007-02-03
I know it's been a long time since your post, but I have just solved the same issue and it might be helpful for anyone who reads this. 

Go to terminal and type this:

```
cd /usr/lib/locale

sudo ln -s es_ES.utf8 es_ES
```

changing the es_ES to your locale settings (en_GB, pt_BZ, or whatever)

---

