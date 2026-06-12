---
title: "adding new ppa's problem"
date: 2012-05-29
forum: General Help
---

### Post by qlum on 2012-05-29
I don't know when it happened, it could have happened anywhere in my updating course from 10.4 to 12.4 as its an htpc I don't really need to add more software. However now I do and I can't seem to add ppa's through console, gives an error when I do that, When I cannot open software sources to add it manually as it crashes when I do that. Anyone know a fix for this?

---

### Post by 2F4U on 2012-05-29
Can you provide the exact command that you use and the error message you get?

---

### Post by qlum on 2012-05-29
very well:```
root@htpc-XBMC:~# sudo add-apt-repository ppa:team-xbmc
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 8, in <module>
    from softwareproperties.SoftwareProperties import SoftwareProperties
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 53, in <module>
    from ppa import AddPPASigningKeyThread, expand_ppa_line
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 27, in <module>
    import pycurl
ImportError: librtmp.so.0: cannot open shared object file: No such file or directory


```

---

### Post by qlum on 2012-05-30
anyone?

---

### Post by dniMretsaM on 2012-05-30
> **qlum said:**
> anyone?

Why are you logged in as [FONT=Courier New]root[/FONT] and running the command with [FONT=Courier New]sudo[/FONT]? I don't know if that's causing your problem or not. Try logging in as a normal user and trying to add it from there (note that this forum doesn't support logging in as[FONT=Courier New][FONT=Verdana] [/FONT]root[/FONT] on Ubuntu).

---

### Post by qlum on 2012-05-30
> **dniMretsaM said:**
> Why are you logged in as [FONT=Courier New]root[/FONT] and running the command with sudo?
basically my htpc logs into xbmc on its own and I didn't notice being root already, sudo is just something I am so used to type anyway's that I did it here as well, I never heard of it causing any problems and I logged and had unity as desktop at some point as well, without being root from the start so that can't be the issue.

---

### Post by dniMretsaM on 2012-05-30
Ok. You can add the repo directly to your sources list. On the PPA launchpad page, click on the "> Technical details about this PPA" button to see what to add to [FONT=Courier New]/etc/apt/sources.list[/FONT].

---

### Post by plucky on 2012-05-30
> sudo add-apt-repository ppa:team-xbmc


From [Here](https://launchpad.net/~team-xbmc/+archive/ppa)

The command should be ```
sudo add-apt-repository ppa:team-xbmc/ppa
```

Just tried it on 12.04 and it worked.

Good Luck

---

### Post by dniMretsaM on 2012-05-30
> **plucky said:**
> From [Here]("https://launchpad.net/%7Eteam-xbmc/+archive/ppa")

The command should be ```
sudo add-apt-repository ppa:team-xbmc/ppa
```Just tried it on 12.04 and it worked.

Good Luck

Good catch. Can't believe I missed that.

---

### Post by qlum on 2012-05-30
well adding manually did infact work, and I copied it from the wiki at first so I doubt what you posted was it. anyway, thanks. 

I am going to reinstall anyway due to some other issues concerning xbmc

---

