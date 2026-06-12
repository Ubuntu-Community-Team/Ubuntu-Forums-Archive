---
title: "apt-get updates are broken"
date: 2012-08-29
forum: General Help
---

### Post by fubar42 on 2012-08-29
Apologies for newbie question - all attempts to apt-get update / dist-upgrade are failing in New Zealand. This has been the case for about two weeks now. It happens on all three of my Ubuntu machines.
I've edited out the normal looking output from apt-get update, please advise.

Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/multiverse Sources
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/multiverse amd64 Packages
  502  Proxy Error ( The Uniform Resource Locator (URL) does not use a recognized protocol. Either the protocol is not supported or the request was not typed correctly. Confirm that a valid protocol is in use (for example, HTTP for a Web request).  )
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/multiverse i386 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/multiverse Sources
  502  Proxy Error ( The Uniform Resource Locator (URL) does not use a recognized protocol. Either the protocol is not supported or the request was not typed correctly. Confirm that a valid protocol is in use (for example, HTTP for a Web request).  )
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/multiverse amd64 Packages
  404  Not Found
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/multiverse i386 Packages
  502  Proxy Error ( The Uniform Resource Locator (URL) does not use a recognized protocol. Either the protocol is not supported or the request was not typed correctly. Confirm that a valid protocol is in use (for example, HTTP for a Web request).  )
...
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages
  404  Not Found
...
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
  404  Not Found [IP: 91.189.92.190 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages
  502  Proxy Error ( The Uniform Resource Locator (URL) does not use a recognized protocol. Either the protocol is not supported or the request was not typed correctly. Confirm that a valid protocol is in use (for example, HTTP for a Web request).  ) [IP: 91.189.92.190 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
  404  Not Found [IP: 91.189.92.190 80]
... 
Fetched 18.9 kB in 8s (2,272 B/s)
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages)  502  Proxy Error ( The Uniform Resource Locator (URL) does not use a recognized protocol. Either the protocol is not supported or the request was not typed correctly. Confirm that a valid protocol is in use (for example, HTTP for a Web request).  )

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  404  Not Found

---

### Post by Bashing-om on 2012-08-29
fubar42;

  HI !

  Is updating the only problem with your internet connection. I mean you are able to surf normally ? 3 machines can not update?

If so the only thing I can think of is terminal server (mirror) problems.
not discounting in-house configurations on a LAN (ping outside destinations ?)

What happens when you try to change your source mirror in the "software sources"  utility?

[INDENT]BDQ
[/INDENT]

---

### Post by fubar42 on 2012-08-29
Hi,
One of the Ubuntu machines is a laptop, and I get the same behaviour at home and in the office. All other internet activity is normal in both locations.
I did try changing all "nz." archive locations to the corresponding "au." but the same thing happens.

---

### Post by fubar42 on 2012-09-01
Anybody have any ideas how to get this fixed? Over three weeks now and updates are broken. 2 workstations and a server all show the same symptoms.

---

