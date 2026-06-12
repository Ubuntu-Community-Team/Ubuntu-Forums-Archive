---
title: "Authenticated proxy problem"
date: 2012-08-02
forum: General Help
---

### Post by MrDogbert on 2012-08-02
I cannot get updates or installs via the terminal etc because I keep getting messages like:

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  407  Proxy Authentication Required

I have done all the things you are supposed to do.

I have put the settings in Network Settings and clicked 'Apply System Wide'.

As my username is DOMAIN\Name I was told to change this to DOMAIN%5CName but neither works.

I have also put:

Acquire::http::proxy "http://DOMAIN%5CName:Password@10.1.2.52:3128/"; 
Acquire::https::proxy  "http://DOMAIN%5CName:Password@10.1.2.52:3128/"; 
Acquire::ftp::proxy "ftp://DOMAIN%5CName:Password@10.1.2.52:3128/"; 
Acquire::socks::proxy "socks://DOMAIN%5CName:Password@10.1.2.52:3128/"; 

in apt.conf.

And also

export http_proxy=http://DOMAIN%5CName:Password@10.1.2.52:3128/
export https_proxy=http://DOMAIN%5CName:Password@10.1.2.52:3128/
export ftp_proxy=http://DOMAIN%5CName:Password@10.1.2.52:3128/

in .bashrc.

Still nothing works.

Any ideas? I'm getting bored and annoyed with this.

Cheers

---

### Post by raja.genupula on 2012-08-02
[www.youtube.com/watch?v=zhkpmPK4GdE](www.youtube.com/watch?v=zhkpmPK4GdE)

see that video . its belongs to your issue .

---

### Post by MrDogbert on 2012-08-02
> **raja.genupula said:**
> [www.youtube.com/watch?v=zhkpmPK4GdE]("http://www.youtube.com/watch?v=zhkpmPK4GdE")

see that video . its belongs to your issue .

As I said, I tried this and it hasn't worked.

---

### Post by cortman on 2012-08-02
Try this.

Comment out everything in apt.conf and close any open terminals you havve. Open up ~/.bashrc in a text editor.
Add this line to the bottom:

```
http_proxy=http://username:password@yourproxyaddress:proxyport
```
Save, open a new terminal, and try running apt-get.

---

