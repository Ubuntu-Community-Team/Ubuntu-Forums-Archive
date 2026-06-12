---
title: "So is 8.10 just completely forgotten now?"
date: 2010-11-12
forum: General Help
---

### Post by jonsayer on 2010-11-12
So I work at a small non-profit, online-only newspaper. I installed Ubuntu 8.10 a while back on some of our editors computer's. I picked 8.10 because it was the last version that I found to be able to support generic Intel graphics cards (which our crappy old machines have). I'm having a problem where none of these machines can install new packages. 

- I am unable to download many if not all packages from repositories
- I am unable to install some .deb packages downloaded from the Web
- I am unable to update programs
- I am unable to upgrade to 9.04

This is happening on all of our Ubuntu 8.10 machines. It only started happening in the last week or so.

See the image below to witness the horrible mess that occurs when I try to upgrade.   

[http://crosscut.com/static/static_file/2010/11/12/Screenshot.png](http://crosscut.com/static/static_file/2010/11/12/Screenshot.png)

I'm not an expert, but** it seems to me that because 8.10 is no longer supported, Canonical decided to pull the repositories. ** If this is so, what can I do to make these machines operational again? Is there an unofficial place I can point my software sources lists to? Should I just give up and wipe out these machines with clean installs of 10.10?

I'd like to keep using 8.10 if at all possible.

---

### Post by kostkon on 2010-11-12
Just point your softwares sources to this url:
```
http://old-releases.ubuntu.com/
```
but, generally, it's not recommended to use unsupported versions since you aren't going to get any security updates (very important imho, especially for business pcs).

Nevertheless, check [this ubuntu wiki page]("https://help.ubuntu.com/community/EOLUpgrades") for help on how to upgrade to 9.04 (and then to 9.10 etc., because 9.04 too became EOL 2-3 weeks ago).

---

### Post by mister_playboy on 2010-11-12
> **kostkon said:**
> Just point your softwares sources to this url:
```
http://old-releases.ubuntu.com/
```

When looking through the directory tree there, I see no mention of 8.10. :confused:

I would suggest using 10.04 as it is a Long Term Support release and is supported until April 2013.  Using 8.10 in a business enviroment at this point seems inappropriate.

---

### Post by cgroza on 2010-11-12
8.10 is a dead now. Go with 10.04 , a long support version. You get 3 years of updates for desktop and 5 years for server.

---

### Post by hawthornso23 on 2010-11-12
Go with 10.04. No chance of proprietary drivers working but the free drivers are fine. If you were in a business where high end 3D graphics mattered then you would have better graphics hardware.

---

### Post by dcstar on 2010-11-12
> **jonsayer said:**
> 
.........
I'm not an expert, but** it seems to me that because 8.10 is no longer supported, Canonical decided to pull the repositories. ** If this is so, what can I do to make these machines operational again?
.........


The machines will always remain "operational", they will not have any repositories to use because unsupported versions (like 8.10) are security risks because they are not maintained and there is no point wasting repository space on them.

As soon as an Ubuntu version reaches End Of Life its repositories are removed, for people who want longer life cycles of releases then LTS releases exist for just that scenario.

---

### Post by jonsayer on 2010-11-13
> **mister_playboy said:**
> When looking through the directory tree there, I see no mention of 8.10. :confused:

Yeah, I looked too and that is what I found. 

I'm going to try to repoint the repositories on monday, but if they don't work, I'll probably just ask the editors to save their files, wipe the machines and install 10.04, which is disappointing I guess, but oh well. 

I wouldn't care about the intel driver thing if it didn't mean instability. I used 9.04 for close to year and the whole thing was a junky mess. I settled on 8.10 as my favorite version and completely forgot that there was a time limit.

---

