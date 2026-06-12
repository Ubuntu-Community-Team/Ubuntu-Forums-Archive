---
title: "About the Jahshaka repository"
date: 2006-06-03
forum: General Help
---

### Post by Amt0571 on 2006-06-03
I want to install Jahshaka and found this repository:
[http://repo.jahshaka.org/ubuntu/dapper/binary-i386/](http://repo.jahshaka.org/ubuntu/dapper/binary-i386/)

But no matter how hard I try, I'm unable to put it the correct way in my sources.list... Synaptic always gives me an error. Can somebody explain me how I should add this repo?


thanks!

---

### Post by bjc on 2006-06-03
Try this:
```

deb http://repo.jahshaka.org/ubuntu/dapper/binary-i386 ./

```

---

### Post by Amt0571 on 2006-06-03
Thanks a lot! it worked perfectly! I finally have Jahshaka up and running!

---

### Post by dangermouse28 on 2006-06-07
Ok, I've tried this - I put in the http address exactly as shown. Jahshska shows up now in Synaptic but when I try to install it I get Error 404 - Not Found. Thinking the website was down or something I went straight over in Firefox and was able to manually download all the files without any problem :-k 
So what am I doing wrong in Synaptic?

---

### Post by Amt0571 on 2006-06-07
Hummm... I don't know... I installed the files manually downloading them as you did, and added the repo in the sources.list later (when bjc told me how to do so).

Anyway, I'll try it later and report if I have success or not :)

---

### Post by Bear Knuckle on 2006-06-15
I am having these errors also:
```
Failed to fetch http://repo.jahshaka.org/ubuntu/dapper/binary-i386[COLOR="Red"]/binary-i386/[/COLOR]/olib-ffmpeg_20060524-1_i386.deb  404 Not Found
Failed to fetch http://repo.jahshaka.org/ubuntu/dapper/binary-i386[COLOR="Red"]/binary-i386/[/COLOR]/olib-mlt_0.2.1-2_i386.deb  404 Not Found
Failed to fetch http://repo.jahshaka.org/ubuntu/dapper/binary-i386[COLOR="Red"]/binary-i386/[/COLOR]/olib-mlt++_0.2.1-1_i386.deb  404 Not Found
Failed to fetch http://repo.jahshaka.org/ubuntu/dapper/binary-i386[COLOR="Red"]/binary-i386/[/COLOR]//openlibraries_0.2.0_i386.deb  404 Not Found
Failed to fetch http://repo.jahshaka.org/ubuntu/dapper/binary-i386[COLOR="Red"]/binary-i386/[/COLOR]/jahshaka_2.0rc3_i386.deb  404 Not Found

```

The URLs are malformed, because the "binary-i386" and a slash are doubled. I am not very familiar with apt and sources.list, but there must be a way to fix this, isn't it?

**edit:** I fixed the problem, the correct line in sources.list is:
```
deb http://repo.jahshaka.org/ubuntu/dapper /binary-i386/
```

---

### Post by transkinetic on 2006-07-06
added the following line to /etc/apt/sources.list
```
deb [http://repo.jahshaka.org/ubuntu/dapper](http://repo.jahshaka.org/ubuntu/dapper) /binary-i386/
```

how do i get past these errors?

```
spacepopeye@spacerig:/etc/apt$ sudo apt-get install jahshaka
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  jahshaka: Depends: openlibraries but it is not going to be installed
            Depends: libopenal0 but it is not going to be installed
            Depends: openlibraries but it is not going to be installed
E: Broken packages

```

---

### Post by mmcmonster on 2006-07-13
The repo is apparently down right now, but the following line should parse correctly, I think...

deb [http://repo.jahshaka.org/ubuntu/dapper](http://repo.jahshaka.org/ubuntu/dapper) binary-i386/

---

### Post by webmadman on 2006-08-04
I'm still getting:

jahshaka:
 Depends: openlibraries but it is not going to be installed
 Depends: libopenal0 but it is not going to be installed
 Depends: openlibraries but it is not going to be installed

I'd really like to have this, played with it back in my Fedora days- it was fun then, and that was a while ago, I imagine it's getting pretty cool by now...

---

### Post by it.henrik on 2006-08-04
[http://www.jahshaka.org/content/view/112/0/](http://www.jahshaka.org/content/view/112/0/)

---

