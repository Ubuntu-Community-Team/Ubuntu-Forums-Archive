---
title: "simple command line gives -  Syntax error: newline unexpected"
date: 2010-06-11
forum: General Help
---

### Post by steamdog on 2010-06-11
Ok I'm new. ... Why do I get an error when trying to do a simple install command?

I'm trying to install VMware player 3.1.0 on Ubuntu 9.10 

After logging in to the terminal and changing directory to the folder containing the VM player bundle file, I used the following command: 

[B]sudo sh VMware-Player-3.1.0-261024.i386.bundle
[/B]
It then prompts me for the password:
**[sudo] password for administrator: **

**After entering the password it then returns the error:**
VMware-Player-3.1.0-261024.i386.bundle: *110: Syntax error: newline unexpected*
administrator@ubuntu:~/Documents/gnb1$

Why? Why? Why?  If I can't find an answer I'm back to Windows after this!

---

### Post by drpjkurian on 2010-06-11
Hi
This is not the command to install the packages

to install the commands are 
```
make && make install
```

See this [link]("http://http://www.wikihow.com/Install-Software-in-Ubuntu")

Why cant you try add remove programmes or synaptic package manager

---

### Post by donato roque on 2010-06-12
Thank you drpjkurian, in behalf of the original poster.

---

### Post by chayzer on 2010-06-12
Make sure the bundle file is ~100MB

Mine installed fine.

---

### Post by drpjkurian on 2010-06-12
> **donato roque said:**
> Thank you drpjkurian, in behalf of the original poster.

Hi
Most welcome

---

### Post by hippi80 on 2010-09-16
**same problom, w**inetricks: 2: Syntax error: newline unexpected

---

### Post by hippi80 on 2010-09-16
**same problom, w**inetricks: 2: Syntax error: newline unexpected    

why ??????   trying to get steam running ....

---

### Post by minglis on 2011-04-07
> **chayzer said:**
> Make sure the bundle file is ~100MB

Mine installed fine.

I originally downloaded VMPlayer with the "Download Manager" on their download page. When I checked the resulting file, it was only ~20MB. I downloaded it again, selecting to download it manually. This time I got the full file. Install worked fine after that.

---

### Post by ahowlett on 2011-04-14
> **minglis said:**
> I originally downloaded VMPlayer with the "Download Manager" on their download page. When I checked the resulting file, it was only ~20MB. I downloaded it again, selecting to download it manually. This time I got the full file. Install worked fine after that.

This works for me- if your "Download Options" is
(*) Use Download Manager (Recommended)
then you will get a 20mb file, unless you have already installed their "Download Manager" application.
If you select
(*) Use Web Browser
then you should get the full file that you are expecting.

---

### Post by LsjLewis on 2011-06-13
Make sure you downloaded the right version...the 64 or 32 bit one
I had the same problem and it worked out fine after I tried installing the 64 bit.
sudo sh VMware-Player-3.1.4-385536.x86_64.bundle
and make sure in the right directory

---

