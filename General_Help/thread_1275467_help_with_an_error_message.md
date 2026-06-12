---
title: "help with an error message"
date: 2009-09-25
forum: General Help
---

### Post by Z06Gal on 2009-09-25
My synaptic is not working and I am getting this message:

E: Malformed line 1 in source list /etc/apt/sources.list.d/chromium.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


I uninstalled chromium but still get this.  Can someone help me out with this?  Thanks.

---

### Post by clonne4crw on 2009-09-25
When you removed the package, did you purge it and everything that came with it? 

```
# apt-get purge (package name)
```

and

```
# apt-get autoclean
```

---

### Post by Z06Gal on 2009-09-25
> **clonne4crw said:**
> When you removed the package, did you purge it and everything that came with it? 

```
# apt-get purge (package name)
```

and

```
# apt-get autoclean
```


I uninstalled chromium and then it gave me a command to completely uninstall.  I did that.  Nothing more.  Thanks.

---

### Post by Z06Gal on 2009-09-25
Here is my entire file if it will help someone figure this out:


## -----------------------
## LINUX MINT REPOSITORIES
## -----------------------

## +++ Linux Mint 7 Gloria (stable) +++
#deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria main upstream import

## +++ Backports (not as stable) +++
#deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria backport

## +++ Community (not as stable) +++
#deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria community

## +++ Romeo (unstable) +++
#deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria romeo

## +++ Source Repositories +++
#deb-src [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria main upstream import
#deb-src [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria community
#deb-src [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria backport
#deb-src [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria romeo

## -------------------
## UBUNTU REPOSITORIES
## -------------------

## +++ Ubuntu 9.04 Jaunty (stable) +++
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security main restricted universe multiverse

## +++ Backports & Proposed (not as stable) +++
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-proposed main restricted universe multiverse

## +++ Source Repositories +++
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse
#deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-proposed main restricted universe multiverse

## ------------------
## OTHER REPOSITORIES
## ------------------

## +++ Canonical (stable) +++
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) jaunty partner

## +++ Medibuntu (stable) +++
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

---

### Post by Z06Gal on 2009-09-25
ok i searched this forum and now understand that i have to change that first line but i don't know what to change it to.  anybody?  thanks. :popcorn:

---

### Post by Z06Gal on 2009-09-25
anybody?

---

### Post by clonne4crw on 2009-09-25
Hmph. Sorry to say that this beats me as well...

IMO, it looks like the sources.list file's clean, but it looks like theres also the ./sources.list.d directory containing chromium.list.

See what happens when you rename the chromium.list file to something else. I don't use Chromium right now, so I couldn't say anything for sure.

---

### Post by Z06Gal on 2009-09-26
ttt

---

### Post by Z06Gal on 2009-09-26
nobody?

---

### Post by TheCelloFellow on 2009-09-26
Can you post or attach your /etc/apt/sources.list.d/chromium.list file? That particular error means there's some kind of syntax error in that particular file.

For the record, the sources.list.d directory is so you can break your sources.list file into several files (.d generally means breaking one config file into a directory of config files). This is especially useful when you can install a deb package or run a script that places something into your apt sources.

So post that file and we'll have you fixed up in no time.

---

### Post by Z06Gal on 2009-09-26
So are you referring to something different than what I posted above?  Not sure what you mean.  Thank you for your help.  This is driving me nuts.

---

### Post by Z06Gal on 2009-09-26
I typed that command in terminal and it says no such file or directory.

---

### Post by TheCelloFellow on 2009-09-26
The error message you put in your original post references the file /etc/apt/sources.list.d/chromium.list. If that files doesn't exist anymore than there shouldn't be any more errors and you can go about your business (sans Chromium, of course).

Still, for future reference that error message will tell you the line and file that has a bad apt source in it. So, next time that happens quickly check the file and make sure the line starts with either "deb" or "deb-src". The most common error is when the line starts with something else.

---

### Post by Z06Gal on 2009-09-26
What do I need to do about synaptic?  It won't allow me to do anything.  That message keeps coming up when I attempt to start it.  Thanks so much for your help.

---

### Post by TheCelloFellow on 2009-09-26
What precisely is the error message you are getting in Synaptic? Do you get error messages using apt-get or aptitude?

Seems to me that there is still something odd going on in you [FONT="Courier New"]/etc/apt/sources.list{,.d/*}[/FONT] files.

---

### Post by Z06Gal on 2009-09-26
this is what keeps coming up:


E: Malformed line 1 in source list /etc/apt/sources.list.d/chromium.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by TheCelloFellow on 2009-09-26
Ok, can you please post the contents of /etc/apt/sources.list.d/chromium.list?

And if that file does not exist, then just run "sudo aptitude update" and post the output from that.

---

### Post by Z06Gal on 2009-09-26
E: Malformed line 1 in source list /etc/apt/sources.list.d/chromium.list (dist parse)
E: Malformed line 1 in source list /etc/apt/sources.list.d/chromium.list (dist parse)
E: The list of sources could not be read.
E: Malformed line 1 in source list /etc/apt/sources.list.d/chromium.list (dist parse)
E: The list of sources could not be read.
E: Malformed line 1 in source list /etc/apt/sources.list.d/chromium.list (dist parse)
E: Couldn't read list of package sources

---

### Post by Z06Gal on 2009-09-26
i meant to post this too if it will help you.  thanks so much for trying to help me out with this. 


## -----------------------
## LINUX MINT REPOSITORIES
## -----------------------

## +++ Linux Mint 7 Gloria (stable) +++
#deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria main upstream import

## +++ Backports (not as stable) +++
#deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria backport

## +++ Community (not as stable) +++
#deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria community

## +++ Romeo (unstable) +++
#deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria romeo

## +++ Source Repositories +++
#deb-src [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria main upstream import
#deb-src [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria community
#deb-src [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria backport
#deb-src [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria romeo

## -------------------
## UBUNTU REPOSITORIES
## -------------------

## +++ Ubuntu 9.04 Jaunty (stable) +++
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security main restricted universe multiverse

## +++ Backports & Proposed (not as stable) +++
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-proposed main restricted universe multiverse

## +++ Source Repositories +++
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse
#deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-proposed main restricted universe multiverse

## ------------------
## OTHER REPOSITORIES
## ------------------

## +++ Canonical (stable) +++
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) jaunty partner

## +++ Medibuntu (stable) +++
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

---

### Post by TheCelloFellow on 2009-09-26
That's /etc/apt/sources.list. I need to see /etc/apt/sources.list.d/chromium.list.

That's the file generating the error. It wouldn't be causing an error if it wasn't there. If it's not there but still causing an error... well that is just illogical.

---

### Post by Z06Gal on 2009-09-26
ok it says permission denied.  is there a way around that?

---

### Post by TheCelloFellow on 2009-09-26
oh, hmm. What does `ls -l /etc/apt/sources.list.d/` show?

---

### Post by Z06Gal on 2009-09-26
The program 'total' is currently not installed.  You can install it by typing:
apt-get install radiance
bash: total: command not found

---

### Post by TheCelloFellow on 2009-09-26
You didn't type that in with the quotes, did you? I got that same output when I included the backtick quotes.

Maybe I shouldn't use backtick quotes...

---

### Post by Z06Gal on 2009-09-26
lol..i sure did.  i didnt' even notice that.  anyway here is what came up:

total 12
-rw-r--r-- 1 root root  86 2009-09-25 18:30 chromium.list
-rw-r--r-- 1 root root  48 2009-09-25 18:25 google-chrome.list
-rw-r--r-- 1 root root 353 2009-09-25 14:55 opera.list

---

### Post by TheCelloFellow on 2009-09-26
ok, those permissions seem right (they match mine). You should be able to open the chromium.list file with this command

gksudo gedit /etc/apt/sources.list.d/chromium.list

---

### Post by Z06Gal on 2009-09-26
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(gksudo:30434): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(gedit:30435): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported

---

### Post by TheCelloFellow on 2009-09-26
Ok, that's a different issue for a different thread.

sudo cat /etc/apt/sources.list.d/chromium.list

and post the output

---

### Post by Z06Gal on 2009-09-26
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty 
main #chromium-browser

---

### Post by TheCelloFellow on 2009-09-26
ah, that should all be one line. modify the file like this:

echo "deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main #chromium-browser" | sudo tee /etc/apt/sources.list.d/chromium.list

That should all be one line.

The run "sudo apt-get update" and all should be well.

---

### Post by Z06Gal on 2009-09-26
is that for line 1 or where?

---

### Post by TheCelloFellow on 2009-09-26
That command I gave you will completely overwrite the chromium.list file with a properly formatted file. What probably happened is that you editted that file with a text editor like nano that does hard wrapping, meaning that it adds newline characters when your line of text reaches the edge of the terminal. That is very likely to mess things up. This echo | tee way won't do that.

---

### Post by Z06Gal on 2009-09-26
got it!!  thank you so much for your time and help! :)

---

### Post by TheCelloFellow on 2009-09-26
Very glad to be of service. :D

---

